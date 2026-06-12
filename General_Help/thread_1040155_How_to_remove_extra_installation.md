---
title: "How to remove extra installation"
date: 2009-01-15
forum: General Help
---

### Post by acroporas on 2009-01-15
My computer has 4 hard drive in it.

A few weeks ago I was having some troubles so I installed an additional instance of Ubuntu on a partition on one of the unused drives in my computer to use until I fixed the problem.

I have since resolved my problem and want to get rid of the extra installation.

What is the proper way to do this?

I know that I could just reformat the drive that the extra installation is on, but I fear that might cause grub/boot problems.

When I go to /boot/grub/menu.lst it only has one (the origional) copy listed.  But when I boot the computer, both the old and the new versions show.

---

### Post by cdtech on 2009-01-15
Yes, you could format the partition in question and then while in the Ubuntu distro you can run "sudo update-grub" this will update the /boot/grub/menu.lst file.
[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz)

---

