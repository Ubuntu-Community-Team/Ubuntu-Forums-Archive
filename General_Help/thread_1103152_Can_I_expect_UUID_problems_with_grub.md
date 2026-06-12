---
title: "Can I expect UUID problems with grub?"
date: 2009-03-22
forum: General Help
---

### Post by anilbhx on 2009-03-22
I have three different *Operating Systems* on the 160 Gb drive . [I]XP , Ubuntu 8.04 and Fedora 7 .
[/I]
I want to delete the *Fedora 7* partition and make the space free for XP data. 

However I anticipate problems . I once installed *FC10* on the *Fedora 7 *partition and *Ubuntu* started giving **UUID** problems .
[I]
 It would load but first go through recovery mode.[/I]

Can anybody give me suggestions to get *Ubuntu *to load smoothly after modifying the *Fedora 7* partition . 

I use **dcfldd** to save the partition image so I can always restore the Fedora 7 partition if things get beyond control . 


Thank you ,
                                                                                                  _______________

---

### Post by Altay_H on 2009-03-22
When you're messing with partitions always be prepared for GRUB problems. I'd suggest making sure you have a copy of [SuperGrub]("http://www.supergrubdisk.org/index.php?pid=5") and some LiveCD that has GParted on it (Ubuntu or Fedora will do).

To install ArchLinux I had to reorganize my partitions so they were in numerical order. As you can imagine that destroyed my GRUB. However with SuperGrub and the Ubuntu LiveCD I had it working perfectly in a few hours.

What you've described doesn't sound to me like it should create any problem in GRUB, but I'd recommend you're prepared for the worst.



To answer your second question, if you press "e" while highlighting a boot option in GRUB it should take you to a screen where it will let you edit the boot options. If you remove the option that makes it boot in recovery mode rather than normal mode it should work the way you want it to. Please be careful when messing with GRUB.

When you highlight an option in GRUB and press "e" you'll see a new menu.
Highlight the second option (the one that begins with "kernel") and press "e" again.
Now you should see a bunch of random-looking numbers and letters followed by:
"ro single"
Without messing with the random numbers and letters change the "ro single" to "ro quiet splash"

---

