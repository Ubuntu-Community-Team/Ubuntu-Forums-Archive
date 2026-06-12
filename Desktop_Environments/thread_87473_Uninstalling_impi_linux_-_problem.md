---
title: "Uninstalling impi linux - problem"
date: 2005-11-08
forum: Desktop Environments
---

### Post by MacStew123 on 2005-11-08
Hi everyone,

I'm new to Linux and recently installed Impi on an AMD previously working on Win XP pro . Installation was easy enough and using Linux has been great but I cannot for the life of me figure out how to either:

1) use dualboot so that I can select either XP or Impi at startup.
      - i have attempted creating a new partition and followed various sets of instructions online that haven't seemed to work. luckily i dont need any of the data currently stored on the drive.
2) formatting the hard disk and re-install XP from scratch (this is ultimately where I feel comfortable since I'll ill likely build a new machine for linux anyway.

Can anyone please help me with this...or rather walk me through the process..im non (really non) technical ;-)

Thanks for your help!

Stewart
[IMG]http://www.cleanfunny.com/i/m/joine.gif[/IMG]

---

### Post by KingBahamut on 2005-11-08
Well first off, Dual booting linux is a dodgy deal. Youll need to install XP first, and then install linux on top of that to correct that oversight. 

As far as instruction to install windows XP , cant support that here. Try the *shudders* Technet forums over at microsoft.com for that.

---

### Post by MacStew123 on 2005-11-08
well, its not Windows that I'm having the problem with...XP installed perfectly the first time round and yeah, I then installed Impi over XP and haven't been able to access XP since...so I've given up trying to recover windows - i dont have the patience to deal with microsofts meaningless error messages anymore...so I want to clean install XP...however...i cannnot get linux off the hard drive and each time i attempt to boot off the XP cd, the Impi Lilo screen defaults and takes me either into Impi OS or hangs during startup...

any ideas?

---

### Post by mips on 2005-11-08
Ok, so you basically want a clean drive ?

I would use the Impi install CD to get up to the partition manager and simply delete every single partition on the drive. I have not used impi but i'm assuming it should be doable (I know all about assumptions!). You might even be able to create a new NTFS/FAT32 partition from here and format it, depending on capabilities of the partition manager.

Then you should be able to boot the XP cd, just ensure your bios is set to boot from CD-Rom first

---

