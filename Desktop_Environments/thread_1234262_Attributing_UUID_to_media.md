---
title: "Attributing UUID to media"
date: 2009-08-07
forum: Desktop Environments
---

### Post by coredeal on 2009-08-07
Hi everyone,

I am seeking advice as to how to attribute a UUID number to one of my medias. Her's what happens.

After installing Jaunty, all my partitions were recognized. Except one : /dev/sda5. I did some research, learned what UUID means, found how to discover the UUID number for that partition, but now I really do not know how to attribute it so this partition too may be available and can be mounted when needed. I do not want to mess up a good installation, even less playing with partition editing without knowing what I am doing. I count on your guidance and I thank you for your time.

---

### Post by snowpine on 2009-08-07
Hi Coredeal,

The terminal command 'blkid' will tell you the UUID of the partition, and the file responsible for automatically mounting it is /etc/fstab. Here is some reading material to get you started: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by coredeal on 2009-08-07
> **snowpine said:**
> Hi Coredeal,

The terminal command 'blkid' will tell you the UUID of the partition, and the file responsible for automatically mounting it is /etc/fstab. Here is some reading material to get you started: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Thanks a lot, Snowpine. I'll definitely take a look at that.

---

### Post by coredeal on 2009-08-08
> **coredeal said:**
> Thanks a lot, Snowpine. I'll definitely take a look at that.

Hi again Snowpine,

by typing your suggested command blkid in Terminal I found that my partition actually has a UUID number. But for some reason Ubuntu does not mount it. Nor does it show it under "Places", "Computer". All other partitions are there except this one.

I read the document you referred to, but all the technical explanations are a bit too complicated for me, and above all. I am reluctant to type commands I do not fully understand, for fear of messing up the partition table. If the whole problem, then, is just mounting the partition, is there a simple way of doing this ? Thanks again for your time, if you have some to spare !

---

### Post by Teh_Messiah on 2009-08-09
I have a problem too with my grub boot loader.
Info:
I have a file server with an IDE HDD 40gb for OS Xubuntu
I have a PCI sata Raid controller card with 4 samsung 250gb hdds in a mdadm raid-5.
In the past when i had to install the OS i had to disconnect the power from the Sata HDDs so i could successfully install the OS to the IDE HDD otherwise the whole thing just gets confused.
I recently messed up something and had to reinstall the OS and decided to try and do it without disconnecting the power because it is a pain having to 
[LIST=1]
[*]pull the tower out
[*]open it
[*]disconnect the power from the HDDs
[*]re-connect peripherals
[*]install OS
[*]pull the tower out again
[*]open it
[*]re-connect the power to the HDDs
[*]close the tower up
[*]re-connect peripherals
[/LIST]
All just to re-install the OS!
And now I am getting all [these errors]("http://ubuntuforums.org/showthread.php?p=7760547#post7760547") on boot up since i did it without disconnecting the power from the HDDs.

Is it something to with the UUID?
How did you find how to discover the UUID number?
Any suggestions on how to fix it without having to edit the grub boot menu every time i restart my server?

---

### Post by Teh_Messiah on 2009-08-10
All i had to do was edit the /boot/grub/menu.lst file to get it to read from disk (hd0,0) instead of (hd4,0)

---

