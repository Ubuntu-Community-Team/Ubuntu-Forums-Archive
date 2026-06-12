---
title: "dell xps m1300 dvd and wireless problem"
date: 2008-03-08
forum: Dell  Ubuntu Support
---

### Post by tdansel88 on 2008-03-08
Hey I'm new to ubuntu and I can't seem to play DVDs. I tried installing vlc to see if my problem was the totem player but both totem and vlc said they couldn't read the disc from source.

also I've done a fair amount of work trying to get my wireless to work including iwl3945 but it's not fixing my problem. i can pick up wireless networks and attempt to connect to them but the connection always fails when i try, often crashing my computer.

if anyone knows how to install the mic and webcam for the 1330 or knows the appropriate thread i would also like to take a look at that.

any help would be much appreciated.

---

### Post by PsychedelicReaction on 2008-03-08
```
sudo apt-get install libdvdread3
``` and then ```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

other issues try to read this [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

have you tried webcam? it should work out of the box. if you didn't try to install cheese from repository

---

### Post by pormogo on 2008-03-08
Wireless on my m1330n is in a pretty bleak state. In the end for me the ipw3945 module appears to be more "workable" while it does break my connection sometimes I am able to reconnect most of the times. During the times when the module completely fails reloading the module 

modprobe -r ipw3945 && modprobe ipw3945 

and then restarting network manager

pkill -9 NetworkManager && NetworkManager

Seems to solve the problem most of the time. I only seem to HAVE to reboot after a suspend where network manager just doesn't want to recognise the module after a reload. The iwl module, while having more reliable connetivity breaks anytime I suspend or hibernate and requires a reboot in order to fix, I have yet to find another way to fix the iwl module after coming back from suspend or hibernate.

---

### Post by notwen on 2008-03-10
Wireless using the ipw3945 module is unstable at best.  You should try blacklisting it and replacing it w/ the iwl module.  See how to do this [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues").  I've done this on my Inspiron 1420n and it has resolved most of my wireless issues.  It' certainly more stable when moving lots of traffic over wifi.  Maybe you'll find this useful.  =]

---

### Post by pormogo on 2008-03-11
Unfortunately I haven't had much luck with the iwl module. I agree that the ipw module is unstable on a good day but the iwl module doesn't surivive a hibernate or suspend, and that's a pretty showstopping break for me. I've tried just about everything even unloaing the module and then reloading the module using shell scripts in  /etc/acapi/resume.d and ./suspend.d that doesn't seem to help it either :(

---

