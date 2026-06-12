---
title: "superkaramba in GNOME, no transparency"
date: 2006-03-09
forum: Desktop Environments
---

### Post by threethirty on 2006-03-09
ok I'm sure that this is not a normal problem, but I have some superkaramba themes that I *really* wanna run in GNOME.  Some look great (Kterroralert looks great), but there are some that have a transparent background and insted of being nice and clear they show up black.  and the terminal shows this
```
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3c005e3
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3c005e3
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3c005e3
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3c005e3
ImportError: No module named compact
------------------------------------------------------
What does ImportError mean?

It means that I couldn't load a python add-on for compact.theme
If this is a regular theme and doesn't use python
extensions, then nothing is wrong.
------------------------------------------------------

```

so what do you think?

---

### Post by taurus on 2006-03-09
Could it be because superkaramba is designed especially for KDE?  I am sure you can get gDesklets to behave the same way in Gnome...

---

### Post by threethirty on 2006-03-09
i couldnt find any themes for gDesklets, when I google searched it I got 2 sites, and none of them were helpful.  

Where can I get themes for gDesklets

---

### Post by blanks on 2006-03-09
Desklets are located here:
[http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

---

### Post by ComplexNumber on 2006-03-09
when you're trying to get gdesklets to work, remember to install all the gnome-python packages. i found that the gdesklets tarball/rpm/deb would install successfully, fbbut wouldn't run until i installed all the necessary python  and gnome-python packages.
also, add 'gdesklets start' to your sessions so that the gdesklets daemons starts whan you log on.

---

### Post by taurus on 2006-03-09
No need to include "start" in your session after gdesklets.  Just add "gdesklets" is good enough...

---

### Post by davebgimp on 2006-04-03
[QUOTE=taurus]Could it be because superkaramba is designed especially for KDE?  I am sure you can get gDesklets to behave the same way in Gnome...[/QUOTE]

Actually, I'm running Kubuntu 5.10 and have the exact same problem, black with no transparancies. I've found the problem went away when I stopped using a flat background on my desktop.

Check this post: [http://ubuntuforums.org/showthread.php?t=42840]("http://ubuntuforums.org/showthread.php?t=42840")

---

