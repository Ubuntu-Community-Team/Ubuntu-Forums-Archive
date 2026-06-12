---
title: "no flash 10 with webcam? (eee pc 900)"
date: 2009-01-21
forum: General Help
---

### Post by deathsshadow77 on 2009-01-21
I have an eee pc 900ha and have installed ubuntu 8.10 on it. I have flash 10 installed and cheese works fine. When trying to record video through flash such as on facebook, it never actually loads the dialogue that asks me about my webcam and if I would allow or deny the use of the camera. The flash just continuously loads. The webcam also doesnt have the light on when this page is open.

another issue is with cheese. it seems that recording video is extremely slow and is like a frame every 5 seconds. Pictures work perfectly though

---

### Post by deathsshadow77 on 2009-01-21
bump

---

### Post by deathsshadow77 on 2009-01-22
bump

---

### Post by JNik on 2009-01-24
I have the same problem with my webcam and facebook (flash video recording object never loads).

But even when a flash object manages to show my webcam on a page, the image is very distorted.

I guess there is something wrong with flash on ubuntu/linux since my camera works just fine with everything else.

Ubuntu: 8.04
Flash: 10
Webcam: Logitech Quickcam Communicate S

---

### Post by JNik on 2009-01-24
I found a solution

Download flash 9 plugin from adobe's site.

Go to /usr/lib/adobe-flashplugin/ folder
make a copy of libflashplayer.so as libflashplayer10.so
copy libflashplayer.so from flash 9 archive as libflashplayer9.so

Now all you have to do is rename _libflashplayer**XX**.so_ as _libflashplayer.so_ depending the version you want to use.

> 
john@user-desktop:/usr/lib/adobe-flashplugin$ dir -l
-rw-r--r-- 1 root root 9980112 2008-12-03 02:29 libflashplayer10.so
-rw-r--r-- 1 john john 8843296 2008-11-18 02:26 libflashplayer9.so
-rw-r--r-- 1 john john 8843296 2008-11-18 02:26 libflashplayer.so


I'm sure there is an easier and smarter way... but that works for now :)

---

