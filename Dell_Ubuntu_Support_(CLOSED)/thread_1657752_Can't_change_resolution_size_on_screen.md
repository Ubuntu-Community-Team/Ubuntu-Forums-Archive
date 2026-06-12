---
title: "Can't change resolution size on screen"
date: 2011-01-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bro brian on 2011-01-01
I have an older Dell Optiplex GX260 computer. I partitioned the hard drive to add Ubuntu 5.10 (Breezy Badger) to it, along with Windows XP Pro. The Ubuntu partition has a screen resolution of 640x480, which is way too big, and there are no other options.
  I have followed the steps outlined on an outdated post located at:
[http://ubuntuforums.org/showthread.php?t=104097](http://ubuntuforums.org/showthread.php?t=104097)

  For some reason, after I add the "vga=792" in the menu.lst as instructed, and I reboot, my modification is not saved. 
  My question is:  Am I suppose to do something else to make the modification stick? :confused:

Here is the original instruction:
**Any help with this is dearly appreciated!!!!**

                                                                    **Re: How to change virtual terminal screen size**             
                                                                This resolution  is set at boot by a setting in the menu.lst file that grub reads  (assuming you use grub from here on out, its the default bootloader for  ubuntu).  Open up menu.lst with your favorite text editor as root:
     
     ```
sudo nano /boot/grub/menu.lst 
```Now, scroll down for a while and find the boot entry you want to  change the resolution of; usually its the first one that is uncommented.   Now, add vga=### to the end of the "kernel" line you want to use  (again, should be part of the section of the kernel you usually boot  into), where ### is one of the following numbers:

.................640x480.........800x600.......... 1024x768........1280x1024
8 bpp............769................771............. .....773 ..............775
16 bpp ..........785 ...............788.................791............ ....794
32 bpp...........786 ...............789.................792............ ....795

For myself, I use 1280x1024 at 32bpp, so i added vga=795 to the end of  the line.  Then when you reboot and select the boot option that you  edited, all your bootup information and any extra virtual terminals you  switch to will be at your desired resolution.

For example, here is the entry in my menu.lst that I boot with.  Notice the end of the kernel line:
     
```
title           Ubuntu, kernel 2.6.12-10-686-smp
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda2 ro quiet splash vga=795
initrd          /boot/initrd.img-2.6.12-10-686-smp
savedefault
boot
```

---

### Post by mikewhatever on 2011-01-02
Did you save the changes? When you press ctrl+x to exit nano, it asks at the bottom of the screen whether to save the changes (y), not to save (n) or cancel (ctrl+c). You may not be able to see that because the resolution is too small, so, just to be clear, hit 'ctrl+x', 'y', 'enter', after editing.

---

### Post by bro brian on 2011-01-02
> **mikewhatever said:**
> Did you save the changes? When you press ctrl+x to exit nano, it asks at the bottom of the screen whether to save the changes (y), not to save (n) or cancel (ctrl+c). You may not be able to see that because the resolution is too small, so, just to be clear, hit 'ctrl+x', 'y', 'enter', after editing.
I'm going to try this right now (just got home from work). Thanks for the expended instruction, Mike. Will give this a try, and see what happens.

** I have done the ctrl+x, 'y", "enter. It is to no avail as of yet. It does go to another prompt that says:
"File Name to write: /boot/grub/menu.lst", and gives me the following options:
^G-  Get Help------             ^T-  To Files            ----------------M-M - Mac Format---          M-P Prepend
^C-  Cancel---------                M-D- DOS Format--------    M-A-  Append-----------M-B  Backup file

I didn't  know if I should append this or what, so at that point I just hit hit the "Enter" key, and it went back to Terminal. When I restarted, the screen resolution was back at 640x480.

---

### Post by mikewhatever on 2011-01-02
That last prompt is basically asking if you want to save the changes to /boot/grub/menu.lst. Just hit 'enter' there.

---

### Post by bro brian on 2011-01-02
Well, that's what I did. I just hit the Enter key, but the screen resolution didn't change when I restarted. Sorry! Don't know what to think about it.
  I'm going to try destroying the Ubuntu Breezy partition (with [SIZE=3]GParted Partition Editor) from tthe Ubuntu 10.04 Lucid live cd, then install lucid on that free space. I see if I end up with the same problem after Lucid is installed. Probably will, but it's worth a try. I'll let you know the outcome when the installation is finished.
  I appreciate your patience!
[/SIZE]

---

### Post by bro brian on 2011-01-03
OK now -
  I was able to get it right! This is what I did:
  I tried installing Ubuntu 10.04 Lucid Lynx (i386 - 32 bit). The resolution problem went away, and I had a nice screen - perfect size, but both the keyboard & mouse were disabled!... ARRRG!
  After reading several threads about this issue, I decided to delete Lucid using the GParted partition editor on the live cd (Mind you that this is a "dual-boot" desktop), and install **Ubuntu 9.10 Karmic Koala** (i386 - 32 bit) from the downloaded cd. Everything worked perfectly.
*
  Mind you that this is on a Dell. I don't know why I've had so much difficulty with this. It really isn't an Ubuntu issue (although it would be nice if they could address this somehow in future distros). I don't think Ubuntu Maverick os would have worked, either. I have Microsoft Windows XP on the other partition, and even that needed resolution AND INTERNET drivers downloaded & installed. From my experience, Dell computers just aren't very "user-friendly". I've got an old Compaq (from the Windows ME days) that has Ubuntu Lucid on it, and it installed flawlessly. I'm sure Ubuntu Maverick would install on it easily as well.
*
  I realize that this wasn't an actual "fix", but it worked. Good enough for me. I don't know if I would mark this thread as solved, but I do think it to be an acceptable solution. :p

---

