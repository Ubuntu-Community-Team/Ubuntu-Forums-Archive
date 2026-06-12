---
title: "Black screen when trying the 8.10 boot cd"
date: 2009-02-14
forum: General Help
---

### Post by jonruiz1 on 2009-02-14
------------------------------------------
Specs:
[ASUS  m51 series laptop]
AMD Turion X2 Ultra Dual-Core Mobile 64
4G RAM
ATI Radeon HD 3650
------------------------------------------
1. Downloaded and burned the v8.10 64-bit desktop iso
2. Booted from the cd drive
3. Disk booted properly and at the menu chose "Install Ubuntu" and "Try Ubuntu..." both in safe graphics mode and standard.

Results: Installing or trying it out both result in a black screen immediately after choosing an option from the ubuntu boot menu, even in safe mode. The machine is stuck on the black screen at this point.

I am currently downloading the 32-bit version, but I just wanted to get others opinions.. Am I on the right track downloading the 32-bit or does the problem lay elsewhere?

Thanks in advance!

---

### Post by jonruiz1 on 2009-02-14
Anyone?

---

### Post by JimBuntu on 2009-02-14
Definitely use the 32 bit version. I have read some ubuntu books that say there is no reason to use the 64 bit. There are a lot of bugs with the 64bit. I had the same problems. First try the easiest the wait a while with the black screen. If that doesn't work try moving the mouse or hitting a couple of keys on the keyboard. If that doesn't work. Search for a post about "noapic". Read and you'll see what I'm talking about. I have a post with step by step instructions on how to do this. Usually the black screen is related to graphics drivers. Just try the 32 bit first. It should work. You should be clicking on the first option which says "start or install". It will not install until you tell it to. It is a great way to test it out.

---

### Post by jonruiz1 on 2009-02-15
I booted up the 32-bit and I still got the black screen.
I have no clue what to do now ](*,)

---

### Post by jonruiz1 on 2009-02-15
Okay, so I booted the cd by adding 'noapic nolapic' to the boot command and it worked, I installed ubuntu via the demo and did all the partitions (ext2 for the main because I wanted to retain my files on another partition, though I don't know if ext2 was the best choice).

Ubuntu is now installed (and vista is gone!) yay!

BUT..

Upon rebooting I got the black screen after the GRUB. No mouse activity during the black screen, it's just stuck. 

I'm guessing I'll have to edit those boot commands. How do I get it running:confused:

---

### Post by jonruiz1 on 2009-02-16
Sorry for being a total newb :/ 
I've been looking at other threads relating to the black screen but I can't seem to figure out what to do.

---

