---
title: "Shutdown--doesn't"
date: 2009-06-23
forum: General Help
---

### Post by JohnMoore on 2009-06-23
I'm unable to shutdown using any of the graphical means.  The _best_ thing that happens if I try is that the interface will completely freeze, excepting the mouse pointer (and I thought I left that with Windoze).  Often, the system will just ignore the button-press.

If I open a terminal and "sudo shutdown now", the system will close running apps out in an orderly manner--but then bring up the menu screen from a "recovery" boot.  Once I hit that, I can do a three-finger-salute, and it will finish shutting down, but -- it will restart, not shut down.

Has anyone ever experienced anything like this?  Any suggestions where to look for a problem?

TIA :confused:

---

### Post by Sub101 on 2009-06-23
The normal shutdown command is:

```
sudo shutdown -h now
```

---

### Post by JohnMoore on 2009-06-24
I've done man shutdown, and I'm actually sending the "power down" (-P) option.  I was concerned about _ever_ asking for a "halt."  On some systems with which I've worked in the past, that's not something to be done except in extreme emergency.  I saw it done once, and it took two days of hard work to get the system back up and online again.  Of course, the reason for the halt was a major disk failure, but...let's just say that I'll try everything else first.

Anyway, do you have any idea why the apps behind the various shutdown buttons no longer work?

---

### Post by ~sHyLoCk~ on 2009-06-24
I always did ```
shutdown -hP now
``` in debian/ubuntu. However just simple ```
shutdown -h now
``` works for me in arch.

---

