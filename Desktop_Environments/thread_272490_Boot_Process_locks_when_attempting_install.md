---
title: "Boot Process locks when attempting install"
date: 2006-10-06
forum: Desktop Environments
---

### Post by Billsey on 2006-10-06
I was recently given a Dell Pentium 3 system (533MHz) with 256 MB RAM. I installed the hard drives without a readable OS (they used to be in my Mac). I find that when I try to boot from the **pressed** live CD, I get a little video garbage with the dialog that says it's loading the Linux Kernal, then it goes to the text screen, saying essentially the same thing, then comes the splash screen where the boot progress is shown. It gets to the second line of that and freezes there. I have not had the opportunity to try other bootable CDs as I do not have Windows and have no wish to have Windows.

What kinds of things should I look for to try to solve this?

---

### Post by Ciego on 2006-10-06
It sounds like the boot is stalling on the line that says "mounting file system".  If this is true, I would check out the hard drive. Make sure that the connectors are plugged in tightly and the jumpers are in the correct position.  Similarly, you should check any other drives that are in your system (optical, other hdds, etc).  I know this sounds like some useless advice, but the only reason I am writing it is because I had the same problem last night and I ended up having a CDROM jumper in the wrong position and it caused the boot to stall in the exact same place (from what it sounds like).  Anyway, it's worth a try if you are stuck.  I hope this helps.

---

### Post by Billsey on 2006-10-07
That was exactly it…kind of. :-)

I had to replace the CD-ROM drive.

Now I have Ubuntu installed. I am using two hard drives in the system. The larger one has two partitions, but I'm not comfortable with the mount point options I was given during the formatting process. What is the prefered place for mounting points and how do I get the partitions to mount where I want them to and with the names I want them to have? In the drive manager when I bring up the partition information, the only options I am given for mount points are pre-existing directories in the root directory of the filesystem, and I am not at all comfortable with those options. What is the safe/prefered place to mount them to and how do I get that done?

I would also like to know how I go about installing additional fonts to my new Ubuntu System. ;)

---

### Post by Ciego on 2006-10-07
I am not sure if I can help you much with the mounting issues. (I am still failry new myself.)  I did see a good guide in the HowTo section here though.  I will try to find it and put a link up here.  From what I do understand, I think you can mount a drive anywhere .... you just have to make the directory first.  You may also have to edit the fstab file.

I better just find a link .... I do not really understand this topic enough to be telling you how it works.

Edit:
I found a good tutorial here
[http://www.ubuntuforums.org/showthread.php?t=137740&highlight=mount](http://www.ubuntuforums.org/showthread.php?t=137740&highlight=mount)

That should give you a better idea of what you are working with.

---

### Post by Billsey on 2006-10-07
I ***MIGHT*** have found a workaround.

My actions attempting to gain access to that second hard drive resulted in me having to reinstall. During that process I discovered something that I had missed the first time around: Manually editing the Partition Table during the install process. That allowed me to work on the configuration of both hard drives. The process is still on going, so I don't yet know the result, but it should be possible to initially install with multiple hard drives. That does not, however, address the person who is actually adding a hard drive after having already installed.

---

