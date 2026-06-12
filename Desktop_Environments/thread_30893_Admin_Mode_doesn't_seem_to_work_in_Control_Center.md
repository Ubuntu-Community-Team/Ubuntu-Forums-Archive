---
title: "Admin Mode doesn't seem to work in Control Center"
date: 2005-04-30
forum: Desktop Environments
---

### Post by mortram on 2005-04-30
trying to use "Administrator Mode" doesn't seem to do anything, and I can't configure login options without it...?

---

### Post by Takis on 2005-04-30
Are you a sudo user, and are you using your own password?

---

### Post by mortram on 2005-05-01
yes and yes

i tried using both my password and the root password (gave root a new password with sudo passwd root)

??

weirdness

---

### Post by mortram on 2005-05-01
Possibly a bug...

The options are available to me if I choose 'Settings' from the System Access icon in the lower left, but not if I launch Control Center from the KDE Menu.

---

### Post by Takis on 2005-05-01
Odd. I've got nothing.

---

### Post by dave9191 on 2005-05-01
The fix has been mentioned on the forums. Clear your kde chache and enable root login in the kde config file. 

[http://ubuntuforums.org/showthread.php?t=30513&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=30513&page=1&pp=10)

1) Delete everything in /var/tmp/kdecache (the one with your username in it)
2) Check the /etc/kde3/kdm/kdmrc file. Somewhere in the file it says "RootLogin" - this should be set to true.

---

