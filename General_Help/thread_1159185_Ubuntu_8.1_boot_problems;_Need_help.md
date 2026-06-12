---
title: "Ubuntu 8.1 boot problems; Need help"
date: 2009-05-14
forum: General Help
---

### Post by neela on 2009-05-14
I have a Ubuntu 8.1 (Wubi install) / XP dual boot laptop. When the machine hungup at boot time, I powered it down to restart the booting process. When it came back up, the boot process stopped at the grub screen. When I give commans like root(hd0,1) and setup(hd0), i get errors like "Error 27: Unrecognized command". Don't know how to boot into ubuntu from here. Any help is appreciated. Thanks. Neela

---

### Post by neela on 2009-05-14
The problem got worse..
I logged onto the XP side and tried to open the ubuntu folder. I got an error saying that the file is corrupted -- probably because it is the ext2 or ext3 file system. Now I downloaded the est2fs_1_11a utility that lets me see ext2/ext3 files from the windows side. The goal was to recover some of my personal files before i trash this installation and reinstall on a native partition rather than a wubi install. Subsequently when I rebooted windows, chkdisk ran and said it needed to fix some disk errors -- now this is a less than 3wk old laptiop -- don't know why there should be disk errors.

Seemingly, I lost the wubi install just like that..
Or did I not?
When i try to boot into Linux, I still come upto the grub prompt. I can't see any hidden files in windows c:\ as some people have suggested on the forums.. But in the ubuntu directory i see docs, winboot and install directories and a menu.lst file in the winboot directory among others.

Can anyone help me recover my personal data from the linux side please? I would really appreciate it. Its at least about 3 weeks of very hard work..

Thank you very much.

---

