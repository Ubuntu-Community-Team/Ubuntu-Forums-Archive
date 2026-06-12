---
title: "Authentication Failed Errors At Login, Can't Type In Username"
date: 2007-11-10
forum: Desktop Environments
---

### Post by hiflyact on 2007-11-10
I'm running Ubuntu 7.10.   I had the same password for the default keyring as well as the system login.  I had a auto-login set up but every time the wireless card tried to get the key to connect to my network I had to enter the password to unlock it.

 I installed this:  sudo aptitude install libpam-keyring, then put "@include common-pamkeyring" in the etc/pam.d/gdm file.  

but I was still having to enter password for the default keyring.  I read that for that to work, it required you to manually login at startup and then it would take that password and unlock the keyring (provided the passwords were the same).  So, unchecked the "auto-login" box and restarted.  

I deleted the gdm file and restarted and that let me login and everything seemed ok.  I then deleted the /etc/pam.d directory thinking that I could reinstall the libpam-keyring, but no that didn't work.  I think this was a big mistake. 

Now all I get from Ubuntu is a "Authentication Failed" logon screen that I can't get rid of and it won't let me type in my username to login.  I can ctrl-alt-F1 and get to the command line but it says "login incorrect maximum number of tries exceed (5) when I only try to log in once.  I don't know what to do or how to fix this?  Did I just hose my whole Ubuntu installation?

---

### Post by icheyne on 2007-12-30
[http://ubuntuforums.org/showthread.php?p=3605925](http://ubuntuforums.org/showthread.php?p=3605925)

---

### Post by palomuuri on 2008-03-28
I'm so glad I found this post. I did the exact same thing!

Jerald

---

