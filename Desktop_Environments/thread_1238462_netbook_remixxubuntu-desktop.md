---
title: "netbook remix/xubuntu-desktop"
date: 2009-08-12
forum: Desktop Environments
---

### Post by tzirtzi on 2009-08-12
Hello all :)

I'm in the process of setting up a Toshiba NB200 netbook to dual boot Ubuntu and XP. I've had various problems (with Wifi, touchpad, audio, hibernation, crashing) which I've dealt with by trying various different versions of Ubuntu (I've settled on Netbook Remix 9.04) and following the instructions [here]("from http://ubuntuforums.org/showthread.php?t=1193429&page=4"), [here](https://help.ubuntu.com/community/OpenSound), [here](http://www.4front-tech.com/forum/viewtopic.php?t=3225&start=26), and [here](http://ubuntuforums.org/showthread.php?t=1215665).

The netbook was pretty sluggish to start, though, so having read that XFCE was optimised for lower spec systems I thought I'd try that. I installed the *xubuntu-desktop* package, and it seemed to work... But now I've noticed that when using the XFCE desktop, the XFCE and Gnome taskbars both appear - whenever I move my mouse over the taskbar, it switches from one to the other. Using icons from the Gnome taskbar when in XFCE doesnt seem to work properly. Also, although I'd assumed that the netbook desktop was associated with Gnome, it seems to be running in the background when running XFCE as when I log out it appears briefly.

Could this strangeness be connected to the various other problems running Ubuntu on the NB200? Or is it likely to be something else? Could I fix it without removing Gnome, which I'd like to leave as an option?

Thanks very much :)
-tzirtzi

---

### Post by ugm6hr on 2009-08-12
Remove the netbook-launcher package.

I have Gnome & Xfce on my Mini 9 with no problems, but I did remove the netbook-launcher package.

---

### Post by tzirtzi on 2009-08-12
I've now removed netbook-launcher and it seems to have made things worse... / weirder: now in XFCE I get the Gnome desktop as well as shifting taskbar...

---

### Post by ugm6hr on 2009-08-13
> **tzirtzi said:**
> I've now removed netbook-launcher and it seems to have made things worse... / weirder: now in XFCE I get the Gnome desktop as well as shifting taskbar...

I have no idea what is going on.  This should not happen.  Had a quick look through some of the fixes you had to do for the NB200; none should cause any long term problems.

How did you install Xfce?

What do you have listed in your autostarted applications list?  Make sure you have thunar managing the desktop too.

---

### Post by tzirtzi on 2009-08-13
Sorry for the delay in posting again, I lost the internet for a day for unrelated reasons.

Gnome has now deteriorated as well... All of the items on the top and bottom panels disappeared, and I had to re-add them. Some I couldn't work out how to re-add, so I've now only got wireless working in XFCE, despite its odd behavior. It's this depleted panel that appears sometimes in XFCE also.

I tried reinstalling netbook-launcher in case that undid some of the deterioration, but the result is that *it* now no longer works very well... I get the netbook-launcher desktop/menus, but the semi-broken Gnome/XFCE panels.

I installed XFCE from the terminal, with *sudo apt-get install xubuntu-desktop*.

In XFCE the following applications are on the startup list:

UME Desktop Launcher
UNR Desktop Launcher
Network Manager
Update Notifier
Maximus Window Management
Check for new hardware drivers
Power Manager
Print Queue Applet
Bluetooth Manager

In Gnome the following applications are on the startup list:

AT-SPI Registry Wrapper
Bluetooth Manager
Check for new hardware drivers
Evolution Alarm Notifier
GNOME Keyring Daemon
GNOME Login Sound
GNOME Settings Daemon
GNOME Settings Daemon Helper
GNOME Splash Screen
Indicator Applet
Maximus Window Management
Network Manager
Power Manager
Print Queue Applet
Remote Desktop
Seahorse Daemon
UME Desktop Launcher
UNR Launcher
Update Notifier
User folders update
Visual Assistance
Xfce Settings Helper
XfConf Migration Script

All in all, I imagine it would be better to reinstall Ubuntu from scratch,  probably starting with Xubuntu instead of having both Gnome and XFCE, but if possible I'd like to avoid that as my Windows installation on this machine is *also* currently broken and it's taken quite a lot of work to get all of the other individual issues working in Ubuntu... But if it's a mystery to everyone, then I'll just do that.

---

### Post by ugm6hr on 2009-08-14
Honestly, I'm not 100% certain what is going on here.  I installed Xfce with apt-get install xfce4, but I don't see why xubuntu-desktop should cause any problems.

I wonder whether some of your gnome user settings have gone awry.  

Try creating a new user (with admin rights) to see ig Xfce works for the new user.  If it does, it should be possible to fix this.

---

### Post by tzirtzi on 2009-08-14
Ah... That seems to work. I'm currently logged in to xfce with a new Administrator user, and as far as I can see, everything is normal and working. Which does indeed imply that the problems must be stemming from user settings - do you know what they might be and how I might go about changing them?

One problem that does remain - which I hadn't previously mentioned - is that Parted can't access my two ntfs or one fat16 partitions when in xfce (but can in Gnome). This is also the case when I'm running Xubuntu live from a USB key, so it's a problem with Xubuntu+my hardware rather than a problem related to the user settings as well, I assume.

Thanks for your help! :)

---

### Post by ugm6hr on 2009-08-14
We'll try and solve the Parted issue later (mainly cos I have no idea what the problem might be).

I think the gnome settings are in ~/.gnome2 (and perhaps ~/.gnome), and deleting the folder and rebooting might help.

However, I would suggest waiting for someone else to confirm before making any drastic changes, since I'm not entirely sure what side effects deleting everything might have.

---

### Post by tzirtzi on 2009-08-15
Well, i threw caution to the winds and tried that anyway, but it doesnt seem to have had any effect im afraid...

---

### Post by tzirtzi on 2009-08-16
(*bump*)

Does anyone have any ideas about what I might do here? Or shall I reinstall - probably with a different release, as both netbook remix and xubuntu don't seem to have worked wonderfully here... Does anyone have any experience with Kubuntu on the NB200? I've tried it from a usb key but as I don't know the interface, coulnd't get much of an impression of it. Is KDE much more resource heavy than Gnome? Than xfce?

---

### Post by ugm6hr on 2009-08-16
Try removing a few more hidden folders.

In fact, if you are considering a reinstall, just delete all the hidden folderss from your home directory.  If you have emails / bookmarks etc that are important, let me know which applications you are using, and I'll tell you how to save them.

---

### Post by tzirtzi on 2009-08-16
Have tried that and here is the result (logged in to a Gnome session):

[Screenshot link]("http://www.superlush.co.uk/images/Screenshot.png")

The top left button is not a menu but the netbook remix go-to-desktop button, and it does nothing. Alt-F2 still works so I can run software, but obviously not very satisfactory...

---

### Post by ugm6hr on 2009-08-16
Is xfce behaving now?

And you should remove netbook-launcher again - it is definitely not required, and perhaps part of the problem.

Have you enabled compiz?

I would suggest:

Alt+F2: gnome-terminal

```
sudo apt-get remove netbook-launcher compiz-core
sudo apt-get install xfce4
```

Then reboot and select xfce.

---

### Post by tzirtzi on 2009-08-16
xfce does indeed appear to be working now (with the exception of the separate-issue partition mounting issue).

Terminal informs me that netbook-launcher is not installed and so will not be removed - this is odd/untrue, as it's evidently running the netbook-launcher type desktop (different task bar etc.) and because I had indeed reinstalled it...

It successfully removed compiz-core and installed xfce4 (incidentally I autoremoved linux-headers-2.6.28-11 and linux-headers-2.6.28-11-generic at the same time).

Unsurprisingly (given that it hasn't managed to do anything to netbook-launcher) this has had no visible effort.

Any idea why it might not be able to find netbook-launcher? Or might it be correct and netbook-launcher isnt the cause of the odd, broken netbook-remix desktop?

Thanks again for all your help :)
-tzirtzi

---

### Post by ugm6hr on 2009-08-16
At least we have xfce working properly - which is presumably what you wanted to begin with....  I would recommend persevering with xfce, it is my preferred DE for my Mini 9, and now on my main laptop too.  Only thing it doesn't too as well as Gnome is network access to files and external monitors.  There are a couple of issues with the default - large text, sound mutes etc, which can all be fixed (look for my posts with xfce / xfce4 tags).

As for Gnome, I don't understand why emptying all the gnome settings hasn't reset it to default.  As for why netbook-launcher isn't found - most common reason is misspelling.

So try again:
```
sudo apt-get purge netbook-launcher ubuntu-netbook-remix
```

Then try re-installing Gnome basics:
```
sudo apt-get install --reinstall xorg gdm acpi-support gnome-session gnome-menus gnome-panel gnome-applets gnome-volume-manager gnome-power-manager metacity nautilus gnome-screensaver xscreensaver menu gnome-utils gnome-system-tools libgnomevfs2-extra smbfs
```

Then reboot into Gnome again.

As for the Parted issue - I haven't been able to use it on my Netbook at all (in Gnome or Xfce), which I presume relates to the internal SD.  Afraid I can't help with that - why do you need it?

---

### Post by tzirtzi on 2009-08-16
Well, I was hoping for Gnome and xfce side-by-side... But yes, having xfce generally working is great :). The partitions thing - well, I'm dual booting with Windows (not successfully atm but that's a different story) and want to keep documents, images, video and music on an ntfs partition to be accessed from ubuntu and windows. Gnome can mount the ntfs partition and GParted can *sometimes* access it. xfce can't see it at all, and if I run gparted from xfce I get an error for each of my non-linux partitions after which it can't do anything with them. The harddrive in there is one that I installed - a 500gb 2.5" Fujitsu laptop hard drive. 

*sudo apt-get purge netbook-launcher ubuntu-netbook-remix* returned "not installed, so not removed" for both packages. I've double checked for typos! Should I try the re-installing the Gnome basics anyway?

---

### Post by ugm6hr on 2009-08-17
> **tzirtzi said:**
> Should I try the re-installing the Gnome basics anyway?

Why not...  And delete all the hidden (i.e. beginning with a ,) folder in ~/ again before rebooting.

Your NTFS partition won't mount in Xfce?  That sounds like a problem with your NTFS partition, not Xfce.  Gparted is not required to fix this.

I would suggest booting Windows and running some diagnostics, and defragmenting.

ntfs-config will sort out the automounting of NTFS partitions.

---

### Post by tzirtzi on 2009-08-17
Cool :) Just running those reinstalls now...

Sadly, I can't boot into windows - I foolishly used the Ubuntu installer automatic partitioner, and it has broken windows. I've been looking for a way to run chkdsk without being able to get into windows for a week... But as I say, that's a different story and not very relevant to this particular category :P It's good to know, though, that fixing that problem might well also fix the one in xfce.

Having now done those reinstalls and deleted the hidden folders again, I'm afraid it seems still to be the same situation.

---

### Post by otsigolf on 2010-01-04
What I could say about xubuntu and Toshiba netbooks from my short experience:

Installed xubuntu 9.04 inside WindowsXP on a Toshiba NB105 8.9" netbook.  All was standard hardware, including factory partition for XP and rescue partition.  Selected install under WindowsXP. Dual boot menu on startup. Granted access to Windows XP NTFS partition.  Absolutely no hardware issues with wifi, screen, keyboard recognition (Spanish), nor synaptics touchpad (didn't tried external screen).  Automounting of any SD card, usb card readers for XD, SD. Automounting and read/write capabilities on usb external drives (both SATA + usb boxes).  Access to WinXP My Documents, Desktop, etc.  Unfortunately tried to upgrade hard disk to 500GB using instructions elsewere and damaged something so now it doesn't boot anyway. Sniff... going to repair centre.
One hint: when the xubuntu installation files inside the NTFS partition (subdir of Program Files made by XP setup) where compressed by XP, then xubuntu was unable to boot.  Uncompressing the directory and files solved the issue and xubuntu returned to work flaulessly.  Hope this helps.

Now, installing xubuntu 9.10 on a Toshiba NB200 with the same option inside WinXP didn't granted access to NTFS on local HD BUT it does on two external USB HD, including 500GB 2.5" WesternDigital Blue Scorpio with a 2.5" usb box, and one 1TB external iomega HD.  Full read/write on NTFS.  But not on local partition!  Tried several ways without any success.  Of note: this setup of xubuntu leaves a 4 options startup for linux: the first one basic, the second basic plus repair routines, and the next two with access to NTFS under dev/sda1.  In my case, only option 1 & 2 were active, don't know why.

Finally XP was unable to boot after some registry changes and the like, so reinstalling XP.  Will try Xubuntu 9.10 again and return here with any news.  I suspect the HD compressing under XP could be a pathway to solve the issue.

---

### Post by Linux Army on 2010-01-04
I would say install the remix versions, I have gone through almost all linux os out there. always came back to ubuntu though. xfce is a great one to

---

### Post by otsigolf on 2010-01-04
After re-installing xubuntu 9.10, no changes: cannot access nfts partition in dev/sda1, but can fully read/write over any of two external usb hard drives (500GB & 1TB).  I am tempted to try 9.04 version as it is the one which worked in Toshiba NB100/NB105 machine.  Hope it will work for NB200.  Version 9.10 sets up a 4 option startup during xubuntu launch, while version 9.04 didn't went in that faulty direction.

I am not convinced if netbook remix will do anything to this issue of non access to local ntfs partition.

---

### Post by otsigolf on 2010-01-06
Solved the ntfs access to local partition:

Installed xubuntu 9.10 inside WindowsXP
Reboot
Selected xubuntu as OS to launch.
Logged into Xubuntu with administrator permissions.
Open terminal.

Introduce commands:
mkdir /mnt/windows
sudo ntfs-3g /dev/sda1 /mnt/windows

Close terminal.

This one gave me full access (read/write) to the ntfs partition, including My Documents, Desktop, etc.

Hope this helps.

---

