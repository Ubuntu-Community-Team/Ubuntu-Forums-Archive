---
title: "Repairing Windows with Linux questions?"
date: 2009-04-18
forum: General Help
---

### Post by Extremeshannon on 2009-04-18
Hello everyone. I have some problem windows machines that I would like to repair using Ubuntu. After I boot with Ubuntu 8.10 and I am at the desktop I can not access the NTFS drive(s) or eject the CD. This might be by design or something I am missing. Thanks for any help.

Shannon

---

### Post by Monotoko on 2009-04-18
Hiya Shannon, if you are using a LiveCD System, you wont be able to eject the CD, as that is what it runs from, dont eject the CD using a live system otherwise the computer will undoubtedly crash like hell.

Im happy to help you get these machines up and running, but i need to know a little bit more information

What exactly is wrong with the Windows machines, what version of Windows are running, and why wont Ubuntu mount the partition (does it give an error of some kind?)

---

### Post by 123456789123456789123456 on 2009-04-18
I've had a simular problem.  When I was going to transfer files from a windows 98SE drive to transfer everything over to Ubuntu, I noticed that the live cd did not mount the drive correctly, it mounted file system, but the files on the file system were exactly that of the cd live partiton.  I had to use Slax to transfer the files.

have you tried to use the terminal and the mount command to mount sda0,1, which should be the windows ntfs partition.

---

### Post by 3Miro on 2009-04-18
If windows has not been properly shut down (i.e. a crash) the NTFS would be tagged as "locked". The normal (and proper) solution is to boot back in windows and let it shut down properly. If that is not an option (i.e. Windozer crashed completely), you can force the mount from the terminal, but prepare for terminal commands.

Is that the case and do you get an error message?

---

### Post by 3Miro on 2009-04-18
> **123456789123456789123456 said:**
> I've had a simular problem.  When I was going to transfer files from a windows 98SE drive to transfer everything over to Ubuntu, I noticed that the live cd did not mount the drive correctly, it mounted file system, but the files on the file system were exactly that of the cd live partiton.  I had to use Slax to transfer the files.

have you tried to use the terminal and the mount command to mount sda0,1, which should be the windows ntfs partition.

Windows 98 is working with FAT32 and I have noticed that a lot of people have trouble with FAT32 under Ubuntu. It is a standard that should no longer be used by anyone (security reasons).

So I suspect the problems here are different.

---

### Post by Monotoko on 2009-04-18
123456789123456789123456, just because sda0,1 is your Windows partition doesnt mean it is everyone elses, for example it may be on a second hard-drive on the fourth partition, it would therefore be sda1,3

---

### Post by Tobine on 2009-04-18
Maybe this is what you need

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

I've used this to fix a windows machine before

---

### Post by Extremeshannon on 2009-04-18
Thanks everyone for helping. I work in a windows environment and have various problems with windows Some times it is just a corrupt file that needs to be replaced or something to that affect and won't boot properly. I have been using Ubuntu on my personal computers and thought the live CD would a great tool to but into a good known operating system and poke around in windows file system, registry etc.. I have Windows PE disks I use but want to use linux. Maybe I need to make another bootable Linux Disk or something to that affect. Any guidiance would be great. The Laptop I am using as a test is a knon good Windows XP machine that has been shutdown properly.
Thanks
Shannon

---

### Post by Monotoko on 2009-04-19
I dont think its possible to access a Windows Registry from inside Ubuntu, but Chapter 7 of: "Knoppix Hacks: 100 Industrial-Strength Tips and Tools" may help you recover Windows.

---

### Post by Extremeshannon on 2009-04-19
Thank you for the advice. I will give that a try.

---

### Post by Monotoko on 2009-04-19
Okay, let me know how it goes and if you need any help :)
Just send me a PM or post here

---

