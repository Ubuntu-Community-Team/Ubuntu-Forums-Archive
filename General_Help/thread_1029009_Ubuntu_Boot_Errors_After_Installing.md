---
title: "Ubuntu Boot Errors After Installing"
date: 2009-01-02
forum: General Help
---

### Post by blahdieblah on 2009-01-02
Hey everyone, today I built a computer and installed Ubuntu. After the install, I rebooted and it found 208 different updates. Before that, I installed an ATI driver for my card. Then, I let it sit for about 3 hours while the updates were installed. When they were all done, I rebooted, but after the preliminary Ubuntu loading screen came on (with the orange moving bar) I got an odd-colored Ubuntu logo repeating itself at the top of the screen. It's hard to describe, and if required I can take a picture. It basically locks up here and I can't do anything. (That I've tried.) Right now I'm on the Live CD, which is still working fine. I have a feeling there's some problem with the video card, maybe the resolution? I've tried it on two different monitors and the same problem exists.

If anyone can provide any help, I would appreciate it so much.

---

### Post by blahdieblah on 2009-01-03
I have done a bit more googling and found an old thread here that looks the same as mine:

[http://ubuntuforums.org/showthread.php?t=143494](http://ubuntuforums.org/showthread.php?t=143494)

However, there wasn't ever any clear instructions on what to do. I've also uploaded a picture of what this screen error looks like.

I'm new to Ubuntu and different Terminal commands, but is there any way I can get past this screen and somehow log in? From there, is there a setting I can change or tweak that will prevent me from having this bug in the future?

I really want to figure out what this is, so if anyone can lend any help at all, I would appreciate it so much!

And I have another question: If I use the Live CD to make any changes to anything, (to possibly fix the problem), would they carry over into future boots? Basically, would they be saved?

---

### Post by lavinog on 2009-01-03
What video card do you have?
Which ATI driver did you install...was it the restricted driver?

First thing I would do is find out where it crashes.
When you boot and grub comes up, highlight the kernel you want to boot to and press 'e'
then highlight the first line and press 'e' again
remove the quiet splash at the end of the line and replace it with verbose
press enter then 'b' to boot with the change.
The change will revert back to normal on the next boot, but what it does is disable the splash display to show you what is going on during the boot.
If it hangs it should give you an indication of why it is failing.
There is also the possibility that it will boot fine with the splash disabled.

---

### Post by blahdieblah on 2009-01-03
> **lavinog said:**
> What video card do you have?
Which ATI driver did you install...was it the restricted driver?

First thing I would do is find out where it crashes.
When you boot and grub comes up, highlight the kernel you want to boot to and press 'e'
then highlight the first line and press 'e' again
remove the quiet splash at the end of the line and replace it with verbose
press enter then 'b' to boot with the change.
The change will revert back to normal on the next boot, but what it does is disable the splash display to show you what is going on during the boot.
If it hangs it should give you an indication of why it is failing.
There is also the possibility that it will boot fine with the splash disabled.

OK, I have an ATI Radeon HD 4850 by Sapphire and I installed the ATI Linux driver from their website. I have found a perfect summary of my problem on this page:

[http://www.dailygeeks.com/howto/top-ubuntu-preinstallation-problems-and-fixes/](http://www.dailygeeks.com/howto/top-ubuntu-preinstallation-problems-and-fixes/)

My problem is "When I select the Install Ubuntu option and press Enter, I see a status bar, but when the Ubuntu desktop should appear, it looks like my computer has crashed - all I see is graphical corruption."

However, when I boot up I don't have a GRUB thing at all. Ubuntu is my only OS so I see text saying it's going to load from the HDD, and then it boots up automatically. Once I'm at the corrupted screen, I can press CTRL + ALT + F1 and get to the terminal. That's progress! But I need someone who knows their commands to tell me what to write that will fix the problem... because there has to be an easy fix!

---

### Post by Moop on 2009-01-03
When you install the video card driver from somewhere other than the repositories and then get a kernel update, it can mess things up. Install the driver from System-Administration-Hardware drivers unless you have a reason for wanting the driver from ATI's website. 

You should be able to get to the grub menu by hitting the escape key during boot. You have a 3 second window so just keep hitting escape. From the grub menu you should be able to boot into recovery mode or your old kernel.

---

### Post by lavinog on 2009-01-03
> **blahdieblah said:**
> OK, I have an ATI Radeon HD 4850 by Sapphire and I installed the ATI Linux driver from their website. I have found a perfect summary of my problem on this page:

[http://www.dailygeeks.com/howto/top-ubuntu-preinstallation-problems-and-fixes/](http://www.dailygeeks.com/howto/top-ubuntu-preinstallation-problems-and-fixes/)

My problem is "When I select the Install Ubuntu option and press Enter, I see a status bar, but when the Ubuntu desktop should appear, it looks like my computer has crashed - all I see is graphical corruption."

However, when I boot up I don't have a GRUB thing at all. Ubuntu is my only OS so I see text saying it's going to load from the HDD, and then it boots up automatically. Once I'm at the corrupted screen, I can press CTRL + ALT + F1 and get to the terminal. That's progress! But I need someone who knows their commands to tell me what to write that will fix the problem... because there has to be an easy fix!

grub should be installed...you might get a 3 sec message that says press ESC to ...
but if you can get the terminal then you should be fine.
from the terminal:
log in
you should be in your home folder '/home/*your user name*'
type pwd to verify (pwd is path working directory, it tells you what folder you are in)

lets make a backup of your xorg.conf file:
```

sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.backup_$(date "+%F_%H%M")

```
you will need to enter your password to copy this file

try enabling the vesa driver to see if the vesa driver works:
```
 sudo nano -w /etc/X11/xorg.conf

```
you should see a line that says driver   "fglrx"
change fglrx to vesa
then press ctrl-x then 'y' to save changes
reboot and see if your desktop comes up.
If it does, the problem is not really fixed, but does point to a driver issue.

---

### Post by blahdieblah on 2009-01-03
> **Moop said:**
> When you install the video card driver from somewhere other than the repositories and then get a kernel update, it can mess things up. Install the driver from System-Administration-Hardware drivers unless you have a reason for wanting the driver from ATI's website. 

You should be able to get to the grub menu by hitting the escape key during boot. You have a 3 second window so just keep hitting escape. From the grub menu you should be able to boot into recovery mode or your old kernel.

Thanks for the reply! I'll try that.

I wanted the ATI drivers because I wanted to try some 3D stuff, like possibly trying some Steam games through Wine. It's not extremely important but I read on the site that they added a lot of important 3D capabilities.

So after I boot into the old kernel, how can I fix this problem for good? I don't want to have to boot into the old kernel each time...

---

### Post by blahdieblah on 2009-01-03
> **lavinog said:**
> grub should be installed...you might get a 3 sec message that says press ESC to ...
but if you can get the terminal then you should be fine.
from the terminal:
log in
you should be in your home folder '/home/*your user name*'
type pwd to verify (pwd is path working directory, it tells you what folder you are in)

lets make a backup of your xorg.conf file:
```

sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.backup_$(date "+%F_%H%M")

```
you will need to enter your password to copy this file

try enabling the vesa driver to see if the vesa driver works:
```
 sudo nano -w /etc/X11/xorg.conf

```
you should see a line that says driver   "fglrx"
change fglrx to vesa
then press ctrl-x then 'y' to save changes
reboot and see if your desktop comes up.
If it does, the problem is not really fixed, but does point to a driver issue.

When I do this, it says no such file exists. Yesterday while on the Live CD I saw that file in /etc/ as something different, I can't remember the name but I think you might be thinking of that? I don't want to make any changes without backing things up, so do you know why it's telling me that that file doesn't exist?

---

### Post by Moop on 2009-01-03
You can get the ATI drivers from System-Administration-Hardware Drivers and 3d will work. It's still the ATI driver. It just gets updated along with a kernel update so you won't run into the problem you're having.

---

### Post by blahdieblah on 2009-01-03
> **Moop said:**
> You can get the ATI drivers from System-Administration-Hardware Drivers and 3d will work. It's still the ATI driver. It just gets updated along with a kernel update so you won't run into the problem you're having.

While I wait for an answer to my other question regarding the terminal, may I ask, how would I go about uninstalling the unneeded ATI drivers once I'm back at my desktop?

---

### Post by Moop on 2009-01-03
Boot into recovery mode and go to Hardware Drivers. Is your ATI driver listed? Choose to activate (install) it, reboot and see if that works.

---

### Post by cariboo on 2009-01-03
Would it not be easier to start in recovery mode and choose xfix from the menu, on xfix is finished select resume, this should get you to your desktop, although it will be in low resolution mode. Then check System-->Administration-->Hardware Drivers to install the closed source driver.

In the future when doing a new install allow the updates to finish first before installing the graphics driver, as there may be an updated driver.

Jim

---

### Post by blahdieblah on 2009-01-03
I can access the old kernel just fine, but off topic, I tried to change the resolution and messed something up. So, I'm booting from the CD to change that setting. (I believe I know how to do that, although it's probably not very efficient)

When that's done I'll try recovery mode.

---

### Post by blahdieblah on 2009-01-03
OK, I think I finally know what the problem is. I ran xfix through Recovery Mode on the main kernel, and it booted successfully. The ATI driver that Ubuntu detected was not in use. I enabled it, and it told me I needed to restart to use it. I did, and boom, the same screen error came up.

This tells me that I shouldn't use the ATI driver, but it seems that if the ATI driver was doing this to people, wouldn't we be hearing more about it?

---

### Post by Moop on 2009-01-03
I'd guess that the old driver install is the problem. Did it come with uninstall instructions? 

You might want to try Envy. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by blahdieblah on 2009-01-03
> **Moop said:**
> I'd guess that the old driver install is the problem. Did it come with uninstall instructions? 

You might want to try Envy. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Everything is running smoothly now, I suppose, but I'm upset that even the closed driver that Ubuntu says I can activate gives me the problem. I'll try Envy... 

Thanks for the help everyone, it means a lot to someone like me who doesn't know much about Linux!

---

### Post by blahdieblah on 2009-01-03
Sigh, I tried using Envy and got the exact same result as when I used the ATI drivers.

I guess I could contact ATI support and ask what's going on, because it seems like it's really just the drivers.

Until then, I'll just keep my setup the way it is... I just don't understand why I'm having problems, and apparantly others aren't.

---

### Post by lavinog on 2009-01-03
> **blahdieblah said:**
> When I do this, it says no such file exists. Yesterday while on the Live CD I saw that file in /etc/ as something different, I can't remember the name but I think you might be thinking of that? I don't want to make any changes without backing things up, so do you know why it's telling me that that file doesn't exist?

where you booting from the live cd or from the hard drive?
the live cd is going to have a different location...i was assuming you were booting from the hard drive.

---

### Post by lavinog on 2009-01-03
> **blahdieblah said:**
> Sigh, I tried using Envy and got the exact same result as when I used the ATI drivers.

I guess I could contact ATI support and ask what's going on, because it seems like it's really just the drivers.

Until then, I'll just keep my setup the way it is... I just don't understand why I'm having problems, and apparantly others aren't.

There are alot of things.
ATI will most likely not help you though.
some things that will help with fixing the issue:
What version ATI driver did you install?
where did you get the driver? There are more than one type of ati driver, and there are a couple of different versions (8-12 is the latest and anything less than 8-11 will not work with Ubuntu 8.10)
```
grep 'Version: '  /var/log/Xorg.0.log
```
also what version is installed in dkms
```
ls /var/lib/dkms/fglrx/
```

if you can, post your /var/log/kern.log and /var/log/Xorg.0.log
after booting into the corrupted screen
press alt-f1
login
```

cat /var/log/kern.log >~/kern_bad_video.log
cat /var/log/Xorg.0.log >~/Xorg.0_bad_video.log

```
then reboot to where you dont have corruption and post those two logs here.

---

### Post by blahdieblah on 2009-01-03
> **lavinog said:**
> There are alot of things.
ATI will most likely not help you though.
some things that will help with fixing the issue:
What version ATI driver did you install?
where did you get the driver? There are more than one type of ati driver, and there are a couple of different versions (8-12 is the latest and anything less than 8-11 will not work with Ubuntu 8.10)
```
grep 'Version: '  /var/log/Xorg.0.log
```
also what version is installed in dkms
```
ls /var/lib/dkms/fglrx/
```

if you can, post your /var/log/kern.log and /var/log/Xorg.0.log
after booting into the corrupted screen
press alt-f1
login
```

cat /var/log/kern.log >~/kern_bad_video.log
cat /var/log/Xorg.0.log >~/Xorg.0_bad_video.log

```
then reboot to where you dont have corruption and post those two logs here.

I'll post those in just a second, after I install the ATI driver once again and reboot.

Until then, when I did the first command you told me to do, I got many lines of this:

```
(II) RADEON(0): EDID Version: 1.3
```

The second command:

```
8.561  kernel-2.6.27-7-generic-i686  kernel-2.6.27-9-generic-i686
```

I saw a topic on this forum about someone who got the same GPU working well, but needed help on getting dual monitors hooked up. I PM'd him, and hopefully he can help too.

---

### Post by blahdieblah on 2009-01-03
I did the commands you told me to do, and just now found the files in the directory, (kern.log and Xorg.0.log) but they're HUGE documents and they wouldn't work to be posted here... maybe I'm missing something but how should I post them?

---

### Post by lavinog on 2009-01-04
> **blahdieblah said:**
> I'll post those in just a second, after I install the ATI driver once again and reboot.

Until then, when I did the first command you told me to do, I got many lines of this:

```
(II) RADEON(0): EDID Version: 1.3
```

It looks as though you are using the radeon driver and not the fglrx driver.
I don't think the radeon driver supports 3d yet.
The ATI driver from ATI's website (commonly refered to as the restricted or proprietary driver) should show this:
```

(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0):     Version: 8.56.4

```

> 

The second command:

```
8.561  kernel-2.6.27-7-generic-i686  kernel-2.6.27-9-generic-i686
```

The 8.561 shows that you have installed the latest restricted driver.

now we need to see why it isn't loading
```
 grep fglrx /etc/modprobe.d/*
```
you should get:
```
/etc/modprobe.d/blacklist-local:blacklist fglrx
```
if you don't try this:
```
echo blacklist fglrx|sudo tee -a /etc/modprobe.d/blacklist-local

```
This appends the line 'blacklist fglrx' to /etc/modprobe.d/blacklist-local
it works the same as echo blacklist fglrx>/etc/modprobe.d/blacklist-local but system files require super user privileges and redirect commands (>) dont work with sudo, so that is why tee is used.
The only reason to blacklist this is because sometimes the restricted-kernel modules might be installed and a lesser compatible fglrx driver was included with them...I believe that has changed with intrepid, but it doesnt hurt to be sure.
 

also we need to find where your xorg.conf is...this is a necessary file
what does this give you:
```
locate xorg.conf
```
it should be located in /etc/X11/
if it is use the backup commands again from my earlier post.
This should be done without using the live CD.
this file is what tells the system what driver to be using.

---

### Post by blahdieblah on 2009-01-04
> **lavinog said:**
> It looks as though you are using the radeon driver and not the fglrx driver.
I don't think the radeon driver supports 3d yet.
The ATI driver from ATI's website (commonly refered to as the restricted or proprietary driver) should show this:
```

(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0):     Version: 8.56.4

```


The 8.561 shows that you have installed the latest restricted driver.

now we need to see why it isn't loading
```
 grep fglrx /etc/modprobe.d/*
```
you should get:
```
/etc/modprobe.d/blacklist-local:blacklist fglrx
```
if you don't try this:
```
echo blacklist fglrx|sudo tee -a /etc/modprobe.d/blacklist-local

```
This appends the line 'blacklist fglrx' to /etc/modprobe.d/blacklist-local
it works the same as echo blacklist fglrx>/etc/modprobe.d/blacklist-local but system files require super user privileges and redirect commands (>) dont work with sudo, so that is why tee is used.
The only reason to blacklist this is because sometimes the restricted-kernel modules might be installed and a lesser compatible fglrx driver was included with them...I believe that has changed with intrepid, but it doesnt hurt to be sure.
 

also we need to find where your xorg.conf is...this is a necessary file
what does this give you:
```
locate xorg.conf
```
it should be located in /etc/X11/
if it is use the backup commands again from my earlier post.
This should be done without using the live CD.
this file is what tells the system what driver to be using.

Thanks for such a detailed reply! I will try this first thing tomorrow.

Thank you so much everyone for all of the help, it's so fantastic.

---

### Post by marcgh on 2009-01-04
Hi blahdieblah,
Thanks for your private message.

I got it finally running, with 2 screens, around 3 am last night.
And it was in fact dead simle, this is how I worked it out:

After uninstalling - I think Ubuntu was completely messed up - I did a clean install.
First I waited patiently that all (220+) updates were done and then I rebooted.
Then I went to the ATI site and downloaded on my Desktop the newest driver being :
ati-driver-installer-8-12-x86.x86_64.run
Then I went into terminal mode and did as follows:

sudo -s  (you will have to type your password to proceed)
cd /usr/share/ati
sh ./fglrx-uninstall.sh (this removes any previous ATI driver)
cd ~/Desktop   (I downloaded the ATI driver on the desktop)
sh ./ati-driver-installer-8-12-x86.x86_64.run   (this will launch the install of the driver)
Follow the instructions fron ATI
Reboot
go to catalyst center in APPLICATIONS

this is how it worked for me in UBUNTU 8.04 (Hardy)

Good luck!

---

### Post by blahdieblah on 2009-01-04
lavinog, I did the commands you suggested. I didn't get anything from the first command so I used the echo one. xorg.conf was located in the correct place, and I used the echo command on it, too. 

marcgh, thanks for the reply. The one difference I noticed was that you're on 8.04. I don't think that will really change much, though. That was the exact ATI driver I tried to use, too.

I have two different courses of action I could take. I'm tempted to reinstall and start fresh, but maybe we could figure it out without that. I think I'll hold off on reinstalling though because everyone has been helping so much and I want to see if we can resolve it. Reinstalling will be a fallback.

---

### Post by lavinog on 2009-01-04
> **blahdieblah said:**
>  xorg.conf was located in the correct place, and I used the echo command on it, too. 

Wait, what echo command did you use on xorg.conf?
I was referring to the backup command from my earlier post, where you responded that xorg.conf didn't exist
```
sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.backup_$(date "+%F_%H%M")
```

make the backup of that file and then post what it looks like.

---

### Post by blahdieblah on 2009-01-04
I will.

And, I don't know if this is related to what I did in Terminal earlier, but the next time I booted up it said Ubuntu was running in safe graphics mode or some term like that. It said it would be reduced resolution but ended up being the same resolution as it always is. (1024x768)

Do you think this driver problem is fixable, or should I just do a fresh reinstallation?

---

### Post by blahdieblah on 2009-01-04
> **lavinog said:**
> Wait, what echo command did you use on xorg.conf?
I was referring to the backup command from my earlier post, where you responded that xorg.conf didn't exist
```
sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.backup_$(date "+%F_%H%M")
```

make the backup of that file and then post what it looks like.

I ran that code, and when you say post what it looks like... this?

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

That's what the backed up file looks like.

---

### Post by lavinog on 2009-01-04
ok so your xorg.conf isn't loading the fglrx driver
so try this

```
sudo aticonfig --initial
```
then post your /etc/X11/xorg.conf file
it should have modified it to add a line that at least says
```
	Driver      "fglrx"

```
in the device section

---

### Post by blahdieblah on 2009-01-04
Alright, I did that, and that line was indeed added to the xorg.conf file.

What next?

EDIT: I just restarted the computer and got the same corrupted screen error.

---

### Post by lavinog on 2009-01-05
You mentioned earlier that you think the corruption is resolution related right?
where are you getting corruption? is it on the desktop, and terminal (alt-f1) or just the desktop?
we can limit the resolution and see if that clears it up.
in the terminal:
```
sudo nano -w /etc/X11/xorg.conf
```
The xorg.conf is arranged in sections
in the screen section see if you have a subsection called display
if not you need to add it right before the EndSection
```
 SubSection "Display"
  Depth 24
  Modes "1024x768"
 EndSubSection

```
If you do have the display subsection already just add the Modes "1024x768" line
when you are done press ctrl-x then y and enter enter
then reboot
if that works you can change the 1024x768 to the next higher resolution: 1280x1024 and test again...if that fails, go back to the 1024x768

If non of that works try and post your /var/log/Xorg.0.log
It is best if you copy and paste it into the post:
use the code buttons to paste it into code quotes (should be the button with the #)
if you would rather post it as an attachment, you have to save it with a txt file extension.
```
cp /var/log/Xorg.0.log ~/xorg_log.txt
```
the ~ is a shortcut to your home folder btw

---

### Post by blahdieblah on 2009-01-05
> **lavinog said:**
> You mentioned earlier that you think the corruption is resolution related right?
where are you getting corruption? is it on the desktop, and terminal (alt-f1) or just the desktop?
we can limit the resolution and see if that clears it up.
in the terminal:
```
sudo nano -w /etc/X11/xorg.conf
```
The xorg.conf is arranged in sections
in the screen section see if you have a subsection called display
if not you need to add it right before the EndSection
```
 SubSection "Display"
  Depth 24
  Modes "1024x768"
 EndSubSection

```
If you do have the display subsection already just add the Modes "1024x768" line
when you are done press ctrl-x then y and enter enter
then reboot
if that works you can change the 1024x768 to the next higher resolution: 1280x1024 and test again...if that fails, go back to the 1024x768

If non of that works try and post your /var/log/Xorg.0.log
It is best if you copy and paste it into the post:
use the code buttons to paste it into code quotes (should be the button with the #)
if you would rather post it as an attachment, you have to save it with a txt file extension.
```
cp /var/log/Xorg.0.log ~/xorg_log.txt
```
the ~ is a shortcut to your home folder btw

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux Alex-Custom-PC 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jan  5 17:42:29 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV770 [Radeon HD 4850] rev 0, Mem @ 0xd0000000/0, 0xe5000000/0, I/O @ 0x0000b000/0, BIOS @ 0x????????/131072
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(**) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeon from file name radeon.ids
(==) Matched radeon for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeon"

(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610, ATI RV670,
	ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE, ATI Radeon HD 3470,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI FireMV 2450, ATI FireMV 2260,
	ATI FireMV 2260, ATI ATI Radeon HD 3600 Series,
	ATI ATI Radeon HD 3650 AGP, ATI ATI Radeon HD 3600 PRO,
	ATI ATI Radeon HD 3600 XT, ATI ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000e5000000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon 4800 Series" (ChipID = 0x9442)
(WW) RADEON(0): R600 support is mostly incomplete and very experimental
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCIE card detected
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"

(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x174b SubsystemID: 0xe810
	IOBaseAddress: 0xb000
	Filename: E81405Q2.SB 
	BIOS Bootup Message: 

Wekiva RV770 B50102 Board                                                   


(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffec
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffec
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 625000
(II) RADEON(0): Default Memory Clock: 993000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 16000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 6000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 100000
(II) RADEON(0): Direct rendering not officially supported on RN50/RS600/R600
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) RADEON(0): Max desktop size set to 2560x1600
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 10000, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 600, max_in_pll: 1600, xclk: 40000, sclk: 625.000000, mclk: 993.000000
(II) RADEON(0): PLL parameters: rf=10000 rd=12 min=64800 max=120000; xclk=40000
object id 0002 02
src object id 211e 30
src object id 2116 22
record type 1
record type 2
record type 4
object id 000f 01
src object id 2116 22
record type 4
record type 7
object id 0002 02
src object id 211f 31
src object id 2115 21
record type 1
record type 2
record type 4
object id 0011 01
src object id 2114 20
record type 4
record type 11
object id 0011 01
src object id 2114 20
record type 4
record type 11
(II) RADEON(0): Output DVI-1 using monitor section Configured Monitor
(II) RADEON(0): I2C bus "DVI-1" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- UNIPHY
 DDC Type  -- 0x7e60
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- Primary
 TMDS Type -- LVTMA
 DDC Type  -- 0x7e20
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-1:ddc2" removed.
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Dac detection success
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 5800  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 28
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Indeterminate output size
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58 V max: 62 Hz, H min: 30 H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S26A10
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9005801010101
(II) RADEON(0): 	1c0f0103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d5332364131300a2020007d
finished output detect: 1
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-1:ddc2" removed.
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 5800  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 28
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Indeterminate output size
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58 V max: 62 Hz, H min: 30 H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S26A10
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9005801010101
(II) RADEON(0): 	1c0f0103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d5332364131300a2020007d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 22528
(II) RADEON(0): Output DVI-1 disconnected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output DVI-0 using initial mode 1024x768
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): No acceleration support available on R600 yet.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit d0000000 0 0
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
mc fb loc is 00ef00d0
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x20000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
(II) RADEON(0): Largest offscreen area available: 1280 x 6909
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x001f0000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00643000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00648000
(II) RADEON(0): Largest offscreen area available: 1280 x 6901
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1024x768 - 1344 806 10
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ef00d0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 65000000
best_freq: 65000000
best_feedback_div: 52
best_ref_div: 8
best_post_div: 10
(II) RADEON(0): crtc(0) Clock: mode 65000, PLL 65000
(II) RADEON(0): crtc(0) PLL  : refdiv 8, fbdiv 0x34(52), pdiv 10
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Output 68 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1024x768 - 1344 806 10
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ef00d0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 65000000
best_freq: 65000000
best_feedback_div: 52
best_ref_div: 8
best_post_div: 10
(II) RADEON(0): crtc(0) Clock: mode 65000, PLL 65000
(II) RADEON(0): crtc(0) PLL  : refdiv 8, fbdiv 0x34(52), pdiv 10
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DAC1 setup success
Output 68 enable success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) RADEON(0): Setting screen physical size to 270 x 203
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event2"
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device LITEON Technology USB Multimedia Keyboard
(**) LITEON Technology USB Multimedia Keyboard: always reports core events
(**) LITEON Technology USB Multimedia Keyboard: Device: "/dev/input/event1"
(II) LITEON Technology USB Multimedia Keyboard: Found keys
(II) LITEON Technology USB Multimedia Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "LITEON Technology USB Multimedia Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) LITEON Technology USB Multimedia Keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) LITEON Technology USB Multimedia Keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) LITEON Technology USB Multimedia Keyboard: xkb_layout: "us"
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-1:ddc2" removed.
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SNY", prod id 22528
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1053 1189 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   81.80  1024 1080 1192 1360  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 5800  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 28
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Indeterminate output size
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58 V max: 62 Hz, H min: 30 H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S26A10
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9005801010101
(II) RADEON(0): 	1c0f0103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d5332364131300a2020007d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 22528
AUDIT: Mon Jan  5 17:42:34 2009: 5769 X: client 4 rejected from local host ( uid=0 gid=0 pid=5991 )
AUDIT: Mon Jan  5 17:42:48 2009: 5769 X: client 4 rejected from local host ( uid=0 gid=0 pid=6206 )
AUDIT: Mon Jan  5 17:42:52 2009: 5769 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6253 )
AUDIT: Mon Jan  5 17:42:52 2009: 5769 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6254 )
AUDIT: Mon Jan  5 17:42:52 2009: 5769 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=6255 )
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-1:ddc2" removed.
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SNY", prod id 22528
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1053 1189 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   81.80  1024 1080 1192 1360  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 5800  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 28
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Indeterminate output size
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58 V max: 62 Hz, H min: 30 H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S26A10
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9005801010101
(II) RADEON(0): 	1c0f0103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d5332364131300a2020007d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 22528
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-1:ddc2" removed.
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SNY", prod id 22528
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1053 1189 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   81.80  1024 1080 1192 1360  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 5800  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 28
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Indeterminate output size
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58 V max: 62 Hz, H min: 30 H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S26A10
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9005801010101
(II) RADEON(0): 	1c0f0103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d5332364131300a2020007d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 22528
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-1:ddc2" removed.
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SNY", prod id 22528
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1053 1189 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   81.80  1024 1080 1192 1360  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 5800  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 28
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Indeterminate output size
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58 V max: 62 Hz, H min: 30 H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S26A10
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9005801010101
(II) RADEON(0): 	1c0f0103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d5332364131300a2020007d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 22528
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI-1:ddc2" removed.
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Dac detection success
(II) RADEON(0): EDID vendor "SNY", prod id 22528
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1053 1189 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   81.80  1024 1080 1192 1360  768 769 772 802 -hsync +vsync (60.2 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: SNY  Model: 5800  Serial#: 16843009
(II) RADEON(0): Year: 2005  Week: 28
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Indeterminate output size
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.333   greenX: 0.275 greenY: 0.595
(II) RADEON(0): blueX: 0.143 blueY: 0.064   whiteX: 0.280 whiteY: 0.290
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 65.0 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1024  h_sync: 1053  h_sync_end 1189 h_blank_end 1344 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 79.5 MHz   Image Size:  0 x 0 mm
(II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
(II) RADEON(0): Ranges: V min: 58 V max: 62 Hz, H min: 30 H max: 50 kHz, PixClock max 80 MHz
(II) RADEON(0): Monitor name: KLV-S26A10
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004dd9005801010101
(II) RADEON(0): 	1c0f0103080000780ad9ada355469824
(II) RADEON(0): 	10474aadc800614f0101010101010101
(II) RADEON(0): 	01010101010164190040410026301d88
(II) RADEON(0): 	36000000000000180e1f008051001e30
(II) RADEON(0): 	4080370000000000001c000000fd003a
(II) RADEON(0): 	3e1e3208000a202020202020000000fc
(II) RADEON(0): 	004b4c562d5332364131300a2020007d
in RADEONProbeOutputModes
(II) RADEON(0): EDID vendor "SNY", prod id 22528
```

---

### Post by lavinog on 2009-01-05
can you post your /etc/X11/xorg.conf and /var/log/dmesg

it doesn't make sense that the radeon driver is still loading instead of the fglrx

---

### Post by blahdieblah on 2009-01-05
> **lavinog said:**
> can you post your /etc/X11/xorg.conf and /var/log/dmesg

it doesn't make sense that the radeon driver is still loading instead of the fglrx

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fee0000 (usable)
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee2000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee2000 - 000000007fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fef0000 - 000000007ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x7fee0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[    0.000000] RAMDISK: 3781d000 - 37fef646
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP 000F7280, 0014 (r0 GBT   )
[    0.000000] ACPI: RSDT 7FEE2040, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: FACP 7FEE20C0, 0074 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: DSDT 7FEE2180, 4CD9 (r1 GBT    GBTUACPI     1000 MSFT  100000C)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: EUDS 7FEE7580, 0470 (r1 GBT                    0             0)
[    0.000000] ACPI: HPET 7FEE74C0, 0038 (r1 GBT    GBTUACPI 42302E31 GBTU       98)
[    0.000000] ACPI: MCFG 7FEE7540, 003C (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: APIC 7FEE6EC0, 0084 (r1 GBT    GBTUACPI 42302E31 GBTU  1010101)
[    0.000000] ACPI: SSDT 7FEE8320, 03AB (r1  PmRef    CpuPm     3000 INTL 20040311)
[    0.000000] 1150MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00008000 - 0000f000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [003781d000 - 0037fef646]          RAMDISK ==> [003781d000 - 0037fef646]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00f5890] 000f5890
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x0007fee0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007fee0
[    0.000000] On node 0 totalpages: 523903
[    0.000000] free_area_init_node: node 0, pgdat c048a580, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 292034 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7ff00000:60100000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 519297
[    0.000000] Kernel command line: root=UUID=952e97ca-02bb-4874-a2b2-c10b4fff6ae3 ro  single
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PMTIMER calibration value
[    0.000000] Detected 2400.075 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 2062428k/2096000k available (2572k kernel code, 32360k reserved, 1160k data, 424k init, 1178496k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
[    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4800.15 BogoMIPS (lpj=9600300)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.017580] ACPI: Core revision 20080609
[    0.018970] ACPI: Checking initramfs for custom DSDT
[    0.296198] ENABLING IO-APIC IRQs
[    0.296397] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.337375] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.340021] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 4800.08 BogoMIPS (lpj=9600167)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.424587] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.424861] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.428108] Booting processor 2/3 ip 6000
[    0.004000] Initializing CPU#2
[    0.004000] Calibrating delay using timer specific routine.. 4800.11 BogoMIPS (lpj=9600220)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 3
[    0.516590] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.516862] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.520100] Booting processor 3/2 ip 6000
[    0.004000] Initializing CPU#3
[    0.004000] Calibrating delay using timer specific routine.. 4800.10 BogoMIPS (lpj=9600203)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 4096K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 2
[    0.608577] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.608851] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.612038] Brought up 4 CPUs
[    0.612083] Total of 4 processors activated (19200.44 BogoMIPS).
[    0.612137] CPU0 attaching sched-domain:
[    0.612139]  domain 0: span 0-1 level MC
[    0.612142]   groups: 0 1
[    0.612145]   domain 1: span 0-3 level CPU
[    0.612147]    groups: 0-1 2-3
[    0.612152] CPU1 attaching sched-domain:
[    0.612153]  domain 0: span 0-1 level MC
[    0.612155]   groups: 1 0
[    0.612158]   domain 1: span 0-3 level CPU
[    0.612160]    groups: 0-1 2-3
[    0.612164] CPU2 attaching sched-domain:
[    0.612165]  domain 0: span 2-3 level MC
[    0.612167]   groups: 2 3
[    0.612170]   domain 1: span 0-3 level CPU
[    0.612172]    groups: 2-3 0-1
[    0.612176] CPU3 attaching sched-domain:
[    0.612178]  domain 0: span 2-3 level MC
[    0.612179]   groups: 3 2
[    0.612182]   domain 1: span 0-3 level CPU
[    0.612184]    groups: 2-3 0-1
[    0.612280] net_namespace: 840 bytes
[    0.612280] Booting paravirtualized kernel on bare hardware
[    0.612304] Time:  1:41:56  Date: 01/06/09
[    0.612354] NET: Registered protocol family 16
[    0.612399] EISA bus registered
[    0.612399] ACPI: bus type pci registered
[    0.612399] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 63
[    0.612399] PCI: MCFG area at e0000000 reserved in E820
[    0.612399] PCI: Using MMCONFIG for extended config space
[    0.612399] PCI: Using configuration type 1 for base access
[    0.616540] ACPI: EC: Look up EC in DSDT
[    0.622112] ACPI: Interpreter enabled
[    0.622154] ACPI: (supports S0 S3 S4 S5)
[    0.622293] ACPI: Using IOAPIC for interrupt routing
[    0.628136] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.628136] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.628148] pci 0000:00:01.0: PME# disabled
[    0.628236] PCI: 0000:00:1a.0 reg 20 io port: [e100, e11f]
[    0.628293] PCI: 0000:00:1a.1 reg 20 io port: [e200, e21f]
[    0.628349] PCI: 0000:00:1a.2 reg 20 io port: [e000, e01f]
[    0.628395] PCI: 0000:00:1a.7 reg 10 32bit mmio: [e7305000, e73053ff]
[    0.628461] PCI: 0000:00:1b.0 reg 10 64bit mmio: [e7300000, e7303fff]
[    0.628493] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.628527] pci 0000:00:1b.0: PME# disabled
[    0.628598] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.628632] pci 0000:00:1c.0: PME# disabled
[    0.628705] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.628739] pci 0000:00:1c.3: PME# disabled
[    0.628810] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.628854] pci 0000:00:1c.4: PME# disabled
[    0.628934] PCI: 0000:00:1d.0 reg 20 io port: [e300, e31f]
[    0.628990] PCI: 0000:00:1d.1 reg 20 io port: [e400, e41f]
[    0.629046] PCI: 0000:00:1d.2 reg 20 io port: [e500, e51f]
[    0.629092] PCI: 0000:00:1d.7 reg 10 32bit mmio: [e7304000, e73043ff]
[    0.629255] PCI: 0000:00:1f.2 reg 10 io port: [0, 7]
[    0.629260] PCI: 0000:00:1f.2 reg 14 io port: [0, 3]
[    0.629265] PCI: 0000:00:1f.2 reg 18 io port: [0, 7]
[    0.629270] PCI: 0000:00:1f.2 reg 1c io port: [0, 3]
[    0.629275] PCI: 0000:00:1f.2 reg 20 io port: [f000, f00f]
[    0.629280] PCI: 0000:00:1f.2 reg 24 io port: [f100, f10f]
[    0.629312] PCI: 0000:00:1f.3 reg 10 64bit mmio: [e7306000, e73060ff]
[    0.629324] PCI: 0000:00:1f.3 reg 20 io port: [500, 51f]
[    0.629361] PCI: 0000:00:1f.5 reg 10 io port: [e700, e707]
[    0.629366] PCI: 0000:00:1f.5 reg 14 io port: [e800, e803]
[    0.629371] PCI: 0000:00:1f.5 reg 18 io port: [e900, e907]
[    0.629376] PCI: 0000:00:1f.5 reg 1c io port: [ea00, ea03]
[    0.629381] PCI: 0000:00:1f.5 reg 20 io port: [eb00, eb0f]
[    0.629387] PCI: 0000:00:1f.5 reg 24 io port: [ec00, ec0f]
[    0.629426] PCI: 0000:01:00.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.629438] PCI: 0000:01:00.0 reg 18 64bit mmio: [e5000000, e500ffff]
[    0.629443] PCI: 0000:01:00.0 reg 20 io port: [b000, b0ff]
[    0.629451] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    0.629464] pci 0000:01:00.0: supports D1
[    0.629466] pci 0000:01:00.0: supports D2
[    0.629488] PCI: 0000:01:00.1 reg 10 64bit mmio: [e5010000, e5013fff]
[    0.629517] pci 0000:01:00.1: supports D1
[    0.629519] pci 0000:01:00.1: supports D2
[    0.629553] PCI: bridge 0000:00:01.0 io port: [b000, bfff]
[    0.629555] PCI: bridge 0000:00:01.0 32bit mmio: [e4000000, e5ffffff]
[    0.629559] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.629683] PCI: 0000:03:00.0 reg 24 32bit mmio: [e7000000, e7001fff]
[    0.629712] pci 0000:03:00.0: PME# supported from D3hot
[    0.629747] pci 0000:03:00.0: PME# disabled
[    0.629813] PCI: 0000:03:00.1 reg 10 io port: [c000, c007]
[    0.629822] PCI: 0000:03:00.1 reg 14 io port: [c100, c103]
[    0.629830] PCI: 0000:03:00.1 reg 18 io port: [c200, c207]
[    0.629838] PCI: 0000:03:00.1 reg 1c io port: [c300, c303]
[    0.629847] PCI: 0000:03:00.1 reg 20 io port: [c400, c40f]
[    0.629918] PCI: bridge 0000:00:1c.3 io port: [c000, cfff]
[    0.629922] PCI: bridge 0000:00:1c.3 32bit mmio: [e7000000, e70fffff]
[    0.629968] PCI: 0000:04:00.0 reg 10 io port: [d000, d0ff]
[    0.629981] PCI: 0000:04:00.0 reg 18 32bit mmio: [e7110000, e7110fff]
[    0.629995] PCI: 0000:04:00.0 reg 20 32bit mmio: [e7100000, e710ffff]
[    0.630008] PCI: 0000:04:00.0 reg 30 32bit mmio: [0, ffff]
[    0.630034] pci 0000:04:00.0: supports D1
[    0.630036] pci 0000:04:00.0: supports D2
[    0.630037] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.630072] pci 0000:04:00.0: PME# disabled
[    0.630132] PCI: bridge 0000:00:1c.4 io port: [d000, dfff]
[    0.630135] PCI: bridge 0000:00:1c.4 32bit mmio: [e6000000, e6ffffff]
[    0.630141] PCI: bridge 0000:00:1c.4 64bit mmio pref: [e7100000, e71fffff]
[    0.630172] PCI: 0000:05:01.0 reg 10 32bit mmio: [e7200000, e7207fff]
[    0.630243] PCI: 0000:05:07.0 reg 10 32bit mmio: [e720c000, e720c7ff]
[    0.630250] PCI: 0000:05:07.0 reg 14 32bit mmio: [e7208000, e720bfff]
[    0.630287] pci 0000:05:07.0: supports D1
[    0.630288] pci 0000:05:07.0: supports D2
[    0.630290] pci 0000:05:07.0: PME# supported from D0 D1 D2 D3hot
[    0.631273] pci 0000:05:07.0: PME# disabled
[    0.631332] pci 0000:00:1e.0: transparent bridge
[    0.631366] PCI: bridge 0000:00:1e.0 32bit mmio: [e7200000, e72fffff]
[    0.631389] bus 00 -> node 0
[    0.631394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.631665] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.632093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.632190] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.632287] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.648520] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.648654] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.649109] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.649562] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.650014] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.650516] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.652235] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[    0.652687] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.653090] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.653090] pnp: PnP ACPI init
[    0.653090] ACPI: bus type pnp registered
[    0.656346] pnp: PnP ACPI: found 14 devices
[    0.656346] ACPI: ACPI bus type pnp unregistered
[    0.656346] PnPBIOS: Disabled by ACPI PNP
[    0.656346] PCI: Using ACPI for IRQ routing
[    0.668041] NET: Registered protocol family 8
[    0.668077] NET: Registered protocol family 20
[    0.668133] NetLabel: Initializing
[    0.668133] NetLabel:  domain hash size = 128
[    0.668133] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.668155] NetLabel:  unlabeled traffic allowed by default
[    0.668191] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.668347] hpet0: 4 64-bit timers, 14318180 Hz
[    0.670119] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.670152]    actual entries 65620
[    0.670246] AppArmor: AppArmor Filesystem Enabled
[    0.670293] ACPI: RTC can wake from S4
[    0.672039] Switched to high resolution mode on CPU 0
[    0.672946] Switched to high resolution mode on CPU 1
[    0.673339] Switched to high resolution mode on CPU 3
[    0.673371] Switched to high resolution mode on CPU 2
[    0.676046] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.676084] system 00:01: ioport range 0x290-0x29f has been reserved
[    0.676121] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.676157] system 00:01: ioport range 0x290-0x294 has been reserved
[    0.676194] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.676234] system 00:01: ioport range 0x4c0-0x4ff could not be reserved
[    0.676274] system 00:0a: ioport range 0x400-0x4bf has been reserved
[    0.676309] system 00:0b: iomem range 0xe0000000-0xe3ffffff could not be reserved
[    0.676349] system 00:0c: iomem range 0xcfa00-0xcffff has been reserved
[    0.676382] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[    0.676415] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[    0.676448] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[    0.676482] system 00:0c: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.676519] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[    0.676552] system 00:0c: iomem range 0x100000-0x7fedffff could not be reserved
[    0.676589] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.676626] system 00:0c: iomem range 0xfed10000-0xfed1dfff could not be reserved
[    0.676663] system 00:0c: iomem range 0xfed20000-0xfed8ffff could not be reserved
[    0.676700] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.676737] system 00:0c: iomem range 0xffb00000-0xffb7ffff could not be reserved
[    0.676774] system 00:0c: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.676810] system 00:0c: iomem range 0xe0000-0xeffff has been reserved
[    0.712108] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.712141] pci 0000:00:01.0:   IO window: 0xb000-0xbfff
[    0.712175] pci 0000:00:01.0:   MEM window: 0xe4000000-0xe5ffffff
[    0.712208] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.712247] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.712279] pci 0000:00:1c.0:   IO window: disabled
[    0.712312] pci 0000:00:1c.0:   MEM window: disabled
[    0.712346] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.712381] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:03
[    0.712414] pci 0000:00:1c.3:   IO window: 0xc000-0xcfff
[    0.712448] pci 0000:00:1c.3:   MEM window: 0xe7000000-0xe70fffff
[    0.712481] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.712517] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:04
[    0.712550] pci 0000:00:1c.4:   IO window: 0xd000-0xdfff
[    0.712584] pci 0000:00:1c.4:   MEM window: 0xe6000000-0xe6ffffff
[    0.712618] pci 0000:00:1c.4:   PREFETCH window: 0x000000e7100000-0x000000e71fffff
[    0.712658] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.712690] pci 0000:00:1e.0:   IO window: disabled
[    0.712724] pci 0000:00:1e.0:   MEM window: 0xe7200000-0xe72fffff
[    0.712758] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.712798] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.712832] pci 0000:00:01.0: setting latency timer to 64
[    0.712838] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.712873] pci 0000:00:1c.0: setting latency timer to 64
[    0.712879] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.712914] pci 0000:00:1c.3: setting latency timer to 64
[    0.712920] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.712954] pci 0000:00:1c.4: setting latency timer to 64
[    0.712959] pci 0000:00:1e.0: setting latency timer to 64
[    0.712962] bus: 00 index 0 io port: [0, ffff]
[    0.712994] bus: 00 index 1 mmio: [0, ffffffff]
[    0.713025] bus: 01 index 0 io port: [b000, bfff]
[    0.713056] bus: 01 index 1 mmio: [e4000000, e5ffffff]
[    0.713088] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.713119] bus: 01 index 3 mmio: [0, 0]
[    0.713150] bus: 02 index 0 mmio: [0, 0]
[    0.713181] bus: 02 index 1 mmio: [0, 0]
[    0.713212] bus: 02 index 2 mmio: [0, 0]
[    0.713243] bus: 02 index 3 mmio: [0, 0]
[    0.713274] bus: 03 index 0 io port: [c000, cfff]
[    0.713305] bus: 03 index 1 mmio: [e7000000, e70fffff]
[    0.713337] bus: 03 index 2 mmio: [0, 0]
[    0.713368] bus: 03 index 3 mmio: [0, 0]
[    0.713399] bus: 04 index 0 io port: [d000, dfff]
[    0.713430] bus: 04 index 1 mmio: [e6000000, e6ffffff]
[    0.713462] bus: 04 index 2 mmio: [e7100000, e71fffff]
[    0.713493] bus: 04 index 3 mmio: [0, 0]
[    0.713534] bus: 05 index 0 mmio: [0, 0]
[    0.713565] bus: 05 index 1 mmio: [e7200000, e72fffff]
[    0.713597] bus: 05 index 2 mmio: [0, 0]
[    0.713628] bus: 05 index 3 io port: [0, ffff]
[    0.713659] bus: 05 index 4 mmio: [0, ffffffff]
[    0.713696] NET: Registered protocol family 2
[    0.728069] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.728303] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.728549] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.728688] TCP: Hash tables configured (established 131072 bind 65536)
[    0.728722] TCP reno registered
[    0.732094] NET: Registered protocol family 1
[    0.732234] checking if image is initramfs... it is
[    1.300502] Freeing initrd memory: 8009k freed
[    1.302422] audit: initializing netlink socket (disabled)
[    1.302480] type=2000 audit(1231206116.300:1): initialized
[    1.307537] highmem bounce pool size: 64 pages
[    1.307576] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.310519] VFS: Disk quotas dquot_6.5.1
[    1.310645] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.310799] msgmni has been set to 1743
[    1.310972] io scheduler noop registered
[    1.311008] io scheduler anticipatory registered
[    1.311047] io scheduler deadline registered
[    1.311086] io scheduler cfq registered (default)
[    1.311245] pci 0000:01:00.0: Boot video device
[    1.311356] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.311389] pcieport-driver 0000:00:01.0: found MSI capability
[    1.311443] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.311491] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.311588] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.311617] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.311676] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.311728] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.311785] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.311891] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.311932] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.311991] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.312040] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.312101] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.312201] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.312237] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.312305] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.312356] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.312405] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.312820] isapnp: Scanning for PnP cards...
[    1.665736] isapnp: No Plug & Play device found
[    1.708148] hpet_resources: 0xfed00000 is busy
[    1.708252] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.708423] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.709294] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.711656] brd: module loaded
[    1.711770] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.712065] PNP: No PS/2 controller found. Probing ports directly.
[    1.712500] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.712544] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.713665] mice: PS/2 mouse device common for all mice
[    1.713845] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.713902] rtc0: alarms up to one month, hpet irqs
[    1.714100] EISA: Probing bus 0 at eisa.0
[    1.714174] EISA: Detected 0 cards.
[    1.714205] cpuidle: using governor ladder
[    1.714237] cpuidle: using governor menu
[    1.714814] TCP cubic registered
[    1.714863] Using IPI No-Shortcut mode
[    1.715097] registered taskstats version 1
[    1.715290]   Magic number: 9:652:659
[    1.715327] block ram12: hash matches
[    1.715374] tty ptyea: hash matches
[    1.715453] rtc_cmos 00:04: setting system clock to 2009-01-06 01:41:57 UTC (1231206117)
[    1.715491] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.715528] EDD information not available.
[    1.715681] Freeing unused kernel memory: 424k freed
[    1.715750] Write protecting the kernel text: 2576k
[    1.715806] Write protecting the kernel read-only data: 936k
[    1.810828] fuse init (API version 7.9)
[    1.831526] ACPI: SSDT 7FEE7A40, 022A (r1  PmRef  Cpu0Ist     3000 INTL 20040311)
[    1.831931] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    1.832118] processor ACPI0007:00: registered as cooling_device0
[    1.833124] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.833355] ACPI: SSDT 7FEE7F00, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20040311)
[    1.833778] ACPI: CPU1 (power states: C1[C1] C2[C2])
[    1.833957] processor ACPI0007:01: registered as cooling_device1
[    1.833996] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.834267] ACPI: SSDT 7FEE8060, 0152 (r1  PmRef  Cpu2Ist     3000 INTL 20040311)
[    1.834721] ACPI: CPU2 (power states: C1[C1] C2[C2])
[    1.834907] processor ACPI0007:02: registered as cooling_device2
[    1.834948] ACPI: Processor [CPU2] (supports 8 throttling states)
[    1.835218] ACPI: SSDT 7FEE81C0, 0152 (r1  PmRef  Cpu3Ist     3000 INTL 20040311)
[    1.835664] ACPI: CPU3 (power states: C1[C1] C2[C2])
[    1.835845] processor ACPI0007:03: registered as cooling_device3
[    1.835884] ACPI: Processor [CPU3] (supports 8 throttling states)
[    1.917624] usbcore: registered new interface driver usbfs
[    1.917674] usbcore: registered new interface driver hub
[    1.917759] usbcore: registered new device driver usb
[    1.928722] USB Universal Host Controller Interface driver v3.0
[    1.928789] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.928828] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.928831] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.928894] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.928957] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000e100
[    1.929083] usb usb1: configuration #1 chosen from 1 choice
[    1.929138] hub 1-0:1.0: USB hub found
[    1.929173] hub 1-0:1.0: 2 ports detected
[    2.000384] No dock devices found.
[    2.014605] SCSI subsystem initialized
[    2.035682] libata version 3.00 loaded.
[    2.036851] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.036891] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.036895] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.036945] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    2.037007] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000e200
[    2.037110] usb usb2: configuration #1 chosen from 1 choice
[    2.037164] hub 2-0:1.0: USB hub found
[    2.037198] hub 2-0:1.0: 2 ports detected
[    2.144731] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.144775] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    2.144778] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    2.144832] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    2.144896] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000e000
[    2.145006] usb usb3: configuration #1 chosen from 1 choice
[    2.145061] hub 3-0:1.0: USB hub found
[    2.145098] hub 3-0:1.0: 2 ports detected
[    2.352350] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.352396] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.352399] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.352449] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    2.356380] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.356386] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xe7305000
[    2.464035] usb 3-1: new low speed USB device using uhci_hcd and address 2
[    2.476026] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.476161] usb usb4: configuration #1 chosen from 1 choice
[    2.476214] hub 4-0:1.0: USB hub found
[    2.476250] hub 4-0:1.0: 6 ports detected
[    2.532048] hub 3-0:1.0: unable to enumerate USB device on port 1
[    2.684288] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.684326] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.684329] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.684378] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.684438] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000e300
[    2.684541] usb usb5: configuration #1 chosen from 1 choice
[    2.684592] hub 5-0:1.0: USB hub found
[    2.684626] hub 5-0:1.0: 2 ports detected
[    2.788426] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.788462] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.788465] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.788521] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.788580] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000e400
[    2.788677] usb usb6: configuration #1 chosen from 1 choice
[    2.788728] hub 6-0:1.0: USB hub found
[    2.788762] hub 6-0:1.0: 2 ports detected
[    2.892465] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    2.892501] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.892504] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.892559] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.892614] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e500
[    2.892712] usb usb7: configuration #1 chosen from 1 choice
[    2.892763] hub 7-0:1.0: USB hub found
[    2.892797] hub 7-0:1.0: 2 ports detected
[    2.996600] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    2.996638] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.996641] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.996698] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.000622] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.000627] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe7304000
[    3.016024] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.016144] usb usb8: configuration #1 chosen from 1 choice
[    3.016208] hub 8-0:1.0: USB hub found
[    3.016243] hub 8-0:1.0: 6 ports detected
[    3.125686] ata_piix 0000:00:1f.2: version 2.12
[    3.125699] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.125736] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    3.125932] ata_piix 0000:00:1f.2: setting latency timer to 64
[    3.125986] scsi0 : ata_piix
[    3.126088] scsi1 : ata_piix
[    3.126705] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    3.126740] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    3.132562] usb 3-1: new low speed USB device using uhci_hcd and address 3
[    3.312080] usb 3-1: configuration #1 chosen from 1 choice
[    3.552051] usb 3-2: new low speed USB device using uhci_hcd and address 4
[    3.600090] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.728073] usb 3-2: configuration #1 chosen from 1 choice
[    3.731169] usbcore: registered new interface driver hiddev
[    3.746258] input: LITEON Technology USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.2/usb3/3-1/3-1:1.0/input/input1
[    3.752088] input,hidraw0: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.2-1
[    3.765212] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.2/usb3/3-2/3-2:1.0/input/input2
[    3.769607] input,hidraw1: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.2-2
[    3.769768] usbcore: registered new interface driver usbhid
[    3.769800] usbhid: v2.6:USB HID core driver
[    3.804200] ata1.00: HPA unlocked: 312579695 -> 312581808, native 312581808
[    3.804237] ata1.00: ATA-7: ST3160815AS, 3.AAD, max UDMA/133
[    3.804269] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.848472] ata1.00: configured for UDMA/133
[    4.325590] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.325718] ata2.01: NODEV after polling detection
[    4.332212] ata2.00: ATAPI: TSSTcorp CDDVDW SH-S223Q, SB02, max UDMA/100
[    4.348212] ata2.00: configured for UDMA/100
[    4.348332] scsi 0:0:0:0: Direct-Access     ATA      ST3160815AS      3.AA PQ: 0 ANSI: 5
[    4.349130] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223Q  SB02 PQ: 0 ANSI: 5
[    4.349320] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.349370] r8169 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.349414] r8169 0000:04:00.0: setting latency timer to 64
[    4.349687] eth0: RTL8168c/8111c at 0xf8836000, 00:1f:d0:d1:1f:da, XID 3c4000c0 IRQ 219
[    4.351580] pata_jmicron 0000:03:00.1: enabling device (0000 -> 0001)
[    4.351617] pata_jmicron 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    4.351677] pata_jmicron 0000:03:00.1: setting latency timer to 64
[    4.351984] scsi2 : pata_jmicron
[    4.352101] scsi3 : pata_jmicron
[    4.352711] ata3: PATA max UDMA/100 cmd 0xc000 ctl 0xc100 bmdma 0xc400 irq 16
[    4.352744] ata4: PATA max UDMA/100 cmd 0xc200 ctl 0xc300 bmdma 0xc408 irq 16
[    4.352917] ata_piix 0000:00:1f.5: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.352957] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    4.353163] ata_piix 0000:00:1f.5: setting latency timer to 64
[    4.353254] scsi4 : ata_piix
[    4.353341] scsi5 : ata_piix
[    4.353850] ata5: SATA max UDMA/133 cmd 0xe700 ctl 0xe800 bmdma 0xeb00 irq 19
[    4.353889] ata6: SATA max UDMA/133 cmd 0xe900 ctl 0xea00 bmdma 0xeb08 irq 19
[    4.671569] ahci 0000:03:00.0: version 3.0
[    4.671588] ahci 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.684144] ata5: SATA link down (SStatus 0 SControl 300)
[    4.685585] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    4.685628] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    4.685669] ahci 0000:03:00.0: setting latency timer to 64
[    4.685778] scsi6 : ahci
[    4.685884] scsi7 : ahci
[    4.685973] ata7: SATA max UDMA/133 abar m8192@0xe7000000 port 0xe7000100 irq 19
[    4.686011] ata8: SATA max UDMA/133 abar m8192@0xe7000000 port 0xe7000180 irq 19
[    5.010653] ata6: SATA link down (SStatus 0 SControl 300)
[    5.010737] ata7: SATA link down (SStatus 0 SControl 300)
[    5.344036] ata8: SATA link down (SStatus 0 SControl 300)
[    5.360087] ohci1394 0000:05:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.409851] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[e720c000-e720c7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.410057] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.410124] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    5.431232] Driver 'sr' needs updating - please use bus_type methods
[    5.435328] Driver 'sd' needs updating - please use bus_type methods
[    5.435437] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.435486] sd 0:0:0:0: [sda] Write Protect is off
[    5.435532] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.435592] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.435685] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    5.435731] sd 0:0:0:0: [sda] Write Protect is off
[    5.435764] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.435787] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.435827]  sda:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.440216] Uniform CD-ROM driver Revision: 3.20
[    5.440314] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.454063]  sda1 sda2 < sda5 >
[    5.475268] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.650564] PM: Starting manual resume from disk
[    5.650597] PM: Resume from partition 8:5
[    5.650598] PM: Checking hibernation image.
[    5.650753] PM: Resume from disk failed.
[    5.667081] EXT3-fs: INFO: recovery required on readonly filesystem.
[    5.667116] EXT3-fs: write access will be enabled during recovery.
[    5.846615] kjournald starting.  Commit interval 5 seconds
[    5.846626] EXT3-fs: recovery complete.
[    5.846970] EXT3-fs: mounted filesystem with ordered data mode.
[    6.680712] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[007e922600001fd0]
[   11.308360] udevd version 124 started
[   11.631055] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.650065] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.655754] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   11.742435] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   11.760521] ACPI: Power Button (FF) [PWRF]
[   11.760622] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   11.762933] Linux agpgart interface v0.103
[   11.792518] ACPI: Power Button (CM) [PWRB]
[   11.958597] fglrx: disagrees about version of symbol struct_module
[   12.092268] parport_pc 00:09: reported by Plug and Play ACPI
[   12.092349] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   12.212778] rt61pci 0000:05:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   12.220009] phy0: Selected rate control algorithm 'pid'
[   12.321218] Registered led device: rt61pci-phy0:radio
[   12.321280] Registered led device: rt61pci-phy0:assoc
[   13.308168] lp0: using parport0 (interrupt-driven).
[   13.434787] Adding 6064496k swap on /dev/sda5.  Priority:-1 extents:1 across:6064496k
[   13.788864] EXT3 FS on sda1, internal journal
[   14.066038] type=1505 audit(1231206129.845:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4382
[   14.200054] type=1505 audit(1231206129.978:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4387
[   14.200192] type=1505 audit(1231206129.981:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4387
[   14.278942] ip_tables: (C) 2000-2006 Netfilter Core Team
```

---

### Post by lavinog on 2009-01-05
why is your xorg.conf bare?
Did it get reset?

---

### Post by blahdieblah on 2009-01-05
> **lavinog said:**
> why is your xorg.conf bare?
Did it get reset?

It probably did, because whenever I get that same corrupted screen error, I use xfix in Recovery Mode to get it back to normal. (It disables the ATI driver, among other things)

Do you notice anything extremely wrong with those files?

---

### Post by lavinog on 2009-01-05
with your xorg.conf bare like that, is your video corrupted?

can you repeat the 
```
sudo aticonfig --initial
```
then add the
```

SubSection "Display"
  Depth 24
  Modes "1024x768"
 EndSubSection

```
then post your xorg.conf
then reboot and see if it works.

---

### Post by blahdieblah on 2009-01-05
> **lavinog said:**
> with your xorg.conf bare like that, is your video corrupted?

can you repeat the 
```
sudo aticonfig --initial
```
then add the
```

SubSection "Display"
  Depth 24
  Modes "1024x768"
 EndSubSection

```
then post your xorg.conf
then reboot and see if it works.

Here's my newly updated file:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes "1024x768"
	EndSubSection
EndSection

```

I'll reboot now.


EDIT: The same corrupted screen happened after editing it. And to answer your question, I don't get the error with a bare xorg.conf.

I really don't know what to do at this point. I'd love to get this working, but if it's a problem you don't know how to fix I could always try reinstalling and trying something differently.

---

### Post by lavinog on 2009-01-05
Well if reducing the resolution didn't help, maybe reinstalling would be the best way to go.

a good site to try out is [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

let me know how it turns out.

also if you have another monitor handy, see if you get the same results with it.

---

### Post by blahdieblah on 2009-01-05
I did have another monitor handy, and the exact same result occured. 

What I'll do is, reinstall the entire OS, let the 200 some updates go, reboot first, and then try the Ubuntu-recommended ATI driver. If that works, I'll try the advanced ones from ATI's website. If one works, I'll stick with that. If neither work, it's no big deal.

---

### Post by blahdieblah on 2009-01-06
My god, it worked!

I reinstalled from the Live CD, let the updates go, rebooted, and followed the instructions fully on the guide you linked to. It worked like a charm! And the resolution is now up to something better. Before even changing a thing I've noticed more desktop effects... which is a good sign that it's recognizing my faster video card.

I know we couldn't get it right without reinstalling, but thanks so much to everyone for the help.

---

### Post by lavinog on 2009-01-14
I just got done installing the 8-12 drivers on a computer at work, and a similar thing happened.
I wound up having to comment out all of the lines in /etc/modeprobe.d/lrm-video
mentioned in [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/149934)
this may have been a different issue though, because this computer is using hardy and has been upgraded from each release since edgy.
Edit: I checked another hardy computer. This one was installed from scratch, but never really had the fglrx driver loaded properly...it turned out that the lrm-video was that only thing preventing 3d from working. This one didn't have any screen distortion when it wasn't working, and for the most part no one suspected that it wasn't working since 3d was rarely used.

---

### Post by Thowsen on 2009-01-17
i fixed this problem last night. press esc at start and do all the recovery things, when u boot after that u will have the standard resoloution again.
manually uninstall catalyst, and disable the accelerated graphics that ubuntu recommended u to install (cuz there lies the problem) after uninstalling catalyst, download catalyst via ati.com. choose properties and enable the installer to run as a program. then type '' sudo -i andhereshouldthenameofthefilebe '' (be sure to have the installer on the desktop) and after this i asks u to reboot, do so, and now it should work :)

i got the exact same graphiccard and have suffered the same problem, and this worked for me

---

