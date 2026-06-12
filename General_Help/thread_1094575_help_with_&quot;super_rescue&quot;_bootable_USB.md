---
title: "help with &quot;super rescue&quot; bootable USB"
date: 2009-03-12
forum: General Help
---

### Post by EvilRobotDrew on 2009-03-12
HI!

I have been banging my head against a wall for a few months trying to get this to work, and now i am asking you all for input. I want to create a "Super Rescue" Bootable USB drive. I want to have a USB drive, with Ubuntu, Backtrack, Ultimate Boot CD, FCCU, STD, DSL and Samurai (if you have any ideas for bootable enviroments that would be a good addition please let me know). So far, i have tried installing grub to a seperate partition on the thumbdrive, then DDing each iso onto another seperate partition (usually creating an extended partition to hold all of them). the problem is that most times, grub simply won't boot them, after i add entries into menu.lst for all of them (usually error 13, or 15). when they do boot, they usually have a kernel panic and fail. I have also tried extracting them all onto one partition, but this is difficult because many have the same basic directory structure. to date the only success i have had is in booting ubuntu and samurai, but i want all of them (preferably with the option of adding more, like Hiren's Boot CD, or BartsPE).

I am considering trying lilo, but before i go down this rabbit hole again i want to get ideas from you guys. How would you go about creating this bootable USB drive? 

<flamebait> I am also posting this to the Fedora fourms, so we will see which form is more helpful for more advanced questions like this :) </flamebait>

---

### Post by EvilRobotDrew on 2009-03-13
as of now, fedora fourms is +2

---

### Post by EvilRobotDrew on 2009-03-13
having wasted my entire friday tring to get this to work, i have a status report.

I downloaded a bunch of Floppy Images, including DBAN; as of now none of them are booting but i think this is just a matter of time, i have spent mabie 10 minutes on them. the most common error is unsupported Executable format, but if i can't get any of them working, i won't fret as their functionality is easily replaced by some of the LiveCDs i am trying to boot.

currently i have Backtrack, and FCCU booting correctly. I installed GRUB on the first (and largest) partition (7gb), formatted as FAT32. I then dedicated the rest of the drive (8gb) to an extended partition, inside that partition i created a separate fat16 partition for each live environment i plan on booting. i opened the ISOs for backtrack, DSL, FCCU, Samurai, and Ubuntu, and extracted them each onto their partition. i pointed Menu.lst to the kernel and initrd of each distro. Currently Samurai and Ubuntu have the same error, after discovering the USB disk they hang, and fail (i have a feeling that the kernel is looking for the CD drive, and freaks out when there isn't a disk there). GRUB cann't even boot DSL, i get a File Not Found error (i have checked the path to initrd and the kernel, and the root partition several times).

FreeDOS, Hiren's Boot CD, KnoppixSTD, and UBCD havent even been tried yet. I know most of them will need to be chainloaded but i am not sure how exactly to proceed. If i DD the ISO to it's partition, then grub refuses to read it (usually the error is "invalid or inexecutable format"), and because most of them will need to run off their own boot loader i am not exactly sure how to proceed. is there a way to convert an ISO to a Fat16 formatted image? something tells me it is impossible.

---

### Post by EvilRobotDrew on 2009-03-15
In addition to Backtrack and FCCU, i have DSl and Darrik's Boot and Nuke booting. 

[http://forums.fedoraforum.org/showthread.php?p=1184625&posted=1#post1184625](http://forums.fedoraforum.org/showthread.php?p=1184625&posted=1#post1184625)

<flamebait>for the record, Fedora fourms +3</flamebait>

---

### Post by EvilRobotDrew on 2009-03-16
SOLVED!

go to [http://informationinsecurity.com/](http://informationinsecurity.com/) for my writeup

---

### Post by mwcmic on 2009-03-27
Hello

I wrote a tutorial which might be helpful to someone on how to boot both Ubuntu and Hiren's boot CD from USB pend drive.

[http://0-fx.com/index.php?/General/how-to-make-a-bootable-usb-flash-drive-with-ubuntu-and-hirens-bootcd.html]("http://0-fx.com/index.php?/General/how-to-make-a-bootable-usb-flash-drive-with-ubuntu-and-hirens-bootcd.html")

---

