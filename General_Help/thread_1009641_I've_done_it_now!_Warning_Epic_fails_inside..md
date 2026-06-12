---
title: "I've done it now! Warning: Epic fails inside."
date: 2008-12-12
forum: General Help
---

### Post by Youbuntoo44 on 2008-12-12
Aw dang. I'm running a super old version of Ubuntu on my old Dell laptop. So I wanted to upgrade to the latest 8.04 (But I attempted 7.10) and it failed due to insufficient hard drive space. EPIC FAIL: I deleted as many programs as I could find to make room for the upgrade, assuming that most space would be restored after everything settled. I DELETED the update manager! No prob, I'll use Syaptic. Whoops! That's gone too. I'll spend some time with the terminal. Gone. Ahh! I have 7.10 on disk, and want to download it. Help me restore my system!

---

### Post by mkvnmtr on 2008-12-12
Put the disk in your computer. Boot from the disk. Click on the install icon that comes up on the desktop. In about 40 minutes you will have Ubuntu 7.10 installes again. You could do the same thing if you get a 8.04 disk.

---

### Post by adult swim on 2008-12-12
try running from a terminal
```
sudo apt-get install update-manager
```

---

### Post by tgalati4 on 2008-12-12
You may get a working system, but a better course would be to boot the Live CD, grab your important data and put it on a thumb drive. Wipe the disk and start fresh.

It might be quicker as well.  My fastest Linux Mint install was 17 minutes.  Western Digital Raptors help.

---

### Post by kuhlbeans on 2008-12-13
> **tgalati4 said:**
> You may get a working system, but a better course would be to boot the Live CD, grab your important data and put it on a thumb drive. Wipe the disk and start fresh.

This would also be my advice.  Also, when installing, make sure you setup a separate partition for your home directory or one for data (as in /data), so if this ever happens again all your personal data (and application settings if you do the whole home directory) will not be affected.

---

