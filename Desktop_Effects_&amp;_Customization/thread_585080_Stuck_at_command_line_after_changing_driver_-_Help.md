---
title: "Stuck at command line after changing driver - Help!"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by JGT on 2007-10-21
Hi

I have an Intel GMA 3100 (on-board graphics). Ubuntu 7.10 didn't detect it (I upgraded from 7.04), i.e. no Compiz. I choose one of the Intel options from the new menu. I choose incorrectly (something like i810), and now I am stuck at the command line when I reboot. Help!

Can I recover from here? If so, please tell me how. I don't have a separate home partition, so I want to avoid a clean reinstall.

Please note that I'm still a Linux novice!

---

### Post by kast on 2007-10-21
sudo dpkg-reconfigure xserver-xorg

Just follow on screen questions and you should able to restore or reconfigure to previous state.

---

