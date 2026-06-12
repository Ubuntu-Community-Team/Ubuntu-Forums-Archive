---
title: "Logitech QuickCam Express (Older Version)"
date: 2006-01-07
forum: Desktop Environments
---

### Post by Kelpie on 2006-01-07
i cannot get camorama to work because it gives me the error of
```
Could not connect to video device (/dev/video0). Please check connection.
```

With that I know the threads for fixing this problem dont work because my version of quickcam express is an OLDER version.

lsusb giving the following:
```
Bus 001 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000

```

it is not a supported version and i have ran into problems with this. I cannot just go out a buy a new webcam as I already spent what little christmas money I had on clothing.

I would actually like it if I can take pictures with my webcam, I do not want to have to partition my master drive and make room for windows 98... as that and windows 98se are the only OSes I have. And its not that hard to get the program for capturing pictures that comes with the camera to work on there... but it doesnt like wine...

i would extremely appreciate your help, people are begging me to take newer pictures...

Thanks much,
~~~Amber

---

### Post by Kelpie on 2006-01-07
Sorry for bumping, but I really wish to have my webcam working.

---

### Post by 47th_Ronin on 2006-01-07
[https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

it seems an auto-script for webcams under Ubuntu
try it... maybe it will work for you...

---

### Post by Kelpie on 2006-01-08
[QUOTE=47th_Ronin][https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam)

it seems an auto-script for webcams under Ubuntu
try it... maybe it will work for you...[/QUOTE]


i still get the same error with camorama, do you think i should reinstall it, maybe?

---

### Post by orrie on 2008-04-13
```
camorama -d=/dev/vide0 &
```
This worked for me ;)

---

