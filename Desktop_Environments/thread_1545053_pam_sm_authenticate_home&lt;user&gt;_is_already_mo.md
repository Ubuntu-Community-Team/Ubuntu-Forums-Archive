---
title: "pam_sm_authenticate /home/&lt;user&gt; is already mounted"
date: 2010-08-03
forum: Desktop Environments
---

### Post by ghost_ryder35 on 2010-08-03
Problem:
I am trying to login from a remote location to my Ubuntu box.  If the screen saver is not active this is not a problem ( I can work on my workstation from the remote workstation).  When the screen saver is active I can not log in (when I try to unlock the screen saver it fails with "Unlocking Failed").  I get the following log lines in /var/log/messages when unlocking kde's screen saver fails.

```

Aug  3 09:42:37 penguin sudo: pam_sm_authenticate: Called
Aug  3 09:42:37 penguin sudo: pam_sm_authenticate: username = [Owner]
Aug  3 09:42:37 penguin sudo: pam_sm_authenticate: /home/Owner is already mounted

```

Machine configuration:
Ubuntu 10.04 x86_64 with the KDE Desktop Environment installed
Running KDE
/home/Owner encrypted with Ubuntu's default encryption
Running 'x11vnc' to connect to all ready running X session

For those about to ask, yes I am typing in the correct password to unlock the screen saver.

Any suggestions/comments welcome.

Thanks!

---

### Post by krunge on 2010-08-05
Some people are having trouble with "Shift" working properly for x11vnc in their environment.  They have to add "-xkb" to make it work properly.  Perhaps that is why your password login doesn't work(?)  You can search these forums for x11vnc+xkb for more info.

---

