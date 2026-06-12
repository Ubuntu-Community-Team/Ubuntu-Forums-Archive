---
title: "D620 - Ubuntu 7.04 New Install - It Just Works !!"
date: 2007-07-09
forum: Dell  Ubuntu Support
---

### Post by carcioni on 2007-07-09
We acquired a new D620 with the NVidia video card and the Intel Wireless chipset on Friday.
Sat down on Sunday afternoon to setup a dual boot machine with Win-XP and Ubuntu. The machine had originally been templated by our corporate IT as a straight Win-XP machine, but that won't fly for me for what I need to do so it was time to repartition and reformat.

We initially installed XP just to get the something bootable, and give me a browser if I needed to download any special drivers etc., for Ubuntu. Usual hour or so later we have a working basic XP install.

Tweaked the BIOS settings to boot from CD first, then dropped in the Ubuntu 7.04 Desktop CD. It boots up, and we run the install. Other than a couple of cryptic 'scsi using deprecated ioctl' errors during partitioning, it installed flawlessly.  It picked up the Intel wireless card right away, found my access point and with a couple of passwords, we were live on the net.

Enabled the NVidia 'restricted' driver following the instructions here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04)
and then enabled the dual head support for two monitors.
see: [http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)
 Works right out of the box!

The whole process took under an hour, and just ran. After a few updates to software, which added another 10 minutes we were there.

Rebooted into Win-XP and spent another 2.5 hours pulling security and OS patches down, locating the correct drivers fro the NVidia and Intel cards, enabling firewalls and virus scanners yada yada yada.

Maybe Dell should just ship Ubuntu on the D620s. 

Anyway, just thought I'd say 'Great Job' to everyone who keeps Ubuntu alive and well.
Couldn't really ask for an easier install short of having it pre-installed on the machine to begin with.

Cheers
D

---

### Post by fjgaude on 2007-07-09
Yep, Ubuntu Linux is getting this good: it just works (for most hardware). <smile>

frank

---

### Post by spud42 on 2007-07-10
i hate to rain on your parade but i also have a d620 dual boot xp/ubuntu 7.04 . i have several problems out of the box. wireless wont work. the screen will not go to 1280 800 native resolution even though its set to do that. 
i previously had dapper running on it and that one did find the wireless and work straight out of the box. however when i updated to use the dual cores i could not get the radio to work or the screen resolution to work either. maybe you have some ideas as to what i need to do to fix this . i admit i am not as strong in linux as i am with xp so i do need help. but *** to your general comment , yes ubuntu is fantastic. much better than some of the others i have dabbeled with over the last 10 years...lol

---

### Post by injunandrew on 2007-07-11
Maybe you've already tried this, but the instructions on this page got my wireless working.  (I have broadcom)

[http://www.sharms.org/blog/?p=106]("http://www.sharms.org/blog/?p=106")

I could still use a better wireless network manager, but I haven't had time to look into that yet.

-andrew

---

### Post by spud42 on 2007-07-12
mine is the intel pro wirless 3945 ABG

---

### Post by lithium06 on 2007-08-02
Does suspend / resume work on your 620 in fiesty? on resume do you have usb working and networking?

thanks

---

