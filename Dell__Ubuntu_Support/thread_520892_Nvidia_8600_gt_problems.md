---
title: "Nvidia 8600 gt problems"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by xspeed9190 on 2007-08-08
So im new to linux... just a computer geek tryin to learn more.  out of all the distros i have tried i really like ubuntu but of course thats the only one that doesnt work on my laptop.  I load it up on my pc runs great i have an older nvidia 7950gt and it runs fine.  Now i just bought a dell 1520 with the nvidia new 8600gt on windows its a monster for a laptop card, i had pclinuxos, gotta say not a fan.  I think i just like gnome better than kde.  seems like kde is just like windows pretty much and gnome is more like mac.  I love windows but i just feel kde is to similar.  anyway, the problem is like all the rest of the dell people on here that say we get the xserver crash.  Now i understand its a lack of video card recignition.  i assume it means there is no generic compatability and no exact driver ie. nvidia driver.  I followed the instructions somone posted [http://ubuntuforums.org/showthread.php?t=509408]("http://ubuntuforums.org/showthread.php?t=509408")   now i donno if is the fact that im new to linux or if it was poorly stated.  but i made another partition in windows and only put those files on the partition.  when i follow the install instrucitons it says cannot find files.  now am i missing an instruction to access a directory or am i doin somthin else wrong.  It jsut seems readin though here theres some other nubs like myself that need step by step instructions.  any help would be greatly greatly appreciated.

Thanks 
Nick

---

### Post by Obor on 2007-08-09
As far as I can see the instructions you followed were not for Nvidia cards.
If you want to install driver for nvidia 8600GT on a new install of Ubuntu Feisty then this worked for me without any problems:
[http://www.robdian.co.uk/content/view/56/27/](http://www.robdian.co.uk/content/view/56/27/)

---

### Post by iAndrew on 2007-08-09
The follow link above did not work for me. It might just be my doing. So, make sure you backup your xserver before you do that.

---

### Post by ridgeland on 2007-08-10
try this thread:
[http://ubuntuforums.org/showthread.php?t=432056](http://ubuntuforums.org/showthread.php?t=432056)
I used ENVY to install nvidia on my Dell-Ubuntu E520n.

---

### Post by PowerlessRacing on 2007-08-15
> **Obor said:**
> As far as I can see the instructions you followed were not for Nvidia cards.
If you want to install driver for nvidia 8600GT on a new install of Ubuntu Feisty then this worked for me without any problems:
[http://www.robdian.co.uk/content/view/56/27/](http://www.robdian.co.uk/content/view/56/27/)

I ran through this tutorial and it was extremely easy to follow, but I am left with questions.

When I type: 
  glxinfo | grep "direct rendering"
It does say "Direct rendering: Yes" so I'm assuming that things went well for me.

Step 5 directs the reader to run 
  sudo nvidia-xconfig
but this step for me didn't do much.  Output was along the lines of:
  Using X configuration file: "/etc/X11/xorg.conf".
  Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
  New X configuration file written to '/etc/X11/xorg.conf'
and then it dumped me back at a prompt, without so much as asking me what screen resolution I would like.  I went into the System -> Preferences -> Screen Resolution menu and the highest resolution available to me was 1024x768.  I know the card will do something like 2560x1600 (MSI NX8600GT OC Edition 256MB That resolution is per the box, per the website it can do 2048 X 1536 [http://www.msicomputer.com/product/p_spec.asp?model=NX8600GT-T2D256E_OC&class=vga](http://www.msicomputer.com/product/p_spec.asp?model=NX8600GT-T2D256E_OC&class=vga)).  The monitor I have will do 1680x1050 (ViewSonic vx2235wm [http://www.viewsonic.com/products/desktopdisplays/lcddisplays/xseries/vx2235wm/](http://www.viewsonic.com/products/desktopdisplays/lcddisplays/xseries/vx2235wm/)).  In the past I have had to edit the xorg.conf file to add resolutions and I have no qualms doing that, but the tutorial made it sound like all that good stuff would be detected and setup for me.  Do I need to do it myself, or did I miss something in the tutorial?

The next question is with regard to the Extensions section.  The tutorial suggests enabling the composite setting in the extensions section but when I looked I didn't have an extensions section.  I also have not installed Beryl or Compiz yet, I wanted to get everything working before I did that.  If I haven't installed it yet, should I even have an extensions section?  If not, this wasn't made particularly clear in the tutorial (just a recommendation to clarify, not an attack) and if I should, well, how do I figure out what is wrong?  I did notice in the tutorial that it said this was optional, but optional indicates to me that I should have this section, and I don't.  I know it's easy enough to add, but I want to make sure I'm supposed to.

I'm also not 100% sure that I picked the right driver.  I have an Intel Core 2 Duo E6750 2.66GHz processor and a Gigabyte P35C-DS3R motherboard, with 2GB Corsair XMS2 (2x1GB) DDR2 Memory.  I chose the:
Linux AMD64/EM64T
Latest Version: 100.14.11 
drivers off the NVidia website.  Maybe you could clarify for me that I made the correct choice...

Thanks for your time.

---

### Post by PowerlessRacing on 2007-08-16
Silly me.  If you type:
sudo nvidia-settings
you get a nice configuration window that even detected that I had my TV hooked up to an S-Video out on my video card and allowed me to configure it (easily!) for Twin View, the same way my XP is set up.  Neat.
It would be really helpful if you added that to your tutorial.  

I still don't know about the extensions section but I'm fairly confident now that I picked the right driver.  Thanks.

---

### Post by daiwai on 2007-08-23
> **Obor said:**
> As far as I can see the instructions you followed were not for Nvidia cards.
If you want to install driver for nvidia 8600GT on a new install of Ubuntu Feisty then this worked for me without any problems:
[http://www.robdian.co.uk/content/view/56/27/](http://www.robdian.co.uk/content/view/56/27/)

Thanks Obor, this worked for me! :)

---

### Post by Obor on 2007-08-23
> **daiwai said:**
> Thanks Obor, this worked for me! :)

Good to know :) I've made few minor changes to it recently to make it easier to follow; based on comments from few people...

---

### Post by Marat Galiev on 2007-08-27
Please use this guide,i write it today,then my 3d with 8600GT worked!
This my way:
```

Only 27 steps:)
1)Install packages xserver-xorg-dev,pkg-config,libc6-dev.
You an find them at packages.ubuntu.com.
2)Press ctrl+alt+F2.
3)sudo nano /etc/init.d gdm stop
4)cd /there/your/driver/location
5)sudo sh NVIDIA-100.14...-xxx.run --ui=none
(without GUI menu).
To the question with nvidia-xconfig answer "Yes".
6)sudo nano /etc/default/linux-restricted-modules-common
Edit line
DISABLED_MODULES="nv nvidia_new"
7)sudo cp /lib/modules/2.6.20-15-generic/kernel/drivers/video/nvidia.ko /lib/modules/2.6.20-15-generic/volatile/
8)sudo modprobe nvidia
9)/sbin/ldconfig
10)/sbin/depmod -aq
11)reboot
12)step 7
13)cd /lib/modules/2.6.20-15-generic/volatile/
13)sudo insmod ./nvidia,ko
14)sudo modprobe nvidia
15)step 9
16)step 10
17)sudo /etc/init.d/gdm start
18)reboot
19)cd /lib/modules/2.6.20-15-generic/kernel/drivers/video/
20)sudo cp nvidia.ko nvidia_new.ko
21)sudo insmod ./nvidia.ko
22)step 9
23)step 10
24)ctrl+alt+F7
25)sudo nvidia-xconfig
26)reboot

```

OK!So,please check you glxinfo command.
You can see what:
[B]OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8600 GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.11[/B]
Thank's.

---

### Post by Surgeon General on 2007-10-19
anyone tried to use nvidia drivers from [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)

---

### Post by captainron042 on 2008-01-10
New linux user here, too.

I've just gotten my 530N from dell with Ubuntu 7.10 pre-installed.

I've got the Nvidia 8600 GT on mine with two digital outputs and an s-video out.

My monitor's great with the digital out, but I plugged my projector system into the S-Video out, and I get nothing.

I've tried system - Screen and graphics window, but I cannot unclick the default screen radio, if that's what I need to do anyway.

Please help. It would be appreciated. I need to watch my Netflix online!

---

### Post by CalvertaBeck on 2008-01-12
I revamped a Dell Inspiron 2650 with Feisty (from a ComputerActive CD). I rencently installed Gutsy Gibbon and have a problem with my display - there is about an inch of screen all the way arounf the monitor that is black... Device manager claims I have a nv11 (nvidia GForce 2 Go). What driver should I use to recitfy my problem? OR have I a different problem altogether?

New to LInux, loving it but frustrated :-)

---

