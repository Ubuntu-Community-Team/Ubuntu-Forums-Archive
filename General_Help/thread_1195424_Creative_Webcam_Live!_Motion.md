---
title: "Creative Webcam Live! Motion"
date: 2009-06-23
forum: General Help
---

### Post by akzouu on 2009-06-23
Is anyone able to give me some advices how to get this webcam working on kubuntu? i have been searching for some guide on the internet but i can't find any guide to get it working:confused:. There is some but they doesn't work. Here is some guide what i got but i don't get it working [http://ubuntuforums.org/showpost.php?p=5210450&postcount=15](http://ubuntuforums.org/showpost.php?p=5210450&postcount=15). I am stucked in 4th point. I have one year experience of using linux so i am still quite beginner with this operating system, but i have said goodbye to Bill Gates :D

$ lsusb 
Bus [002]("http://fin.afterdawn.com/sanasto/tiedostopaatteet/002.cfm") Device 003: ID 041e:4041 Creative Technology, Ltd WebCam Live! Motion 
Bus 002 Device 002: ID 059b:0277 Iomega Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus [001]("http://fin.afterdawn.com/sanasto/tiedostopaatteet/001.cfm") Device 008: ID eb1a:2861 eMPIA Technology, Inc. 
Bus 001 Device 011: ID 152e:2507 [LG]("http://fin.afterdawn.com/laitteet/valmistaja.cfm/lg") (HLDS) 
Bus 001 Device 010: ID 043d:00ff Lexmark International, Inc. InkJet Color Printer 
Bus 001 Device 009: ID 043d:007d Lexmark International, Inc. Photo 3150 
Bus 001 Device 007: ID 043d:007a Lexmark International, Inc. Generic Hub 
Bus 001 Device 005: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 004: ID 15a4:9016 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 002: ID 1241:1166 Belkin MI-2150 Trust Mouse 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 0518:0001 EzKEY Corp. [USB]("http://fin.afterdawn.com/sanasto/termit/usb.cfm") to [PS2]("http://fin.afterdawn.com/laitteet/laitteen_tiedot.cfm/4226/sony_playstation_2") Adaptor v1.09 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by s3MA00RRNY on 2009-06-23
What is the error for the make command?

---

### Post by akzouu on 2009-06-24
Here it is and "virhe" is finnish and it means "failure".

akzouu@akzouu-pc:~$ cd /home/akzouu/Työpöytä/pwc-10.0.12-rc1
akzouu@akzouu-pc:~/Työpöytä/pwc-10.0.12-rc1$ make           
make -C /lib/modules/2.6.28-13-generic/build SUBDIRS=/home/akzouu/Työpöytä/pwc-10.0.12-rc1 modules
make[1]: Siirrytään hakemistoon "/usr/src/linux-headers-2.6.28-13-generic"                        
  CC [M]  /home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.o                                          
In file included from /home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:69:                          
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc.h:28:26: error: linux/config.h: Tiedostoa tai hakemistoa ei ole
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc.h:37:27: error: asm/semaphore.h: Tiedostoa tai hakemistoa ei ole
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:166: virhe: muuttujalla &#8221;pwc_template&#8221; on alustin, mutta vaillinainen tyyppi                                                                                                                 
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:167: virhe: unknown field &#8221;owner&#8221; specified in initializer             
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:167: varoitus: excess elements in struct initializer                   
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:167: varoitus: (&#8221;pwc_template&#8221;:n alustuksen lähistöllä)                
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:168: virhe: unknown field &#8221;name&#8221; specified in initializer              
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:168: varoitus: excess elements in struct initializer                   
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:168: varoitus: (&#8221;pwc_template&#8221;:n alustuksen lähistöllä)                
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:169: virhe: unknown field &#8221;type&#8221; specified in initializer              
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:169: varoitus: excess elements in struct initializer                   
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:169: varoitus: (&#8221;pwc_template&#8221;:n alustuksen lähistöllä)                
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:170: virhe: unknown field &#8221;hardware&#8221; specified in initializer          
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:170: virhe: &#8221;VID_HARDWARE_PWC&#8221; undeclared here (not in a function)     
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:170: varoitus: excess elements in struct initializer                   
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:170: varoitus: (&#8221;pwc_template&#8221;:n alustuksen lähistöllä)                
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:171: virhe: unknown field &#8221;release&#8221; specified in initializer           
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:171: virhe: &#8221;video_device_release&#8221; undeclared here (not in a function) 
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:171: varoitus: excess elements in struct initializer                   
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:171: varoitus: (&#8221;pwc_template&#8221;:n alustuksen lähistöllä)                
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:172: virhe: unknown field &#8221;fops&#8221; specified in initializer              
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:172: varoitus: excess elements in struct initializer                   
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:172: varoitus: (&#8221;pwc_template&#8221;:n alustuksen lähistöllä)                
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:173: virhe: unknown field &#8221;minor&#8221; specified in initializer             
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:173: varoitus: excess elements in struct initializer                   
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:173: varoitus: (&#8221;pwc_template&#8221;:n alustuksen lähistöllä)                
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;pwc_isoc_init&#8221;:                                              
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:921: varoitus: sijoitus yhteensopimattomasta osoitintyypistä           
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: At top level:                                                         
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1017: varoitus: &#8221;struct class_device&#8221; esitelty parametrilistan sisällä 
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1017: varoitus: näkyvyysalue on vain tämä määrittely tai esittely, mikä ei todennäköisesti ole sitä, mitä halusit                                                                            
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;cd_to_pwc&#8221;:                                                  
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1019: virhe: funktio &#8221;to_video_device&#8221; esitelty implisiittisesti       
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1019: varoitus: alustuksessa tehdään osoitin kokonaisluvusta ilman tyyppimuunnosta                                                                                                           
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1020: virhe: funktio &#8221;video_get_drvdata&#8221; esitelty implisiittisesti     
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1020: varoitus: palautuksessa tehdään osoitin kokonaisluvusta ilman tyyppimuunnosta                                                                                                          
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: At top level:                                                         
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1023: varoitus: &#8221;struct class_device&#8221; esitelty parametrilistan sisällä 
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;show_pan_tilt&#8221;:                                              
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1025: varoitus: annettu yhteensopimatonta osoitintyyppiä oleva 1. argumentti funktiolle &#8221;cd_to_pwc&#8221;                                                                                          
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: At top level:                                                         
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1030: varoitus: &#8221;struct class_device&#8221; esitelty parametrilistan sisällä 
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;store_pan_tilt&#8221;:                                             
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1032: varoitus: annettu yhteensopimatonta osoitintyyppiä oleva 1. argumentti funktiolle &#8221;cd_to_pwc&#8221;                                                                                          
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: At top level:                                                         
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1046: virhe: expected &#8221;)&#8221; before &#8221;(&#8221; token                             
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1049: varoitus: &#8221;struct class_device&#8221; esitelty parametrilistan sisällä 
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;show_snapshot_button_status&#8221;:                                
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1051: varoitus: annettu yhteensopimatonta osoitintyyppiä oleva 1. argumentti funktiolle &#8221;cd_to_pwc&#8221;                                                                                          
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: At top level:                                                         
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1057: virhe: expected &#8221;)&#8221; before &#8221;(&#8221; token                             
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;pwc_create_sysfs_files&#8221;:                                     
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1062: varoitus: alustuksessa tehdään osoitin kokonaisluvusta ilman tyyppimuunnosta                                                                                                           
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1064: virhe: funktio &#8221;video_device_create_file&#8221; esitelty implisiittisesti                                                                                                                    
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1064: virhe: &#8221;class_device_attr_pan_tilt&#8221; esittelemättä (ensimmäinen käyttökerta tässä funktiossa)                                                                                           
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1064: virhe: (Jokaisesta esittelemättömästä tunnisteesta ilmoitetaan vain                                                                                                                    
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1064: virhe: ensimmäinen käyttökerta kussakin funktiossa.)             
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1065: virhe: &#8221;class_device_attr_button&#8221; esittelemättä (ensimmäinen käyttökerta tässä funktiossa)                                                                                             
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;pwc_remove_sysfs_files&#8221;:                                     
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1070: varoitus: alustuksessa tehdään osoitin kokonaisluvusta ilman tyyppimuunnosta                                                                                                           
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1072: virhe: funktio &#8221;video_device_remove_file&#8221; esitelty implisiittisesti                                                                                                                    
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1072: virhe: &#8221;class_device_attr_pan_tilt&#8221; esittelemättä (ensimmäinen käyttökerta tässä funktiossa)                                                                                           
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1073: virhe: &#8221;class_device_attr_button&#8221; esittelemättä (ensimmäinen käyttökerta tässä funktiossa)                                                                                             
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;pwc_video_open&#8221;:                                             
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1112: virhe: funktio &#8221;video_devdata&#8221; esitelty implisiittisesti         
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1112: varoitus: alustuksessa tehdään osoitin kokonaisluvusta ilman tyyppimuunnosta                                                                                                           
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1117: virhe: dereferencing pointer to incomplete type                  
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;pwc_video_close&#8221;:                                            
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1231: virhe: dereferencing pointer to incomplete type                  
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;pwc_video_read&#8221;:
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1292: virhe: dereferencing pointer to incomplete type
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;pwc_video_poll&#8221;:
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1359: virhe: dereferencing pointer to incomplete type
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;pwc_video_ioctl&#8221;:
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1375: virhe: funktio &#8221;video_usercopy&#8221; esitelty implisiittisesti
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;pwc_video_mmap&#8221;:
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1388: virhe: dereferencing pointer to incomplete type
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;usb_pwc_probe&#8221;:
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1722: virhe: funktio &#8221;video_device_alloc&#8221; esitelty implisiittisesti
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1722: varoitus: sijoituksessa tehdään osoitin kokonaisluvusta ilman tyyppimuunnosta
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1729: virhe: epäkelpo &#8221;sizeof&#8221;:n soveltaminen vaillinaiseen tyyppiin &#8221;struct video_device&#8221;
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1729: virhe: epäkelpo &#8221;sizeof&#8221;:n soveltaminen vaillinaiseen tyyppiin &#8221;struct video_device&#8221;
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1729: virhe: epäkelpo &#8221;sizeof&#8221;:n soveltaminen vaillinaiseen tyyppiin &#8221;struct video_device&#8221;
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1730: virhe: dereferencing pointer to incomplete type
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1731: virhe: dereferencing pointer to incomplete type
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1732: virhe: dereferencing pointer to incomplete type
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1733: virhe: funktio &#8221;video_set_drvdata&#8221; esitelty implisiittisesti
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1756: virhe: dereferencing pointer to incomplete type
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1757: virhe: funktio &#8221;video_register_device&#8221; esitelty implisiittisesti
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1757: virhe: &#8221;VFL_TYPE_GRABBER&#8221; esittelemättä (ensimmäinen käyttökertatässä funktiossa)
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1760: virhe: funktio &#8221;video_device_release&#8221; esitelty implisiittisesti
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1765: virhe: dereferencing pointer to incomplete type
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c: Funktio &#8221;usb_pwc_disconnect&#8221;:
/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.c:1819: virhe: funktio &#8221;video_unregister_device&#8221; esitelty implisiittisesti
make[2]: *** [/home/akzouu/Työpöytä/pwc-10.0.12-rc1/pwc-if.o] Virhe 1
make[1]: *** [_module_/home/akzouu/Työpöytä/pwc-10.0.12-rc1] Virhe 2
make[1]: Poistutaan hakemistosta "/usr/src/linux-headers-2.6.28-13-generic"
make: *** [all] Virhe 2
akzouu@akzouu-pc:~/Työpöytä/pwc-10.0.12-rc1$

---

