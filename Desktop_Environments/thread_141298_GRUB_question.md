---
title: "GRUB question"
date: 2006-03-08
forum: Desktop Environments
---

### Post by hyde200j on 2006-03-08
Hi everyone,

I did a number of administrative things after installing Breezy today.  These include installing Java, adding a number of repositories to synaptic and updating ubuntu.  When rebooting afterwards, two more entries were added to the grub menu.  

Originally there was "ubuntu, kernel 2.6.12-9-386" and its recovery mode.  2.6.12-10-386 entries are now there.
I really only want the one of these.  Aside from removing the entry from /boot/grub/menu.lst, is there something else I should do??  Very new to linux.

Searching for any info on this was unsuccessful, hence my post.

Thanks

---

### Post by Sutekh on 2006-03-08
Did you boot with the newer kernel from the GRUB menu (2.6.12-10-386)?  Is everything working ok with that new kernel?

If so then you are safe to delete the old one

Open up Synaptic (in the System -> Administration Menu) and Search for a package called **linux-image-2.6.12-9-386**.  When you find it you can completely remove it.  Synaptic will update the GRUB menu for you too.

---

### Post by nahas on 2006-03-08
[QUOTE=hyde200j]Hi everyone,

I did a number of administrative things after installing Breezy today.  These include installing Java, adding a number of repositories to synaptic and updating ubuntu.  When rebooting afterwards, two more entries were added to the grub menu.  

Originally there was "ubuntu, kernel 2.6.12-9-386" and its recovery mode.  2.6.12-10-386 entries are now there.
I really only want the one of these.  Aside from removing the entry from /boot/grub/menu.lst, is there something else I should do??  Very new to linux.

Searching for any info on this was unsuccessful, hence my post.

Thanks[/QUOTE]

Hi,
   Thats the only thing u should do.
regards
Nahas

---

