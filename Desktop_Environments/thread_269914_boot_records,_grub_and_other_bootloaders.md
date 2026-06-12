---
title: "boot records, grub and other bootloaders"
date: 2006-10-02
forum: Desktop Environments
---

### Post by rossmiester on 2006-10-02
Here is the situation:

I have windows XP, and ubuntu installed on my laptop.  I also had a bunch of free space (Since I keep my partitions set at 60gb, 20gb, 27gb, and 5gb - fat32).  XP was on 60, and ubuntu was on the 20.  I then installed windows vista on the 27gb space.  Up till now I had been using grub and chainloaded xp.  I knew that vista would want to rewrite my MBR, and knew it would let me boot XP, but I knew it wouldn't see the ubuntu partition.  So, I copied the grub bootsector to linux.bin and emailed it to myself, and put a copy on the fat32 partition.  Then, installed vista.  I hadn't realized that it would mess me up this bad.  It uses a new system as a bootloader, and I haven't the time to see how to set this up.  At the moment, I wiped vista, but the bootloader is still on the MBR, and only boots windows XP, while I still have Ubuntu, but can't get to it.  

How would I go about fixing this? I have the ubuntu live cd.

---

### Post by Scheater5 on 2006-10-02
Sounds to me like the easiest solution would be to make grub the bootloader again, in a fashion similar to those who install XP after Ubuntu - I've done this myself.  

quoted from help.ubuntu.com
> 1. Pop in the Live CD, boot from it until you reach the desktop.

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).

3. Type "sudo grub"

4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

5. Type "setup (hd0)", ot whatever your harddisk nr is.

6. Quit grub by typing "quit".

7. Reboot. 

This was not the exact page I followed, and somewhere on the net is a very clear description of how to find out precisely what your harddisk and boot partition numbers are, as that becomes very important - I would assume it would be critical on a setup as partitioned as your's.  Unfortunatly, that I can't help you with.
The good news is that, as far as I know, Grub should recognize both XP and Vista, allowing you to easily triple boot - although I do not know this for certain.  It kinda sucks that you already wiped Vista, because you could have easily done this and kept the Vista partition in tact.  So, then, my recomendation would be to reinstall Vista, and then as the last step make Grub the bootloader again.

---

