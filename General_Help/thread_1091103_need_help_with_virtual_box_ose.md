---
title: "need help with virtual box ose"
date: 2009-03-09
forum: General Help
---

### Post by banana jama on 2009-03-09
I've downloaded virtual box ose from add/remove today (like messing around with other Linux OSes for fun in a virtual environment) but have came along to problems.

    1) Ubuntu repositories has version 2.04 but the newest version is 2.14. i added ```
http://download.virtualbox.org/virtualbox/debian
``` to third party sources along with the proper key in authentication in software sources. even though i did this it still says there's no new updates also when i run VB and go to preferences update i'm not allowed to check the check for update box.

     2) i want higher resolution when i run my OSes virtually i try to download guest installations but when i try it says "download failed connection timed out" i tried to download the .iso and place it in usr/share/virtualbox/VirtualBoxGuest.iso but when i click install guess installation nothing happens (i kow this because i still can't use auto resize right+ctrl+g)

is there anyone in the forum who had these problems and solved them know  
what to do? any suggestions is appreciated.
                                                 bananajama

---

### Post by davidryder on 2009-03-09
If you have the .ISO for guest additions you can mount the CD before you launch the OS.

[img]http://img131.imageshack.us/img131/7501/ssmar0820092328.png[/img]

---

### Post by banana jama on 2009-03-09
i tried that  when i mount it nothing happens

---

### Post by davidryder on 2009-03-09
What OS are you attempting this from? If linux, you have to browse into the CD that is mounted and run VBoxLinuxAdditions.run

---

### Post by banana jama on 2009-03-09
the host os is ubuntu 8.10 the os im virtualizing is puppy linux

---

### Post by davidryder on 2009-03-09
Does the CD mount? You can also mount it while the OS is running.

Devices|Mount CD/DVD Rom

If it is mounting, open the CD and run VBoxLinuxAdditions.run

---

### Post by banana jama on 2009-03-09
what do u mean? when i mount the Vbox guest it says error and when i run puppy linux and click on install guess installation nothing happens.

---

### Post by banana jama on 2009-03-09
ok i did what u said device mount and chose vbox guess now in puppylinux a cd popup on the home screen with a bunch of options(most are in .exe format) but i don't know what to chose. i clicked on vboxlinux addition but it said something about gnu installation needed.

---

### Post by captain_conrad on 2009-03-09
hey man

I also recently started playing with this virtualbox thing and despite problems, it is SO much fun!

First problems i ran into is that the OSE editions that you can get from add/remove programs, won´t let all sorts of things work. Especially USB and graphics card drivers.

Hit search on ubuntuforums and lookup threads on virtualbox. I learned that the OSE edition is nowhere near as usefull as the PEUL version (not that i have the faintest idea what all this means)

So i went to the virtualbox website [http://www.virtualbox.org/](http://www.virtualbox.org/) and downloaded myself the 2.1.4 version.

And? Everything works. Like beautifully. USB, sound, vieo, graphics drivers, CD, DVD, mounting ISO´s, the whole lot works very nicely. Even my internet (inside the virtual machine)

I run Windows XP as a guest OS, and setting the ¨screen¨ resolution was pretty simple, virtualbox has no problem with it, you just gotta figure out how to do it within your guest OS.

I havn´t played with linux OS´s on virtualbox yet, started with the easy windows one
(how easy is it to dominate windows when u have linux?! hahaha!!)

good luck man, have fun!

peace

---

### Post by banana jama on 2009-03-09
i just downloaded virtualbox 2.14 from virtualbox's website and my first problem has been solved. also piece of my second problem been solved i was able to click guest installation and download it through virtualbox. but a problem still remains as i posted previously the virtualguest iso comes up on puppy's screen and when i click the configuration for linux it says that it can't go it because make gnu isn't install also because of the kernel install. 

i do not think that puppy linux plays nice with virtualbox. how can i get puppy linux in an virtual environment to install gnu install and the proper kernel?

---

