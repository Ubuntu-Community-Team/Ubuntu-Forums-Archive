---
title: "Doesnt give me an option for which hdd to boot from..."
date: 2009-01-03
forum: General Help
---

### Post by dcjose20 on 2009-01-03
I have 2 hard drives on my pc. One has vista business, which is the master drive. The second drive has ubuntu and is set up as a slave. When i turn the pc on it does not give me the option of which hdd to boot from. I can press F8 everytime and choose which hdd to boot from, but seems like too much of a pain to do. Can someone plz tell me how to fix the boot loader. Thanks in advance for the help!

---

### Post by logos34 on 2009-01-03
Switch the Bios so ubuntu is the boot drive.  Then add mapping to the windows boot entry in /boot/grub/menu.lst, something [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

Post your

sudo fdisk -l

if unsure

---

