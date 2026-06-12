---
title: "Lightweight Gnome"
date: 2006-11-13
forum: Desktop Environments
---

### Post by veli on 2006-11-13
This is a supplement to the Gnome - (semi)minimalistic topic. 
Most of the stuff has been discussed many times, and my initial idea was to collect everything in one place. 

Feel free to add and correct what I've written here.
 
This is for guys who like Gnome and prefer it over XFCE or other WM. It&#8217;ll give you almost the default Ubuntu desktop without the applications, few services, and no language packs. It contains roughly 700 packages. 
  
So, I&#8217;ve started from Dapper alternate CD with the server install option.
After that edit the sources.list file, &#8216;cause you&#8217;ll need the universe repo:
Uncomment every line starting with # 
$ sudo nano /etc/apt/sources.list
Save the file: ctrl+O, press enter and quit  nano by ctrl+X

$ sudo apt-get update

In addition to gnome-core and xorg-core you&#8217;ll need to get a few more packages that we&#8217;ll provide you almost a complete Gnome desktop environment with few apps just to administer the system.

$ sudo apt-get install x-window-system-core gnome-core gdm gnome-media gnome-system-monitor gnome-system-tools gnome-volume-manager gnome-utils gnome-app-install synaptic firefox  

Reboot and you&#8217;ll get the Gnome desktop, but very lightweight and snappy. 

I&#8217;ve added some programs to make my life easier: 

$ sudo apt-get install evince file-roller gdebi alacarte totem sound-juicer

Beyond this set-up you could add whatever program you want (including multimedia codecs, Java, Flash). I&#8217;ve also installed all tools for kernel compiling, dev tools, make, etc, making my Ubuntu having 800 packages, and running at 70 MB RAM when idle after a fresh reboot (see the screenshot). With time, you could expect some increase in memory consumption; usually it comes from xorg and nautilus.


When you set up everything, it&#8217;s time for optimization.
This is what I&#8217;ve done:

1.	Install kernel-686. After a while I compiled my own from kernel.org.
2.	Tweak the file system-I decided to use reiserfs, and did data_writeback, and noatime tricks. 
3.	Clean up all necessary files in Synaptic.
4.	Enable DMA (it is I think) and other hdparm stuff for getting the best from your drives.
5.	Remove unneeded services from booting.
6.	Change swappiness from 60 to 15.
7.	Make CFQ default IO scheduler. 
8.	XML optimization.
9.	Prelink
10.	Preload

I can&#8217;t remember for more, if someone knows please add it here. The links to the 10 optimizations can be found in this forum or Google.
Reboot and you&#8217;ll enjoy a very clean and neat Ubuntu desktop.

Hope this helps out other novices like me to optimize their systems for best performance.
My comp is rather old IBM PIII desktop, 660 MHZ CPU, 256 RAM, 20 GB HDD. My boot time is 1 minute and the system eats around 70 MB when idle. Once it got down to 58 MB, I don&#8217;t know why, but I never got that again.

Opera starts for 4 sec the first time, 2-3 sec. the next ones (in Windows 2000 I got the same-I heavily tweaked Win2000 too). Nautilus starts for 1 sec. I have Cross Over Office Pro 5 for running Origin, first time it starts for 10 sec, the second one&#8211; 5 sec.

Happy ubuntuing, :-D

Some of the tweaks can be found below:

many tweaks:
[http://www.ubuntuforums.org/showthread.php?t=189192&highlight=performance](http://www.ubuntuforums.org/showthread.php?t=189192&highlight=performance)

CFQ:
[http://ubuntuforums.org/showthread.php?t=119220](http://ubuntuforums.org/showthread.php?t=119220)

Faster gnome menus:
[http://www.ubuntuforums.org/showthread.php?t=215119&highlight=faster+Gnome](http://www.ubuntuforums.org/showthread.php?t=215119&highlight=faster+Gnome)

For ext3 file system:
[http://forums.gentoo.org/viewtopic-t-305871-highlight-dirindex.html](http://forums.gentoo.org/viewtopic-t-305871-highlight-dirindex.html)

Swappiness:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by liljoe76 on 2006-11-15
instead of **xwindow-system-core** in the first step, please read **x-window-system-core**.
i dont find any reference to gnome-core nor xorg-core in synaptic, are those a type of bulk package or typos? i'd just like a clarification before i try to do this install again. 
thanks for walkthrough,
-joe

---

### Post by veli on 2006-11-15
gnome-core is in Universe repo. Here are its dependences:

[http://packages.ubuntu.com/dapper/gnome/gnome-core](http://packages.ubuntu.com/dapper/gnome/gnome-core)

---

### Post by liljoe76 on 2006-11-15
ah, yes. thank you. that whole enabling source.list, yea missed that this morning, pre-coffee :) thanks for the reply. 
-joe

---

### Post by disturbedsaint on 2006-11-19
Is the x-window-system-core metapackage really needed?
It depends on xserver-xorg which adds all the video and inputdrivers, which usually is unnecessary.
It also adds fonts and some mesa libs though, so I'm not sure if it can be skipped.

The how-to posted here: [http://www.ubuntuforums.org/showthread.php?t=299669](http://www.ubuntuforums.org/showthread.php?t=299669)
doesn't use both x-window-system-core and xserver-xorg, so it seems to work.

---

### Post by psyke83 on 2006-11-24
disturbedsaint,

Excellent little HOWTO, but I suggest adding usplash, usplash-theme-ubuntu and ubuntu-artwork (not much extra ram used, and avoids gdm theme errors). It gave a new lease of life to an old PII 300Mhz with 196mb ram ;)

---

### Post by aanderse on 2006-11-24
this is what i've been meaning to do for a while (but wasn't 100% sure on the packages i would need, so i never tried it until now).  this doesn't just have to be for lightweight systems though ... the reason i wanted to do this was because of the package bloat in ubuntu.  all the dependancies of meta-packages is really a bog down and just kludges your system up if you don't use all those wacky dependancies.

thanks for the how-to!

---

### Post by Chouca on 2006-12-10
Hi,

this is exactly what I have been looking for with my 128MB Ram and PIII 500Mhz. 

I have followed the instructions but when I re-boot any graphical interface does not show up - still in server mode.

I had a message that gnome-core was replaced by gnome-desktop-environment is that OK?

How will I get de GUI to boot up?

Martin

---

### Post by veli on 2006-12-11
Did you enable the universe repo first by removing the "#' in the beginning of the rows starting with "deb"?

And after that, did you do the "sudo apt-get update" before installing the packages?

Did you install the x-window-system-core package?

Gnome-desktop-environment is also in Universe and would have given you complete and working desktop. I don't know what happen with your installation.

When you are in command line interface log in with your user ID and type startx to see what will happen.

It seems to me that the X-system is not installed.

---

### Post by Chouca on 2006-12-11
Hi Veli,

well, I did exactly as You described and then - I got the "gnome foot" and nothing more, I really need some light type Ubuntu so I have now started all over again with a normal Dapper install... I can get a Dapper install to work OK but what I really WANT to achieve is a a light version that my laptop can cope with.

Thanks anyway and if You have got an idea how to get to a light Ubuntu "backwards" from a normal Ubuntu install I am all ears!!!

Regards

Martin

---

### Post by veli on 2006-12-12
Hi Martin, I'm sorry it didn't work for you. It worked for  me after few attempts. What exactly are your problems? Discuss here, may be somebody else could find a solution.

You could slim the default Dapper certainly. You could start removing all fonts for languages you don't need. You could decrease the number of running services, see in the links above. Removing of packages will also provide you with some lightweight Gnome. Open office is a bit hard to remove though. But be careful when removing packages because you could remove some dependences and f...d up your system. Just don't hurry up, explore the system, get known to it. Tweak the ext3 file system and install 686 kernel, this will boost the speed a bit. I'm also a new user, running Linux for a year, and I'm learning from my mistakes. But believe me, it's fun.

Regards,

Veli

---

### Post by Chouca on 2006-12-14
Thanks Veli,

I have now installed Xubuntu and is evaluating it - looks promising.

Regards

Martin

---

### Post by rskovacs on 2007-01-08
Veli,

Thanks again for putting this guide together.  I'm excited to get it working!  I am in the process of trying, but I've hit a snag and I was wondering if you could help.  I have the default server install up and running, but I can't connect to the Internet to carry out the other steps.  It has something to do with my university's ISP.  When I have installed the desktop version of Ubuntu, the first thing I would have to do is deactivate and then reactivate my Ethernet connection in Network Manager, and then it would work, but for whatever reason the connection is not automatically made at first. (although isn't that the point? arrgh)

So my question basically is: is there a way to reactivate the Ethernet connection using the packages available in the default server install?  Thanks in advance for any help you can offer.

---

### Post by veli on 2007-01-09
What kind of IP do you have? Is it a dynamic or static one? If it's dynamic (but I don't think it's your case) the internet connection should be up upon installation of the server. If it's static, you have to configure that during the server install. I think you've been assigned a static IP address, subnet mask, default gate and DNS servers from your university administrator. It's possible to configure the IP stuff after installation, but I don't know the command line for that. Hopefully somebody else could help you in resolving this issue. 

Otherwise, you could start over with the server install. You'll need your IP information ready. When the server install goes into "configuring network with DHCP" or something like that, select and press "Cancel" and this will provide you with dialogs for inputting your IP, mask, DNS servers, etc. That is, you can configure your static IP address instead of dynamic one.

I remember, I did that once at work. I installed everything as described in the guide (because of the faster connection), but with static IP configuration. Later on, at home, and with the GUI, I reconfigured the ethernet card for DHCP, rebooted and internet was up and running.

Hope this helps.

---

### Post by ginjabunny on 2007-10-20
I can't get this to work properly on 7.10 Gutsy server, I have tried twice now (it worked on 7.04).

All the packages install ok, it seems as though it is missing some sort of gnome window manager components, when I open a window there is no title bar so no minimise etc and I can't resize by dragging the corners. Also the appearance app won't let me do any customising at all and just hangs, I have tried to find if there are bits missing but I can't figure it out. I even did apt-get install gnome-desktop-environment but still the same.

Anyone got any idea what is missing??

---

### Post by phreaky- on 2008-05-14
I got the same problem as the person above me. I found out that the problem lies within the metacity package which doesn't seem to start automaticly how to solve this for Ubuntu 7.10.

---

### Post by ladjack on 2008-06-10
**For Ubuntu 8.04**

*Note: It is for fresh installation instance. So there is NO previous /home partitions from old system. As old system settings from dot files may affect new installation.*

**1.** Get .iso image of ubuntu-8.04-server. Burn cd using the image.
**2.** Make general installation of minimal system. After booting from cd just hit 'Enter'.
**3.** After installation is complete enter the system and:
[INDENT]**3.1.**
```
sudo vim /etc/apt/sources.list
```
Uncomment all commented sources in that file. Remove '#' symbol before source entry line.
*Note: You may change 'vim' with any other text editor, for example: nano*
[/INDENT]
[INDENT]**3.2.**
```
sudo apt-get update
```
[/INDENT]
[INDENT]**3.3.**
```
sudo apt-get install x-window-system-core gnome-core gdm ubuntu-gdm-theme
```
**x-window-system-core** - This metapackage provides the components for a standalone workstation running the X Window System. It provides the X libraries, an X server, a set of fonts, and a group of basic X clients and utilities.
**gnome-core** - These are the essential components of the GNOME.
**gdm** - Gnome Display Manager. gdm provides the equivalent of a "login:" prompt for X displays- it pops up a login window and starts an X session.
**ubuntu-gdm-theme** - This package contains the GDM theme. Installation of this package help us to avoid gdm's alerts on start-up like "Can't open file /usr/share/gdm/theme/Human/Human.xml"

Also when we first loging in Gnome may alert you that applet Fast User Switching is not loaded. That is cause we didn't install it. I jast remove it from top panel as i don't need it. But if you are using that stuff, you may also install following package: **fast-user-switch-applet**
[/INDENT]

That is all -) A very base system is complete.
Usage of RAM is about 70-80 MB.
Installed packages is about ~570.
Space used about ~1 GB.

---

