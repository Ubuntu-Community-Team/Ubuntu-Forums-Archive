---
title: "Inspiron 1300, Ubuntu 9.10 and MBR"
date: 2010-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by error023 on 2010-01-10
I have an Dell Inspiron 1300 laptop operating Windows XP SP3 on a 40 GB hard drive and an 250GB USB Seagate External Expansion Portable Drive, partitioned into two equal sections. I downloaded and burned Unbuntu 9.10 to a CD. I booted up from the CD and installed Ubuntu on one part of the Expansion Drive. When it was completed, I shut down my laptop, unplugged the Expansion Drive and ate dinner.

Later on and came back and turned on my laptop. When I turned it on, I received this message:

GRUB loading,
error: no such disk
grub rescue>

When I connected the expansion drive to my laptop, GRUB starts up and I can choose from using Ubuntu or Windows. The laptop was given to me as a hand-me-down,
so I do not have a copy of Windows XP, nor can I locate a copy to repair the MBR on my laptop. Is there a way I can fix what has happened so I can normally boot Windows
without needing to plug in my expansion drive? Thank you.

---

### Post by error023 on 2010-01-18
*bump*

---

### Post by argosreality on 2010-01-18
Are you actually seeing the full grub menu listing the Ubuntu install as well as the windows XP install? If so, does it fail to load both the Ubuntu install (without external drive connected) as well as XP or does XP load fine?

---

### Post by error023 on 2010-01-19
With my external hard drive plugged in, I am able to see the full GRUB menu listing the Ubuntu install as well on the external hard drive, and the windows XP install on my internal hard drive. 


Without my external drive plugged it, my laptop fails to XP. It goes straight to. 

GRUB loading,
error: no such disk
grub rescue>

The part I don't understand is why it i looking for GRUB on my internal hard drive when I installed Ubuntu on an external hard drive.

Windows XP is only installed on the 40 GB hard drive, which is the internal drive. The 250GB USB Seagate External Expansion Portable Drive, partitioned into two equal sections, has Ubuntu install on one of the partitions. The other partition is blank.



Here is some additional information that I hope helps. This is what my GRUB menu looks like when the external HD is connected:

Ubuntu Linux 2.6.31-14 generic 
Ubuntu Linux 2.6.31-14 generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+) serial console 115200
Dell Utility Partition (on /dev /sda1)
Microsoft Windows XP Home Edition ( on /dev/sda2)
Ubuntu 9.10, kernel 2.6.31-17-generic (on /dev/sdc1)
Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode) (on /dev/sdc1)
Ubuntu 9.10, kernel 2.6.24-26-generic (on /dev/sdc1)
Ubuntu 9.10, kernel 2.6.24-26-generic (recovery mode) (on /dev/sdc1)
Ubuntu 9.10, kernel 2.6.22-16-generic (on /dev/sdc1)
Ubuntu 9.10, kernel 2.6.22-16-generic (recovery mode) (on /dev/sdc1)
Ubuntu 9.10, (memtest86+) (on /dev/sdc1)

When I hit the e buttom for edit, this is what I have seen:

insmod ntfs
set root = (hd 0,2)
search--no-floppy--fs--uuid -set9eb812ed812c327
drivemap -s (hd0) ${root}
chainloader +1


Sometimes I see this instead:

ismod fat
set root = (hd0,1)
search--no-floppy--fs--uuid -set9eb812ed812c327
drivemap -s (hd0) ${root}
chainloader +1

---

### Post by error023 on 2010-01-27
I downloaded the .9799 iso file of Super Grub Disk, burned it to an empty CD. I rebooted my laptop and repaired my MBR.

---

