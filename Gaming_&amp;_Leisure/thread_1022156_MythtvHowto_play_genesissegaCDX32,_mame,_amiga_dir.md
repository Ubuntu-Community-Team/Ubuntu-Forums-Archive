---
title: "Mythtv/Howto: play genesis/segaCD/X32, mame, amiga directly in fullscreen (no click)"
date: 2008-12-26
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-12-26
Howto: play genesis/segaCD/segaX32  and  amiga 500 directly in fullscreen (no click):
----------------------------------------
 
The target: We want something NO MOUSE for mythtv or freevo:
[http://i166.photobucket.com/albums/u91/speedsix80/misc/100_2227.jpg](http://i166.photobucket.com/albums/u91/speedsix80/misc/100_2227.jpg)
and its 2 gamepads ;)
  
Requirements: Icewm 
(alt F11 to fullscreen)
   
  
Installing from source : 
- gens    (./configure ; make ; make install ) as always
- e-uae   (./configure ; make ; make install ) as always 

```
apt-get install libfakekey0  libfakekey-dev 
```
 
and placing those files from the tar.gz in the /usr/bin
(check the permissions and so on)

and finally add this to the .freevo/local_conf.py
 
 
If you need information for installing the emulators, please post.
 
To kill the process of the emulator, kill it with lirc:
 

***If it helped you, please post !***
Edited

---

