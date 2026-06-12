---
title: "Graphical artifacts and tearing"
date: 2008-08-11
forum: Desktop Environments
---

### Post by spintriae on 2008-08-11
I've included a screenshot of what I'm dealing with, hosted on imageshack because the "manage attachments" dialog on this forum has crashed my desktop the last 3 times I tried! It's been doing this all morning, I've done nothing to provoke it: changed nothing; installed nothing. It works for a little while at startup and begins glitching after a few minutes. Please help me troubleshoot this, I've got a lot of work to do.

[[IMG]http://img120.imageshack.us/img120/8571/failul2.th.png[/IMG]](http://img120.imageshack.us/my.php?image=failul2.png)

---

### Post by spintriae on 2008-08-11
Any ideas? Any other info I should post? Config files I should dump? This is ridiculus.

---

### Post by obx-jdt on 2008-08-11
Let your graphic card "auto detect". Artifacts & tearing is usually cause by setting your FPS too high, or not using the correct refresh rate. If you use Nvidia, type ```
 nvidia-settings
``` in the term. You may need to install it ```
sudo apt-get install nvidia-settings
``` If you use ATI, sorry, I can't help you:(

---

### Post by spintriae on 2008-08-12
Hi obx-jdt, thanks for your reply. I should have mentioned that the video card it a Voodoo3. Xubuntu detects it just fine and offers only one refresh rate. I really believe it's the OS because I reinstalled Xubuntu on another partition and it's been working fine. I didn't want to have to do that but my computer crashed so many times yesterday that it corrupted my harddrive:

```
[   95.455655] eth1: no IPv6 routers present
[  102.118019] EXT3-fs error (device hdd1): ext3_check_descriptors: Block bitmap for group 442 not in group (block 148701184)!
[  102.135809] EXT3-fs: group descriptors corrupted!
[  209.035595] EXT3-fs error (device hdd1): ext3_check_descriptors: Block bitmap for group 442 not in group (block 148701184)!
[  209.037360] EXT3-fs: group descriptors corrupted!
[  218.566903] EXT3-fs error (device hdd1): ext3_check_descriptors: Block bitmap for group 442 not in group (block 148701184)!
[  218.574347] EXT3-fs: group descriptors corrupted!
[  595.328828] kjournald starting.  Commit interval 5 seconds
[  595.344544] EXT3 FS on hdd1, internal journal
[  595.344695] EXT3-fs: mounted filesystem with ordered data mode.
```

This is the second time this has happened to me in a month and last time I lost a weeks worth of work. I've installed several versions of Ubuntu in that time and this one (Xubuntu 7.10) has been giving me the least amount of problems until these last couple of days. In that time, my system has crashed at least 40 times I assume because I've had two forced disk checks!

This is really unacceptable guys. Please help me troubleshoot this.

---

### Post by spintriae on 2008-08-12
Sorry to bump this guys, but despite claims that Ubuntu "just works," my problem hasn't magically fixed itself, which wouldn't be unreasable to me considering the number of times it has magically broke itself. The probability that one of those artitrary and indiscriminate changes might actually improve the system rather than hose it is fast approaching one. :)

In all seriousness, please help me out.

---

### Post by spintriae on 2008-08-12
Five hours later, back on page 2, problem still not magically solved. If nobody here can help me with my problem could somebody please direct me to a forum that can? Thanks.

---

### Post by spintriae on 2008-08-13
Day 3. Please help.

---

