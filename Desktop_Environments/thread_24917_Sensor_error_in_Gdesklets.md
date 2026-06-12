---
title: "Sensor error in Gdesklets"
date: 2005-04-08
forum: Desktop Environments
---

### Post by arrizaba on 2005-04-08
Hi

I get lost of problems trying to run the various displays of gdesklets in Hoary.  Some of them are discussed in other forums but I get a problem related to the sensors and that has not been discussed in any forum (that I know of, at least..)
The problem is the following:
When I try to use Display that requires a sensor, I get this type of error:

exceptions.AttributeError:                                                           
'module' object has no attribute 'cpu'                                               
/usr/share/gdesklets/Sensors/CPU/__init__.py                                         
   22                                                                                
   23           self._add_timer(int(interval), self.__on_tick)                       
   24           self._add_thread(self.__command_thread)                              
   25                                                                                
   26           #Get 'static' infos                                                  
[COLOR=Red]>  27           self.__model_name = libdesklets.cpu.get_model()     [/COLOR]                 
   28           self.__cpu_mhz = libdesklets.cpu.get_speed()                         
   29           self.__cache = libdesklets.cpu.get_cache_size()                      
   30                                                                                
   31   def __on_tick(self):                                                         
   32           data = self._new_output()      

This one I obtained with the gdesklet [COLOR=Teal]cpuload[/COLOR], but I get the same error for all of the gdesklets that use sensors. Funny, I can use [COLOR=SandyBrown]SideCandy[/COLOR] desklets (which are not included in the package gdesklets-data for ubuntu).

Does someone know how to fix this??  ](*,)

---

### Post by Xian on 2005-04-08
[QUOTE=arrizaba]Funny, I can use [COLOR=SandyBrown]SideCandy[/COLOR] desklets (which are not included in the package gdesklets-data for ubuntu).[/QUOTE]
A lot of the older sensor desklets won't work in the latest Gdesklets releases. I had to remove quite a few desklets that I used to run with the old 0.2x series as they would not perform anymore.

---

