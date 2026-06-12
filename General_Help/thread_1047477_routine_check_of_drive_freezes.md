---
title: "routine check of drive freezes"
date: 2009-01-22
forum: General Help
---

### Post by robbclark1 on 2009-01-22
Dear all,

I realize that this topic comes up frequently as I have already searched and tried a few things.  First, I set my check to every 50 times rather than every 30.  Second, I tried to run fsck but it says "permission denied". I've also tried umount /dev/sda1 and got nothing.  

The % that the check gets to varies.  Sometimes it is 6% and today it got up to 46%. Then it freezes and does nothing.  I've waited for it and it still doesn't move.  I've just skipped it but I realize that it needs to check and fix the drive errors if there are any.

Please realize that I am an absolute noob to ubuntu so if you need more info from me, please tell me how to get it.  

Thank you all
Rob

PS: I'm running Ubuntu 8.10 on a HP Pavilion zx5000.  I am NOT booting windows, just ubuntu.

---

### Post by jerome1232 on 2009-01-22
Do you have a live cd on hand? 
I would boot from it and run fsck on each partition from there.

```
sudo fsck -f /dev/sdxx
```

---

### Post by robbclark1 on 2009-01-22
I don't know what the LiveCD is although I have read about it.  My friend installed ubuntu on this computer since it is just a beater computer.  However, I am enjoying, albeit a little frustrated, at learning about linux.  

So
1) How do I get the LiveCD?
2) How would I boot from it?

Again, I apologize for my noobiness.

---

### Post by jerome1232 on 2009-01-22
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Just download the desktop edition, once the iso is downloaded burn it to cd with brasero (applications-Sound and Video-Brasero Disc Burning, Select burn image to cd.

Once done burning you should be able to just reboot the computer with the cd in the drive and it'll boot from the cd, select try ubuntu without installing and you will get to a live cd enviroment. Just open a terminal and fsck your drives from there.

---

### Post by robbclark1 on 2009-01-22
Aye Aye captain. Thanks.  I will try tomorrow when I have access to a CD.  It won't freeze if I run the file system check during a boot?  And will it fix errors automatically?

---

### Post by jerome1232 on 2009-01-22
> **robbclark1 said:**
> Aye Aye captain. Thanks.  I will try tomorrow when I have access to a CD.  It won't freeze if I run the file system check during a boot?  And will it fix errors automatically?

The live cd won't try to fsck the drives during boot time because it won't try and mount them, the fsck -f should check the drive and if there's problems ask you whether it should attempt to repair them or not.

---

