---
title: "Boot pausing"
date: 2009-06-03
forum: General Help
---

### Post by wtrsltnk on 2009-06-03
Hi all,

I have a really itchy problem with my ubuntu installation. It started a few weeks before ubuntu 9.4 was released and I thought it would be gone after installing 9.04 but it didn't. I searched the Internet several times now, but without results. There were some similar problems but they differ slightly. The problem is as follow:

While booting ubuntu with spash screen, at around 30% the bootloader pauses. After something like 5 seconds the splash screen is removed(without touching the keyboard) an the log is shown. The log says:

Activating swapfile swap                        [ OK ]

after that, nothing. I tried waiting for it to continue but without result. The first time i though I had the solution from the internet I cleared my /tmp because there where like a million small files. This did work a little bit because now after a few minutes the booting continued with:

Starting AppArmor                               [ OK ]
blalblabla...
...

Now the boot has a pause of about 5 minutes, my /tmp is practically empty and I am running out of ideas to fix this. Is there any one with a idea what the problem might be? Your help is greatly appreciated, I only use the suspend function now because booting take too much time.

grtz Wouter

---

### Post by VMC on 2009-06-03
From a terminal type ```
df -T
``` to make sure your not running low on disk space.

Also you can edit "/boot/grub/menu.lst" and remove the "splash" and "quiet" at the end of the "kernel" line to see where it may be having trouble.

You can also check messages at "System > Admin > Log file viewer"

---

