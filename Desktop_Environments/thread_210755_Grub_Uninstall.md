---
title: "Grub Uninstall"
date: 2006-07-07
forum: Desktop Environments
---

### Post by thepocketdrummer on 2006-07-07
I have decided I want to remove linux and just use windows for now. After I uninstalled linux, Grub still started (with an error) and I could not get into ANY OS without reinstalling Ubuntu.

How would I go about removing Ubuntu without having to completely wipe my hard drive?

How do I get Grub off and use another boot loader?

---

### Post by Jagot on 2006-07-07
Boot from your Windows CD and go into recovery mode or whatever it is.  At the prompt type:

```
fixmbr
```

Now it should just boot Windows as normal.

---

### Post by TheMono on 2006-07-07
When you go to install XP it should put its own Bootloader over the top of Grub to the best of my knowledge? Just boot from the XP disc, install, and you should be fine.

EDIT: My mistake, I didn't pick up you were dual booting.

---

### Post by thepocketdrummer on 2006-07-07
Also, if I decide to put linux back on, how to I take part of my windows partition and use it for linux (without ruining the windows partion... I did that last time)?

Lets say I have an 80Gb, 6Gb currently free (which I was using to test linux) but I want to have at least 15gb free. Windows has 68Gb visible in Windows right now, so I'm not sure what I would do.

---

### Post by Jagot on 2006-07-07
Both the graphical installer on the LiveCD and the text based one on the Alternate CD allow you to resize NTFS partitions without destroying data, so you could just shrink your Windows partition a bit more and the data on it will be left intact.

If Ubuntu isn't the distro you want to put back on, other distro's come with capable partitioning software, such as DiskDrake with PCLinuxOS.  You could also use a live cd just for partitioning, such as the GParted LiveCD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by thepocketdrummer on 2006-07-07
If I put linux back on, I'll definitely use Ubuntu.

By the way, when I make space on Windows, am I putting how big I want the windows partition to be or how much space I want from it? I think I put how much I wanted to free up last time and it killed the windows partition.

Can someone walk me through that?

---

### Post by Jagot on 2006-07-07
If you're talking about the installer on the Alternate CD then the size you put in is the size of the Windows partition.  You can see it demonstrated here:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by thepocketdrummer on 2006-07-07
It doesn't work. I tried having linux on it already and doing that, uninstalled linux and did it again, did it with a swap partition, did it with just the windows partition and free space... It just goes back to the partition screen with the size exactly the same.

And the cherry on top... my closet door just broke and fell on top of my $150 case, which in turn broke the case door off and dented the top.

...joy :KS 

(no anger towards anyone in particular... the case just put me in a bad mood)

---

### Post by Jagot on 2006-07-07
Did you make sure you selected 'Finish partitioning and write changes to disk'?

---

### Post by thepocketdrummer on 2006-07-07
Yep, does nothing... just goes back to the partition screen.

---

### Post by thepocketdrummer on 2006-07-07
I  had 73 GB on there,  I tried reducing it to 65, didn't work... went to 60 and I am now at a blue screen with a white command bar I'm assuming...

Is there another way to do this? I've been trying this for 7 hours now...

---

### Post by thepocketdrummer on 2006-07-08
Ok, figured it out.

Windows has to be defragmented. My drive was pretty bad, so it wouldn't work.
Had to remove the password on windows to get fixmbr to work, otherwise it wouldn't take my password for some reason.

---

