---
title: "CD burning from image repeatedly failing"
date: 2005-04-03
forum: Desktop Environments
---

### Post by timelord726 on 2005-04-03
Hello all!  I've got a relatively new HP DVD Writer 200j, and all of a sudden the CD's that I am trying to burn from ISO images keep failing, over and over.  First they worked in Nautilus (right click -> Write to Disc...), but then they started showing as "completed" but the final burned image would not work.  Then I moved over to GnomeBaker's "Burn Image" option, which again worked for a while, but now it's stopped working too!  Virtually every image I try to burn ends up failing.  What's going on?  Can someone suggest a solution to this burning madness?   ](*,)

---

### Post by electroglas on 2005-04-03
"Burning madness"


Antibiotics my friend...

---

### Post by jonny on 2005-04-04
I had this problem, too.  Then I discovered that DMA wasn't enabled for my optical drives.  I fixed that, and everything worked fine.

---

### Post by timelord726 on 2005-04-04
Okay, thanks.  Assuming this is a viable solution, how would I go about enabling the DMA on my drive?

---

### Post by 23meg on 2005-04-04
you can do it with the hdparm command. i can't remember the parameters now but type "man hdparm" at the terminal and you'll find the answer.

---

### Post by hda on 2005-04-04
Actually it's:

hdparm -d <device>

also check out the /etc/hdparm.conf file

---

### Post by jonny on 2005-04-04
Sorry to have given such a cryptic reply, timelord726.  Hopefully your DVD recorder is working by now.

For the benefit of anyone else reading this, DMA is used to increase the speed with which data can be transferred to and from disc drives, including CD/DVD readers and burners.  While all modern devices use DMA, some older drives might not support it.  By default, Hoary enables DMA for hard drives, but fails to do so for optical drives.  I believe, but haven't checked, that this is logged as a bug.

To check the situation on your PC, open Applications --> Terminal and enter ```
hdparm /dev/hdc
```(Note that you need to change the letter 'c' to reflect the actual drive letter of your drive.  This is not the same as the Windows drive letter  and you might need to experiment to find yours; c is the most common)

You should see a result like this:```
/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
```The line you're looking for is```
using_dma    =  0 (off)
```In this case, I've got a problem.  DMA is disabled, high speed CD burning will fail, and DVD playback will be jerky.

To remedy the situation, I can type ```
sudo hdparm -d1 /dev/hdc

```to enable dma for the drive, and I get this reassuring message:```
/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

```Unfortunately, you have to repeat this step each time you turn your computer on.  There are ways of permanently fixing dma problems, but they're a little more complex and outside the scope of this mini-tutorial.  Search the forums for details if you want to try.

Good luck!

---

### Post by timelord726 on 2005-04-04
Well, I checked out the instructions given, but my hard drive already had the DMA turned on, and it apparently wasn't an option for the CD-ROM drives.

---

### Post by jonny on 2005-04-05
DMA should be enabled for your CD drive, too.  If you don't have a DMA option for those drives, that could be the cause of your problem.

On many motherboards, its possible to disable DMA in the BIOS.  Do you dual boot the PC with Windows?  If you get the same problem burning CDs with Windows applications, that points to a hardware problem.

Try going into your PCs BIOS settings.  To do that, you need to switch off and press some key while it powers up - check your manual, or experiment with esc, del, F1 and F12.  Work through all the menu options (they're subtly different on almost every PC), to see if any mention DMA.  If so, make sure it's enabled.

---

### Post by timelord726 on 2005-04-05
Well, here's what I get:

```
danny@danny-ubuntu:~$ sudo hdparm -d1 /dev/hda

/dev/hda:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
danny@danny-ubuntu:~$ sudo hdparm -d1 /dev/hdb

/dev/hdb:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
danny@danny-ubuntu:~$ sudo hdparm -d1 /dev/hde

/dev/hde:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
danny@danny-ubuntu:~$ sudo hdparm -d1 /media/cdrom0

/media/cdrom0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
danny@danny-ubuntu:~$ sudo hdparm -d1 /media/cdrom1

/media/cdrom1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

---

### Post by jonny on 2005-04-05
You don't need to set dma for /media/cdrom0 and /media/cdrom1.  It's a little confusing, but your cdrom device is actually in /dev.  /media is only the place where you access the files on the cdrom.

The two are linked together by a process called mounting.  You can mount and unmount devices anywhere in the filesystem, but the system uses a file (/etc/fstab) to tell it how to mount drives when you boot up.  If you're interested, try looking in /etc/fstab; that'll tell you for certain which device is your cdrom.

But the good news is that you've enabled DMA for all your drives.  Has your problem been solved?

---

### Post by timelord726 on 2005-04-05
Thanks for your help, Jonny, but regrettably I'm still suffering the same problem.

---

### Post by disturbed1 on 2005-04-08
You can add a me too to this list. Filing a bug report after this post.

It's the same across 4 systems all on Hoary.
Intel 850, Intel 845, Intel 440bx, and Via KT133 chipsets. Nec 2500a DVD+/-RW, Pioneer A05, Lite On 52x, Toshiba SR 5112. 

Each system fails to burn anything with Nautilus CD/DVD burning. Burning a 600mb ISO, it gets to ~300mb then just says complete, no error message. Gnome Baker (which uses CDRECORD) works just fine in non-root mode. The log(s) states that a min fill rate was 98% and that burnfree was never needed.

Yes, DMA is enabled on all drives, enabled in the BIOS, hdparm.conf was edited correctly, along with the start up script moved from S07 to S41. The quite parameter is commented out, so I can see that DMA is enabled during the boot scripts.

---

