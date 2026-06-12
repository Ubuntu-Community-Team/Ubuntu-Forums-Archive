---
title: "Your disk drives are being checked for erros. this may take some time"
date: 2011-04-16
forum: Desktop Environments
---

### Post by nshiell on 2011-04-16
...you aint kidding

---

### Post by promet on 2011-04-16
Do you have some gi-normous 1TB drive(s)? LOL, I know, it can be a frustrating wait, can't it?

---

### Post by rudihawk on 2011-04-16
Haha, thank goodness most of my drives are quite small :D

---

### Post by I-love-maverick on 2011-12-18
I've 1TB HD and it's frustrating. Why does it take sooooooooooo looooooong?

---

### Post by lsemmens on 2011-12-18
I'm not looking forward to that on my system, or some of the newer 3Tb drives on the market! It's a pity that it does not happen in the background.

---

### Post by nshiell on 2012-01-26
One thing that fascinates me is that MacOS doesn't perform any drive checks and I have not heard any horror stories of broken files etc.

Yet on Linux we need drive checking? This is not sensible to force end users to wait 20mins for a computer to boot.

---

### Post by Frogs Hair on 2012-01-26
The check runs every 30 boots and there may be a way to change that if one knew where . I am not opposed to disk checks but If I were booting up a laptop or netbook in a class or work situation and had to wait 20 minutes that could be a problem .

---

### Post by CharlesA on 2012-01-26
> **nshiell said:**
> One thing that fascinates me is that MacOS doesn't perform any drive checks and I have not heard any horror stories of broken files etc.

Yet on Linux we need drive checking? This is not sensible to force end users to wait 20mins for a computer to boot.

I have never had a disk check take 20 minutes, even on a 4TB RAID array.

It checks the drive after 30 mounts by default but that can be changed with tune2fs.

---

### Post by lisati on 2012-01-26
On my machines, the time for the checks seems to have become shorter with newer releases. The only time I've had disk activity take longer than a few minutes has been when I've resized a partition with several gigabytes of data or I've been copying a lot of files.

---

### Post by btindie on 2012-01-26
Partitions are automatically checked for consistency around every 30 mounts or every 6 months, what ever comes first.

You can see what yours is set to with:
 mount | grep 'on / ' | cut -f1 -d' ' | xargs sudo tune2fs -l

It does normally give you the option to skip the disk check should you need to. Also by using tune2fs you can increase the number of mounts or set it to 0 to not check at all, though this isn't recommended. The same applies to the check interval.

---

### Post by mcduck on 2012-01-26
> **nshiell said:**
> One thing that fascinates me is that MacOS doesn't perform any drive checks and I have not heard any horror stories of broken files etc.

Yet on Linux we need drive checking? This is not sensible to force end users to wait 20mins for a computer to boot.

Actually OSX can break files (as can any modern operating system/filesystem), and in that situation fixing things can get really frustrating. That's why the disk management tools in OS X have options for checking file integrity and permissions...

(the last time that happened to me was because of a power outage during updates, and repairing the filesystem required booting with the install disc and running file system checks and repairs multiple times, each time fixing a bit more of the errors. Took me hours to get the machine back to a state where all the programs worked again)

Anyway, if fsck is taking that long for you there sure must be something wrong. My 1TB drive completes the check in less than 30 seconds. What filesystem are you using? If it's Ext3 or older, you might really want to upgrade to Ext4 instead, it reduced the fsck time quite radically...

---

### Post by Johnny3 on 2012-01-26
This 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103960](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103960)
and 8 G of memory will help.

---

### Post by CharlesA on 2012-01-26
> **Johnny3 said:**
> This 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103960](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103960)
and 8 G of memory will help.
You really don't need an 8 core CPU to speed up disk checking...

---

