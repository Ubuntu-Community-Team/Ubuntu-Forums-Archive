---
title: "How to display hard drive partitions as hda1 hda2, etc."
date: 2007-07-27
forum: Desktop Environments
---

### Post by serge on 2007-07-27
Hi to all. This is so basic that I hope you don't blast me for bugging you.
I'm using 7.04, and loving it. The question:  when I click Places -> Computer, I get all of my hard drive partitions displayed, but they are named like "9.3 GB Volume(2)". But I would like them to be named like hda2, for example.  How can I do that?

Best regards,
serge.

---

### Post by miggols99 on 2007-07-27
Try typing in
```
sudo fdisk -l
```
into the terminal.

---

### Post by serge on 2007-07-27
Thanks miggols99: Yes, the command you suggested works, but this was not my problem. As I explained in my post I want to see partitions labeled as hda1, hda2.. using Gnome's Places -> Computer clicks.

---

### Post by zanglang on 2007-07-27
Try changing your /etc/fstab so the mount points are /media/hda1, hda2 and so on?
For example,
> UUID=xxx-xxx /media/hda1 vfat defaults,utf8,rw 0 0

---

### Post by serge on 2007-07-27
Thanks zanglang: Here is the line from the /etc/fstab: 
UUID=72dd9447-3ad5-484b-be48-7a57dffc2251 /media/hda7     ext3    defaults        0       2

But when I click:  Places -> Computer, I see this

9.3 GB Volume (3)

---

### Post by coffeecat on 2007-07-27
For ext3 partitions, simply relabel them using the terminal utility e2label. When you next boot up they will appear with their partition labels in Computer. As an example:

```
sudo e2label /dev/hda2 hda2
```Or, more imaginatively:

```
sudo e2label /dev/hda2 Bananas
```and your hda2 partition will appear as 'Bananas' in Computer after you reboot or remount. :wink:

By the way, with the relatively new libata drivers in Feisty most (but not all) pata drives are now appearing as sdx, rather than hdx. You might want to check this.

**Edit:** If you want to label filesystems other than ext2/3, have a look at [this link](http://doc.gwos.org/index.php/Understanding_fstab). Scroll down past the fstab stuff until you get to the 'How to Label' bit.

---

### Post by serge on 2007-07-27
coffeecat: YES, it worked. Thanks a million!!! Just a totally stupid question: Wouldn't it be better if  Ubuntu labeled hard drive partitions with names as they are really called (like hda1 or sda1 etc.)?

Thanks again to all who helped. I'm totally impressed with the speed, politeness and competency of your help.

serge.

---

### Post by coffeecat on 2007-07-27
> **serge said:**
> Just a totally stupid question: Wouldn't it be better if  Ubuntu labeled hard drive partitions with names as they are really called (like hda1 or sda1 etc.)?

It's not a stupid question at all - quite a good one. Trouble is, I think you'll find the devs would never get agreement on what labels to use. I've set my systems up as multi-boots, so my partitions are labelled Feisty, Gentoo, PCLinuxOS, Shared_Data and so on. Other people would probably want something different.

One distro - I can't remember which - came up with disk-0, disk-1, disk-2 and so on for a dozen or so unlabelled partitions which I found just as unhelpful as '10GB volume'.

Difficult one, isn't it? :)

**Edit:** Actually, thinking about it, your idea of hda1, hda2, etc or sda1 etc is good. Much more informative than disk-0, disk-1 which didn't seem to bear any relationship to anything I could discern. Why not make a suggestion in the Gutsy Gibbon subforum?

---

### Post by serge on 2007-07-27
coffeecat:

> Difficult one, isn't it?

For sure!

And one more (stupid) question: If someone wanted to change the partition names, it would be nice if this could be done using some sort of GUI (Gnome) process, instead of the command line way, which you just showed me how to. 

serge.

---

### Post by coffeecat on 2007-07-27
Suggest that in the Gutsy Gibbon subforum? :lol:

I'm not a programmer but I should imagine it would be trivially easy to write a GUI app to do this. Thing is, you have to be able to convince the devs that it's worth doing. As a newcomer to Linux you have a fresh way of looking at Linux and it seems to me that's a good idea.

---

