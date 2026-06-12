---
title: "Automounting cdrom and usb disks on minimal ubuntu"
date: 2012-10-17
forum: Desktop Environments
---

### Post by PeterTaps on 2012-10-17
Folks,

I have created a system with Minimal Ubuntu + Openbox. Now, I am trying to understand what I need to do to get DVDs and external USB drives to be automatically mounted.

Searching the net, I came across multiple solutions. 

Option #1:
$ sudo apt-get install udisks ntfs-3g usbmount

Option #2:
$ sudo apt-get install gnome-volume-manager

Option #3:
$ sudo apt-get install dconf-tools

I am confused on what the best solution is. 

Not sure if option #1 takes care of DVDs.
Not sure if option #3 (dconf-editor) even works in openbox environment.

I would appreciate your help in understanding what my best option would be. Any pointers would be appreciated.

Thank you in advance for your help.

Regards,
Peter

---

### Post by Cork87 on 2012-10-17
Try gnome-volume-manager as first option, it has not much dependencies and seems to be created for you needs. 

But to be honest with you, I should try them all to see which one fits your needs the best and to learn what the big difference is between the packages.  

Please let us know which option works best.

---

### Post by PeterTaps on 2012-10-18
It turns out gnome-volume-manager is not even available in standard repository. Therefore, I am not going to use it.

I used usbmount. It works very well for FAT32 disks. However, it does not work with exFAT disks (although fuse-exfat has already been installed).

Another great application I found is a file manager called PCManFM. It is quite good. Plus, it knows how to mount and unmount external disks.

Regards,
Peter

---

