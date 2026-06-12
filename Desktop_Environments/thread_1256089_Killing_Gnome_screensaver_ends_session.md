---
title: "Killing Gnome screensaver ends session"
date: 2009-09-02
forum: Desktop Environments
---

### Post by springer_a on 2009-09-02
Hi,

when switching users in ubuntu, the session of the previous user is locked by gnome-screensaver. What I tried now as I didn't have the password of the other user was to unlock the session by killing the gnome-screensaver process as root. But instead of unlocking it the whole session of the other user was ended. 

I'm wondering now if this is some weird bug or a security feature. Does anyone know more?

---

### Post by asmoore82 on 2009-09-02
I would bet it's a feature.

If you have root access you can unlock it by backing up, changing, using, and restoring that user's password:

```
**root#** cp /etc/shadow /root/shadow.backup
**root#** passwd *thatuser*
[COLOR="Blue"]#then unlock with the password you just set
#then restore their old password with:[/COLOR]
**root#** cat /root/shadow.backup >/etc/shadow
```

---

### Post by springer_a on 2009-09-02
Thanks a lot for the idea. Should work but I guess it is a bit overkill to rewrite the shadow file twice, just because I don't want to bother the other user to come to the computer and enter the password. Nevertheless thanks for the reply.

---

### Post by asmoore82 on 2009-09-02
another [better?] option...

```
**root#** export DISPLAY=:0
**root#** sudo -u *thatuser* gnome-screensaver-command -d
```

^works great but it's easy to forget that `export` magick.

---

### Post by springer_a on 2009-09-02
Ok, that should be the more proper way to do it. I consider my problem as solved now.

---

