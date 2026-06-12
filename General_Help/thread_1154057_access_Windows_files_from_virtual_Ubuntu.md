---
title: "access Windows files from virtual Ubuntu"
date: 2009-05-09
forum: General Help
---

### Post by ragtimer on 2009-05-09
Is there a way to access Windows files from Ubuntu, when running Ubuntu under VMware as a virtual machine under Windows XP?
There is no /host file system in Ubuntu in a virtual machine, so that method is out.
 
CUrrently I keep a USB stick plugged in, and switch it back and forth between WIndows and Ubuntu, but direct file access would be much quicker.
 
Should I consider networking, via the wireless card in Bridge mode?  It seems to allow both VMware/Ubuntu and WinXP to access the Net simultaneously.
 
Alternately, is there a way for WIndows to access Ubuntu files inside the VMware container?
 
It's really great being able to switch back and forth between the two OSes without rebooting.  Thanks, Mike K.

---

### Post by cariboo on 2009-05-09
You cans set up shared folders if you have the geust addtitions installed.

---

### Post by DeMus on 2009-05-09
> **ragtimer said:**
> Is there a way to access Windows files from Ubuntu, when running Ubuntu under VMware as a virtual machine under Windows XP?
There is no /host file system in Ubuntu in a virtual machine, so that method is out.
 
CUrrently I keep a USB stick plugged in, and switch it back and forth between WIndows and Ubuntu, but direct file access would be much quicker.
 
Should I consider networking, via the wireless card in Bridge mode?  It seems to allow both VMware/Ubuntu and WinXP to access the Net simultaneously.
 
Alternately, is there a way for WIndows to access Ubuntu files inside the VMware container?
 
It's really great being able to switch back and forth between the two OSes without rebooting.  Thanks, Mike K.

You have one pc running both Windows and Ubuntu? You use vmware? Why not simply a dual boot so you don't need Windows to get to Ubuntu. This way Ubuntu can run on full speed without the downside from Windows.
When doing this, it is easy to set up a system with which you can read and write the windows disks from Ubuntu as well.
Just try this:

Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time

```
sudo aptitude update
sudo aptitude install ntfs-config
```

Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you see any Windows disks on your desktop right-click on the icon and choose unmount.
Then run the program from System > Administration > NTFS Congiguration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for **Internal** Drives" and click OK.

Success.

---

### Post by ragtimer on 2009-05-10
> **cariboo907 said:**
> You cans set up shared folders if you have the guest addtitions installed.
Is this related to the Guest acccount under Fast User Switching, or is this something beyond that? How do I install this? By
sudo apt-get install guest
?
Thanks, Mike K.

---

