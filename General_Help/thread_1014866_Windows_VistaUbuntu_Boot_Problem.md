---
title: "Windows Vista/Ubuntu Boot Problem"
date: 2008-12-18
forum: General Help
---

### Post by abarthle on 2008-12-18
Hello all! I got a little problem I hope you guys can help me with. I decided to dual boot my computer with Ubuntu. I Shrank my harddisk to make space for the Ubuntu install and everything went fine. I played around with it and decided I wanted to go back into Windows. I then resized my hard drive and erased my Ubuntu from the the hard drive. The only problem now is, the GRUB doesn't come up at start-up and Windows Vista doesn't automatically load. I'm attempting to re-install Ubuntu so maybe I can get back into windows, but I'm not sure what to do from there. Any idea's how I can get back into automatically having Windows boot up? I would like to have it auto boot and be able to remove Ubuntu.

Any help would be appreciated!
Thanks!

---

### Post by _noob_ on 2008-12-18
> **abarthle said:**
> Hello all! I got a little problem I hope you guys can help me with. I decided to dual boot my computer with Ubuntu. I Shrank my harddisk to make space for the Ubuntu install and everything went fine. I played around with it and decided I wanted to go back into Windows. I then resized my hard drive and erased my Ubuntu from the the hard drive. The only problem now is, the GRUB doesn't come up at start-up and Windows Vista doesn't automatically load. I'm attempting to re-install Ubuntu so maybe I can get back into windows, but I'm not sure what to do from there. Any idea's how I can get back into automatically having Windows boot up? I would like to have it auto boot and be able to remove Ubuntu.

Any help would be appreciated!
Thanks!

Well you may just have to reformat and reinstall windows.

---

### Post by caljohnsmith on 2008-12-18
If you have your Windows Vista Install CD, how about booting that, go to the command line, and run:
```
bootrec /fixmbr

```
And that should allow you to boot directly into Vista, assuming you don't have any issues with Vista. If you don't have a Vista Install CD, you can instead boot your Ubuntu Live CD (install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
That will install a Windows type MBR to your sda drive, i.e. it is equivalent to doing the "bootrec /fixmbr" command. How about giving one of those two methods a shot and let me know how it goes. :)

---

### Post by sPiN1 on 2008-12-18
I had this problem and there's a few options, keep ubuntu on a partition, you cna make the ubuntu partition ~3gb so it's almost like you don't have it. You can completely reformat your windows vista, or you can try what caljohnsmith said. any of those will work.

---

