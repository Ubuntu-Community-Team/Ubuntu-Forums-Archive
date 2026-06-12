---
title: "Vista broke my GRUB; Now What?"
date: 2006-09-18
forum: Desktop Environments
---

### Post by jdralphs on 2006-09-18
Yes, I've seen quite a few posts similar to mine and I have attempted to follow the solutions there -- using the live cd to reinstall GRUB --> that did not work.  I also tried using the "Super GRUB CD" (which IS pretty awesome) to automatically restore my GRUB -- the cd reported a success, however, when I try to boot, no bootloader comes up and my system hangs frozen after it checks for bootable cd's.

I can get into my old GRUB from the Super GRUB CD, 'problem is that when I try to execute anything other than the recovery options I get a error #15 -- "File not found".  

Does anyone have any suggestions on how I might fix this issue?  ((Vista blows pretty hard ... just so everyone knows ... so if anyone has a solution, I'd love to hear it so I can end my Microsoft usage)

---

### Post by artinla on 2006-09-18
do you know which drive your linux partitions are on?

I usually use the superrescuecd and type "grub"

Then at the grub> prompt type "setup hd0,0" or whatever the HD# is.

You may have to tweak the /boot/grub/menu.lst after you get back into your load to reflect the proper harddisk as well.  Just hit "E" when the grub menu is displayed and edit the hd0,x and root=hda(x) lines to suit your particular drive configuration.

#Re-install Grub with Live CD Example:

art@fartbox~:$ sudo grub

GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
This is an example of one use of a grub shell.  The Grub shell can be used with either a live cd or an installed system to re-install GRUB to MBR. (For example after a Windows re-install has overwritten your MBR and installed the IPL for the Windows bootloader.)
To enter the grub shell, I typed 'sudo grub', and pressed 'Enter'.
It is important in Ubuntu, to use the 'sudo' preface to the 'grub' command. If not, you will get what appears to be a grub shell, but you won't be able to do very much with it. You will probably get some confusing error messages.


grub> find /boot/grub/stage1
   (hd0,1)
   (hd0,3)

Here, I typed 'find /boot/grub/stage1' because I want to find out which partitions in my computer have Grub installed in them, (just to remind me).


grub> root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83

The 'root (hd0,1) will tell grub which operating system partition contians the grub I want to install somewhere.  The Grub menu from that operating system's /boot/grub/menu.lst will be the one that appears on boot up.
If grub recognises the filesystem, it will reply with an output similar to the one shown above.



grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

'setup (hd0)' is the command to install Grub's stage1 to MBR.
Stage1_5 will also be installed to the 15 sectors following the MBR in the first track of the hard disk.
It is also a good idea to install Grub to the first sector of a Linux operating system's partition too, (I'm not sure about what you would do if you had a separate /boot partition, install to that instead I presume). To install Grub to a partition, you would use a command like, 'setup (hd0,1), or 'setup (hd0,3)', where (hd0,1) and (hd0,3) are Linux partitions. If you do that, you should be able to 'chainload' your operating system in an emergency. 


grub> quit

This is just to take you back to the regular terminal prompt again.

---

### Post by jdralphs on 2006-09-18
I'd tried that method earlier as well; after completing the above and restarting, instead of getting the Vista bootloader, or GRUB my computer hangs when GRUB should be loading up but nothing loads.

Thanks though.

I'm still trying to find a good way around this ... any other ideas?

---

### Post by artinla on 2006-09-18
You should disconnect your Vista drive and redo the grub setup.

**After** you get grub working and linux boots again, disconnect the linux drive and then load your Vista setup DVD.  There is an option to go to a "Recovery Console".. Do that.

*Remember, at this time you should only have the Vista drive connected.*

At the Recovery console, run fixmbr and then fixboot.  Reboot and verify that the Vista drive boots properly.

Once all that is done, it is easiest to just manually edit the grub.lst file and enter the boot information for the windows drive.  There are hundreds of howto's that explain how to do this.

This method works for me every time, but if you have more trouble just post back here.

---

