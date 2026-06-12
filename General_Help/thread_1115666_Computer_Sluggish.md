---
title: "Computer Sluggish ?"
date: 2009-04-04
forum: General Help
---

### Post by suffer1989 on 2009-04-04
Hey I installed Ubuntu (8.10) about 6 months ago and all is going well. however, recently, the system has began to run really sluggishly. It takes about 2-3 seconds to open a folder(as opposed to instanty before), and it takes TOTEM about 20seconds to open, and play a video file(as opposed to 1-2 seconds previously). During this, there are no spikes in CPU usage. Everything elso appears to run fine, EG desktop switching, Advanced compiz effects, opeining applications, etc... Also, the menu in the top menu bar also respond really slowly ? 

Has anyone been having this issue- the entire reason i moved to linux was that it is (usually) faster than windows.

Thanks :D

---

### Post by vandorjw on 2009-04-04
1.) How much RAM do you have?
    Not enough memory can seriously slow down your PC.
2.) Do you have a lot of programs/daemons running on startup?
    Running to many programs at once puts stress on your CPU and can make you run out of memory.

Ofcourse, it might be a kernel issue.

When you start up your computer, is it still slow if you select an older kernel using grub?

---

### Post by suffer1989 on 2009-04-04
I have plenty of ram (3GB), and not that many programs on startup. It was running very fast untill a few days ago... I didnt do any major Installations/Uninstallations  either.  

As for Kernel, it only give me 3 options : The OS, the OS in safemode, and Memtest...
The kernel is same for each of them...

---

### Post by DJonsson2008 on 2009-04-04
If you have plenty of memory try using preload which can be found 
in the synaptic repository. 

Here is more info on that. It does the job for me.

[http://www.techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/](http://www.techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/)

---

### Post by iswear on 2009-04-04
You might want to try linux mint its the same thing as ubuntu but it runs a lot faster, atleast it did for me and i only have a 1.3gh prossser and a gig of ram.

---

### Post by Monotoko on 2009-04-04
Yeah, but it shouldnt be sluggish on his system with 3GB of RAM, i only have 1GB of RAM and it works smooth as anything

so something appears to be making it slugglish

can you open up your system moniter by typing gnome-system-manager into the terminal and post the output please?

---

### Post by DJonsson2008 on 2009-04-04
Can Linux Mint be added to boot up page session options
like XFCE/Xbuntu?

If so I sure like to try it.

* NOTE: Its not easy drilling down to the performance bottlenecks
in Ubuntu is what I'm finding. I'm sitting here with a dual   intel cpu 1.8 ghz 1 gig of ram and my PIII 500Mhz Windows 2000 machine out performs Ubuntu on many tasks.

Xbuntu is a bit better, but still not as fast as W2K on a PIII
500 MHZ with Xbuntu running on a dual 1.8ghz.

---

### Post by lswb on 2009-04-04
Check to see if your disk is close to being filled. The command "df" will show per cent use.

---

### Post by suffer1989 on 2009-04-05
Im fairly sure i have plenty of space, but heres the output :

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5             34446012  23517964   9178180  72% /
tmpfs                  1551456         0   1551456   0% /lib/init/rw
varrun                 1551456       204   1551252   1% /var/run
varlock                1551456         0   1551456   0% /var/lock
udev                   1551456      2868   1548588   1% /dev
tmpfs                  1551456        36   1551420   1% /dev/shm
lrm                    1551456      2004   1549452   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda1            103860188  76431632  27428556  74% /media/mediadrive
/dev/sdb1            976727896 443981208 532746688  46% /media/New Volume

```

---

### Post by lswb on 2009-04-05
> **suffer1989 said:**
> Im fairly sure i have plenty of space....


I agree, disk space is not the problem.

---

### Post by VII on 2009-04-05
Just want you to know I have the same/similar problem. Everything is a bit slow. Not to mention having multiple tabs open in FF3. It didn't use to be like this. 2gb ram here, and there's enough disk space.

---

### Post by suffer1989 on 2009-04-06
The system manager command doesnt work for me :-/

```
sufy@sufy-laptop:~$ gnome-system-manager
bash: gnome-system-manager: command not found
sufy@sufy-laptop:~$ 


```


BTW this sluggishness began fairly recently, about 1 month back it was runnig fine (IE really well)

---

### Post by DJonsson2008 on 2009-04-06
You need to install the gnome-system-monitor 
either via synaptic or via command line
i believe the command is

> apt-get install gnome-system-monitor 

Then go check the processes tabs, it can provide significant leverage and insight. It sorts like an Excell spread-sheet, you can click on the CPU or MEM columns and see whats eating your resources, very similar to windows task monitor.

Also Xbuntu has proven to be very good in helping resolve things.
You can load it via synaptic as well "xfce", and it inherits all most of your Ubuntu settings, from there you also use gnome-system-monitor and compare speed with Ubuntu.

---

### Post by DJonsson2008 on 2009-04-06
Should also mention that have made considerable performance gains on my sluggish workstation by adding an nvidia video card and getting the video driver and video settings correct using the GUI's that you get with displayconfig-gtk and jockey-gtk from the root terminal. Not sure where these both are in the menus.

---

### Post by suffer1989 on 2009-04-06
> **DJonsson2008 said:**
> You need to install the gnome-system-monitor 
either via synaptic or via command line
i believe the command is

> apt-get install gnome-system-monitor 

Then go check the processes tabs, it can provide significant leverage and insight. It sorts like an Excell spread-sheet, you can click on the CPU or MEM columns and see whats eating your resources, very similar to windows task monitor.

Also Xbuntu has proven to be very good in helping resolve things.
You can load it via synaptic as well "xfce", and it inherits all most of your Ubuntu settings, from there you also use gnome-system-monitor and compare speed with Ubuntu.

I did : ```
sufy@sufy-laptop:~$ sudo apt-get install gnome-system-monitor 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-system-monitor is already the newest version.
The following packages were automatically installed and are no longer required:
  libsm-dev libcaca-dev libboost-regex1.34.1 libgsf-gnome-1-114 libice-dev
  libgoffice-0-common lsb-languages texi2html diffstat libtheora-dev
  libaudiofile-dev libaudio-dev libsdl1.2-dev postfix lsb-graphics quilt
  libdc1394-22-dev lsb-desktop m4 ncurses-term mesa-common-dev libsysfs-dev
  libdirectfb-extra libglu1-xorg-dev libcucul-dev libdirectfb-dev
  libgnomescan0 bodr libgnomescanui-common doxygen libglu1-mesa-dev libfltk1.1
  libxt-dev lsb pax virtualbox-ose-source libraw1394-dev libesd0-dev
  lsb-multimedia libgnomescanui0 libasound2-dev libgl1-mesa-dev lsb-printing
  libgnomescan-common libslang2-dev libncurses5-dev bsd-mailx mailx
  libartsc0-dev lsb-core alien libgsm1-dev libaa1-dev lsb-cxx
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sufy@sufy-laptop:~$ 

```

, then ran

```
sufy@sufy-laptop:~$ gnome-system-manager
bash: gnome-system-manager: command not found
sufy@sufy-laptop:~$ 

```

....

I assume ive already got it installed ? regardless, here is a screenie of the GUI.

I understand firefox being a hog, but firefox is running as slow(or as fast) as normal, its just everything else thats running slowly.

---

### Post by suffer1989 on 2009-04-06
I just remembered, this slow responsiveness began after i was having some issues with pulse audio. I installed it, but it was giving me problems, so inorder to remove it, i was instructed to run a series of commands. One of those commands involved removing gnome desktop or something. anyways, the guide told us to remove pulseaudio (and i assume with it, gnome desktop, and reinstall gnome desktop). after this procedure, my desktop, and file managment has been really sluggish.

---

### Post by DJonsson2008 on 2009-04-06
i'm finding pulse audio works better in Xbuntu for some reason,
in Ubuntu I'm not using it anymore.

perhaps you can though try to get gnome-system-monitor 
going via a root terminal or
$  sudo gnome-system-monitor

---

### Post by suffer1989 on 2009-04-06
Ive disregarded pulse audio for reasons that are not important right now. The thing which has caused my system to go sluggish is the reinstall of Gnome desktop (see post 16). Are there anyways to restore this to the factory defaults (I.E as if youre installing a fresh copy of Ubuntu ) ?

I found the guide here (to remove pulse audio) 

[http://ubuntuswitch.blogspot.com/2008/07/how-to-removeuninstall-pulse-audio.html](http://ubuntuswitch.blogspot.com/2008/07/how-to-removeuninstall-pulse-audio.html)

and someone mentions that "ubuntu-desktop" will also be fromved. I went to another site, where the complete instructions were given (i cant find them). Upon rebooting, i had to login (before, i was set to login automatically), and Wicd was replaced by the default network managers...


so..... can i re-install "ubuntu-desktop" from a live CCD, as though i was installing a fresh copy of Ubuntu ?

---

### Post by DJonsson2008 on 2009-04-06
Some people say try creating a new user, and
see if the problem is local to the account.

Some people say install xfce4 (aka Xbuntu) and
try to deduce what is happening based on what
you see there. xfce4 is available via the
synaptic installer. once it's installed log
off chose the xcfe from the loggon screen options
and see if its any better. 

you can then use applications>settings>settings manager 
and work xbuntu's slightly easier interface to see what 
autostarting.

as to reseting gnome you can check this link, but do read
the comments and caveats that follow the blog before trying
anything.

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

there may be other solutions out there but the above may
be a start.

whatever the case you should likely either get a grip on TOP
or the GUI gnome-system-manager to see what your system 
is doing at some point in the process.

---

### Post by suffer1989 on 2009-04-06
> **DJonsson2008 said:**
> Some people say try creating a new user, and
see if the problem is local to the account.


[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

there may be other solutions out there but the above may
be a start.

whatever the case you should likely either get a grip on TOP
or the GUI gnome-system-manager to see what your system 
is doing at some point in the process.

The problem also is present on any new accounts i create.

Also, Exactly what does this do ?

```
    rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

???

---

### Post by ubuwatson on 2009-04-06
I had the same problem with 8.10.  I downloaded the latest nvidia drivers for my graphics card and now my machines is ridiculously fast.  I would have never guessed the video card, as everything I did was slow (from loading an application or just opening a file or picture).

---

### Post by suffer1989 on 2009-04-06
I just re-installed ubuntu-desktop using synaptic, and everything has been rectified. Thanks for all the support :D


:D :D :D

---

### Post by DJonsson2008 on 2009-04-07
I'm not exactly sure how ubuntu works but I get the impression that how efficiently or not efficiently ubuntu uses the video drivers is a major factor in performance. the same is somewhat 
true in windows, i've had slower lower-powered w2k and xp machines gain considerable leverage after the installation of a good 64 or 128MB plus video card. The results though are no where near as dramatic as what I've experienced with Ubuntu,
in this Intel GMA onboard graphics card scenario, Intel GMA and
Ubuntu did not like each other at all.

Anyhow in the meantime I've made the switch to Xbuntu for daily work for now. It is a bit more snappy for most things, I'm doing web programming and Xbuntu for now suits me fine, its good though I can switch to Ubuntu at anytime for its expanded features when needed simply by choosing to do so at the logon window.

---

