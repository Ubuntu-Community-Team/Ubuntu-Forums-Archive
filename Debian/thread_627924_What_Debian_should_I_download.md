---
title: "What Debian should I download?"
date: 2007-11-30
forum: Debian
---

### Post by Fixman on 2007-11-30
Okay, [here]("http://ubuntuforums.org/showthread.php?t=626997") you convinced me to install Debian. But what branch should I install? Please note that I prefer having pretty actualized software.

Also, I ask the following two questions:

What is the best thing that Debian has and Ubuntu hasn't?
What is the best thing that Ubuntu has that Debian hasn't?

---

### Post by SunnyRabbiera on 2007-11-30
both testing and unstable should do you, there is a way to use the unstable repositories in testing and vice versa (though its risky either way)
I only suggest those two as they do offer more up to date software then the stable version (though you can also use the unstable and testing repos in that too, also at great risk)
My biggest gripe with debian is of course getting stuff like codecs and flash to work, its a bit rougher around the edges over there.

---

### Post by 11hjpphty76lkjj on 2007-11-30
Before I answer I want to ask several questions;

What do you plan on using the system for?

What would you rate your linux experience to be?

:)

A

---

### Post by zippy028 on 2007-11-30
If you have a decent internet connection you can download the business card iso at [this]("http://www.debian.org/CD/netinst/")location. The business card image does a network install but it gives you the option to choose which branch you would like to install from I.E. testing,stable,unstable. You have to enter```
 expert
```  at the boot prompt when the disc boots to get the option to choose the different branches though. If you do not it will install "Etch" or stable. You can also opt for KDE  simply enter at boot prompt```
 tasks="standard, kde-desktop"
```I believe the quotes are required in the KDE example. If not the installer will probably tell you. If you enter "expertgui" you will get the graphical installer. I do not see a need for it as the standard installer is pretty much the same as the installer Ubuntu uses. If you do not do the network/business card install and want KDE you will have to get either the 4.0 DVD or download the KDE disc [here]("http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/")

---

### Post by g2g591 on 2007-12-04
if you're pretty experianced and willing to do a little hackery and digging around I'd say unstable (but with testing repos too, so some packages like adept won't break) and expertgui is the installer of choice (more choices) 
(and go KDE!)

---

### Post by Ozeuss on 2007-12-06
the best is to download stable, and then change the sources to whatever you want. That's because etch's installer is, well... more stable.

---

### Post by sicknor on 2007-12-08
I usually download the stable release , after that i just add the unstable and testing repositories 
```
pico /etc/apt/sources,list
```
example :)
```

deb http://ftp.uk.debian.org/debian testing main contrib non-free
deb http://ftp.uk.debian.org/debian unstable main contrib non-free
```
than just run
```
apt-get dist-upgrade
```
and your system is up to date . Sid always worked fine with me , never had problems with "unstable" packages.

---

### Post by angryfirelord on 2007-12-09
If you're a newbie to Debian, I would stick with Stable and get used it first. Then, you can play around with Testing or Unstable.

Be careful though when you do decide to upgrade. Watch for any packages that might get removed. Sometimes incomplete dependencies may cause you to loose something important, such as openoffice. (although the Debian devs are good about fixing that within the next day or two)

Otherwise, Debian's a joy to use!

---

### Post by kellemes on 2007-12-10
I think "testing" is much more stable as Ubuntu has ever been..
Personally I'd use "testing" and get individual packages from other branches based on your needs and wishes.
But whatever branch you choose, it's pretty cool and gives you GNU/Linux at it's best.

---

### Post by kerry_s on 2007-12-10
> **Fixman said:**
> Okay, [here]("http://ubuntuforums.org/showthread.php?t=626997") you convinced me to install Debian. But what branch should I install? Please note that I prefer having pretty actualized software.

Also, I ask the following two questions:

What is the best thing that Debian has and Ubuntu hasn't?
What is the best thing that Ubuntu has that Debian hasn't?


start with xfce4, till ya learn the ropes-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

after that the net installer can get you what ever you want your system to be, a custom install is the way to go-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

---

