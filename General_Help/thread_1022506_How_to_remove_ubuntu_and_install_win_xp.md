---
title: "How to remove ubuntu and install win xp"
date: 2008-12-26
forum: General Help
---

### Post by utnubuzz on 2008-12-26
First of all my english is not so good and im sorry if this thread doesn't belong here but i am desperate with this problem.

So.. I have tried to install Windows XP Normally from it's CD but it always comes up with a bluescreen and the blue screen says something about it have noticed a problem "IRQL_NOT_LESS_OR_EQUAL"

This have never happened earlier and I have done some google and im pretty sure that it has something to do with the hardrive partitions.. I have Formatted all partitions to ntfs and I have also deleted all partitions so that Win XP could do new ones but it always gives this error screen.

My friend managed to install Xp normally from Xp CD sameway that I tried but it just wont work with my computer. I have also tried the FIXMBR command on windows recovery but it didn't work either.

This might be pretty inarticulate text but hope you'll understand it. And please don't ask why I want to remove ubuntu, simply im just too noob.

PS: i can't even use these forums properly..

---

### Post by oilchangeguy on 2008-12-26
enter the bios, and locate the option to use the default settings. irq is interrupt request. think of it as hardware asking the cpu permission to do something. if two pieces of hardware have the same irq number this can sometimes cause problems.
after you set the default settings reboot, and enter the bios again, and set the cd drive as the first boot item. do not make any other changes, and exit.

---

### Post by 2hot6ft2 on 2008-12-26
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
TestDisk is a powerful free data recovery software! It was primarily designed to help recover lost partitions and/or make non-booting disks bootable again when these symptoms are caused by faulty software, certain types of viruses or human error (such as accidentally deleting a Partition Table). Partition table recovery using TestDisk is really easy.

Instructions are on their site.

Using the livecd in a terminal
Applications>Accessories>Terminal
you should be able to use this
```
sudo apt-get install testdisk
```

Or download and burn a livdcd that already has it from here.
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

---

### Post by rbmorse on 2008-12-26
Also, in your BIOS setup, verify that on the chipset settings page that the SATA disk controller is set to SATA as IDE mode. 

Windows does not understand AHCI or RAID modes without help.

---

### Post by utnubuzz on 2008-12-27
Well I first i tried that TestDisk.
I typed in to the terminal

"sudo apt-get install testdisk"

but it gives 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

I typed "dpkg --configure -a" also in to the terminal but it claims that asked command needs roots rights.

Well I'll try those BIOS things later also and tell if it helped.
Thanks!

---

### Post by oilchangeguy on 2008-12-27
> **utnubuzz said:**
> Well I first i tried that TestDisk.
I typed in to the terminal

"sudo apt-get install testdisk"

but it gives 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

I typed "dpkg --configure -a" also in to the terminal but it claims that asked command needs roots rights.

Well I'll try those BIOS things later also and tell if it helped.
Thanks!

type sudo dpkg --configure -a then press enter.

---

### Post by utnubuzz on 2008-12-27
I set the default settings in BIOS but it didn't help. And I didn't even found that verify chipset thing?

And that testdisk I cant install because i messed up a Sun Java install and now it tries to install it even when I'm trying to install something else.. Its hard to explain..

But any other advice how to get windows back and remove ubuntu completely. Sorry im a rookie with computers :/

---

