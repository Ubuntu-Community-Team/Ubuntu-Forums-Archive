---
title: "Help! CDROM stopped working (XPS M1330)"
date: 2009-03-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geoffm on 2009-03-17
I can't read any DVD's, data or video. It spins but nothing appears in /cdrom, /media/cdrom or anything. When I try to read a video DVD using Kplayer or VLC it spins, gets really noisy and doesn't load.

At one point, I ran a text-based application that made recommendations to optimise power consumption, one of the things it made me do was cd-rom related (something about refresh or probing rate I think), I can't remember what it was or what the application is.
I got the laptop with preinstalled ubuntu, cdrom must have been working before. Here is what lshw says.

```
           *-cdrom                                                                                                   
                description: DVD writer                                                                              
                product: DVD+-RW GSA-S10N                                                                            
                vendor: HL-DT-ST                                                                                     
                physical id: 0.0.0                                                                                   
                bus info: scsi@3:0.0.0                                                                               
                logical name: /dev/cdrom                                                                             
                logical name: /dev/cdrw                                                                              
                logical name: /dev/dvd                                                                               
                logical name: /dev/dvdrw                                                                             
                logical name: /dev/scd0                                                                              
                logical name: /dev/sr0                                                                               
                version: A103                                                                                        
                capabilities: removable audio cd-r cd-rw dvd dvd-r                                                   
                configuration: ansiversion=5 status=open              
```

---

### Post by geoffm on 2009-03-17
The thing that program made me do must have been hal-disable-polling

I reenabled it and the problem seems to be solved.

```
sudo hal-disable-polling --device /dev/cdrom --enable
```

---

