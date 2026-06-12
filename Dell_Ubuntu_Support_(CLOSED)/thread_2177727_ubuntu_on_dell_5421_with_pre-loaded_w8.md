---
title: "ubuntu on dell 5421 with pre-loaded w8"
date: 2013-09-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by auben on 2013-09-30
hi!

i bought a dell 5421 a few months ago and have decided to dual boot the system (removing w8 was my original plan) with ubuntu 12.04. following instructions i found on the internet (everyday linux user) i seem to have successfully installed 12.04 in the machine. i am now to the point where i am able to boot in windows but am unable to boot into ubuntu (which is my preferred os).

i have the result of the boot repair at [http://paste.ubuntu.com/6174537](http://paste.ubuntu.com/6174537).

can anybody help? 

i would appreciate any help or suggestion!

---

### Post by oldfred on 2013-09-30
You are showing BIOS boot loaders in the MBR and UEFI boot loaders in the efi partition. But you somehow have an XP boot loader in the efi partition as well as old Windows BIOS boot files? Did you copy those in. Windows only boots from a gpt partitioned drive with UEFI.

You have run the rename function with Boot-Repair. That is for buggy UEFI, but I thought it was not required for most Dell. I might run the un-rename and see if you can then boot Windows. But you may need to change your sda3 Microsoft reserved partition first. It looks like you formatted it?

I think you did this, see below for undoing it.
       Rename will occur if Boot-Repair sees Windows kernel issues, but may not always be required. 
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]?
Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your UEFI/BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   To undo & to rename files to their original names, you just need to tick the "[COLOR=#ff0000]Restore EFI backups[/COLOR]" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

      
 Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)

---

### Post by gordintoronto on 2013-09-30
Quite often, when you have a computer which is newer than the OS, some parts of the computer will not be supported. If I had your computer, I would try the beta of Ubuntu 13.10; the release date is less than a month away.

---

### Post by auben on 2013-10-01
thanks for the prompt reply. i have tried some of suggestions you have mentioned. as i am new to linux, at least in the nitty-gritty of it (although i have been using it for about a year), i am trying to learn my way around the terminal so that i can better understand and better implement them. sorry for this. i know i haven't been much help in explaining. 

in following instructions in [http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html) , i have done only those mentioned, and i really do not know where the old windows bios files came from. it may be that i have done something wrong along the way, but i have not added or copied anything. i tried to rename the efi files but nothing happened. incidentally, maybe i should mention that whenever i run boot repair, i type in "sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update" and "sudo apt-get install -y boot-repair && (boot-repair &)". is this correct? i somehow feel that i may be re-installing everytime i boot-repair. 

last time i tried boot repair, i got this - [http://paste.ubuntu.com/6178164](http://paste.ubuntu.com/6178164).

hope this helps. 

thanks for all the help. i really appreciate it! 

regarding the 12.04 install, i was thinking of the lts nature of this version in installing it. besides, i have tried it on another machine and it worked really well. it was an acer netbook. when the 13.10 comes, i may upgrade if reviews are good.

thanks and regards

---

### Post by oldfred on 2013-10-01
The installer is an image and unless you enable persistence, you have to reinstall Boot-Repair each time you reboot.

When you say Windows boots is that from UEFI menu or from grub menu. And then Ubuntu does not boot, it that a black screen. If so then you may have booted but have video issues.
What video card/chip do you have?

From terminal in live installer:
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

---

