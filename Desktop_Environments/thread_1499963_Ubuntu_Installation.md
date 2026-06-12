---
title: "Ubuntu Installation"
date: 2010-06-02
forum: Desktop Environments
---

### Post by hamzah01 on 2010-06-02
Hi guy’s 
  I faced problem when trying to instill Ubuntu. The first time I instilled ubuntu it fails to complete the installation and it show me message that saying “Ubuntu can’t be instilled on this drive and it need cooler environment.” I then tried to instilled 2 more time, but it keep show me the same message. And now my Hard Drive only shows me that I have 40 GB of space even though I have 80 GB of space and when I try to format the HD it would let me because there are three other discs that been reserved for ubuntu  but it would let me format them or delete them. [COLOR=#C00000]So is there a way that I can wipe out the entire HD partitions with Ubuntu CD and instill fresh and only Ubuntu on my HD.  [/COLOR]

---

### Post by ajgreeny on 2010-06-02
From the ubuntu live CD run System-Administration-Gparted and you will be able to delete all the partitions on the disk.  You may need to right click on the swap partition and choose "swapoff" in order to delete that, as the live CD will probably have found that swap and be using it.  It should be possible, however, to just ask ubuntu to install to the whole disk at the partitioning stage of the install, and thus delete all that is on the disk at that point.

However, I am amazed at the error message about a "cooler environment".  That is something I have never seen, or even heard of before.  At which point of the installation do you see it?  Also, why do you think anything will have changed just because you have an empty disk to install to?  I don't see how that will affect the machine's running temperature at all.

I think the reduced disk size that you see is probably because you have already got some partitions on the disk that is being used for the install.  Make the choice of the whole disk as mentioned above and the full size should become available.

---

### Post by sanderd17 on 2010-06-02
So you want to format your HDD and only put ubuntu on it? 
If you reformat your hdd from the live CD, do you get the same error?

If so, could you try physically cleaning your computer? getting all the dust out of it. This way the hdd will be cooler if that's what's meand by the error.

---

### Post by hamzah01 on 2010-06-02
[SIZE="4"]Thanks for help. 

I can't apply the method you told me about because I don't have an OS installed yet. all what I have is Ubuntu CD and WIN XP cd for Boot.
and when I insert the Ubuntu CD on my computer it only show me few choices like 
* Install Ubuntu without any change to your computer
* Install Ubuntu
*Install Ubuntu in text mode
* check CD for defects
*test memory 
*Boot from 1st Hard Disk 
and when I chose Install Ubuntu or Install ubuntu without any change. it start to load and then show me this message.
below is the exact message 
"n.
changing Numbers here: { DRDY ERR}
changing Numbers here: Error {UNC}
"buffer I/O error on device sro, Logical Block. also some numbers here" 

and this message keep contuniue and the numbers mentioned keep changing but the content of the message is same."
[/FONT][/FONT][/SIZE]

---

### Post by 3rdalbum on 2010-06-03
It sounds like your CD or CD-drive might be faulty. Try burning the CD at a lower speed, onto good quality media.

---

