---
title: "Configuration file /home/username/.kde.....not writable"
date: 2010-12-26
forum: Desktop Environments
---

### Post by wainwrit on 2010-12-26
10.04LTS, Gnome and KDE
Help please - I get 'Configuration file /home/username/.kde.....not writable' message or variant of it. It doesn't happen everytime i log on but when it does I can not open or run certain programs (e.g evolution, dolphin), anything that needs to write to (I think) \.kde.

Also, problem takes several minutes to manifest itself after logon, so can open and use Dolphin (for example) but later on problem may or may not occur. Problem is active now and tried runnjing dolphin get this error....
p, li { white-space: pre-wrap; } 
p, li { white-space: pre-wrap; }Configuration file "/home/timwainwright/.kde/share/config/dolphinrc" not writable. Please contact your system administrator.


THis issue has also corrupted my package index and so tried to run dpkg and got:
do dpkg --configure -a
dpkg: unable to access dpkg status area: Read-only file system

At boot 10.04 sometimes reports problem with filesystem but can fix (F) and boots ok.

Really need some help here please!!!

---

### Post by lvm on 2010-12-26
> **wainwrit said:**
> 
I get 'Configuration file /home/username/.kde.....not writable' message or variant of it. 


It may be caused by running a process as other user - su/sudo. Is the file writable? What permissions does it have? Who is the owner of the offending process?

> **wainwrit said:**
> 
At boot 10.04 sometimes reports problem with filesystem but can fix (F) and boots ok.


ext4 I presume?

---

### Post by wainwrit on 2010-12-26
Thanks lvm

I' a complete Linux newbie so Ihink it's ext3, as f file permissions etc how would I find out?

---

### Post by lvm on 2010-12-26
As for file permissions, even dolphin can show them in detailed view (configuration may have to be tweaked - something like view modes-detailed-columns - sorry, I haven't got KDE 4.5 handy at the moment), process owner can be viewed by running ps/grep in a terminal window, to count your dolphins - 

ps -fe|fgrep dolphin|fgrep -v fgrep

---

