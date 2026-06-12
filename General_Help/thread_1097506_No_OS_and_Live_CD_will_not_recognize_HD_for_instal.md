---
title: "No OS and Live CD will not recognize HD for install!!!"
date: 2009-03-16
forum: General Help
---

### Post by shanex on 2009-03-16
Ok. My first build, no previous OS installed, installing linux, using live cd, and on option 4 'Prepare Partitions'. Nothing appears in the partitions list. All of the buttons, such as [New Partition Table] and [Edit Partition], are disable. When I click forward it gives me the "No root system is defined..." message.

My BIOS recognizes my Hitachi 7K1000.B HD but the Live CD does not! When i open terminal to cfdisk it it displays a gray screen and says 'FATAL ERROR: Cannot open disk drive'.

Have no clue what to do. I have searched forum after forum but am unable to find a solution or many other situations similar to mine.

Please if you guys have any idea...
Thanks

---

### Post by Admiral Yi on 2009-03-16
Hello,
This problem happened to me. I was using Ubuntu Hardy and it would not find either of my two hard drives. However, when I tried a distro with a newer version of the kernel, it worked fine. If your using Hardy, try again with Intrepid. If it still doesn't work, I suggest trying another distro called Linux Mint that is almost exactly the same as Ubuntu.

---

### Post by shanex on 2009-03-16
Thanks for the help AdmiralYi I appreciate it. I tried both though and still no dice. Linux Mint would not recognize my HD neither would 8.10 Intrepid. I get the same error for both of them on the same 'Prepare Partition' option of installation.

I just don't understand this error. Never have I seen it before and I have had quite a few hard drives.
Any other ideas?

---

### Post by mike555 on 2009-03-16
If your gparted shows your hard drive it is there ..... I think the error your seeing is because you haven't set the " /  " in the installer .....you must do that to continue....

---

