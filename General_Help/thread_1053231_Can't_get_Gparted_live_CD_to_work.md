---
title: "Can't get Gparted live CD to work"
date: 2009-01-28
forum: General Help
---

### Post by gufur on 2009-01-28
I have just installed ubuntu in one partition on my Dell Laptop. i have Windows on the other. The ubuntu was from the beginning just a test to see how it worked. To my surprice I got very fond of it and it feels far better and structured then Windows. 
With this feeling I want to increase the ubuntu partition on the expense of Windows. I succeeded to decrease windows with the built in GParted partition manager. Next step is to increase ubuntu partition. I cant do that from ubuntu so I found out that Gparted is possible to boot directly from a CD. I tryed a lot of ways and read a lot on ubuntu forums but did not succeed. Finally I found another way to do it via the Smart Boot Manager/MemDisk. see [http://ubuntuforums.org/showthread.php?t=374555](http://ubuntuforums.org/showthread.php?t=374555). 
To my surprice I got it working and the CD started booting but then something happened. After lot of executed tasks the booting stopped with the following error printout
I got the following 
  PCI interrupt .....text...-->GSI 10 ....some more text...IRO 10
  Sonic Silicone Backplane found on dev 00.002.0010
  cv2.0
  invalid MAC adressfound in EEPROM
  ssb ...text....aborting
  probe ssb.. failed with error -22
  
  after that ubunto seems to do something repetedly after 61 s but nothing happens

How do I get solve that problem

Gunnar

---

### Post by jimv on 2009-02-04
If you have the CD that you installed Ubuntu from, and it's the LiveCD (or Desktop version) you can just boot up from that CD and do your partitioning.  The partition editor is in System > Administration > Partition Editor.

---

### Post by RedSingularity on 2009-02-04
Yeah thats what i did, Live CD.  That works perfectly.

---

