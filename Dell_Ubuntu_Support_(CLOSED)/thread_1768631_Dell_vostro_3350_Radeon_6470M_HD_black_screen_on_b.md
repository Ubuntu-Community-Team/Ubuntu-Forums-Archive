---
title: "Dell vostro 3350 Radeon 6470M HD black screen on boot - Ubuntu 11.04 64bit"
date: 2011-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Eu4ia on 2011-05-27
Hi everyone,

I've recently purchased a Dell Vostro 3350 with 2 integrated graphics card
1 - Intel HD
2 - AMD (ATI) Radeon 470M HD

No problem installing Ubuntu 11.04 64 bit using a CD (not USB)
i just needed to add noapic options.

After the first reboot no problem occurred, but after some try it freeze at startup with a black screen (also no baklight!).

That's happen also after a variable number of reboot, then it starts normally, then no more!

That's is due to the unsupported ATI card by the radeon open driver, maybe it's too new :)

DAMN!

Some searching in this formu and than I've solution that's right for me.

Once you boot don't start normally but choose a shell.

Instead of removing the module with

```
rmmod radeon
```

I prefer to blacklist that module by

```
echo "blacklist radeon" > /etc/modprobe.d/blacklist-radeon.conf
```

I need to alert you that's a problem by choosing this way:
it seems that you've both the videocard POWERED ON so if you need to keep the consuption low you need to chose a different solution.

Any idea about that?

Maybe here but I can't understan very well:
[COLOR="RoyalBlue"][http://ubuntuforums.org/newreply.php?do=newreply&p=10832728](http://ubuntuforums.org/newreply.php?do=newreply&p=10832728)[/COLOR]

Bye Bye

---

### Post by RavenArkadon on 2011-06-07
Hi, I recently bought the the same Laptop and I am also having these issues.
So I'll share my experience so far.

It seems as if the open source radeon driver* is crashing on boot, therefore doing the
```
echo "blacklist radeon" > /etc/modprobe.d/blacklist-radeon.conf
``` indeed solves part of the problem.

I am not sure why this happens (sry, forgot to make a copy of the dmesg output, where the crash is logged), but so far it seems that the radeon module succeeds to load afterwards:
```
sudo modprobe radeon
```With the module loaded, it is possible to switch, enable and disable the two graphic cards using "switcheroo' that comes into play when the driver is loaded:

```

sudo su -c 'echo ON > /sys/kernel/debug/vgaswitcheroo/switch; echo IGD > /sys/kernel/debug/vgaswitcheroo/switch; echo OFF > /sys/kernel/debug/vgaswitcheroo/switch'

```This statement turns on the integrated graphics card, and disabled the radeon.
More details can be found here: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

In my case, the fan that was running all the time stopped within a few seconds.
Hope this helps.

ps:
In regard to [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
. The problem of the fan running at full speed after reboot does not apply to my notebook, so I infer it does not apply to the whole series.
. The initramfs script, which should switch to the integrated graphics card, did not work for me, because at the time initramfs is executed, the radeon module has not been loaded yet, therefore '/sys/kernel/debug/vgaswitcheroo/switch' does not exist.
Note however, that the link points to a wiki page, so it might be updated soon.

* There is also the official catalyst one, but version 11.5 did not find the device.
I did not try to figure out if there was a workaround for this.

---

### Post by Batapa on 2011-06-27
Hello,

I just bought the vostro 3350 and I got the same black screen issue at times after booting.
I installed ubuntu 11.04 from a cd alongside windows 7.

I tried to run the echo blacklist command like you described at the boot time (I pressed the key c on the screen where I choose the os to run) but I got a syntax error.
I believe this might be because I could not see any blacklist-radeon.conf file in the /etc/modprobe.d directory (I see some others like blacklist-firewire.conf, blacklist-watchdog.conf etc).

I've noticed something that looks weird to me about the graphic card.
In windows 7, it says it is the radeon 6490 but when I ran the command to list the pci devices via a terminal in ubuntu the radeon seems to be the 6450?!

Any ideas?

Thanks in advance for your help.

ps. my knowledge of linux/ubuntu is close to zero. I've tried to read some forums here and there to try to understand a bit more about the way to fix this issue.

---

### Post by AlexValex on 2011-07-15
I have the same problems with the same laptop.
Details here: [http://ubuntuforums.org/showthread.php?t=1800160](http://ubuntuforums.org/showthread.php?t=1800160)
My solution, for the moment (I'm at my first interactions with linux and my level of expertise in PC is zero): 
1. when in GRUB (I have a dual boot system) I select the OS and press E
2. in the third line of the menu - 
> set gfxpayload=$linux_gfx_mode I put a "#" in front of this line (it ignores this line, someone explained me);
3. Press F10 and it boots properly, but with the ATI/Radeo deactivated.

I'm curious if and how could I save this modification, so I don't have to enter this menu every time I boot.

I also have problems with the fingerprint reader and with the sound. Do you? If yes, have you managed to solve them?

---

### Post by engrin on 2011-07-15
[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

This solved the black screen of death for me :)

---

### Post by vostro3350 on 2011-07-18
Hello everyone!
 
first of all, I am new to this forum and although I have some experience with linux I would regard myself as a beginner.
 
Two weeks ago I bought a DELL vostro 3350 with i5-2410M with hybrid graphics and when trying to install Ubuntu 11.04, 64 bit version, I face the same problems as many other users do.
 
I have seen that some people found ways to circumvent the problem. Despite, I am not even able to install Ubuntu. 
 
I tried to follow the instructions recommended by engrin 
([[COLOR=#000000]http://ubuntu4beginners.blogspot.com...n-problem.html[/COLOR]]("http://ubuntu4beginners.blogspot.com...n-problem.html")). According to that, you should be able to choose the "nomodeset" option, which should enable you to install Ubuntu without black-screen.
The problem is, that when I try to install it, there are no options to select. As I read in other posts, the options should appear after pressing F6, but unfortunately they do not, which is why I am stuck.
 
 
I downloaded the following versions at ubuntu.com and created a USB bootable device with the recommended software:
 
ubuntu-11.04-desktop-i386.iso
ubuntu-11.04-desktop-amd64.iso
ubuntu-10.04.2-desktop-amd64.iso
 
 
I think the instructions are intended for Lucid/Maverick. Is it possible to choose "nomodeset" with Ubuntu 11.04 (64bit) as well? If yes, could you please tell me exactly how to do it?
 
Thank you for your help in advance!
 
Peter

---

### Post by engrin on 2011-07-18
I installed 11.4 64bit and used the method on there afterwords to fix it. Still working fine. Haven't had a black screen and I have restarted and rebooted several times.

---

### Post by vostro3350 on 2011-07-18
Hello engrin,
 
many thanks for your quick response. As I understand, you installed the version ubuntu-11.04-desktop-amd64.iso. Did you use a CD or USB? (I guess it doesn't really matter, but I want to follow your steps exactly).
 
You said you were able to install this version first without a black-screen and afterwards you used this method?
I thought you have to use the method before/during installation? What about the "nomodeset" option? Were you able to select it as described (during the installtion)?
 
best regards, Peter

---

### Post by engrin on 2011-07-18
My computer came with 10.4. I created a "startup usb disk" using the creator that came with the OS. I installed ubuntu-11.04-desktop-amd64.iso I had frequent black screens after shutdown and restarts. I followed the steps in the guide to get rid of it. Make sure to read the entire thing :) The part about radeon.nomodeset=0 is what helped.

---

### Post by vostro3350 on 2011-07-18
okay, thanks again. Now I really start thinking I am stupid. Apart from the fact that windows 7.0 is installed on my computer, I followed exactly the instructions at the bottom:
 
1.) I created the USB boot media with the same version you did
2.) I boot from the USB device (pressing any key). Then a screen appears similiar to this one, but not exactly the same (maybe because it's a different version). HERE the problem arises: I press F6 but nothing happens, because there are no advanced options.
 
I really do not think, that I did something wrong, because there is not much left to being done wrong. Therefore, I do not understand why you were able to do it this way.
 
Do you have any further advice or recommendations?
 
 
-----------------------
[COLOR=#7d181e]_Live CD/USB Environment_[/COLOR]
 
Pop in your CD/USB and boot from it. As soon as the computer starts booting from the boot media, keep on pressing any key until you are presented with this page.
 
 
[[IMG]http://1.bp.blogspot.com/_Aq4pKLMYUTk/TT787nivR_I/AAAAAAAAABs/TX_Jr1cbmGs/s400/Boot-Options.png[/IMG]]("http://1.bp.blogspot.com/_Aq4pKLMYUTk/TT787nivR_I/AAAAAAAAABs/TX_Jr1cbmGs/s1600/Boot-Options.png")Ubuntu Main Page Options
 
Once you see this page, press F6 and you'll see some options pop up. Navigate to *nomodeset* and hit Enter. You'll see a mark in the beginning. Press Esc and now choose *Try Ubuntu Without Installing* or *Install Ubuntu*, whichever you want to.
 
Hopefully, you'll see the desktop this time.

---

### Post by vostro3350 on 2011-07-18
Good news: Instead of using a USB boot media, I created a DVD (Ubuntu-11.04-desktop-amd64.iso) which allowed me to select the "nomodeset" option. Installation is currently in progress but it looks like everything works out fine.

Thank you!

---

### Post by engrin on 2011-07-18
Was offline for a while. Sorry for the slow response. Happy to hear it is working out for you :)

---

### Post by vostro3350 on 2011-07-18
Thanks! I should add that "ubiquity" crashed at about 80% of the  installation process, after I was prompted to determine which keyboard I  am using. Some other people had the same problem. 

I stopped the installation and booted directly from the DVD without  installing it first. After it booted successfully from the disk I  installed it using the shortcut on the desktop.

Finally the os was installed! Following  [http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html),  I did these steps:

1.) check for updates; there was one driver and I installed it.  Unfortunately, after rebooting there was some flickering which wouldn't  vanish. After I removed the driver again and rebooted, the unity surface  appeared for the first time.

2.) open the terminal window and type
gksudo gedit /etc/default/grub

3.) edit the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"

Save and close the file.

4.) sudo update-grub

Now restart and everything should work fine!
In some threads I saw, that people complaint about the fan running all  the time. After step 1.) I had the same problem. But steps 2.-4.) seem  to solve this problem!

Good luck and thank you for your help,
Peter

---

### Post by engrin on 2011-07-18
Did you install the recommended driver for the ATI card? Did Ubuntu switch to Classic View automatically? I can't get Unity to work the driver is installed. Should I un-install the driver?

---

### Post by vostro3350 on 2011-07-21
Hello Engrin!
 
When I first started, the Classic View appeared. Then I checked for driver updates and I found an ATI driver, which I downloaded and installed. Unfortunately, the thing didn't work properly. Parts of the screen were blinking... That is why I uninstalled the driver and rebooted again. This time it switched automatically to the Unity View. Now I changed the grub settings to radeon.modeset=0 and it worked fine. Before I made the changes in the grup-properties file, I noted that the cooler went all the time. 
At the moment I am not using the Radeon but the Intel graphics card which means less performance. However, Unity works as well.
 
There is one thing I am not completely sure about: Sometimes (after maybe 20 s) the mouse arrow blinks once as if the screen has been updated. I am not sure, if this has something to do with the driver, but it could be. Anyway, now everything is fine. Maybe someone noticed this as well!?

---

### Post by vostro3350 on 2011-07-21
Please let me know, in case you get everything to work properly with the ATI card.

---

### Post by engrin on 2011-07-21
> **vostro3350 said:**
> Please let me know, in case you get everything to work properly with the ATI card.

I have the ATI driver installed using classic view. I'm happy with classic and will continue with it. The things I can't get to work are my office's printer and VGA to projector :(

How do I know if the ATI card is actually working?

---

### Post by raintracks on 2011-07-29
I've had the same issues with my Vostro/Radeon as described here. The tips in post #2 are working to quiet down the fan after I boot without the Radeon driver. Also the driver update that was released by AMD two days ago didn't solve this issue, too bad really, I had hoped the Radeon chip would speed up the shell a little. Hopefully it will be addressed soon.

Now I would like to put these commands in a startup script somewhere so that I don't have to execute them manually every time I start my system.

It's been years since I used linux, I remember the startup scripts are somewhere around the /etc/rc.d folders, and that the numbers had something to do with the runlevel during startup, but I'm afraid the specifics are a bit hazy. Could someone point me in the right direction of where to put the modprobe command and the vgaswitcheroo command so that it's executed automatically at startup?

Incidentally, no one here actually got the AMD chip to work with Ubuntu since the last post, did they?

Edit:  an entry in /etc/rc.local did the trick

---

### Post by -iy- on 2011-09-14
Hi All

I have a Dell Vostro 3350 laptop with i7 processor and AMD 6470M graphics card (dynamic switchable). I had problems with graphics. It caused crashes of system. Now laptop works, I hope. Only AMD card can not be used. Dynamic switchable cards don't work under linux at all now ([https://bbs.archlinux.org/viewtopic.php?id=120622](https://bbs.archlinux.org/viewtopic.php?id=120622))

After installation of xubuntu 11.04, random crashes occured on boot (on load of radeon driver). I use radeon open source driver. This was solved by instalation of new 3.0.0 kernel from oneiric. I followed this instructions:

 [http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/](http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/)

Additionaly I upgraded xserver-xorg-video-radeon package, but it probably is not necessary.

The 3.0.0 kernel have increased power consumption. But in can be improved by ading kernel atributtes.

In /etc/default/grub change

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

to

```

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"

```

(Based on [https://bugzilla.redhat.com/show_bug.cgi?id=727579](https://bugzilla.redhat.com/show_bug.cgi?id=727579) )

AMD card is powered in default. But can be turned off by switcharoo. I added this lines into /etc/rc.local
```

while ! [ -e /sys/kernel/debug/vgaswitcheroo/switch ];
do
    echo "hack: Trying to load radeon driver"
    modprobe radeon
    sleep 1
done

eecho ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```

It is based on:

[http://ubuntuforums.org/showthread.php?t=1768631](http://ubuntuforums.org/showthread.php?t=1768631)

But then another problem occured. After suspend/resume, AMD card was powered and any attempt to turn it off caused crash. What more the
```

cat /sys/kernel/debug/vgaswitcheroo/switch

```
showed that AMD card is off, fan was not running, but power consumption was 10W above normal. I have found a workaround. With this workaround power constupmtion stays normal after suspend/resume.

Workaround is simple: Turn ON AMD card during suspend.

create script:
/etc/pm/sleep.d/10-radeon
Containing

```

case "$1" in
    suspend)
	echo "radeon: powering on"
        echo ON > /sys/kernel/debug/vgaswitcheroo/switch
	;;
    resume)
	echo "radeon: powering off"
        echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
	;;
esac

```

Now AMD card do not cause any problems. Only, it can't not be used :{.

---

### Post by vostro3350 on 2011-09-21
Hi!

Now it works for me as well and I want to give a brief summary of what I have tried before. I faced to problems. When I changed the GRUB-file to "radeon.modeset=0" like previously described, my screen started flickering after a while. In another approach, I messed around with the latest ATI-Drivers, the graphics card seemed to work, but the fan ran all the time and the laptop was getting hot. Neither of the results where desirable and I tried something else. When I started Ubuntu 11.04 in the failsafeX mode everything worked fine! So I just set failsafeX configuration to my default one. It is so easy, and now it works:

1.) modify the file /etc/default/grub 

> gksudo gedit /etc/default/grub

instead of 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
write
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.modeset=0"
and save it.

2.) sudo update-grub
3.) cp xorg.conf xorg.conf.backup
4.) mv xorg.conf.failsafe xorg.conf
5.) restart and it should work


Good luck, Peer

---

### Post by binnisb on 2012-11-18
> **-iy- said:**
> Hi All

I have a Dell Vostro 3350 laptop with i7 processor and AMD 6470M graphics card (dynamic switchable). I had problems with graphics. It caused crashes of system. Now laptop works, I hope. Only AMD card can not be used. Dynamic switchable cards don't work under linux at all now ([https://bbs.archlinux.org/viewtopic.php?id=120622](https://bbs.archlinux.org/viewtopic.php?id=120622))

After installation of xubuntu 11.04, random crashes occured on boot (on load of radeon driver). I use radeon open source driver. This was solved by instalation of new 3.0.0 kernel from oneiric. I followed this instructions:

 [http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/](http://marcin.juszkiewicz.com.pl/2011/06/20/linux-3-0-under-ubuntu-natty-11-04/)

Additionaly I upgraded xserver-xorg-video-radeon package, but it probably is not necessary.

The 3.0.0 kernel have increased power consumption. But in can be improved by ading kernel atributtes.

In /etc/default/grub change

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```

to

```

 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"

```

(Based on [https://bugzilla.redhat.com/show_bug.cgi?id=727579](https://bugzilla.redhat.com/show_bug.cgi?id=727579) )

AMD card is powered in default. But can be turned off by switcharoo. I added this lines into /etc/rc.local
```

while ! [ -e /sys/kernel/debug/vgaswitcheroo/switch ];
do
    echo "hack: Trying to load radeon driver"
    modprobe radeon
    sleep 1
done

eecho ON > /sys/kernel/debug/vgaswitcheroo/switch
echo IGD > /sys/kernel/debug/vgaswitcheroo/switch
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

```

It is based on:

[http://ubuntuforums.org/showthread.php?t=1768631](http://ubuntuforums.org/showthread.php?t=1768631)

But then another problem occured. After suspend/resume, AMD card was powered and any attempt to turn it off caused crash. What more the
```

cat /sys/kernel/debug/vgaswitcheroo/switch

```
showed that AMD card is off, fan was not running, but power consumption was 10W above normal. I have found a workaround. With this workaround power constupmtion stays normal after suspend/resume.

Workaround is simple: Turn ON AMD card during suspend.

create script:
/etc/pm/sleep.d/10-radeon
Containing

```

case "$1" in
    suspend)
	echo "radeon: powering on"
        echo ON > /sys/kernel/debug/vgaswitcheroo/switch
	;;
    resume)
	echo "radeon: powering off"
        echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
	;;
esac

```

Now AMD card do not cause any problems. Only, it can't not be used :{.
Thank you so much. Your beautiful sleep script finally fixed the last of my problems with the discrete graphics.

I had a script that did echo ON and an echo OFF on resume which lead to a black screen. This however works perfectly.

You just saved me hours, I can finally go to sleep :D

/Binni

---

### Post by wildmanne39 on 2012-11-21
Old thread closed.

---

