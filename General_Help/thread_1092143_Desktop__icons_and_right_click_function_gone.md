---
title: "Desktop  icons and right click function gone"
date: 2009-03-10
forum: General Help
---

### Post by superkret on 2009-03-10
Hi. I'd appreciate some help after messing up. I changed some things on my system, mainly deinstalling packages and removing start-up procresses. But I don't know what exactly I removed anymore.

Now, my Desktop icons are gone, but everything can still be accessed via Nautilus. Right-clicking on Desktop does nothing anymore.

So far, I've tried:
-gconf-editor -> apps -> Nautilus -> Show Desktop (Box is checked, unchecking, rechecking and restart did nothing)

-apt-get install ubuntu-desktop (it said, it's already installed, and did nothing.)

What else can I try? Thanks for some help.


EDIT: Sorry, I forgot: I run Intrepid with grub bootloader

---

### Post by byStanderone on 2009-03-10
...i'd assume you have grub, try recovery mode and start from there.

---

### Post by superkret on 2009-03-10
No, I've tried that out, too. But it didn't work. Is there nothing I can do?

---

### Post by Peter09 on 2009-03-10
Sounds like nautilus is not running.....

try in a terminal

```
nautilus&
```

---

### Post by superkret on 2009-03-11
Thanx a lot. That did it :)

It comes back up, however, I get this warning/error-message:

** (nautilus:3591): WARNING **: Unable to add monitor: Not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: »net usershare« returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by Peter09 on 2009-03-11
OK,
does nautilus come up now when you boot normally, or do you have to start it from a terminal every time.

Here is a thread with a fix for the user share problem.

[http://ubuntuforums.org/showthread.php?p=3781751](http://ubuntuforums.org/showthread.php?p=3781751)

---

### Post by superkret on 2009-03-13
The problem no longer exists. I reinstalled Ubuntu for a different reason (because I wanted to try out a cli install). Thank you for your help.

---

