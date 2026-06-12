---
title: "Booting (or installing) problem"
date: 2008-12-22
forum: General Help
---

### Post by crazy2be on 2008-12-22
A strange problem with xUbuntu 8.10-i386

The CD is able to Boot into the first menu, with:
"Try xubuntu without any change to your computer" -> appears to do something, at first, but soon stops, and does nothing for 15 minutes, still displaying the menu (but not letting you choose anything in it)
"Install xubuntu" -> displays a messagebox with the title "Boot Loader" and message "live-install"
"Check CD for defects" -> displays a messagebox with the title "Boot Loader" and message "check"
"Test memory" -> displays a messagebox with the title "Boot Loader" and message "memtest"
"Boot from first hard disk" -> Works fine and boots from the first hard disk, but that doesn't help any :P

Any idea how to fix this?

[I have tried the IRC channels, and the ISO passes the md5 test]

the system is a fairly old Aopen PC with ~192MB of ram and a 433 Mhz proc (i think)

---

### Post by pytheas22 on 2008-12-22
That hardware is a bit weak for the live CD, even Xubuntu.  You really need at least 256 megabytes of memory to run a live environment.  This is likely the problem.

You should try installing via [the alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate"), which provides a text-based installer that's not as pretty as the live CD but requires much less memory.  That should work for you.  If not, please let us know and we can try some other things.

---

### Post by crazy2be on 2008-12-22
I checked the hardware in the BIOS:
Pentium III 550 Mhz Processor,
196 MB of RAM.
that is pretty close, but it should work (once installed):/
i'm downloading the alternate CD now, going to take 1.5 hours...

But if there wasn't enough memory, wouldn't it give me that as an error?

And shouldn't the 'install ubuntu' choice work in that case?

...or atleast the 'memcheck' or 'check cd for defects' options?

---

### Post by pytheas22 on 2008-12-22
> But if there wasn't enough memory, wouldn't it give me that as an error?

Maybe, but maybe not.

> And shouldn't the 'install ubuntu' choice work in that case?


No, that option actually just starts the normal graphical installer, which uses a lot of memory (this option is exactly equivalent to booting to Ubuntu and then clicking the 'install' icon on the desktop).  You need a text-based installer, which isn't available anywhere on the live CD.

> ...or atleast the 'memcheck' or 'check cd for defects' options?

I would expect these things to work even with low system memory, but it's hard to know for sure what the behavior would be.

Anyway, I think the bottom line is that there could be something else going on here in addition to the memory problem.  But either way, your system doesn't have enough RAM to be able to run the live installer, so the first step in getting Ubuntu on your machine is to try the text-based installer.  If problems persist even with the alternate CD, we'll have to deal with them as they come.
> 
that is pretty close, but it should work (once installed):/

Yes, Xubuntu should work once it's installed, although it may be less than zippy (it might be fine though).  If it's too slow on your hardware, there are of course other distributions that you can try.

---

### Post by crazy2be on 2008-12-23
Thank you for the very informative reply. i have downloaded the alternitive install CD, and i get a "Kernel Panic" error when i select "install xubuntu" or "check CD for defects". the third option, "rescue a broken system" also gives a kernel panic error, although for a different reason (exception in hardware interrupt). the memtest works, and it giving me loads of errors. (weird, since windows 98 was working only a week ago).

Any way to get around the errors? like telling xubuntu that the memory is bad, so it won't try to use it?

---

### Post by pytheas22 on 2008-12-23
Unfortunately, I guess it's more than just the live CD at fault, then.

I don't now of any way to tell Xubuntu to ignore bad memory.  There might be a way in BIOS to tell it to ignore one of the sticks or something, but I doubt it.  Can you open the machine up and take out one of the sticks, then see if things work better (if not, try taking out the other stick)?  Maybe only one stick is bad.

If that doesn't work, could you try to write down some of the exact error messages that you get when you try to launch the installer, or the last things you see on the screen before it freezes?  With those, we can see if Google will lead to any hints, which at this point is unfortunately the only other thing I can think to try.

---

### Post by crazy2be on 2008-12-23
I got it to work, the problem was apparently an old HD that was not getting properly treated (allocated as ram?)

I unplugged it, and i was able to install xubuntu with the alternate installer. The memtest can now run fully without any problems, and it must of somehow told the computer about my bad ram, since i'm missing 64MB worth now.

Thank you for all your helpful replies!

---

