---
title: "The Best Way To Install Ubuntu?"
date: 2010-09-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bikekid450 on 2010-09-23
Okay, those of you that have been looking on here these last few days will have noticed I have had loads of problems with Ubuntu, After installing it in around a week ago yesterday it somehow wiped itself off my PC. I said I wasn't going to install it again however I have decided to try one last time because while it was working I did love it!!

So, what is the best way to install it? I have tried all the ways I know...

The first time I booted from the CD and installed it that way, I was very confused with the partitions and the way they're showen but Istalled it onto the one I wanted after a while, it got half way then corrupted some how 3 of my Hard Drives (Apart from my XP one) So I started again with the ones I lost then tried again but using Wubi as some of you on here said it's best, the other 3 times it's had errors while I'm using it I couldn't install anything on it and after about the 3rd time I would turn my pc on and boot in Ubuntu it's say error Low Graphics Mode, With Windows will boot fine though. 

One of you on my other post said Wubi install inside Windows isn't for long use, So please tell me what is the best and how to understand the Partitions in the boot from CD method.

Thanks guys for being to patiant with me :)

---

### Post by perspectoff on 2010-09-23
There are lots and lots and lots of threads about partitioning on Ubuntu forums, on the help wikis, on external guides, and all over the Internet. Hunt around a little bit, first.

The problem usually isn't the partitions, it's the Grub bootloader. Unless it is set up correctly, it will point to a partition that doesn't actually have an OS on it, or has settings that are not correct, and then it appears that things are "corrupt," which ends up usually being a generic error message and doesn't really mean the hard disk is corrupted.

I recommend you start Ubuntu from the Desktop LiveCD, then start GParted and examine your partitions so that you can learn about them. Then read about partitions (even Wikipedia has a lot of good info).

Once you get an idea about partitions (and the partitions on your hard drive), you are ready to try installing Ubuntu again. 

A lot of users like Wubi, and a lot don't (citing lots of hiccoughs with it). Wubi installs Ubuntu within the Windows partition as a gigantic file. Using Wubi you don't presumably need to worry about partitions because it completely resides within the Windows partition.

The problem is, once you try to install Ubuntu without Wubi, your system is now configured to use partitions and the Grub2 bootloader has taken over your system. If it screws up, you have to start over using the same method (hoping Grub2 gets it right the second time). You can't switch gears and go to Wubi if the regular installation screws up. You must do the regular installation over again.

---

### Post by Bikekid450 on 2010-09-23
I have but none say reasons why it's corrupt and have so many errors so I thought I'd post about it and hope someone would help me one to one and maybe tell me what I've done wrong =/

---

### Post by mörgæs on 2010-09-24
Have you tried more than one Ubuntu release? 

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by Bikekid450 on 2010-09-24
Yeh, I think I solved it now! Fingers crossed lol it's lasted a day so far =]

---

