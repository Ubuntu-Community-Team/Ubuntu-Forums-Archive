---
title: "Vista Drive Gone Following Ubuntu Install"
date: 2009-02-17
forum: General Help
---

### Post by Chris^%$£&quot;! on 2009-02-17
Hello, HELP!

I have recently installed Ubuntu Ultimate 2.0, I thought to a spare partition I had made in Vista.

I have 2 hard drives, C:(80gb with vista ultimate) and D:(500gb, lots of important data and work on it!)

I sharnk the D: drive and made a 50gb partition (E:) for the Ubuntu install, all good, booted from CD installed fine although partitioning was confusing but I was sure I selected the newly made 50gb partition on the 500gb D: drive and installed away.

Love Ubuntu, all great.

Booted back in to vista today to work on my 'work' on my D: drive only to find I have no D: drive any more in Vista arrrggg, there is 5 years worth of artwork and all manner of important data there I need to recover. HELP! HELP! HELP!

I hav done a bit of tweaking in Ubuntu including installing ATI drivers and setting up all the lovely eye candy, want to keep Ubuntu as dual boot, but have no clue how to get access to my D: drive again.

This is very very important I get the drive back the way it was as my job could depend on this, I don't mind removing Ubuntu and re-installing after, but does anybody here know how to get my drive back.

---

### Post by kanikilu on 2009-02-17
Can you copy and paste the output of the following command:

```
sudo fdisk -l
```

Just go to Applications > Accessories > Terminal and run that command (note that's a lower case "L" not the number one). It will ask for your password. Just highlight the output and right-click and choose "copy" (or press CTRL+SHIFT+C) and then paste it in a reply here.

---

### Post by Chris^%$£&quot;! on 2009-02-17
Hello, thanks for responding, I cant paste that here because i am on the forum here on a borrowed pc from work, its my home pc thats messed up, dont know how to paste from Ubuntu, very green sorry, have a memory stick, the command gave an output that i dont understand, cant see any of my old windows files very worried now.

---

### Post by cd-r80 on 2009-02-17
sudo apt-get install gparted. Human friendly app. to see your partition if it is there.

---

### Post by jespdj on 2009-02-17
> **Chris^%$£"! said:**
> Booted back in to vista today to work on my 'work' on my D: drive only to find I have no D: drive any more in Vista arrrggg, there is 5 years worth of artwork and all manner of important data there I need to recover. HELP! HELP! HELP!

...

This is very very important I get the drive back the way it was as my job could depend on this, I don't mind removing Ubuntu and re-installing after, but does anybody here know how to get my drive back.
If this data is so important to you, then how is it possible that you do not have a backup of it? Harddisks and other hardware don't last forever, you know. You MUST make backups of important data.

---

### Post by Chris^%$£&quot;! on 2009-02-17
ill type in what i see on screen

Disk /dev/sda: 81.9GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f3f3f3f

Device Boot Start End Blocks Id System
/dev/sda1 * 1 9965 80040960 7 HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 1605 * 512 = 8225280 bytes
Disk identifier: 0xc2d4c2d4

Device Boot start End Blocks Id System
/dev/sdb1 1 54427 437184000 82 Linux swap / Solaris
/dev/sdb2 54428 60801 51199155 5 Extended
/dev/sdb5 54428 60801 51199123+ 83 Linux

Not exactly as on screen with the columns, but mean anything to you, thank you.

---

### Post by Chris^%$£&quot;! on 2009-02-17
I stupidly dont have backup of data, havn't run into a situation where you don't get warned about data destruction before you press the 'go' button before, that coupled with my lack of experience in Linux is my failing I would have to admit.

---

### Post by kanikilu on 2009-02-17
> **Chris^%$£"! said:**
> Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 1605 * 512 = 8225280 bytes
Disk identifier: 0xc2d4c2d4

Device Boot start End Blocks Id System
/dev/sdb1 1 54427 437184000 82 Linux swap / Solaris
/dev/sdb2 54428 60801 51199155 5 Extended
/dev/sdb5 54428 60801 51199123+ 83 Linux

Someone else correct me if I'm wrong, but it would appear that the entire 500GB drive has been reformatted. Also, I've done more than a few Ubuntu installs, and I don't believe there is a way to use an entire hard disk that doesn't warn you that you are using *the entire hard disk*.

You can do a search of these forums for **testdisk** to try to recover that data, but I've never used it, so can't really help with that.

It's been said before - I've tried to drive it into my family's heads for years - but, if there is data you cannot live without, running without a backup is suicide. Even 1 backup is not good enough, you need multiple backups in different physical locations (or at least in a fire-resistant safe).

Sorry, I don't mean to preach, but it just sucks when people lose important data or irreplaceable memories (e.g. pictures) because they can't be bothered to back up :cry:

---

### Post by kanikilu on 2009-02-17
> **kanikilu said:**
> Someone else correct me if I'm wrong, but it would appear that the entire 500GB drive has been reformatted.

Wait, nevermind, I think I read that wrong. That looks like the 50GB partition you mentioned. I'm not really sure where the rest of the 500GB drive is, but maybe it wasn't formatted afterall? I would have expected it to show up as /dev/sdb6 or something... ?

I'm not sure about Vista, but in XP (and I think it's similar) I would go to Start > right-click My Computer > Manage > Disk Management to see if there are partitions/drives that it can see but just don't have a drive letter assigned.

If you do manage to find your data, run, don't walk, to your nearest computer store and get an external hard drive to make a backup!

---

### Post by Chris^%$£&quot;! on 2009-02-17
Hello, and thanks for the responses, have found some old backups from XP. so only a year of so's work gone, going on to the linux machine and going to copy the output properly for some clarity

---

### Post by Chris^%$£&quot;! on 2009-02-17
Here is the output from the command:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3f3f3f3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9965    80040960    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2d4c2d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       54427   437184000   82  Linux swap / Solaris
/dev/sdb2           54428       60801    51199155    5  Extended
/dev/sdb5           54428       60801    51199123+  83  Linux

I have used partitions in windows when installing etc, but its Linux seems so alien to me at the moment, steep learning curve, getting the ATI drivers to work took me all day. Still I am determined to bin Microsoft all together and press on with Linux, despite data loss if there is any.  Data loss is a fact of life with windows LOL

---

### Post by Chris^%$£&quot;! on 2009-02-17
Hello again, with regard to seeing the drive in Vista Disk Management, YES, the drives are there showing the partitions, but as you said, no drive letter assigned?

---

### Post by kanikilu on 2009-02-17
It's been a while since I've been in there...can you post a screenshot? Or can someone with more recent Windows experience help out?

---

### Post by Chris^%$£&quot;! on 2009-02-17
I did find the partition manager very confusing to use, especially not being familiar with Linux file structures and hovered on options for ages before pressing the button, and was sure I had picked the 50gb partition, I also checked in Vista that the partition was ok before re-booting and installing. Just can't understand where I went wrong.

---

### Post by Chris^%$£&quot;! on 2009-02-17
Ok, I'll go back to vista get a screen grab and post it on here, not sure how but ill have a go brb

---

### Post by kanikilu on 2009-02-17
When you have the screen up, just press your Print Screen (PrtScn) key on your keyboard and then go into Paint or another graphics program and paste it (CTRL+V). Then just save it as a jpg or bmp or whatever and use the Manage Attachments button under Additional Options to attach it to your post. Do a "new reply", if you do a quick reply, you won't see this option...

---

### Post by Chris^%$£&quot;! on 2009-02-17
Hope this works.

---

### Post by kanikilu on 2009-02-17
I don't see anything. Did you attach it?

---

### Post by meganox on 2009-02-17
It looks like you have formatted the 50GB partition as you wanted, but you have let the installer format the rest of the 500GB as swap space. Oops.

On the up side, you have learned the first and most important lesson in Linux - slow down, back up, and ask questions *before* you do anything that could destroy data!

---

### Post by Chris^%$£&quot;! on 2009-02-17
Hi, Thanks for that, that was really clever of me.   Guess the screenshots academic now, many thanks to all for the attention. all the best

---

### Post by kanikilu on 2009-02-17
> **meganox said:**
> It looks like you have formatted the 50GB partition as you wanted, but you have let the installer format the rest of the 500GB as swap space. Oops.
That's what I thought I was reading in the fdisk output, but wasn't sure...I've never seen a swap partition use that much disk space :shock:

If that's the case, and if you don't want to purse data recovery, I would recommend booting back up with the Live CD and non-destructively resize your linux and swap partitions. Go to System > Administration > Partition Editor, then in the drop down at the top, select your 500GB drive (/dev/sdb) and you should be able to shrink your swap space and expand the linux partition. You could alternatively setup a "shared" NTFS partition in the free space created by shrinking the swap partition.

There are many opinions on what the size of the swap should be, but a general rule-of-thumb is 1-1.5 times the amount of RAM you have. So if you have 2GB of RAM, 2-3GB of swap space should be fine. What you do with the free space after shrinking it is up to you...

---

### Post by Chris^%$£&quot;! on 2009-02-17
Hello and thanks all for all the input and help, feel like a complete idiot now.

kanikilu, you mentioned "purse data recovery", does this mean that I can attempt a data recovery operation for my files?

Any pointers to instructions for a complete novice would be much appreciated.

I could go through installing Ubuntu again if necessary.

I also wanted to ask what to do with the drive afterwards, if I attempt a recovery or not, should I just go back and re-partition the drive using a dos partition manager if I want to use some of the drive for windows and start from scartch again, thanks?

---

### Post by sigurnjak on 2009-02-17
Just in case it is still not to late . There is a software called Acronis that i have used to recover lost partition and was very successful ..
[http://www.acronis.com/](http://www.acronis.com/)
I have used it to make recovery disk with easy gui that is a nice live cd and very easy to use . Hope it is not too late .

---

### Post by Chris^%$£&quot;! on 2009-02-18
Thank you very much I will give it a go.

---

