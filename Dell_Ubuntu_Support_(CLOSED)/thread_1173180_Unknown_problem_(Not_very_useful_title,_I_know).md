---
title: "Unknown problem (Not very useful title, I know)"
date: 2009-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by worm94 on 2009-05-29
Hi, I'm "new" to ubuntu, I've installed it before on my system (Dell Inspiron 1501, 1.8Ghz Amd Sempron, 1.5GB ram, no other OS installed) but everytime I ran into some problem I didn't have time to work out (college takes almost all my time:D) but when Jaunty came out i thought "hey, let's give it a try" and now I'm in some kind of problem :roll:
Last night, I shut down the system and everything was fine, but today morning when I turned it on, ubuntu won't boot completely, it loads everything fine but when it should get to the login screen, everything it shows is a distorted version of the last image present in the screen before shutting it down, but with color lines and black spaces, then the screen flashes a few times and it finally gets stuck in a black screen with some color lines and weird patterns, when loading the boot files I don't see any error, but maybe there's one I haven't noticed... I know this isn't the kind of info you need to give me useful information, so if you're so kind as to tell me how to get logs and the info you might need to help me, please do so. 
Ps: I don't care if I have to format and do a clean install, what I'm worried about is recovering some college stuff, pictures and some music...
Thanks in advance :p

---

### Post by Blue Sassley on 2009-05-29
On your last good shutdown did you run any updates or install and restricted drivers like a video card driver?

Also how did you install Ubuntu? Did you dual boot or did you install in within Windows using WUBI?

Thanks,
Blue

---

### Post by Pidgin on 2009-05-29
Don't worry. Everything's gonna be all right.
You can use a LiveCD to recover your files.

---

### Post by Fac51 on 2009-05-29
> **Blue Sassley said:**
> On your last good shutdown did you run any updates or install and restricted drivers like a video card driver?

Also how did you install Ubuntu? Did you dual boot or did you install in within Windows using WUBI?

Thanks,
Blue

he/she stated there is no other OS so we can skip straight to restricted drivers

> **worm94 said:**
> Hi, I'm "new" to ubuntu, I've installed it before on my system (Dell Inspiron 1501, 1.8Ghz Amd Sempron, 1.5GB ram, no other OS installed) but everytime I ran into some problem I didn't have time to work out (college takes almost all my time:D) but when Jaunty came out i thought "hey, let's give it a try" and now I'm in some kind of problem :roll:
Last night, I shut down the system and everything was fine, but today morning when I turned it on, ubuntu won't boot completely, it loads everything fine but when it should get to the login screen, everything it shows is a distorted version of the last image present in the screen before shutting it down, but with color lines and black spaces, then the screen flashes a few times and it finally gets stuck in a black screen with some color lines and weird patterns, when loading the boot files I don't see any error, but maybe there's one I haven't noticed... I know this isn't the kind of info you need to give me useful information, so if you're so kind as to tell me how to get logs and the info you might need to help me, please do so. 
Ps: I don't care if I have to format and do a clean install, what I'm worried about is recovering some college stuff, pictures and some music...
Thanks in advance :p

if you have installed the restricted drivers, try booting into recovery mode and restore /etc/X11/xorg.conf.<oldest date> to /etc/X11/xorg.conf

then reboot

First, lets check to see if you do have xorf.conf backups
```

# cd /etc/X11

# ls -lF xorg.conf*

```
if you see "xorg.conf" and a bunch of "xorg.conf.<date>" files, you're good to go

just delete the xorg.conf and rename the oldest backup to that name:
```

# rm xorg.conf

# mv xorg.conf.<oldest date> xorg.conf

# reboot

```

then cross your fingers

---

### Post by Blue Sassley on 2009-05-29
> **Fac51 said:**
> he/she stated there is no other OS so we can skip straight to restricted drivers

Sorry, I missed that part in the hardware specs...

Blue

---

### Post by worm94 on 2009-05-31
Let's hope everything works fine:p

---

### Post by worm94 on 2009-05-31
I have just got home, I'll check, cross my fingers and expect everything works fine... thanx for your help, I hope it works

---

### Post by worm94 on 2009-05-31
Ok, so I checked what Fac51 said, and when I try to cd to said file, I get a "Error: No such file exists" or something like that... I'm kinda lost here, being used to windows, command line isn't something I'm very familiar with, so if you please could explain to me  step by step, it would be very appreciated:D

---

### Post by Daveski on 2009-06-01
So 
**cd /etc/X11**

Did not work? Please note that Linux is case sensitive and the X11 folder has a capital X.

---

### Post by Fac51 on 2009-06-01
> **Daveski said:**
> So 
**cd /etc/X11**

Did not work? Please note that Linux is case sensitive and the X11 folder has a capital X.

yeah, what he said... i should have mentioned that before

---

### Post by Fac51 on 2009-06-02
worm94:  you throw it out the window or what

---

