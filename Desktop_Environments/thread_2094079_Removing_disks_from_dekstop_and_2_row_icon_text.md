---
title: "Removing disks from dekstop and 2 row icon text"
date: 2012-12-12
forum: Desktop Environments
---

### Post by netrick on 2012-12-12
Hey, I'm currently a Lubuntu user but I want to migrate to xubuntu as it's more polished. However there are 2 things that destroy the whole xubuntu beautyness for me. So i want to know how to get rid of them. I'm not afraid of file editing.

1) How to remove ALL disk icons from desktop (all, mounted, not mounted, pendrives etc)?

2) How to make the icon's text to be 2 row like in every other desktop? Because I don't like that "My appli...".

Thanks in advance!

---

### Post by LewisTM on 2012-12-12
Hi netrick and welcome to Xubuntu!

1) Right-click on the desktop -> Desktop Settings -> Icons -> Uncheck Removable Devices

2) There might be a magic setting in the ~/.gtkrc2.0 file, I don't know. What works for me is to insert a newline character where I want to create a new row. Put the cursor next to the desired word, press Ctrl-Shift-u, type 000a then Enter.

Cheers!

---

### Post by LewisTM on 2012-12-12
Well well, I just found the magic setting.
Press Alt-F2 and run this command
```
leafpad .gtkrc-2.0
```
Insert this text
> style "xfdesktop-icon-view" {
XfdesktopIconView::ellipsize-icon-labels = 0
}

Save the file, logout and log back in.
The full text should now be visible!

---

### Post by netrick on 2012-12-12
Big thanks mate!

---

