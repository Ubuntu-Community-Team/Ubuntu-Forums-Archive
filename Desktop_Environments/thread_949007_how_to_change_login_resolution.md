---
title: "how to change login resolution?"
date: 2008-10-15
forum: Desktop Environments
---

### Post by jrecortel on 2008-10-15
hello.i installed ubuntu hardy on my pc.my pc's video card is nvidia gforce fx5500.in login screen, the resolution is 1280x1024@60hz.i want to change it into [email]1024x768@75hz.how[/email] can i change the login resolution?any help is greatly appreciated.thanks in advance.
btw,im a new linux user.

---

### Post by atheon on 2008-10-16
Hi. Had the same problem.
Check out this thread : [http://ubuntuforums.org/showthread.php?t=642192](http://ubuntuforums.org/showthread.php?t=642192)

Cheers.

---

### Post by greatscott on 2008-11-08
> **atheon said:**
> Hi. Had the same problem.
Check out this thread : [http://ubuntuforums.org/showthread.php?t=642192](http://ubuntuforums.org/showthread.php?t=642192)

Cheers.
This didn't work for me.

Here is what did.

```
sudo gedit /etc/gdm/Init/Default
```

Go the end of the file and add this before the exit 0 line:
```
xrandr -s 1280x1024
```

Now the resoultion of GDM will be 1280x1024.

---

### Post by hictio on 2008-11-08
Sorry, but I don't understand, once you are logged in, the resolution of your Gnome desktop is Ok, but only the resolution of the login screen is FUBAR?
Is that so?

---

### Post by shazel on 2008-11-08
yes it is true

---

