---
title: "Startup/ log in problem"
date: 2015-03-01
forum: Desktop Environments
---

### Post by jos_carlos3 on 2015-03-01
I cannot log in when I turn on my laptop. It gets "stuck"  at the Xubuntu logo and the circle spinning. I am not an expert in the  matter.

It was caused when I tried to enable Num Lock at startup.  I installed numlockx, then edited /etc/gdm/Init/Default - showed up  a blank file - typing**:**

if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi[/SIZE]
[http://ubuntuforums.org/showthread.php?t=1694845 ]("http://ubuntuforums.org/showthread.php?t=1694845")

Then saved and reboot.

Thanks in advance.



OS**:**Xubuntu 14.04.2 LTS Trusty Tahr.

---

### Post by v3.xx on 2015-03-01
Xubuntu does not use 'gdm'.
[http://manpages.ubuntu.com/manpages/hardy/man8/gdm.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/gdm.8.html)

You should be running lightdm.
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by jos_carlos3 on 2015-03-01
Thank you, v3-xx

Took me through the right path.
[URL="http://askubuntu.com/questions/155679/how-to-enable-numlock-at-boot-time-for-login-screen/588576#588576"]
http://askubuntu.com/questions/155679/how-to-enable-numlock-at-boot-time-for-login-screen/588576#588576[/URL]

---

### Post by v3.xx on 2015-03-01
Good find :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

