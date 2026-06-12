---
title: "wont login..."
date: 2009-02-04
forum: Desktop Environments
---

### Post by huggies15 on 2009-02-04
hi,
i just installed a version of xfce on my 2g eee following the steps from here:
[http://forum.eeeuser.com/viewtopic.php?id=55247](http://forum.eeeuser.com/viewtopic.php?id=55247)
i then installed adamms kernel, did a restart and everything was working fine. i then downloaded and installed open office restarted again fine. finally i tried to install songbird - the download failed due to lack of space, so i restarted the pc. upon the login screen i typed my name and p.w. as normal and the screen went black, looked like loading up and then returned to the login screen. i turned the pc off and on again, and same problem...
does anyone have any idea whati can do other than reinstall everything, or is that the easiest/quickest fix?!
cheers.
Steve Hughes

---

### Post by Hooya on 2009-02-04
Can you boot to a recovery console?

---

### Post by huggies15 on 2009-02-05
yeah, ive got to a screen with options saying:
resume
clean
dpkg
fsck
root
xfix

wouldnt knwo what to do or where to start tho...
cheers,
Steve

---

### Post by taurus on 2009-02-05
> **huggies15 said:**
> yeah, ive got to a screen with options saying:
resume
clean
dpkg
fsck
**[COLOR="Blue"]root[/COLOR]**
xfix

wouldnt knwo what to do or where to start tho...
cheers,
Steve

Scroll down and highlight the root shell.  Then, clean out the cache to make some room on your root filesystem, /.

```
apt-get clean
apt-get autoremove
df -h
```
Type exit to reboot.

Don't forget to empty your trash bin after you log back in with your account.

---

### Post by huggies15 on 2009-02-05
Worked a treat, thank u so much :)

---

