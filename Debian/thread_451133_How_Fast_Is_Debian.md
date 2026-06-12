---
title: "How Fast Is Debian?"
date: 2007-05-22
forum: Debian
---

### Post by VoodooSteve on 2007-05-22
Having little experience with Debian, I was wondering how fast it would be if I installed it on a Pentium II 266MHz, 196MB RAM machine? Would I be able to run KDE? When I used a Knoppix LiveCD with KDE, the system was very responsive.

---

### Post by kerry_s on 2007-05-22
Kde is the heaviest of desktops. You should consider using something lighter if you want to make your system useful.

If it was mine i would just go totally custom. Start from a server install and build up from there. If you just have to have kde try kde-core instead of all of kde.

i recommend-> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

kde if you want to try-> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-kde-CD-1.iso)

net installer if you want to try a custom or gnome-> [http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-netinst.iso](http://mirrors.kernel.org/debian-cd/4.0_r0/i386/iso-cd/debian-40r0-i386-netinst.iso)

---

### Post by VoodooSteve on 2007-05-22
I agree that I should go with something lighter. However, it surprised me how snappy KDE is under my Knoppix LiveCD. Is this a feature unique to Knoppix then?

---

### Post by tkjacobsen on 2007-05-22
With that processor I would even go with fluxbox and xfe as file manager

[http://wiki.debian.org/Fluxbox](http://wiki.debian.org/Fluxbox)

---

### Post by Rashid584 on 2007-05-22
KDE is heavy yes, but its not "the heaviest" as such...depends how you look at it, what packages are included etc

I think you could go with a kdecore installation, it would be fast but you might not have all the apps you want.

Give sidux a try...I tried it and its extremely fast...I don't have much more ram than you (256MB) but my processor is a lot faster...

-Rashid

---

### Post by ThinkBuntu on 2007-05-22
KDE flies in Debian, in my experience with a so-so processor (1.6GHz). Debian is significantly faster than Ubuntu without a doubt, but slightly harder to setup.

---

### Post by raul_ on 2007-05-22
[http://ubuntuforums.org/showthread.php?t=430003]("http://ubuntuforums.org/showthread.php?t=430003")

---

### Post by cunawarit on 2007-05-23
I'm currently using Debian on my Celeron 700, with 512MB RAM. With GNOME or KDE it is frankly rather unusable. But it works OK with Fluxbox. I'd recommend going the Fluxbox route with something that slow.

---

### Post by Pobega on 2007-05-23
Debian isn't the greatest distribution for you speed demons out there, but it gets the job done. I'd say it's one of the faster distros, being that all/most of the packages are vanilla (With no un-needed stuff patched into them).

If you really want speed, try Gentoo or apt-build in Debian; Building from source may make a world of difference on older computers.

---

### Post by tkjacobsen on 2007-05-23
> **Pobega said:**
> Debian isn't the greatest distribution for you speed demons out there, but it gets the job done. I'd say it's one of the faster distros, being that all/most of the packages are vanilla (With no un-needed stuff patched into them).

If you really want speed, try Gentoo or apt-build in Debian; Building from source may make a world of difference on older computers.

But it will take a year to compile the system ;)

Zenwalk is actually quite fast.

---

### Post by Pobega on 2007-05-23
> **tkjacobsen said:**
> But it will take a year to compile the system ;)

Zenwalk is actually quite fast.

Compiling doesn't take as long as most people say. So long as you don't compile things like GNOME/OpenOffice you should be fine.

Recompiling a Debian system takes about a day and a half, with no work from you. All you have to do is leave the computer on.

---

### Post by plb on 2007-05-23
IMO Gnome is MUCH heavier than KDE.

---

### Post by mips on 2007-05-24
> **plb said:**
> IMO Gnome is MUCH heavier than KDE.

Mentioning things like that in a Gnome centric forum will probably start another flame war, although I believe you stated the truth :)

Complex number will probably be around to set you straight soon ;)

---

### Post by Rashid584 on 2007-05-24
> **mips said:**
> Mentioning things like that in a Gnome centric forum will probably start another flame war, although I believe you stated the truth :)

Complex number will probably be around to set you straight soon ;)

Haha, don't worry, I'll back you guys up ;)

-Rashid

---

### Post by melancholeric on 2007-05-25
gnome vs kde doesn't make the slightest difference on 196 MB: they're both equally unusable. i'm running fvwm-crystal on debian with 256 MBs and it's dog slow at times.

Granted, I multitask a lot and have some extra daemons running, but still ...

---

### Post by Rashid584 on 2007-05-25
> **melancholeric said:**
> gnome vs kde doesn't make the slightest difference on 196 MB: they're both equally unusable. i'm running fvwm-crystal on debian with 256 MBs and it's dog slow at times.

Granted, I multitask a lot and have some extra daemons running, but still ...

I'm running kde now with 256MB of ram and it absolutely flies. Actually I've started some extra daemons and generally have more apps open at a time, so now its particularly-fast, not flying.

The difference between KDE that comes with something like Kubuntu/opensuse and a slim kde installation is like day and night ;)

-Rashid

---

### Post by happy-and-lost on 2007-05-26
It'll fly with Fluxbox. You could cut the KDE down a bit, but Fluxbox is every bit as sexy and powerful.

---

### Post by SkyNet2029 on 2007-06-12
Debian with KDE or Gnome is (or can be, with a little tweakage) just a fast as you want it to be, as long as you are willing to drop some CLI usage on top of all of that, as well.

!**! ! !   </FLAME OFF> please..make it stop.. ;)

What I mean is that yes, Gnome or KDE can both be very resource intensive desktop's, but so can the Flux if given the same amount of negligence. Things you should pay attention to in the actual layout of your spanking new Debian installation, like the differences between nosync,async, and updating access times, when to tweak with hdparm (and when not to, as well), what is needed (how many print servers do you actually need(?), are you really needing to have eight tty's going at all times?, can go a long way in using what few resources you do have available for something other than being gobbled up by essential system daemons and vital (or not so vital depending on your definition of minimal) processes. 

If for your machine 198MB is the ceiling on upgrades, which is probably the case, as in the late 90's that was a very respectable amount of Ram, then use it to your full advantage. Give the machine priority over tasks, not the other way around. Things like setting DMA to on, or re-niceing the xserver (Debian's dpkg-reconfigure your_pkg_name_here is exceptional at allowing for (over)tweakage, on a maniacal level), using what you have to build up your system in a way that creates a rock-hard base, and then moving on to the desktop environment of your choosing is my personal favorite. 

At any rate, I am rambling now, as Debian just gets me super-pumped(! ! ), especially in the ease of its administration and configuration. Bottom line of what I am saying here is that start with a goal in mind and build the machine for its purpose, not the purpose around the machine. Engineer for perfection, don't just hope for it. Debian won't let you down in that department..

Ok, as expected .. here are some useful reference points:

[http://www.debian-administration.org]("http://www.debian-administration.org")
the obligatory link

[http://www.ibm.com/developerworks/linux/library/l-tune-lamp-1/]("http://www.ibm.com/developerworks/linux/library/l-tune-lamp-1/")
While the title is for a LAMP install, this is more akin to what we are looking for anyways, high-speed, low-drag. IBM (IMHO) has the greatest repository of UNIX/Linux info out there. Definitely worth a read or two.

---

### Post by VoodooSteve on 2007-06-14
Thanks  everyone. Once my exams finish at the end of the month, I'll have tons of time to devote to tinkering around. I'm looking forward to following all of your advice and making the machine usable, I think I'll try KDE and Fluxbox and if all goes well, I'll do the same on my other slightly faster computer (PIII 1GHz, 256MB RAM) and make them both really fly! :D

---

### Post by juxtaposed on 2007-06-14
>  How Fast Is Debian?

Faster then ubuntu.

---

### Post by deanlinkous on 2007-06-14
700mhz pIII with 256mb ram laptop
boots to a slim gnome desktop in about 35sec total
shutdown in about 15sec

Heavy apps take a second or two to launch but not bad, light apps are fast...

---

