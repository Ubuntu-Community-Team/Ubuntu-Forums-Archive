---
title: "Ubuntu is not loading"
date: 2009-06-18
forum: General Help
---

### Post by farazafzal on 2009-06-18
Hello genious' around,

I was using WinXP and ubuntu 8 which i upgraded to 9 (latest) quite safe and sound. today ubuntu froze the desktop and after restarting system when i selected the Ubuntu from the OS selection it starts loading for a couple of seconds and then directly jumps to  grub menu.. prompting  as grub>.. 
i tried like anything but of no use. for example root (hda,0) and bla bla.

ANy help??

---

### Post by spiderbatdad on 2009-06-18
have you tried something like the method used in this thread?
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by farazafzal on 2009-06-18
Yeah yeah I tried that... 
No luck..

I was not using grub for OS loading. It was like I had WinXP installed and then i installed Ubuntu as an application within XP environment. Which says that you can remove Ubuntu whenever u want. So i had list of both OS liek we have in WinXP normally. Select ubuntu and it works... but after i shut it down by long pressing power key all is gone.. 
any Hint?

---

### Post by spiderbatdad on 2009-06-18
sounds liike the file system got corrupted by unclean shutdown. I believe you should try running chkdsk /r from the windows recovery partition.
Ubuntu/Wubi cannot be booted after unclean shutdown. See here: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

