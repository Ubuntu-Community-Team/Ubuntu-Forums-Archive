---
title: "cant run ubuntu !!!"
date: 2009-03-30
forum: General Help
---

### Post by raedbenz on 2009-03-30
Hi,,

i installed ubuntu8.10 to an old PC.
I remove the bootable Cd and i restart. In the login screen, i enter the username and password, and it hangs just after that. there is only orange screen and the mouse pointer in the middle of the screen.hints??
thanks

---

### Post by _Purple_ on 2009-03-30
Was your cd burnt properly? Did you check the hash?

---

### Post by raedbenz on 2009-03-30
yes it was....i t has been tested on other PC.
what do u mean hash??

---

### Post by _Purple_ on 2009-03-30
I meant the MD5 sum. You can check the following link:

[click here](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by raedbenz on 2009-03-30
is it possible to be hardware issue??

---

### Post by raedbenz on 2009-04-02
i got another cd of ubuntu 8.10 and i have the same problem and when i run Ubuntu from cd i get the same problem..????
ubuntu8.04 works fine...hints???

---

### Post by SteveNorman on 2009-04-02
how old is the pc? also can you run it from the cd? If you can run it from a live cd still booted then it should install pk). If your hardware is very old you may have to stick to older versions.

---

### Post by raedbenz on 2009-04-02
Hi,,
it is compaq EvoD510, P$ 1.8Ghz, 512 Ram
i cant run 8.10 from cd only 8.04...

---

### Post by SteveNorman on 2009-04-02
need more ram, id stay away from gnome and use fluxbox, but you really need more ram

---

### Post by SteveNorman on 2009-04-02
you may want to try one of the netbook remixes or use a lite distro like dam small linux.

---

### Post by raedbenz on 2009-04-02
i dont think the RAM is bad..

[https://help.ubuntu.com/8.10/installation-guide/i386/minimum-hardware-reqts.html]("https://help.ubuntu.com/8.10/installation-guide/i386/minimum-hardware-reqts.html")

---

### Post by sahabcse on 2009-04-02
Hi

Login to the recovery mode and fix the grub. or press alt+ctr+F1 and type startx.

---

### Post by SteveNorman on 2009-04-02
If you can log into a terminal I would try getting another desktop environment. like xfce4 or fluxbox. Gnome and kde are heavy resource hogs, and I would bet thats where the problem is. Another possibility is that 8.10 doesnt have a module for your video card. 

```
sudo aptitude install fluxbox

on log in

change sessions>fluxbox


```

can you post the results of lspci?

---

### Post by coffeecat on 2009-04-02
> **SteveNorman said:**
> need more ram, id stay away from gnome and use fluxbox, but you really need more ram

Why on Earth are you saying this? The OP has got 512MB RAM. My laptop has "only" 512MB RAM, and I've been happily running various gnome and KDE distros on it for the last four years. Ubuntu is running fine on it at the moment. And...

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> Recommended minimum requirements Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

[LIST]
[*]700 MHz x86 processor
[*]**384 MB of system memory (RAM)**
[*]8 GB of disk space
[*]Graphics card capable of 1024x768 resolution
[*]*Sound card*
[*]*A network or Internet connection*
[/LIST]
Before the OP installs fluxbox, let's see if we can find the real issue.

---

### Post by coffeecat on 2009-04-02
> **raedbenz said:**
> i got another cd of ubuntu 8.10 and i have the same problem and when i run Ubuntu from cd i get the same problem..????
ubuntu8.04 works fine...hints???

That's interesting. I'm tempted to say use 8.04 if it works. And that's not being flippant. version 8.04 is the long-term support version. You don't have to run 8.10, and your problem might go away in 9.04. 

However, you haven't told us what graphics card you're using. You don't have two nvidia cards do you - perhaps onboard and PCI/AGP card? there's an issue in 8.10 with two nvidia cards.

---

### Post by SteveNorman on 2009-04-02
ok

---

### Post by rahul_bhise on 2009-04-09
may be this will help
[http://ubuntuforums.org/showthread.php?p=6075895#post6075895](http://ubuntuforums.org/showthread.php?p=6075895#post6075895)

---

### Post by CrusaderAD on 2009-04-09
I had this exact problem... it was an issue with my hardware. This fixed it:

While booting, Ubuntu provides a way to go into boot menu just like any other operating system and in the menu it provides an option to boot into recovery mode. The recovery mode is nothing but the "Safe mode" that we are all very much familiar in the Windows world. The recovery mode essentially provided me with root access to the file system without asking for the login prompt. Once I was at the bash prompt, I entered the command mentioned above to remove the desktop and it gave me a very helpful message saying that dpkg was aborted during configure and to fix it Ubuntu gave me the command to run.

```
sudo dpkg --configure -a
```

Once I ran the command above, it started running the configuration of the desktop from where it had left and completed the installation without further troubles.

---

### Post by CrusaderAD on 2009-04-09
I had this exact problem... it was an issue with my hardware. This fixed it:

While booting, Ubuntu provides a way to go into boot menu just like any other operating system and in the menu it provides an option to boot into recovery mode. The recovery mode is nothing but the "Safe mode" that we are all very much familiar in the Windows world. The recovery mode essentially provided me with root access to the file system without asking for the login prompt. Once I was at the bash prompt, I entered the command mentioned above to remove the desktop and it gave me a very helpful message saying that dpkg was aborted during configure and to fix it Ubuntu gave me the command to run.

```
sudo dpkg --configure -a
```

Once I ran the command above, it started running the configuration of the desktop from where it had left and completed the installation without further troubles.

---

### Post by lolol i r linux noob on 2009-04-11
why doesnt he just use ubuntu 8.04 and then press alt+f2 and type update manager -d.
That will search for a new distro and update it that way. maybe tht will fix the problem.

---

