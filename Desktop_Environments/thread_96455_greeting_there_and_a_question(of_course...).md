---
title: "greeting there and a question(of course...)"
date: 2005-11-28
forum: Desktop Environments
---

### Post by kostaris on 2005-11-28
Hello there, it is a bit common but have to thank you for sorting out so many problems i've had and keeping open source real, i am using ubuntu 5.10 on my desktop and cannot see any of my  hard drives under the "storage media" tab, i ve seen it reported as a bug and tried-among-other to reconfigure h.a.l. through Kcontrol and didn't worked out, help will be much appreciated

Cheers

---

### Post by aysiu on 2005-11-28
Are they Windows partitions?
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

---

### Post by GoldBuggie on 2005-11-28
Uncomment the last line in /etc/default/hal so that it says DAEMON_OPTS=--retain-privileges. This will give hal root priviliges and you should be able to see your harddrives.

Other solution is to make a link to your harddrive and put the link in a folder that you can access(maybe thrue a button via konq.). But this is just another workaround. The first solution solves the storage media thingy.

---

### Post by Paul Casey on 2005-11-28
guessing you're talking about viewing (storage media tab) from Konqueror.  I'm running Kubuntu 5.10 and from that view only shows Hard Disk (hda#)  the partition that Kubuntu is installed on.  From this computer there is only one disk drive. But on that disk are 3 primary partitions and one swap slice.  Konqueror media tab only shows the one partiion that Kubuntu is installed on.

HOWEVER -  open the K Menu,  System Settings,  System Administration --> Disk & Filesystems:  there you may see more info.

---

### Post by kostaris on 2005-11-28
ok i tried that and nothing happens shoud i restart hal?

---

### Post by kostaris on 2005-11-28
Yes this is what i wanted to say and cannot see any hard drive at all only my cd rom when i insert a disk and my usb

---

### Post by GoldBuggie on 2005-11-28
for the hal you need to reboot.

---

