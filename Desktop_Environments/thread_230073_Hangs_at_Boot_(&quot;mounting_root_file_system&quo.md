---
title: "Hangs at Boot (&quot;mounting root file system&quot;)"
date: 2006-08-05
forum: Desktop Environments
---

### Post by blacktorch on 2006-08-05
When Ubuntu boots it fails to get past "mounting root file system". How to fix this?

---

### Post by Anduu on 2006-08-05
How long do you wait?

It may be doing a disk check whick can take some time...

---

### Post by Kodiak3000 on 2006-08-07
I am having the same problem.  I've waited 5 minutes.  Do I need to wait longer?  It never took this long before.  It was working fine until this morning.

---

### Post by MasterZ on 2006-08-07
Hello, 

I have the same problem sometimes, I don't know if it's related to a checkdisk or anything because when it happens, I cannot get out of the ubuntu splash screen to see the comman line output... 

Anyway, I've seen that the problem appears often when my external DVD burner is connected (LG usb drive if you want to know...)
I can cut the power and reboot many times (even the Live DVD) and it get stuck at that same point. 
If I cut the power and disconnect the Usb port, it runs fine again. 


MasterZ

---

### Post by Kodiak3000 on 2006-08-07
well that's more than a little odd.

I did find, by the way, that rebooting with the "Quick Boot" option (in BIOS) disabled got me past the hang up.  I did that with the boot CD in place, had to remove that and reboot again (left QB disabled) and it let me in...

---

### Post by MasterZ on 2006-08-07
I just re-tested with my external DVD attached, and I had the problem again. Then unattached it, and it passed through again. 

I'll test changing the quick boot option ASAP. I think it's enabled here. 

MasterZ

---

### Post by EnderTheThird on 2006-08-07
It sounds like it "loses" the HDD with your root file system on it.  I had a similar problem, where the installer referred to my 2nd SATA HDD as "sdb" (which was correct), but after the installation when GRUB was loaded, it had to be referred to as "sdc" in order to boot.  I had to manually edit the line from GRUB (and later in /boot/grub/menu.lst to make it permanent) so that I could boot my computer.  I had 3 HDDs, and if it was left as "sdb" my computer wouldn't boot.  Maybe you're having the same problem?

---

### Post by MasterZ on 2006-08-20
Hello, 

Long time not posting. 

I tested the quick boot thing without any success. Then I stopped trying for a week or so, but I was so annoyed with that issue (I always forgot to unplug the DVD-writer) that I began searching again. 

I found a solution (for me at last): 

I had to change the following option in my BIOS: 
"BIOS EHCI HAND-OFF" was set to "HiSpeed", I've tuned it down to "FullSpeed". 

The BIOS help message tells me that : 
"This is a workaround for OS without EHCI HAND OFF Support."

I don't really understand the message but OK. I know that EHCI is related to USB 2.0 support (the "HiSpeed" is USB 2.0 speed, "FullSpeed" is slower). 

I did not test the drive speed now in Ubuntu, but I think it is still working at HiSpeed (480Mbps). I don't know how to test that to be sure. 

Anyway, it completely solved the problem, I'm now able to boot ubuntu with the drived plugged-in. (note that before I wasn't even able to boot the live CD from that external drive). 

To give a little more context (I don't know if it helps), my external USB drive seems to be acting like a SCSI device in linux (it's /dev/sr0).


Hope this can help other people too. 


MasterZ.

---

### Post by Anduu on 2006-08-20
Good stuff :)

It's nice to see someone actually update when they find a solution :p

---

### Post by brlock on 2006-08-29
Very good indeed MasterZ. I had the same issue and it was solved thanks to you.

---

