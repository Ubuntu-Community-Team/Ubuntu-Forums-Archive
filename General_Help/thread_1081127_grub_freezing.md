---
title: "grub freezing"
date: 2009-02-26
forum: General Help
---

### Post by Matroc on 2009-02-26
Hi,

before i come to my problem, my setup:
I'm running a thinkpad x41t (i guess the hardware is not the problem here though)

I have set up a dual boot environment with windows xp tablet and ubuntu 8.10. The mbr contains the windows bootloader as this is required for the access ibm button (which is a functionality that i want to keep). So putting grub into the mbr is _not_ an option.
The windows bootloader loads either windows or grub (which lies on /dev/sda5 -> my ubuntu partition).
This worked flawlessly for about half a year.

however since yesterday when grub is starting it only shows "GRUB" and freezes. No prompt, no list, no log (that i know of), no error message, nothing, just "GRUB".

What puzzles me even more is that the day before, it worked and i don't remember making any changes that would affect grub.

When i boot using a live cd and look at the filesystem, it tells me that no files in /boot and /boot/grub have been modified within the last week. And e2fsck finds no errors.

I've also tried to rewrite grub (grub-install/grub-update) using a tutorial from the german ubuntuusers community. However the problem is still the same.

The day the problem occurred i didn't boot windows or even mount the windows partition. So i would rule out that as problem source.

I have no idea how to debug or fix this problem. Any suggestions would be welcome...

---

### Post by caljohnsmith on 2009-02-26
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Matroc on 2009-02-26
Thanks,

that script helped big time. Especially this part:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub in the file /linux.bin looks at sector 60972172 
                       of the same hard drive for the stage2 file, but no 
                       stage2 files can be found at this location.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM
```

Some time ago i shrunk the windows partition and enlarged the linux one. That of course moved the bootsector of sda5. It seems the old bootsector was still in place though and it worked, until that block in sda5's free space got overwritten and contained no useable data.

I replaced the old linux.bin -> problem solved.

---

