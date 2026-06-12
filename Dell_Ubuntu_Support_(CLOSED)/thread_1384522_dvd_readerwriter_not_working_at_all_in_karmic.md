---
title: "dvd reader/writer not working at all in karmic"
date: 2010-01-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by v1nsai on 2010-01-18
I'm using a Dell Studio 1555 laptop, and the dvd drive isn't able to do anything.  I've tried burning cds, dvds, and watching dvds and listening to cds and it isn't able to do any of these things.  I thought it was defective until I tried booting into Windows 7 and it worked no problems there.

Linux doesn't seem to be reading the drive correctly, but I'm not sure what to do from here, could anyone suggest something?  I'm posting some more info about the drive.

lshw
```
*-cdrom                                                                                                                    
                description: DVD-RAM writer                                                                                           
                product: DVD+-RW GA11N                                                                                                
                vendor: HL-DT-ST                                                                                                      
                physical id: 1                                                                                                        
                bus info: scsi@1:0.0.0                                                                                                
                logical name: /dev/cdrom                                                                                              
                logical name: /dev/cdrw                                                                                               
                logical name: /dev/dvd                                                                                                
                logical name: /dev/dvdrw                                                                                              
                logical name: /dev/scd0                                                                                               
                logical name: /dev/sr0                                                                                                
                logical name: /media/cdrom0                                                                                           
                version: A102                                                                                                         
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                                                            
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
```

---

### Post by KyleAnderson on 2010-01-18
I have a very similar Dell and I have the same issue. Here are some more people with that issue:
[http://ubuntuforums.org/archive/index.php/t-1300173.html](http://ubuntuforums.org/archive/index.php/t-1300173.html)

Maybe we should file a bug report? I'm not sure what else to do or even where to go digging.

---

### Post by surfed on 2010-01-22
> **KyleAnderson said:**
> I have a very similar Dell and I have the same issue. Here are some more people with that issue:
[http://ubuntuforums.org/archive/index.php/t-1300173.html](http://ubuntuforums.org/archive/index.php/t-1300173.html)

Maybe we should file a bug report? I'm not sure what else to do or even where to go digging.

Its a Firmware issue with this drive. No Distro supports it as of now.

---

### Post by surfed on 2010-01-28
The actual problem for me was device-manager-plasmoid 1.1.1, replacing it with device-notifier everything works again.

---

### Post by v1nsai on 2010-01-31
I complained and got Dell to replace my drive and it works now, it was a bunk drive for me :-D

---

