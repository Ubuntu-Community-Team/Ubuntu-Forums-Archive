---
title: "Blank screen w/ blinking cursor"
date: 2009-04-13
forum: General Help
---

### Post by Kilroy Higgins on 2009-04-13
Hello,

Recently I used a GTK partition manager on my Asus C90S with a 250GB HDD to divide it into a 210 GB Vista section and a 40GB blank section with the intention of using those 40GBs for a dual boot install of Ubuntu linux. I went through the procedure and installed Ubuntu into the 40 GB section, taking 5 GB of that and making it a swap area. However, now that I want to start my computer back up and get back to Vista (or anything at all) it gives me the blank/black screen with the underscore cursor blinking in the top left.

I've looked around already on the net, and have seen that this -could- be a master boot registry error, but I've since run the vista recovery utility and executed the bootrec.exe from console and restored that, but to no avail. In the Partition menu of the vista recovery, I deleted the new Ubuntu partitions and extended vista back over to take over back up to 250GB and tried restoring my MBR again, but it still gives me the blank screen. In the selection menu, the Vista CD detects that I still have my full install of Vista and it hasn't gone anywhere. I've also tried using the automatic system recovery tool, but that hasn't found anything nor fixed anything of value.

Long story short, after partitioning, installing ubuntu, deleting the partition and ubuntu, and making Vista the only native OS again, it still doesn't start up. So, in an effort to get it working again, I repartitioned with Gpartition, installed Ubuntu as originally intended and let it mount GRUB into my MBR this time, and I'm back up with Ubuntu running, however, Vista is still refusing to boot properly. A few of my friends have told me that Vista may be confused as to exactly where it had installed itself, and when I had attempted to reconfigure the BCD to try and look for winloader.exe in the D: drive instead (I only have 1 hard drive mind you) in the recovery console it gave me the error of "The boot configuration data store could not be opened. Access is denied."whereas trying to assign it to C: drive gives me ""An error occurred whiel attempting to reference the specified entry. The system cannot find the file specified." Can anyone provide some help?

---

