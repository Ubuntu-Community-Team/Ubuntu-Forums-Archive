---
title: "big screwup- installed fedora in external hdd, screwed up GRUB"
date: 2009-03-11
forum: General Help
---

### Post by twitch2197 on 2009-03-11
i just installed fedora in an external hard drive i have, and it overwrote my ubuntu (internl hd) grub. when i try booting, nothing happens (my guess is it can't read the external one right) but when i unplug the external hard drive i get "hard disk error". from the ubuntu live disk can i restore the grub for my kubuntu from my internal hard drive?

---

### Post by MaxIBoy on 2009-03-11
Easy. Boot off the CD, mount with read/write privileges whatever partition is your root ("/") partition, go to /boot/grub, then fix up your "menu.lst." Don't actually go to /boot/grub from the liveCD, you'll just get a file on the CD itself. But while you're in the liveCD environment, if your main partition gets mounted as, for example, /media/disk, just go to /media/disk/boot/grub/menu.lst. 
There are a lot of guides for editing this file, just Google it. 


Also, you might have to change your BIOS settings if they automatically want you to boot from the external drive.

---

### Post by twitch2197 on 2009-03-11
just checked and the grub wasn't messed up at all, i guess.
and i played around with the bios and still ended up with 'hard disk error' or an everlasting blinking cursor.
what else could it be?

---

### Post by MaxIBoy on 2009-03-11
It could be the MBR.


Actually, that's probably it. Just look in your menu.lst file to see what your boot partition is. You're looking for something like (hd0,2) or similar. In the example, that means hard drive zero, partition two. 

Then, unmount the hard drive, pull up a terminal, and do this:
```
grub
#(a different prompt appears)
root (hdwhatever,whatever) #don't use any spaces!
setup (hdwhatever) #no need to specify which partition, this time.
quit
```
Then restart and it should work.

---

### Post by twitch2197 on 2009-03-11
you're my hero. all fixed :) 
i think what might have happened is when i was installing fedora i checked "boot from: hd0". should i have selected to boot from my external drive or should i just boot from hd0 but fix the mbr and change menu.lst?

---

### Post by MaxIBoy on 2009-03-11
I don't really remember much about the Fedora installer, but run a Google search for "fedora don't install GRUB to MBR" or something like that. Because that was the problem: the installer detected that you were booting from your internal hard drive, and put a new installation of GRUB on the master boot record of that hard drive.


My preference is to open up the computer case and unplug all my internal hard drives before I install an OS to an external drive, but with laptops that's not going to be possible.

---

### Post by sgosnell on 2009-03-11
For a removable drive, you should choose to put the bootloader on the removable drive, not (hd0).  If you put it on hd0, you can't boot unless the removable drive is connected.  After putting it on the removable drive, you need to change your BIOS to have it boot from the removable drive first, and the internal HD next.  That way if the removable drive is missing, it will boot normally from the internal drive.

---

### Post by MaxIBoy on 2009-03-11
> **sgosnell said:**
> For a removable drive, you should choose to put the bootloader on the removable drive, not (hd0).  If you put it on hd0, you can't boot unless the removable drive is connected.  After putting it on the removable drive, you need to change your BIOS to have it boot from the removable drive first, and the internal HD next.  That way if the removable drive is missing, it will boot normally from the internal drive.
Good point, actually!

If the BIOS has your internal hard drive set to the second priority, you should use (hd1) instead of (hd0.)

---

