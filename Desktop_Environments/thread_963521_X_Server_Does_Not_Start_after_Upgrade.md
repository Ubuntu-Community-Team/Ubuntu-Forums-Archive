---
title: "X Server Does Not Start after Upgrade"
date: 2008-10-30
forum: Desktop Environments
---

### Post by skateoroma on 2008-10-30
Using Hardy 8.04.1 with kernel 2.6.24-21 generic

I ran an update the other night that contained 751 files.  The update did not complete and I had to restart the computer which produced horrible results.

When the system started up I received tons of errors and could not capture all of them.  Here are a few.  Also, I am using a KVM switch and using virtualization so the KVM error confuses me even more.

1) Your system does not have extensions to use KVM.
2) Failed to start x server.  It is likely that it is not set up correctly.
3) (EE) Nvidia(0): Failed to load nvidia kernel module!
4) Fatal server error: No screens found restart GDM.

**What I've tried so far.**
Booted to previous kernel 2.6.24-19 in recovery mode and was able to get to the terminal.

Uninstalled nvidia using 'sudo apt-get remove nvidia*'
Reinstalled 'sudo apt-get install nvidia-glx-new'
Then issued nvidia-xconfig then replaced the new config with the previous with to backup /etc/X11/Xorg.conf.backup

Reinstalled 'aptitude install x-window-system-core x-window-system xterm'

I was able to restart into kernel 2.6.24-19 generic, but wasn't able to use the mouse.  I really don't want to reinstall because I spent a lot of time configuring the desktop.  Also, the hard drive is dual booted with XP and I don't want to lose the grub settings.

Thanks for any help.

---

### Post by ddrichardson on 2008-10-31
KVM - input is now handled by input-hotplug and there might be a configuration issue there try:
```
sudo dpkg-reconfigure console-setup
```
Although it looks more like a screens issue so:
```
sudo dpkg-reconfigure xserver-corg
```

---

### Post by skateoroma on 2008-11-01
Thanks for the response ddrichardson, however, I decided to do a clean install.  Everything was working well until I took the upgrade again.  The upgrade installed without problems, but after the upgrade, I couldn't log back into ubuntu.  I couldn't even get to the prompt. All I get now is a blank screen with (initramfs) at the top.

This is so disappointing.  I was really hoping that I would not have to use windows anymore, but this past event has me back to windows.

I'm going to give it another try and download 8.10.  Hopefully this will be stable.

Thanks again for your help.

---

### Post by ddrichardson on 2008-11-01
You can still recover your home folder using the live cd and I hope you have more sucess with a clean install.

---

### Post by skateoroma on 2008-11-01
> **ddrichardson said:**
> You can still recover your home folder using the live cd and I hope you have more sucess with a clean install.

Can you tell me how to do that?

---

### Post by ddrichardson on 2008-11-01
Boot the LiveCD. It should identify the previous Ubuntu partition, so you can backup your home folder:
```
cd /
sudo tar cvfz home.tar.gz home
```
Then copy that file to a USB disk and install, but specify a /home partition (this is not necessary but should you need to reinstall again you will already have all your data on a seperate partition).

Once reinstalled decompress that file into the root directory, overwriting the /home folder.

---

### Post by skateoroma on 2008-11-01
OK I misunderstood what you said, but I do have my home folder on a separate partition.

Now I'm totally upset with ubuntu!!!  My system was running smooth for a month until this latest set of updates.  

I did a clean install of 8.10 and it was cool.  Then I took the updates minus all the kernel upgrade stuff, and rebooted.  When I rebooted I got,

Begin: Waiting for root file system.

After waiting for a while, it goes to

(initramfs)

I'm lost man...  If I could recovery without reinstalling that would be the best options.  There is something wrong with the latest set of updates and I wish I could provide more insight to which package is causing the problem.

---

### Post by alexcckll on 2008-11-01
Skateoroma - care ot join a bunch of us over here - [http://ubuntuforums.org/showthread.php?t=948584&page=16](http://ubuntuforums.org/showthread.php?t=948584&page=16) ?

we've got a large thread where a few of us are going to try to get the developers to own this and get a permanent fix in.  You're not the only one who's suffered this.

---

