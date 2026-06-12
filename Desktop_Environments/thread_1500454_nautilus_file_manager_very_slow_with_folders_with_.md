---
title: "nautilus file manager very slow with folders with many files"
date: 2010-06-03
forum: Desktop Environments
---

### Post by oebuntuUser on 2010-06-03
Hello all,

With Ubuntu 9.10 and 10.0.4 I have seen that the nautilus filemanager is extremely slow with folders that contains many files or/and folders.

I made sure that "Assistive Technologies" is diable. 
On the filemanager preference I set all preview to "Never", tried all possible views, but the filemanager remains extremely slow. It seems like it becomes even slower when the subfolders in the folder you are viewing new files are being created by for example a program. Possibly nautilus filemanager is updating continuously ?

I use to be using debian etch nautilus file manager. With the same directories, nautilus in debain etch was working much faster. But contrary to the one in Ubuntu 9.10 and 10.0.4 is is far less stable. It seems like the newer version is more stable but however extremely much slower. I was wondering if I am missing something. Or whether this is a bug. If it is a bug, then I am wondering when this is going to be solved in nautlius filemanager.

Thanks

Oebuntu user

---

### Post by lkjoel on 2010-06-28
Try LinuxEssentials in my sig.
Extract it then type in a Terminal(Applications->Accessories->Terminal) window:
```
chmod +x ./FASTGNOME.sh
# Are you using gnome?
# If not, replace FASTGNOME.sh to FASTKDE.sh or FASTXFCE.sh
./FASTGNOME.sh
# or your other environment
```
Check the bugs first though.

---

### Post by afrodeity on 2010-06-28
Try turning off previews in nautilus preferences

There are also a few fixes available like reseting nautilus via gconf

[http://ubuntuforums.org/showthread.php?p=9424292#post9424292](http://ubuntuforums.org/showthread.php?p=9424292#post9424292)

---

### Post by afrodeity on 2010-06-28
> **afrodeity said:**
> Try turning off previews in nautilus preferences

There are also a few fixes available like reseting nautilus via gconf

[http://ubuntuforums.org/showthread.php?p=9424292#post9424292](http://ubuntuforums.org/showthread.php?p=9424292#post9424292)

[http://ubuntuforums.org/showthread.php?t=1503801&page=3](http://ubuntuforums.org/showthread.php?t=1503801&page=3)

---

### Post by oebuntuUser on 2010-07-09
Hi IKJoel,
It may sound a bit stupid, but I don't quite understand when you say "Try LinuxEssentials in my sig." What is LinuxEssentials and what is "sig". Is it something I need to download ? I have tried searching on the net for it, but it was hard for me to find anything. Maybe you give a link to where it is.
Thanks in advance.
oebuntuuser

---

### Post by oebuntuUser on 2010-07-09
Hi, 
I've found it and tried it out. Now I open the folder with many files and I get a message that nautilus can not handle that many files and that some files will not be shown. I am not happy with that. I like to see all my files. Nautilus now shows only about 4000 files. I don't think that that is acceptable for a file browser which is being used as standard gnome file browser. 
oebuntuuser

---

### Post by lkjoel on 2010-07-09
> **oebuntuUser said:**
> Hi IKJoel,
It may sound a bit stupid, but I don't quite understand when you say "Try LinuxEssentials in my sig." What is LinuxEssentials and what is "sig". Is it something I need to download ? I have tried searching on the net for it, but it was hard for me to find anything. Maybe you give a link to where it is.
Thanks in advance.
oebuntuuser
sig=signature
Check below this paragraph for LinuxEssentials, Fix your sound and Terminal Enhancements

---

### Post by DigDesignEng on 2010-08-31
I have two computers with Ubuntu.  One with 10.04 and the other with 9.10.  The computers have about the same processing power.  I have been running Ubuntu 9.10 for several months now and never noticed a problem.  However, in the last week or so, I noticed a VERY large change in the time it takes to view the /usr/bin directory.  For comparison purposes I opened the folder in each computer and did a timing test.  For my 10.04 computer, it took about 4 seconds to load the directory.  However for my 9.10 computer it took about 90 seconds!  Previously, this may have taken about 6 to 10 seconds on this computer. I did have assistive technologies turned on, so I disabled it.  This did not help when I first applied the change so I rebooted the computer.  After reboot, my /usr/bin open time was reduce down to 9 seconds.  Still slow, but compared to 90 seconds...

---

### Post by panticz on 2011-12-28
Try PCMan File Manager instead of Nautilus to open such directrys:
sudo apt-get install -y pcmanfm

---

### Post by coffeecat on 2011-12-28
Old thread. Closed.

---

