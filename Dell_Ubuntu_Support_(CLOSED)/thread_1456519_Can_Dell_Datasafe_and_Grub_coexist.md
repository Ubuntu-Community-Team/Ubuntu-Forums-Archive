---
title: "Can Dell Datasafe and Grub coexist?"
date: 2010-04-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Amurko on 2010-04-17
Is it possible to fix grub and/or Dell Datasafe backup in any way so that they don't interfere with each other and occasionally cause your computer not to boot normally?  It seems every solution out there involves uninstalling Dell Datasafe backup or something..

---

### Post by geekwanabe on 2010-04-20
I don't know.  It ate my Grub and wiped Karmic.  I finally just wiped Windows entirely and now run Lucid.  Problem solved!

---

### Post by reiki on 2010-04-21
Wiping windows completely is not always the best available option. It depends on the needs of the individual. I'm using a computer now that I bought from Dell with 3 years of support. If I completely remove the factory OS, then the first time I have an issue Dell is going to have me restore it to factory condition.

Leaving the factory OS installed also makes some things, such as doing BIOS updates or other firmware updates, easier.  Now this is all from the perspective of someone who has purchased a factory-built machine with something other than Ubuntu as the factory-installed OS.

Back to the question of whether or not Grub2 can coexist with DataSafe? I don't think so. At least not at this time. I have deleted Dell DataSafe from my machine. My Windows partition is booted about once a month and I really don't use it for anything other than system maintenance.

---

### Post by fahadysf on 2010-04-24
I have a Dell Studio XPS 1645 and have had tons of problems with Dell Datasafe messing with the MBR and making grub unusable. I am going to try to install Grub on the Mint Partition (its practically interchangable with Ubuntu Partition based on the distro you are using) and try the Grub4dos approach. I'll post the results here.

Here is a quote from the Linux Mint forum. 
[http://forums.linuxmint.com/viewtopic.php?f=46&t=41555]("http://forums.linuxmint.com/viewtopic.php?f=46&t=41555")

> 
There is another way which does not require removing DELL datasafe or similar HP programs. Here are the steps:

1. While installing MINT don't install GRUB to MBR rather install in into the partition where MINT is. (use advanced option during install)
2.Copy files from GRUB4DOS to your C:\. Let GRUB4DOS boot GRUB2 menu. Here is the reference for GRUB4DOS [http://diddy.boot-land.net/grub4dos/fil](http://diddy.boot-land.net/grub4dos/fil) ... m#windows3

Yes it's not idle what Linux purist will expect but makes life much simpler.


---

