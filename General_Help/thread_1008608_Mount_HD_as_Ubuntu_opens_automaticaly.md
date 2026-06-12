---
title: "Mount HD as Ubuntu opens automaticaly?"
date: 2008-12-11
forum: General Help
---

### Post by sandman3838 on 2008-12-11
Hello

Quick question...

I have an additional hd, it's a NTFS format and I use it a lot.
Is it possible to have the HD mount as my desktop opens up instead of doing it manually?

Where in Ubuntu 810 should I go?

Thank you all!

---

### Post by 2hot6ft2 on 2008-12-11
Applications>System Tools>NTFS-Configuration Tool

If it's not there then install it in System>Administration>Synaptic Package Manager by searching for ntfs-config and install it.

Make sure the drive you want to auto mount is UNMOUNTED then open up the NTFS-Configuration Tool then select the drive you want and click Apply in the next window select enable write support for which ever it is (internal or external) and click OK. All done

Now it will auto mount with read/write support after you reboot.

---

### Post by tuxxy on 2008-12-11
You could edit you fstab

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by sandman3838 on 2009-05-04
Sorry I should have put in a reply earlier!

Thank you it's been working for some time.

Applications>System Tools>NTFS-Configuration Tool

---

