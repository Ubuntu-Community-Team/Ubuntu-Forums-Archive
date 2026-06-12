---
title: "HELP! I messup up my Xorg"
date: 2006-08-19
forum: Desktop Environments
---

### Post by simukas on 2006-08-19
Ok the story goes like this :

   Well i didn't like no 3D acceleration so i  searched the internet for my graphics card (build-in) driver and found a rpm package that i converted to deb using alien. I installed it and restarted my PC. And froze, did something and the asked me for my login. I gave the login and the password and wrote startx. After that i got some standart messages and then the log was like this:


(==)log file "/var/log/Xorg.0.log time (now)
(==)using config file "/etc/X11/xorg.conf
(EE)GARTInit: unable to open /dev/agpgart/ no such file or directory
(EE) 1810(0): AGP gart support is not avaible. Make sure your kernel has agpgart support, or that Kernel nodule is loaded.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 request, 10 known processed 1 with 0 events remaining.


Plz help.

---

### Post by meng on 2006-08-19
One strategy is to enter at command prompt:
sudo dpkg-reconfigure xserver-xorg

---

### Post by simukas on 2006-08-19
and waht do i do?? i cna't find my graphics card there..

---

### Post by simukas on 2006-08-19
srr i found. but when select the color depth it sais something oi forgot. i tried again but i can't get pass the Keyboard .......

---

### Post by meng on 2006-08-19
Keyboard? as in keyboard layout? Most common option here is us, but I don't know if you may have a different keyboard layout.

---

### Post by simukas on 2006-08-19
i see that there's no point in asking for help... can i just get a quick toturial how to reinstall ubuntu without getting my stuff deleted... 


this sucks... and i enjoy it...

---

### Post by meng on 2006-08-19
> **simukas said:**
> i see that there's no point in asking for help...
Oh, I guess I should feel insulted! :p
Sorry I couldn't help, but I couldn't understand your question.

---

### Post by simukas on 2006-08-19
srr it's not you. it's me. i'm just too lazy too sit for 6 hours and talk about  something while i can just paly some games while i'm reinstalling...

---

### Post by meng on 2006-08-19
I'm just kidding, no offence taken. You're right that reinstalling is pretty quick, but it's always nice to know how to fix things without resorting to that.

---

### Post by simukas on 2006-08-19
and the best thing when yoiu uninstall you clean up your PC too.

---

