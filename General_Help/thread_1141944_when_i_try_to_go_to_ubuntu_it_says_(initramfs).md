---
title: "when i try to go to ubuntu it says (initramfs)?"
date: 2009-04-28
forum: General Help
---

### Post by chrisx16x2008 on 2009-04-28
Hey I dual booted xp and ubuntu the other day by installing ubuntu through windows.  I restarted and ubuntu worked then i restarted again to go back to xp.  Now i restarted today and selected the ubuntu option and i get something like this...

BusyBox v1.1.3
Enter 'help' for a list of built in commands
(initramfs)

then i can type in help or other commands after (initramfs).
Anyone got any idea how i can get back to ubuntu?

---

### Post by codeseer on 2009-04-28
What file system do you have set up on the Windows install?

Have you tried properly restarting the Windows system?

You could edit C:\ubuntu\disks\boot\grub\menu.lst and change the kernel boot line by replacing 'quite splash' with 'all_generic_ide'. Then see if it boots right.

---

### Post by jmszr on 2009-04-28
chris....,

Wubi installs Ubuntu into a windows folder usually a NTFS type of file system. this file system has a known reaction of being unstable in other operating systems like Ubuntu.. because people sometimes fail to unmount the drive correctly, heck even Windows can be blamed for this.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties.
Select the "Tools" tab and click "check now" under error checking (On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago)
                  
You can also accomplish the immediate previous tip by running chkdsk/f  in Windows and then shutting down properly.

---

### Post by codeseer on 2009-04-28
I recommend ditching Wubi and dual-booting.

---

