---
title: "Question: Desktop performance on Ubuntu?"
date: 2005-07-22
forum: Desktop Environments
---

### Post by Morcas on 2005-07-22
Having played around with Ubuntu using both Gnome and Xfce it seems to me that the desktop performance is much slower under these environments than Windows XP or Server 2003.

That is, window opening, moving etc.  It just seems 'sluggish'

I was wondering if I am missing something, some configuration file/s that may need be tweaked to provide the same level of performance I see under the MS OS environments?

My system (not a super spec)

P4 2.4
MSI 865 PE Neo 2
MSI FX5600
512 Dual channel PC3200

I have the Nvidia drivers from the rep installed and working.

---

### Post by pmj on 2005-07-22
I think that's just the way it is. :(

---

### Post by mad_scientist03 on 2005-07-22
I would try to use window managers, insteall of full-blown desktops, and see if your performance increases. In an extreme over-simplification, window managers just do that, manage your windows, while desktops try to do a host of other things in addition to managing windows.

I use IceWM exclusively, and I am very happy with its performance. You can also try Enlightenment, FVWM, WindowMaker, etc.

---

### Post by damonw5 on 2005-07-22
[QUOTE=Morcas]Having played around with Ubuntu using both Gnome and Xfce it seems to me that the desktop performance is much slower under these environments than Windows XP or Server 2003.[/QUOTE]

Yes, but wait a year, install applications, browse the internet, download files, etc. 
Now which one is faster and which one needs a complete reinstallation to clean up spyware, ads, obsolete programs, registry entries, etc?

---

### Post by Morcas on 2005-07-22
[QUOTE=mad_scientist03]I would try to use window managers, insteall of full-blown desktops, and see if your performance increases. In an extreme over-simplification, window managers just do that, manage your windows, while desktops try to do a host of other things in addition to managing windows.
[/QUOTE]

I appreciate that 'desktops' have to do more, but really thats all MS offers and on my system they are pretty quick.

> I use IceWM exclusively, and I am very happy with its performance. You can also try Enlightenment, FVWM, WindowMaker, etc.

I have looked at IceWM but the default themes are terrible, guess I'll take a look around for something better. I'll also take a look at Fluxbox, heving used Blackbox and BBLean on windows it should be familar.

Thanks.

---

### Post by maruchan on 2005-07-22
Give Kubuntu a try. KDE can be much more responsive.

(Note: I use Gnome every day)

---

### Post by Morcas on 2005-07-22
[QUOTE=damonw5]Yes, but wait a year, install applications, browse the internet, download files, etc. 
Now which one is faster and which one needs a complete reinstallation to clean up spyware, ads, obsolete programs, registry entries, etc?[/QUOTE]


I appreciate that many seem to have these problems but to be honest I haven't had to reinstall XP (unless you include installing SP2) for the last 18 months or so and that box is on 24/7, nor have I had a virus, trojan or any spware. My system is as fast today as it was when first installed, if anything, with the tweaks it has had applied, its faster.

Providing one knows one's way around a system its easy enough to prevent these things and to keep one's system clean.

I imagine Linux is similar. one just needs to know the 'how' and as yet I don't. 

By the way, I am not knocking ubuntu here, just stating a fact and I want to know how to make things better.

Thanks

---

### Post by Morcas on 2005-07-22
[QUOTE=maruchan]Give Kubuntu a try. KDE can be much more responsive.

(Note: I use Gnome every day)[/QUOTE]

I did think about downloading kde for ubuntu as that would be an easier option being on dialup. But would that really be more responsive than say xfce?

Thanks

---

### Post by az on 2005-07-22
I think that window rendering is slightly less responsive in linux than windows, but overall, I seem to find that on a varietry of machines (fast and slow), Ubuntu runs faster than Windows XP.

There are fewer lags, and you can be more productive, and not spend time waiting for something to load or wondering whether your click got noticed by the OS.

---

### Post by varunus on 2005-07-22
I've heard people complain that GNOME has been unresponsive, but for me, its much much faster than Windows XP...

One thing to ask, though:  how big is your swap partition on your computer?  I made mine equal to the amount of RAM I have (512 MB).

Windows seem to open quickly for me, and don't seem sluggish...

Also, do you have DMA enabled on your hard drive?  (There's a howto on this forum somewhere...)

---

### Post by hapibooda on 2005-07-22
There are about a gazillion tips for enhancing your display and improving performance in these forums.  Here are a few that I use with my nVidia FX 4400.

1. Set your resolution to 96dpi (a display enhancement).  I got this tip from a [Hoary Clear-Type Fonts HOWTO](http://www.ubuntuforums.org/showthread.php?t=20976&highlight=displaysize)  by deelerious:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/xorg.conf

Look for the section labeled "Monitor" and add the following before the EndSection:

#DisplaySize 270	203 # 1024x768 96dpi
#DisplaySize 338	254 # 1280x960 96dpi
#DisplaySize 338	270 # 1280x1024 96dpi
#DisplaySize 370	277 # 1400x1050 96dpi
#DisplaySize 423	370 # 1600x1400 96dpi

Uncomment the line corresponding to your current resolution.

Save the file and reboot X (CTRL+ALT+BACKSPACE).

FYI...To get other values, use the following formula: displaysize = <pixelsize>/96*25.4

2.  Use nVidia native GART and not the kernerl's GART (Performance Improvement).  I got this tip from wyfling in the [nVidia Driver Broken](http://www.ubuntuforums.org/showpost.php?p=253989&postcount=3) thread:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/xorg.conf

Look for the section labeled "Device" and add the following before the EndSection:

Option "NvAGP" "1"

Save the file and reboot X (CTRL+ALT+BACKSPACE).

3.  Enable the rendering option for your nVida card (Performance Improvement).  I got this tip from arnoct's [Making Your Windows Look Super Sweet in Hoary](http://http://www.ubuntuforums.org/showpost.php?p=98674&postcount=1) thread:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/xorg.conf

Look for the section labeled "Device" and add the following before the EndSection:

Option "RenderAccel" "true"

Save the file and reboot X (CTRL+ALT+BACKSPACE).

---

### Post by Morcas on 2005-07-22
[QUOTE=azz]There are fewer lags, and you can be more productive, and not spend time waiting for something to load or wondering whether your click got noticed by the OS.[/QUOTE]

Its interesting, thats exactly the opposite I see, with XP I don't have any lag but under ubuntu, things just don't happen as quickly.

I am sure its a matter of configuration, but the question is what and where?

---

### Post by ritger on 2005-07-22
There are a few tweaks you can do to increase performance, but from reading most of the TS posts he/she seems to be interested more in running Windows then trying to fix this (no own suggestions, researched material).

That said, one of the things i usually do first on my Athlon 2600+ is remove the via_agp driver and use the nvidia built-in nvagp driver. This almost doubles responsiveness on my Abit motherboard with GeForce 2. You have to figure out which agp driver you have loaded, add that to /etc/hotplug/blacklist (to prevent it from being loaded at boot) and add the ```
NvAGP "1"
``` option to /etc/X11/xorg.conf right below the ```
Driver "nvidia"
``` bit.

Checking DMA is important too (as someone else already mentioned). In my experience DMA is enabled by default for harddrives, but not for my cd drives (DVD burner and DVD player). Check this with ```
hdparm /dev/hdX
``` where X is your master/slave number (usually a through d). ```
hdparm -d1 -u1 -c1 /dev/hda 
``` is usually safe (look up in the manpage what that does exactly. No warranty given though, messing around with hdparm can seriously screw with your system.

Disabling services to keep them from being booted saves on memory. For instance, replacing postfix by exim (or disabling postfix all together (which can cause your system to malfunction)) saves on resources.

You can also try using the cfq kernel scheduler, on some hardware it seems to outperform the default anticipatory scheduler. Edit /boot/grub/menu.lst and add ```
elevator=cfq
``` to the kernel line for the current kernel you are using.

Everything written here doesn't keep in mind any level of expertise you may or may not have with a linux system. If you don't get something google first on what it does and then try asking here again. Good luck.

---

### Post by Morcas on 2005-07-22
Edited for brevity 

[QUOTE=hapibooda]There are about a gazillion tips for enhancing your display and improving performance in these forums.  Here are a few that I use with my nVidia FX 4400.[/QUOTE]


Thanks for the links, I had read those but I though they were more 'cosmetically' inclined tips and hence had not implemented them, but I will give them a go and see what happens.

---

### Post by Morcas on 2005-07-22
[QUOTE=varunus]I've heard people complain that GNOME has been unresponsive, but for me, its much much faster than Windows XP...

One thing to ask, though:  how big is your swap partition on your computer?  I made mine equal to the amount of RAM I have (512 MB).[/QUOTE]

The swap is 1024Mb, twice the size of RAM


> Also, do you have DMA enabled on your hard drive?  (There's a howto on this forum somewhere...)

I haven't tried that as I thought the DMA settings were for removable media devices, but I will investigate that.

Thanks

---

### Post by jimbob on 2005-07-22
I'm using the Gnome that comes with it and I think it's great - really snappy.

If you want to see a real dog, download Linspire sometime!

---

### Post by Morcas on 2005-07-22
[QUOTE=ritger]There are a few tweaks you can do to increase performance, but from reading most of the TS posts he/she seems to be interested more in running Windows then trying to fix this (no own suggestions, researched material).[/QUOTE]


Thanks for the info, I will investigate all of the material mentioned.

As for being "interested more in running Windows",  that is not the case, but you have to understand that I have been using MS Windows, since there was a Windows and before that DOS, going all the way back to 1990.

Linux is new to me and although I have looked at distros before, real life has prevented my having the time necessary to learn the environment well. The time for that is now and ubuntu is the frst step on that journey. 

As for research, I have read 'The Guide' and a lot of the 'How to's'. I have also been reading other threads in this forum as well as other forums. This I will continue to do until i am as familar with Linus as i am with Windows.

By the way, this may be of interest to those seeking a more resonsive experience.

[http://www.linuxjournal.com/article/8308](http://www.linuxjournal.com/article/8308)

A three part guide :)

---

### Post by fishfork on 2005-07-26
[QUOTE=Morcas]I have looked at IceWM but the default themes are terrible, guess I'll take a look around for something better.[/QUOTE]

Have you tried the blueCrux theme for IceWM? I'm using it at the moment - makes things look much nicer.

---

### Post by graigsmith on 2005-07-26
for me, gnome seems to run at exactly the same speed as windows does.

however it did run slow till i updated the kernel to the k7 kernel.  then it got faster, and used less cpu for certain things.

---

### Post by dtfinch on 2005-07-26
The gnome menu is a little unresponsive for me. The first time I click it, it takes about 5 seconds to appear. If I click it a 2nd time in my frustration, it'll never appear, because I closed it before it had a chance to open. These sorts of things should be preloaded or something, or at least display an empty box to tell that it's doing something. Some MS programs use tricks like this to feel more responsive, displaying a user interface as early as possible, many seconds before the interface is actually usable.

The "Linux in Government" article on linuxjournal was pretty helpful.

The hdparm defaults were looked a little too conservative, like 16bit i/o and stuff. I tuned it as best I could, and it took some work to make it reload my hdparm settings on reboot. I don't think I can feel the difference. There's no change in sequential read performance.

I added "noatime" in my fstab. I assume it's faster.

I reduced swappiness to 10, which I think I can feel. Programs don't swap out as much when I still have plenty of memory. Swapping something back in takes 10x as long as swapping out.

My low end video chipset is noticeably faster at 16 bit color. Ubuntu defaulted to true color.

Some of the default cron jobs take a long time to complete, and the slowdown is very noticeable when trying to do anything disk intensive. This mainly affects people who don't leave their systems on overnight, causing the jobs to start shortly after their next boot.

Since the 486 era, I've always believed that there's no reason that most software couldn't be optimized to be able to respond faster than the screen could refresh. I don't see it happen much. Software just grows to consume the resources of whatever hardware its developers expect it to run on. Desktops are no faster now than they were 10 years ago.

---

### Post by Perfect Storm on 2005-07-26
This may seem a bit silly question, but have you tried to install the 686 kernel for your system?

---

### Post by Quest-Master on 2005-07-26
> Yes, but wait a year, install applications, browse the internet, download files, etc.
Now which one is faster and which one needs a complete reinstallation to clean up spyware, ads, obsolete programs, registry entries, etc?

I stopped using Ubuntu on this computer a few weeks ago, and Ubuntu is now exactly what I once thought Windows was-- slow, laggy, unresponsive, and a general unusable desktop experience. And, amazingly, with some work like anti-virus and spyware programs in place, I haven't felt the need to go back to Windows besides when I want my un-buggy X-Chat back.

I'm not trying to dumb down Ubuntu or anything-- have been with it since the month it was released. I've just found that using open source software on Windows as yielded far better results than Ubuntu here so far. :\

---

### Post by dtfinch on 2005-07-26
[QUOTE=Artificial Intelligence]This may seem a bit silly question, but have you tried to install the 686 kernel for your system?[/QUOTE]
$ cat /proc/sys/kernel/osrelease
2.6.10-5-686

---

### Post by Kitty on 2005-07-26
[QUOTE=dtfinch]$ cat /proc/sys/kernel/osrelease
2.6.10-5-686[/QUOTE]
 But have you installed ubuntu 686 metapackage?

---

### Post by robert114 on 2005-07-26
I'm experiencing a better performance with swappiness=90 (programs start a bit faster) I'm having a AMD 2200 with 756 MB RAM

---

### Post by smoon on 2005-07-26
You can replace Metacity with [Openbox3](http://icculus.org/openbox/), this makes the Gnome Desktop feel more responsive, at least for me. Check out the [Howto](http://www.ubuntuforums.org/showthread.php?t=34239).

---

### Post by Hamman on 2005-07-26
[QUOTE=smoon]You can replace Metacity with [Openbox3](http://icculus.org/openbox/), this makes the Gnome Desktop feel more responsive, at least for me. Check out the [Howto](http://www.ubuntuforums.org/showthread.php?t=34239).[/QUOTE]
 To me Gnome is about the same speed as Windows. Some things are faster, and some are slower. To me, metacity seems to be the bottleneck. Moving around windows extremely fast is a big nono. Sure, I don't need to, but it's nice to be able to do it :P
With the introduction of exa and cairo (and, further down the road xgl) we'll probably see a quite big speedgain. 
And the Gnome devs are working on a smaller memory footprint for 2.12 (mainly to make gnome useable on systems with 128 mb RAM or less) so it's not to far ahead :)

---

### Post by Quest-Master on 2005-07-26
> 
But have you installed ubuntu 686 metapackage?

What is this?

> I'm experiencing a better performance with swappiness=90 (programs start a bit faster) I'm having a AMD 2200 with 756 MB RAM

Where do I add the "swappiness" variable?

---

### Post by Stormy Eyes on 2005-07-26
[QUOTE=Quest-Master]Where do I add the "swappiness" variable?[/QUOTE]

Read the [Linux Memory Management FAQ](http://gentoo-wiki.com/FAQ_Linux_Memory_Management) from Gentoo WIKI. Section 5 in particular deals with the swappiness kernel parameter.

---

### Post by Quest-Master on 2005-07-27
[QUOTE=Stormy Eyes]Read the [Linux Memory Management FAQ](http://gentoo-wiki.com/FAQ_Linux_Memory_Management) from Gentoo WIKI. Section 5 in particular deals with the swappiness kernel parameter.[/QUOTE]
 
Thanks.. I really hope it'll solve my problem. :(

---

### Post by cotcot on 2005-07-27
I run Ubuntu on a P3 500 with a 40 G HDD and XP on a P4 3000. I am surprised how fast Ubuntu 5.04 is on my P3. The P3 has 384 Mb ram and the swap partition is (as recommended) 768 Mb. I tried Kubuntu too which was not significantly slower or faster although KDE (3.4) is heavier. I replaced SuSE 9.2 by Ubuntu because SuSE 9.2 with KDE 3.3 was too slow on my P3.

---

