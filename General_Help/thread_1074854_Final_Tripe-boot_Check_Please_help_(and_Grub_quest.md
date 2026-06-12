---
title: "Final Tripe-boot Check: Please help (and Grub question)"
date: 2009-02-19
forum: General Help
---

### Post by BEND IT 7 on 2009-02-19
Okay, today I am almost sure I am going to install XP onto my laptop which already has Vista and Ubuntu as a dual boot.  I can NOT boot off of a CD, but flash drive booting works perfectly.  That is how I installed Ubuntu in the first place.  Anyway, I was wondering if my list of things compiled looks good:

-the flash drive with XP installer enabled (went through all the complicated steps for that)

-an external hard drive with VistabootPro installer

-a flash drive with Ubuntu Live loaded via unetbootin

And, now my planned steps:

1) Install XP onto the D:/ drive
2) Load VistabootPro in XP and restore the Vista bootloader
3) Log off XP and boot into Ubuntu Live and re-install Grub with the following code:   
sudo grub
  > root (hd0,0)
  > setup (hd0)
  > exit
4) Restart my computer and be able to boot into either Windows and then choose from Vista or XP or boot into Ubuntu.

- - - - - 

Does anyone see any flaws in my checklist?

Now I have a few quick questions:
How do I double check to make sure Grub was originally installed to hd0?  And, if it wasn't, how do I just do a complete re-install and have it recognize the Windows bootloader?
Will VistabootPro work properly if Grub has been installed and within Windows XP?


Thank you times a million in advance!

---

### Post by caljohnsmith on 2009-02-19
> **BEND IT 7 said:**
> 
And, now my planned steps:

1) Install XP onto the D:/ drive
Just a caveat, but it is quite likely that when you install Windows XP, it will put its boot files in the Vista partition and also change the Vista partition boot sector so that it boots XP's "ntldr" rather than Vista's "bootmgr". If you were installing Vista after XP, that wouldn't be a problem, but installing XP after Vista can be a big problem for the aforementioned reasons. If XP does modify your Vista boot sector, you will be able to boot XP but not Vista any more. To prevent that from happening, I would recommend "hiding" the Vista partition before you install XP so that XP doesn't touch the Vista partition, and then you can keep them separate; there are a number of ways you can hide a partition, including:
```
sudo sfdisk -c /dev/sda [COLOR="Blue"]<partition number>[/COLOR] 17
```
So if you want to hide sda3 for example, you would do:
```
sudo sfdisk -c /dev/sda [COLOR="Blue"]3[/COLOR] 17
```
Then when you are done installing XP you can unhide the partition with:
```
sudo sfdisk -c /dev/sda [COLOR="Blue"]<partition number>[/COLOR] 7
```
Those commands assume you are using NTFS and not a FAT file system. 
> **BEND IT 7 said:**
> 
2) Load VistabootPro in XP and restore the Vista bootloader

I'm not following you here, but if you hide the Vista partition before you install XP, I don't think you will need this step. :)
> **BEND IT 7 said:**
> 
3) Log off XP and boot into Ubuntu Live and re-install Grub with the following code:   
sudo grub
  > root (hd0,0)
  > setup (hd0)
  > exit
4) Restart my computer and be able to boot into either Windows and then choose from Vista or XP or boot into Ubuntu.

Those Grub commands assume Ubuntu is on sda1, is that true? 
> **BEND IT 7 said:**
> 
How do I double check to make sure Grub was originally installed to hd0?  And, if it wasn't, how do I just do a complete re-install and have it recognize the Windows bootloader?
Will VistabootPro work properly if Grub has been installed and within Windows XP?


Thank you times a million in advance!
If you want, you could run the "Boot Info Script" on your setup and I could look it over to see if I can find any "gotchas" that you might have missed in your strategy (if you think it would help). You can download the Boot Info Script from:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your present setup.

---

### Post by BEND IT 7 on 2009-02-19
Repairing the Vista bootloader is exactly what VistabootPro is for...;-)

Other than that, thank you so much for the suggestions!

---

### Post by BEND IT 7 on 2009-02-19
```
 Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda4 starts at sector 186177285.
    Operating System:  
    Boot files/dirs:   
```

That's all my summary says, if that helps you help me.  Do you have any more advice?

---

### Post by caljohnsmith on 2009-02-19
Since Ubuntu is on sda3, you should use "root (hd0,2)" when you do the Grub commands. That's about all I can tell from just the summary that you posted. Anyway, good luck and hope the installation goes smoothly.

---

