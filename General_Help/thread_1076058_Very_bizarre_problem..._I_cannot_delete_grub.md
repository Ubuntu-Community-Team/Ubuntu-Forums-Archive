---
title: "Very bizarre problem... I cannot delete grub"
date: 2009-02-20
forum: General Help
---

### Post by LodeRunner on 2009-02-20
The remnants of Grub are apparently interfering with a Windows install (black screen bug when booting from setup CD.  According to Google, this is a common occurrence related to hardware or MBR messups.)

Where I am now: I have unplugged all disk drives except one.  I have ANNIHILATED everything on the hard drive.  I have repeatedly formatted it and deleted/remade the partition table. I have used shred and wipe to overwrite THE ENTIRE DISK (/dev/sda) with random data.

And yet, when I boot up I see this:

Verifying DMI Pool Data ..........................
Grub Loading Stage1.5



Grub loading, please wait...
Error 21


This SHOULD be impossible, so I have attempted to find another explanation.  I unplugged all other hard drives. I tracked down every single USB device plugged in, and made sure none of them was an external drive or SD card reader. I unplugged my ethernet cable, in case it was somehow some kind of odd network booting. I unplugged my Razer Diamondback mouse because I knew it had a few kilobytes of flash memory in there that might conceivably hold Grub.  I unplugged my keyboard and CD drive, even though I knew damn well that neither had any nonvolatile memory. I fiddled around in the BIOS and was forced to conclude that Grub must somehow be on this hard drive.  This hard drive that has been thoroughly wiped at the lowest possible level.

I can find no other explanation. How is this possible?  From my understanding, the MBR isn't special from a hardware point of view.  It's just the first X number of bytes on a disk.  Reformatting should kill it.  "sudo wipe -q /dev/sda" should most certainly destroy every last bit of it.

Something that might possibly be significant: Prior to this, I had been fiddling around with Truecrypt trying to get a setup where Windows is fully encrypted (by Truecrypt) and Ubuntu is encrypted using the dm-crypt option provided by the alternate installer.  I don't know if this is relevant or not, but Truecrypt's bootloader is a weird one, and the Truecrypt "encrypt partition" wizard did offer to wipe/encrypt an area of the hard drive which they claimed was normally inaccessible (supposedly intended for special hard drive utilities.) I am wondering if maybe it was somehow possible to (accidentally?) create an MBR in this inaccessible area.

Right now, my only inkling is to attempt to install Windows on some other hard drive (which would be a real PITA), then see if I can download Western Digital's hard drive tools and access this mythical hidden area of the drive.

Any other ideas?

---

### Post by caljohnsmith on 2009-02-21
In order to get a clearer picture of your setup to see where Grub might be hiding, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by LodeRunner on 2009-02-21
My friend managed to kill grub with a dd if=/dev/zero of=/dev/sda bs=4k count=1

Don't ask me how this worked when wipe failed, but it did.  (can't remember how long I let shred run for, but I let wipe completely finish one iteration.) XP boot disk working now.

I must admit, I'm a just a bit saddened.  It was a great mystery while it lasted. Thanks for the advice, unneeded though it was.

---

### Post by oldos2er on 2009-02-21
Probably the tools you used wiped everything except the MBR.

---

### Post by ddmdllt on 2009-02-21
Yes, before the partitions themselves, there is the [Master Boot Record (MBR)]("http://en.wikipedia.org/wiki/Master_boot_record"). It contains the partition table and a very very small program. When you have grub, the code in the MBR just load some more complex code outside, and then it boots your OS.

You have to erase your MBR fully and not only your partition table.

Are you able to run the old DOS's fdisk program? (for an ugly "FDISK /MBR")

---

### Post by Axanon on 2009-02-21
Also, depending on the variant of windows, if you can get a console off the Windows CD, the command may be 'fixmbr', which has worked for me in the past as well. Just a warning though, if you do have a Linux partition it will not be usable until you reinstall some kind of boot loader for it.

---

