---
title: "GRUB's Gone!"
date: 2006-05-22
forum: Desktop Environments
---

### Post by tomfoolery on 2006-05-22
Hi folks,

This is my first post here, though I've often been directed to threads here when searching for solutions on Google. I have been using Ubuntu 5.10 for about a month now, and look forward to making it my primary PC desktop OS.

I have ran into a slight problem now, and so far haven't managed to find an easy solution... hence this post! Sorry if it's been asked before, but I couldn't find it.

My PC dual-boots Win XP Pro and Ubuntu 5.10, with the latter being installed on a separate partition after XP had been installed. Until now I could chose which OS to start from the GRUB menu on booting, which was perfect. However, I recently booted-up my PC with the Windows XP CD in the drive by mistake, and even though I made no changes to my Windows partition (or so I thought), GRUB didn't appear on reboot. In fact I haven't seen it since...

My PC now boots straight into Windows XP - no questions asked. I assume (hope!) my Linux partition still exists untouched, and if so I'd dearly like to know how I can get GRUB back!

Thanks a lot in advance :)

tF

---

### Post by Fass on 2006-05-22
Boot with your ubuntu CD and at the boot prompt write rescue. Then, when it has finished booting, execute the following command:

```
grub-install /dev/hdX (or sdX)
```
Where hdX or sdX is where your /boot is.

---

### Post by tomfoolery on 2006-05-22
Hi Fass, thanks for the info. Two questions... first I only have an install disc for 5.04 - I upgraded to 5.10 via Synaptic. Should the process you describe still work?

And second, what is hdX/sdX and how do I know which to use? Will anything terrible happen if I get it wrong? I am not usually skittish about ploughing straight in and hoping for the best, but where the consequences could make the whole disk unbootable, I'm a little more apprehensive.

Sorry for the n00b questions! Thanks again...

tF

---

### Post by Irony on 2006-05-22
Boot from the install ubuntu CD (doesn't matter which version)  and at the boot prompt type;

[PHP]rescue[/PHP]

Go to the mount point (where ubuntu is located, say hda3);

[PHP]dev/disc/disc0/part3[/PHP]

At the sh-3.00# prompt type (installing it to MBR);

[PHP]grub-install /dev/hda[/PHP]

After being returned to the prompt, do;

[PHP]#umount /dev/hda3
#reboot[/PHP]

Thus grub is installed to the MBR and grub points to the ubuntu in hda3. hdx is normal ide disks, sdx is raid disks - you've probably got hd disks.

If it doesn't work you can always try again, trying something slightly different, as it only takes a few minutes.

---

### Post by tomfoolery on 2006-05-22
That did the trick!

Thanks very much to you both :grin:

tF

---

