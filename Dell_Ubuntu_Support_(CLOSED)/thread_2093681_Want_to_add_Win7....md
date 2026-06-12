---
title: "Want to add Win7..."
date: 2012-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lloydvh on 2012-12-11
Hi!
 
I will be receiveing my new Vostro 2520 with ubuntu later today. I am a noob when it comes to Linux, but am a fairly seasoned IT guy otherwise.
 
I would love to add a Dual Boot with Win7, and I have done a lot of Googling. Most of what I have found shows how to add ubuntu to a Win7 machine - not how to add Win7 to a ubuntu machine!
 
And what I did find apparently wont work for the newer versions of ubuntu!
 
Ack!
 
Could someone please point me in the right direction to get this done right the first time???
 
Thanks

---

### Post by mikewhatever on 2012-12-13
It's probably best to break up what you want to do into smaller problems:

1. Making disk space for Windows.
You'll need to shrink one of the existing partitions, which can be done with Gparted from the Ubuntu Live CD/USB. Shrinking a partition will leave unallocated space, which can be used for installing Windows.

2. Install Windows using the unallocated space.

3. Dealing with bootloaders.
If everything has gone well so far, you'll have Windows installed and bootable, and Ubuntu, somewhere one the hdd, but unbootable. To make both bootable, you can use [EasyBCD]("http://neosmart.net/EasyBCD/"), and add Ubuntu to it, or [reinstall Grub]("https://help.ubuntu.com/community/Boot-Repair") from the Live CD/USB.

---

### Post by Hyvver on 2012-12-19
I want to add another domain name to my account, however i dont seem to be ale to find out how to do this. It keeps asking me to pay for another 3 years hosting. I know im a bit thick but all this is new to me.
Any help on how to do this would be greatly appreciated.

---

