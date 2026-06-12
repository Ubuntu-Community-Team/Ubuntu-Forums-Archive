---
title: "disable bold fonts for in terminal"
date: 2007-03-31
forum: Desktop Environments
---

### Post by synss on 2007-03-31
I use a dark background in GNOME Terminal 2.16.1 and colored ls but the output is ugly b/c bold is used on top of the colors, bold is also ugly in vim.

In short, I want to get rid of the boldface in my terminal, setting
```

XTerm*wideChars:   false
XTerm*boldMode:    false
XTerm*boldColors:  false
XTerm*colorBDMode: false
XTerm*colorBD:     yellow
XTerm*font: 7x14
XTerm*boldFont: 7x14

```
in ~/.Xdefaults followed by
```
xrdb -merge .Xdefaults
```
does not help.

---

