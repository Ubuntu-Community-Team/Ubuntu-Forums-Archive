---
title: "Windows 2000 install corrupted by Feisty update?"
date: 2007-09-16
forum: Desktop Environments
---

### Post by jimzat on 2007-09-16
I have an old PC that was running Windows 2000 from a 30Gig harddrive.  I used the Windows Computer Management utility to shrink the partition down so that I could install Feisty.

After installing Feisty, I checked to see that the Windows partition still booted and spent a little time under Windows to verify that all was OK.  I then rebooted into feisty and installed the updates that were pending since the initial install.  (After installing and rebooting I noticed that the grub menu now included two entries for the new kernel.)

Since my children are not yet Linux aware, I decided that I wanted the Window grub item to be the default choice and be at the top of the list.  To that end, I edited menu.lst and moved the Windows stanza above the initial Linux entry and ran "sudo grub-install /dev/sda0".  I then rebooted and waited for the windows partition to boot....

The text based status bar went to 100%, then the Windows splash screen appeared.  Its status bar stopped just beyond mid-screen and then I got a BSOD indicating "*** STOP: 0x0000007B (0XED41B84C,0XC000000E,0X00000000,0X00000000) INACCESSIBLE_BOOT_DEVICE"

I have searched through Google as well as directly through the Ubuntu forums with no luck as to finding a solution... The MBR is OK since it would still load grub and boot into Feisty, regardless, I loaded the recovery console and executed fixmbr.  Windows still won't boot and since no grub (due to the fixmbr), therefore no Feisty.  I also ran "chkdsk /r" from the recovery console and it found no errors.

I don't want to have to reinstall Win2K, since I only have the MS disk not all of the additional software disks for the software that was licensed to this machine and still loaded when the company got rid of this machine.


What next?!?

JiMZ

---

### Post by louieb on 2007-09-16
> **jimzat said:**
>  and ran "sudo grub-install /dev/sda0".  I then rebooted and waited for the windows partition to boot....

I'm surprised you got anything out of windows.  Assuming that win2000 is installed in the first partition of the hard drive. You just replace the widows boot code with GRUB.  
I believe you can boot your win2000 cd and run **fixboot**  from the recovery console to put the win2000 boot code back. 
But grub-install does more that just overwrite the boot sector of a partition. So that might not work.
Please post the output of **sudo fdisk -l** and lets see what that shows.

---

### Post by jimzat on 2007-09-16
I ran the repair selection from the Feisty Alternate Install CD and am again able to boot Feisty, but still the same error from Win2k.

my execution of "sudo fdisk -l" is:

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/sda2            1217        3556    18796050   83  Linux
/dev/sda3            3557        3649      747022+   5  Extended
/dev/sda5            3557        3649      746991   82  Linux swap / Solaris

---

### Post by louieb on 2007-09-17
Looks like a pretty typical Dual Boot setup. If **fixboot** does not repair it. Check here Herman lists the important XP needs to boot. Win2000 should be pretty much the same. 
[http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP](http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP)

---

### Post by az on 2007-09-17
> **jimzat said:**
> I edited menu.lst and moved the Windows stanza above the initial Linux entry and ran "sudo grub-install /dev/sda0".  I then rebooted and waited for the windows partition to boot....


not that I can help you with fixing your windows install, but...

Just editing the menu list is enough to make the changes.

You did not have to run anything to make those changes take effect.

If you make changes to the automagic grub configuration, (the double-commented lines in the file), then you need to run 
sudo update-grub
for each stanza to get rewritten, but again, nothing but that file gets changed.

---

