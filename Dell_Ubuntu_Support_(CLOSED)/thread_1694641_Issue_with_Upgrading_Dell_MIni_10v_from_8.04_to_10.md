---
title: "Issue with Upgrading Dell MIni 10v from 8.04 to 10.10"
date: 2011-02-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by candeos on 2011-02-24
Hello and thanks in advance for the assistance.

I am trying to upgrade my Dell Mini 10V from 8.04 to 10.10

I have read the forums and the FAQ.  One says that you can go from 8.04 to 10.04 by going into software sources and choosing long termupdates. That option doesnt appear for me.

I can do a clean install, but then I read somewhere that there are drivers that Dell puts on that need to be backed up.

I have spent the whole day messing with this and I am ready to just pay someone to do this.

Any help would be greatly appreciated  Thanks!

Dave

---

### Post by mikewhatever on 2011-02-24
Can you post the output of the **uname -m** command from a terminal window.
A clean install should work for you, and whatever drivers missing (probably the wireless), can be found under System->Admin-Hardware Drivers. Test either 10.04 or 10.10 by running from usb, I would expect everything but the wirelees to just work.

---

### Post by candeos on 2011-02-25
Mike

Thanks for your reply!

i686 is the response i get from uname -m

I'm a total noob as far as ubuntu, so I really appreciate the help. 

DO I upgrade from a uSB?  The problem is that usb-creator is not loaded on the computer ( or I cant find it)  When I went to my other windows box, I tried using universal usb installer on another box and the message about overwriting the MBR scared me away....

Dave

---

### Post by mikewhatever on 2011-02-27
> **candeos said:**
> Mike

Thanks for your reply!

i686 is the response i get from uname -m

Hi again, and sorry for the delay, I've been away. i686 means the OS is the regular 32bit which is good, and you should be able to upgrade at least as far as the architecture goes.

> DO I upgrade from a uSB?  The problem is that usb-creator is not loaded on the computer ( or I cant find it)  When I went to my other windows box, I tried using universal usb installer on another box and the message about overwriting the MBR scared me away....

Dave

USBs and CDs are for reinstalling, not upgrading. The latter is usually done from the update manager. Usually, when the new version becomes available, the update manager just offers is as an option. Perhaps Dell's installations have the upgrade option disabled? You can check under System->Administration->Software-Sources.
There is also an option to upgrade from the Alternate image locally (see the link).
[https://help.ubuntu.com/community/LucidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/LucidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)

In case you decide to format the disk and install Lucid, use a usb device. Overwriting the MBRs is kind of standard when installing and operating system, it ensures you can boot afterwards. MBR is just the first sector (512bytes) on disk and doesn't contain any personal data.
Reinstall or upgrade, backup your data before beginning, and if you have further questions, do not hesitate to ask.

---

### Post by new 2 linux on 2011-06-15
im having a similar problem but its for my Dell Inspiron 910 evertyme i try do upgrade thru the network i get network connection problems even though im connected to the net so formatting would be the best solution?

---

### Post by mörgæs on 2011-06-15
Yes, as mentioned in your other thread. 

A fresh install will also give you Grub 2 and (if you want) ext4.

---

### Post by new 2 linux on 2011-06-17
oh okay a fresh install of ubuntu 10.04

---

### Post by w7hd on 2011-06-18
> **new 2 linux said:**
> oh okay a fresh install of ubuntu 10.04

You may experience wireless connection problems after the upgrade.  Anything newer than 9.04 appears to have problems.  I have posted a thread I found on my website that will help.

[http://w7hd.homelinux.net/linux/mini10v_wireless_problems.htm](http://w7hd.homelinux.net/linux/mini10v_wireless_problems.htm)

---

