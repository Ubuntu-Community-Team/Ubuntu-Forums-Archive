---
title: "ubuntu multi monitor setup"
date: 2009-02-22
forum: General Help
---

### Post by aquanuke1 on 2009-02-22
Ive just installed the latest ubuntu and having problems setting up a quad monitor setup.

I have two video cards one agp one pci both out to two monitors.

From a fresh Ubuntu install I have one video card working displaying two monitors but mirrored output and locked at max res of 800x600.

How can I set up a 4 sceen monitors with individual screens.

---

### Post by komputes on 2009-02-24
:-k(I'm assuming you're using hardy or intrepid)
You may just have an X configuration problem, reboot into recovery mode (press ESC right after POST to get the GRUB menu, and choose the recovery kernel option from the GRUB menu). Choose "xfix" from the blue recovery menu. Wait a bit then select "Resume" from the menu.

If this doesn't work there may be a specific solution for your hardware, if you run the following command in a terminal, you can then attach the resulting file from your home folder.

```
$ lspci -nn
```

---

