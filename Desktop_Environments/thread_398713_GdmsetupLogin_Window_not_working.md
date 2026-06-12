---
title: "Gdmsetup/Login Window not working"
date: 2007-04-01
forum: Desktop Environments
---

### Post by StylusEcho on 2007-04-01
Hi guys,

Whilst I was fiddling around in Login Window settings, I accidentally turned on XDMCP. So instead of the login screen, the XDMCP thing would come up instead.

So I went into superuser mode, and edited /etc/gdm/gdm.conf. *slaps forehead*

The login screen would then work, but i'd get this when attempting to execute gdmsetup aka Login Window.

```
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
^X  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

```

Your help would be much appreciated. I am new to Linux, but so far, I think Ubuntu is better than Vista :)

---

### Post by alien21010 on 2007-04-01
Well without the gdm.conf file you're kind of hosed.  See if you can't boot into the live cd and then pull the conf file off of the live cd...  You're going to have to mount your hard drive.  Once you get the gdm file restored, then post the error output.

---

### Post by StylusEcho on 2007-04-01
I think I fixed it by reconfiguring Xserver-xorg :)

---

### Post by Storymaker81 uhuruman on 2008-01-30
Hi I have the same problem. Ubhuntu goes to this xdmcp mode. I cant seem to find my login window either, even if i turn off xmdcp in gdmsetup. ANy way to get my standard login back?

---

