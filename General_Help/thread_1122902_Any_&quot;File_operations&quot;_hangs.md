---
title: "Any &quot;File operations&quot; hangs"
date: 2009-04-11
forum: General Help
---

### Post by bsmith1051 on 2009-04-11
My wife and I share a machine running Ubuntu 8.10.  In the past 24 hours something has gotten borked on my login.  Now, anything I do with Nautilus will hang.  Even just trying to empty the trash causes the File Operations pop-up to appear, run the hard drive for several seconds, and then hang indefinitely.

Everything works fine under my wife's login so I'm assuming it's something wrong with mine.

How can I troubleshoot this?  My only idea is to start deleting/hiding my "." configuration folders, then re-logging-in.  But I'm hoping there's an error log somewhere that will give me a better idea.  This all started spontaneously today.  The only recent change was the kernel update/reboot a couple days ago.

**UPDATE**
OK, here's a better description of the problem!  I have a digital camcorder that I can plug in directly via USB, and then the recordings are directly accessible through the built-in flash drive.  This has worked fine for about a year, so far.  _Now_ what's happening is that it's causing Nautilus to freeze, but only on my login/profile.  If I mount it from my wife's login then everything works fine.

---

### Post by cubeist on 2009-04-11
System logs are in the system/administration/system log menu.  You might be able to see an error there.  Or, you could go into synaptic and downgrade to the last stable kernel...when grub comes up, select an older kernel.

Or, try re-configuring nautilus in case there is a corrupt file of some sort
```
sudo dpkg-reconfigure nautilus
```

---

### Post by bsmith1051 on 2009-04-12
Thanks for the reply!  So far, all I've done is reboot (a 2nd time) and use my wife's profile to Empty Trash.  Now my profile seems to be working properly again.  So something -- either the reboot or 'her' trash-empty -- seems to have unstuck something.

---

### Post by cubeist on 2009-04-12
probably the reboot, I sometimes forget the simplest solutions...

For your reference, aside from a kernel update, a linux system never actually has to reboot.  If you know which service isn't working (say networking) you can force re-initialize it with the command:
```
sudo /etc/init.d/networking restart
```

cheers

---

### Post by bsmith1051 on 2009-04-13
**UPDATE**
OK, here's a better description of the problem!  I have a digital camcorder that I can plug in directly via USB, and then the recordings are directly accessible through the built-in flash drive.  This has worked fine for about a year, so far.  _Now_ what's happening is that it's causing Nautilus to freeze, but only on my login/profile.  If I mount it from my wife's login then everything works fine.

---

### Post by cubeist on 2009-04-16
> **bsmith1051 said:**
> **UPDATE**
OK, here's a better description of the problem!  I have a digital camcorder that I can plug in directly via USB, and then the recordings are directly accessible through the built-in flash drive.  This has worked fine for about a year, so far.  _Now_ what's happening is that it's causing Nautilus to freeze, but only on my login/profile.  If I mount it from my wife's login then everything works fine.

The simple answer is there is probably a configuration error of some sort, and there are two ways to check for it.

First manually, open a nautilus window and in the view menu check "show hidden files"
Next, requiring some manual work look through the hidden files/folders for anyone that matches the name of your camcorder, if you find something, make a backup of it, then delete it, and hopefully the problem is fixed. (the backup is simply in case something else goes haywire)

The other method is to run dmesg in a terminal.  Run it before you plug the camcorder in, then after, then again after you open nautilus.  Check for errors and warnings and then post them here.  Also, in you system logs, check your XSession errors log, as nautilus messages are often posted there.

---

