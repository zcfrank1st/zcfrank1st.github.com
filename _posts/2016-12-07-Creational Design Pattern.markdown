---
layout: post
title:  "Creational Design Pattern"
date:   2016-12-07 20:32:56 +0800
categories: jekyll update
---
### Creational Design Pattern

最近code了点东西，等整理好再写。

关于Creational Design Pattern，我从一本书上摘了一些精华，如下：

`Creational Design Pattern`
    
* **Singleton Pattern**

    >There should be only one instance allowed for a class and we should allow global point of access to that single instance.
    
    better use `Enum`
    
    
* **Factory Pattern**
    >Factory pattern provides approach to code for interface rather than implementation.
    Factory pattern removes the instantiation of actual implementation classes from client code, making it more robust, less coupled and easy to extend.
    Factory pattern provides abstraction between implementation and client classes though inheritance.
    
 
        public interface IMobile {
             public void cost();
             public void pictureCapacity();
             public void batteryPower();
        }
        
        public class Samsung implements IMobile {
            
            @Override
            public void cost() {
                //
            }
            
            @Override
            public void pictureCapacity() {
                //
            }
            
            @Override
            public void batteryPower() {
                //
            }
        }
        
        public class MobileFactory {
            public MobileFactory() {}
            
            IMobile createMobile(String type) {
                IMobile mob = null;
                if ("sam".equalsIgnoreCase(type)){
                    mob = new Samsung();
                }
                
                return mob;
            }
        }

* **Abstract Factory Pattern**

    >Abstract Factory pattern provides approach to code for interface rather than implementation.
    Abstract Factory pattern is “factory of factories” and can be easily extended to accommodate more products.
    Abstract Factory pattern is robust and avoid conditional logic of Factory pattern.
    
        public interface IMobileFactory {
            IMobileFactory createMobile(String type);
        }
        
        public class MobileFactory implements IMobileFactory {
            @Override
            public IMobileFactory createMobile(String type) {
                IMobileFactory mob = null;
                if ("".equalsIgnoreCase(type)) {
                    mob = new SamsungMobileFactory();
                }
                
                return mob;
            }
        }
        
        public class SamsungMobileFactory extends MobileFactory {
            Samsung createSansungMobile() {
                return new Samsung();
            }
        }
        
* **Builder Pattern**

>The intent of the Builder Pattern is to separate the construction of a complex object from its representation, so that the same constriction process can create different representations. This type of separation reduces the object size.The design turns out to be more modular with each implementation contained in a different builder object. Adding a new implementation becomes easier. The object construction process becomes independent of the component that make up the object.This provides mode control over the object construction process.

**when to use:**
        
        1. The algorithm for creating a complex object should be independent of the parts that make up the object and how they’re assembled.
        
        2. The construction process must allow different representations for the object that’s constructed.

better `new XXX.Builder().xx().yy().build();`

* **Prototype Pattern**

待续...
