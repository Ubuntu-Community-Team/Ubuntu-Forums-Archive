---
title: "No X"
date: 2009-02-25
forum: Desktop Environments
---

### Post by BiynaYahu on 2009-02-25
I am running a Dell Inspiron 1501.  Yesterday I switched my wifi driver over to the STA proprietary Broadcom driver.  Upon doing so, while it still connected to my router, I had no internet.  Eventually I updated my file which controls the loading of network interfaces, and added a line to it to bring up eth1 the new name of my WIC.  Upon restarting my computer X Window Manager no longer would load.  I read this thread: [http://ubuntuforums.org/showthread.php?t=591664&page=2](http://ubuntuforums.org/showthread.php?t=591664&page=2) .  I tried to do the advice given in post #17 with ext3 replaced with jfs (my filesystem type).  It gives me the error "wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error".  I'm completely lost.  I think in the end what I'm going to do is copy my home folder, or at least what I can fit onto a usb stick, and then do a fresh install (I want to give myself a 4GB swap).  Anyway, I know this is like four questions in one.  So, what I wan now is help figuring out what's wrong with X, for my own knowledge and growth.  Then I'll start a new thread in the appropriate category, and link this thread.  Thank you in advance.

---

### Post by dbbolton on 2009-02-25
> **BiynaYahu said:**
> I am running a Dell Inspiron 1501.  Yesterday I switched my wifi driver over to the STA proprietary Broadcom driver.  Upon doing so, while it still connected to my router, I had no internet.  Eventually I updated my file which controls the loading of network interfaces, and added a line to it to bring up eth1 the new name of my WIC.  Upon restarting my computer X Window Manager no longer would load.  I read this thread: [http://ubuntuforums.org/showthread.php?t=591664&page=2](http://ubuntuforums.org/showthread.php?t=591664&page=2) .  I tried to do the advice given in post #17 with ext3 replaced with jfs (my filesystem type).  It gives me the error "wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error".  I'm completely lost.  I think in the end what I'm going to do is copy my home folder, or at least what I can fit onto a usb stick, and then do a fresh install (I want to give myself a 4GB swap).  Anyway, I know this is like four questions in one.  So, what I wan now is help figuring out what's wrong with X, for my own knowledge and growth.  Then I'll start a new thread in the appropriate category, and link this thread.  Thank you in advance.
Did you save a backup of your /etc/fstab file?

---

### Post by BiynaYahu on 2009-02-25
No.

---

### Post by dbbolton on 2009-02-25
> **BiynaYahu said:**
> No.
Ok, are you able to boot into recovery mode?

---

### Post by BiynaYahu on 2009-02-25
I'm sure I can, and when X fails it drops me into command prompt, and I'm actually running on a live CD right now.  As per this thread I have just finished altering my partitions: [http://ubuntuforums.org/showthread.php?t=1080663](http://ubuntuforums.org/showthread.php?t=1080663) .  Also, I am no longer planning a reinstall.  I'm going to boot into recovery mode now.

---

### Post by BiynaYahu on 2009-02-25
Should I select xfix, or root?

---

### Post by dbbolton on 2009-02-25
Try the xfix first. If it doesn't work, we can try logging in to the root account to fix it manually.

---

### Post by BiynaYahu on 2009-02-25
Hey!  That's a good boot.  Thanks friend.

---

