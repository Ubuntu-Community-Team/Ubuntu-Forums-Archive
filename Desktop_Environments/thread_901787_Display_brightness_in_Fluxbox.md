---
title: "Display brightness in Fluxbox?"
date: 2008-08-26
forum: Desktop Environments
---

### Post by SomeGuyDude on 2008-08-26
Hey folks.

In my pursuit of making my notebook last long enough for me to go to class without a power cable, I'm trying Fluxbox. Unfortunately, I cannot find any way to dim the display. There's no monitor settings applet, nothing in the GNOME Control Center, nuthin'.

What do I do?

---

### Post by itzmiko on 2008-12-02
ditto.  any solution?  The brightness function keys on my keyboard worked fine when running gnome, but after switching to fluxbox they dont.  fluxbox users SOL?

---

### Post by darthshak on 2008-12-05
Yup same here.
I tried installing tpb on fluxbox and adding to ~/.fluxbox/startup, but to no avail.

I also tried directly writing to the brightness file in /proc/acpi but no luck either. Do the unstable releases fix this issue?

I have a thinkpad T61 (and yes, the wiki was not much help either except for saying "It doesnt work on fluxbox")

---

### Post by iggykoopa on 2008-12-05
have you tried the program xbacklight?

---

### Post by Ahadiel on 2008-12-05
Afaik you can run gnome-settings-daemon (if you had gnome previously configured). I used to do this when I ran openbox.

---

### Post by darthshak on 2008-12-05
Well, running xbacklight gives the following message:

```

darthshak@T61:~$ xbacklight -dec 10%
No outputs have backlight property

```

That said, gnome-settings-daemon doesnt open on fluxbox for some odd reason (at least for me).

---

### Post by frankob on 2009-07-03
gnome-power-manager did the trick for me. Including suspend mode when I close the lid and all the other gnome-power-manager options working just fine. If you still have gnome installed (or at least some of its components) give it a try.

---

