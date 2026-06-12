---
title: "Using LiveCD to recover files/Problem with permissions"
date: 2009-02-11
forum: General Help
---

### Post by freshtealeaf on 2009-02-11
Hello

I'm using a Xubuntu 8.10 to recover files from my laptops hard drive (NTFS) onto my Xubuntu 8.04 x64 system.

Now, I've successfully mounted my laptops hard drive and the hard drive on my system that I want to transfer files into.

/dev/sdb1 = PC Hard drive (files will be stored here) mounted under /media/linux1

/dev/sdc1 and /dev/sdc2 = Laptop partitions mounted under /media/windows1 and /media/windows2

Now I can't seem to write any files to /dev/sdb1.. I don't know why. I suspect its a permissions problem, in which case can anyone help me out with what I should do next?

Thank you!

**PROBLEM HAS BEEN SOLVED!** I issued a sudo mount -a command it it all seemed to work. :) Before that command I also issued a sudo apt-get install ntfs-config. :) Hope this helps anyone else in my situation!

---

