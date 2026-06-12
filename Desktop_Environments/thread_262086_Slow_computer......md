---
title: "Slow computer....."
date: 2006-09-21
forum: Desktop Environments
---

### Post by netnut on 2006-09-21
Hi all,

I'm trying to get acquainted with Linux... and this I really liked the Ubuntu distro (after a failed attempt with Edubuntu). But, can anyone please tell me why, and suggest remedies as well, my computer is slow? It takes up too long to boot up, and is sluggish whilst launching application.

While boot up, it is idle a long time on "Preparing restricted drivers". I am a newb to this environment....

My hard drive is formatted into 4 partitions with FAT32, while Ubuntu has a separate partition 3GB including swap of 512MB.

Please help.... 

Netnut.

---

### Post by jd65pl on 2006-09-21
What does you computer have in terms of

a) processing power
b) memory 

Thanks

J

---

### Post by netnut on 2006-09-21
Oh.. how silly of me to have forgotten to give my system specs?!
Well, this is the system that I'm running ubuntu on:

Intel Pentium 4 2.8GHz
512MB RAM
80 GB HDD
Onboard Graphics.

I expect better performance from this system than what it has been doing so far... its, like I said, sluggish. I read somewhere that there is a problem with the ext3 file system and that is what causes the bottleneck... will changing the file system help?

Netnut.

---

### Post by wpshooter on 2006-09-21
With those specs that machine should be pretty darn quick.

I assume that is a SATA drive.

I have one machine with almost exactly the same specs except mine has an add-in ATI video card.

If you system is taking more than 1 to 2 minutes to boot all the way to the desktop, me thinks you have something wrong.

P. S. - Ext3 works fine on my machine, but I only have Ubuntu and nothing else on it.  I have a feeling that your other partitions are the heart of the problem.

---

### Post by netnut on 2006-09-22
Yes.. I also expect a fast PC. I've got WinXP installed as well. I don't think that is a problem though. Another strange thing is that the system is slower than when Ubuntu is run from the LiveCD!

Any workarounds?

netnut.

---

### Post by lagagnon on 2006-09-22
Something is definetely wrong with your Ubuntu system. Check the output of the command line command "top" and see if any process is consuming your CPU. Also, check output of command "free" and "df" and post the results here.

---

### Post by netnut on 2006-09-23
Ok here are the results from varios tests that I was requested to do... I have put all the "output" from various tests in text files with the same name. Hope this helps you out.

Thanks again for helping me out.

Netnut.

---

### Post by netnut on 2006-09-24
Hi all,

I have found the root of the problem it seems - whenever I launch/double click an icon to "launch something for the first time" the processor usage seems to shoot up to 100%. Can anyone tell me why... moreover.. only about 30% of the RAM is used and the swap file usage stays at 0%.

With so much free system resources I expect my PC to be lightning fast, but it isn't its "sluggishly slow"... I'd like to taste some Linux... but this is a big obstacle.... help me please.

Regards,
Netnut.

[edit] 
In fact, my CPU usage shoots up to 100% any time and everytime the hard drive is accessed... what's wrong?
[/edit]

---

### Post by ghanu on 2006-09-26
hi..even i m facin a similar kind of prob only 50% of my RAM  n 2.5% of swap(750mb) is used.with 512MB RAM ,80GB PATA HDD,n 2GHz AMD Athlon this seems too slow.help me.

if this fails/impossible can i format swap partition n merge with the root partitn without losin any data

thanx

---

### Post by rogier.de.groot on 2006-09-26
I think you don't have DMA enabled. Do "sudo hdparm /dev/hda" (or whatever you have instead of hda, don't know SATA) and post the output please.

---

### Post by utab on 2006-09-26
What is that, I am also experincing the same problem.

Regards

> **rogier.de.groot said:**
> I think you don't have DMA enabled. Do "sudo hdparm /dev/hda" (or whatever you have instead of hda, don't know SATA) and post the output please.

---

### Post by rogier.de.groot on 2006-09-26
There are basically two ways of getting data from your IDE controller (HDD, CD/DVD drives) to memory: PIO and DMA. PIO is CPU-intensive since it uses the CPU to do the copying, DMA doesn't. Use "sudo hdparm -d 1 /dev/hda" or similar to enable DMA. It won't stay enabled though. Also nice for harddisks is multi-sector transfers, "sudo hdparm -m 16 /dev/hda", but don't use that on CD/DVD drives.
Try it, see if it makes a difference. If it does enable the "hdparm" boot-up script and edit /etc/hdparm.conf to match your preferences.
Good luck.

---

### Post by netnut on 2006-09-27
> admin@beanstalk:~$ sudo hdparm -m 16 /dev/hda

/dev/hda:
 setting multcount to 16
 multcount    = 16 (on)
admin@beanstalk:~$ sudo hdparm -d 1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)


Ok.. I tried what you suggested. There has been an improvement but only slight... it still isn't at optimum performance. Any more ideas?

Netnut.

---

### Post by rogier.de.groot on 2006-09-27
Hmm... darn, I'm running out of ideas... Try "sudo hdparm /dev/hda" and post the output please, maybe something else is weird. Also, I noticed some messages in dmesg.txt which look like it it's too happy with the FAT drives. Could you try removing / commenting out their entries in /etc/fstab and see if your computer boots faster? You said your drive was SATA? (Last time I tried, this is a while ago mind, Ubuntu didn't even recognize SATA disks)

---

### Post by netnut on 2006-09-29
> /dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 16383/255/63, sectors = 156301488, start = 0


That is the output that I get for "sudo hdparm /dev/hda"... hope this helps.

Netnut.

---

### Post by waltrothfuss on 2006-11-16
I had the same slow-down problem with a laptop running an 80 gb ide drive and on another machine, a dual xeon server running sata drives when I upgraded them ](*,) to 6.10 from 6.06.  I don't know what the reason is or what the cure for it is in 6.10.  I reinstalled 6.06 on both machines and now they run normally again.

Good luck -
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
Walt

---

