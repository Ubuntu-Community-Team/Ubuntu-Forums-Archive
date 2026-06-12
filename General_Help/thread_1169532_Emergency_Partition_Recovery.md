---
title: "Emergency: Partition Recovery"
date: 2009-05-25
forum: General Help
---

### Post by chaoszerox on 2009-05-25
Right now I'm in quite a pinch
I am running off of a Ubuntu 8.10 live CD

The problem: I accidently deleted my NTFS partition with Vista's installer partitioner.

Look at these pictures taken from testdisk-6.11.3 and gparted. I used the command "sudo /bin/bash" command (to become the root) before I dragged the "testdisk_static" to run the app in the terminal, and still got the error in the 2nd image

[IMG]http://i239.photobucket.com/albums/ff70/num1narutofan/this.png[/IMG]
[IMG]http://i239.photobucket.com/albums/ff70/num1narutofan/this2.png[/IMG]
[IMG]http://i239.photobucket.com/albums/ff70/num1narutofan/Screenshot.png[/IMG]

"Write isn't available because the partition table type "None" has been selected." see 2nd image

I'm guessing this is why I wasn't able to recover the partition. I did look at the files on the analized partition, and the files are there. I could have just copied the files I needed, but that is over 150 GB of files, and the largest storage device I have is this 250 GB harddrive with the deleted partition, so I have to recover the partition itself, in whole.

If you want to talk to me live on MSN(pidgin): [email]cahoszerox@hotmail.com[/email]

P.S. The 16 GB media on the desktop is my USB flash drive

---

### Post by killabee44 on 2009-05-25
The best option I have found for recovering files off an NTFS partition that has been formated is to use R-studio from a windows machine. Hook up the messed up hard drive up to a windows machine via usb, sata, etc and run R-studio on that windows machine. 

I was able to recover all ntfs files off the hardrive with no problem. Try to see if you can find a hard drive with sufficient space to recover the partition to. Sorry its not exactly the solution you wanted, but I know this one works.

---

### Post by chaoszerox on 2009-05-25
> **killabee44 said:**
> The best option I have found for recovering files off an NTFS partition that has been formated is to use R-studio from a windows machine. Hook up the messed up hard drive up to a windows machine via usb, sata, etc and run R-studio on that windows machine. 

I was able to recover all ntfs files off the hardrive with no problem. Try to see if you can find a hard drive with sufficient space to recover the partition to. Sorry its not exactly the solution you wanted, but I know this one works.
1st of all thanks for you response. =)

I don't have a second machine I can hook it up to though....and I have about 150 GB of stuff I need to recover. The only thing I can store that on is this harddrive, so partition recovery is my only option I think

---

### Post by albinootje on 2009-05-25
> **chaoszerox said:**
>  I don't have a second machine I can hook it up to though....and I have about 150 GB of stuff I need to recover.

I think that the only way to work on this, is to ask a friend or relative with some other machine to work with, or some usb drive with enough diskspace to work with, that you can temporarily use.

I come to this conclusion after looking at your screenshot of gparted, you simply don't seem to have enough free diskspace to restore data on the same disks, without destroying to option to restore your data.

And in the future, do yourself a favor, and buy some usb drive to make regular backups on of your important data, that will pay off in the end.

---

### Post by chaoszerox on 2009-05-25
> **albinootje said:**
> I think that the only way to work on this, is to ask a friend or relative with some other machine to work with, or some usb drive with enough diskspace to work with, that you can temporarily use.

I come to this conclusion after looking at your screenshot of gparted, you simply don't seem to have enough free diskspace to restore data on the same disks, without destroying to option to restore your data.

And in the future, do yourself a favor, and buy some usb drive to make regular backups on of your important data, that will pay off in the end.
Are you saying I can't simply do a partition recovery :cry:

I have 2 friends with PCs, but they are too old, and only have about 30 GB of disk space, which are most likely at least 1/2 full

---

### Post by chaoszerox on 2009-05-25
I think I may have solved the problem, I'll report back soon

---

### Post by chaoszerox on 2009-06-19
It's been a while, sorry I didn't post when I had indefinately solved the problem. I did resolve the issue, but I forgot exactly how I did it now =/

---

