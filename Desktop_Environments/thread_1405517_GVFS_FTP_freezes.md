---
title: "GVFS FTP freezes"
date: 2010-02-12
forum: Desktop Environments
---

### Post by alex.rayu on 2010-02-12
I do websites work and for some time now have been using gvfs for ftp transport. I noticed that I periodically experience the following. When I copy a folder from FTP server to a Desktop, a copying process interface is displayed, and copying is frozen somewhere in the first 20-30Kb. Then, you can't close this dialog or cancel copying. The dialog stays even if you unmount the server. You actually have to kill and restart nautilus to fix this. Once this happened, it will happen most of the time until computer is restarted.

Can you help me out with it? What can be causing this? How can I diagnose?

Update: I think this can be the problem - [http://ubuntuforums.org/showthread.php?t=1010463](http://ubuntuforums.org/showthread.php?t=1010463)

This would render GVFS useless for web development. One timeout - and you need to restart Gnome. Any fixes?

---

### Post by Niva on 2010-02-13
Not sure why the hangups, I use Filezilla and haven't had any of the issues you mention, it's OSS works for both linux and windows.

---

### Post by alex.rayu on 2010-02-14
FileZilla works just fine. But the gnome GVFS that allows you to open an ftp as if it were a folder, behaves bad.

---

### Post by steelsteel! on 2010-09-06
> **alex.rayu said:**
> FileZilla works just fine. But the gnome GVFS that allows you to open an ftp as if it were a folder, behaves bad.

*confirmed* 2010, lucid 64-bit

Nasty behviour, i Tried to copy files between two different nas-ftp-servers.
A Mess!

---

