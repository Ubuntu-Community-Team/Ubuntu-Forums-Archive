---
title: "HP Scanjet 8250 and XSane issue"
date: 2009-03-12
forum: General Help
---

### Post by js@lloyd on 2009-03-12
Xsane is just shutting itself down after I click "scan".  It recognizes the scanner, because the scanner sounds like it's getting ready to scan, but then the program just closes out.  The 1st time I tried Xsane it actually restarted my computer.  I usually scan to a PDF document.

Thanks, 

JS

---

### Post by Peter09 on 2009-03-12
Run it from a terminal

```
xsane
```

see what error messages you get

---

### Post by js@lloyd on 2009-03-12
> **Peter09 said:**
> Run it from a terminal

```
xsane
```

see what error messages you get

(xsane:6328): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6328): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6328): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6328): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6328): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6328): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6328): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:6328): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

---

### Post by js@lloyd on 2009-03-12
Just hoping to find out if anyone has any suggestions in solving this problem.

Thanks,  JS

---

### Post by js@lloyd on 2009-03-14
Still looking for some help on this one.  Any suggestions would be appreciated.

Thanks,
JS

---

### Post by Peter09 on 2009-03-15
Try doing the same but using sudo

```
sudo xsane
```

note that you may get dire warnings but you can ignore those.

---

### Post by js@lloyd on 2009-03-15
> **Peter09 said:**
> Try doing the same but using sudo

```
sudo xsane
```

note that you may get dire warnings but you can ignore those.

Wow...never seen that warning before.  Have to admit, made me pretty hesitant to run that.

---

### Post by bo_n_tulsa on 2009-04-22
I've got almost the same exact issue.  Xsane will see the scanner and will go as far as scanning, but as soon as scanning seems to be completed, Xsane simply shuts down.
I tried running as root, but same thing happens.

I'm lost.

I might try just using the scanner in virtualbox, but would really rather be able to use in Ubuntu.

---

