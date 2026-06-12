---
title: "Panels reseting on boot!!!"
date: 2008-06-05
forum: Desktop Environments
---

### Post by XMAG on 2008-06-05
Hi,

First of all let me way I'm using ubuntu 8.04

I found a website on the internet where it was suggested that I could backup my panels configuration by keping a copy of ~/.gconf/apps/panel
directory. I wanted to try having one panel (like Mint or Windows) so I deleted my upper panel and reconfigured the bottom one. I'm so used to the gnome layout I quickly gave up the idea and wanted my panels back. I have them a bit customized, transparent, with some stuff removed on the bottom one and all my launchers on the top one, so it takes a while configuring all that back (20+ launchers centered on the upper panel) so I deleted the directory referred above and replaced it with a copy of my backup.

As I expected the panels didn't instantly change so I runned "killall gnome-panel" but there was still only one panel. So I thought of changing the runlevel with "sudo init 1" and as root did the same thing again. When I logged in to my account once more I found the panels not as they were before but as they where when I first installed Ubuntu 7.10, so I manually set them as they were before I deleted the top one.

The thing is every time I reboot or log in and out my panels appear as they were at first boot!!! I can't get them configured the way I want anymore because every time I reboot I'll have to do it again and again!

Any ideas why this is happening and how to stop it?

Thanks!

---

### Post by XMAG on 2008-06-05
[[IMG]http://img111.imageshack.us/img111/3712/capturadatelafi6.th.jpg[/IMG]](http://img111.imageshack.us/my.php?image=capturadatelafi6.jpg)

just a screenshot of the panels I used to have

---

### Post by XMAG on 2008-06-05
(how can I delete wrongly posted messages?)

---

