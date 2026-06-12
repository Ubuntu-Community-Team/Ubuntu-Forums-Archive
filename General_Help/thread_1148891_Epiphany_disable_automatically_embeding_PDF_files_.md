---
title: "Epiphany: disable automatically embeding PDF files with Adobe Reader 9.1"
date: 2009-05-04
forum: General Help
---

### Post by m83 on 2009-05-04
Recently, when I made some upgrades, Adobe Reader 9.1 was installed (I had Adobe Reader 8 ). Now, the update automatically put the plugin into Firefox and geko-enabled apps so that the PDF files open inside the browser window. Previously the PDF files were downloaded and opened with Evince in another window not inside the browser. I want this behaviour back. In Firefox I found out how to disable the Adobe Reader plugin, but not in Epiphany. Please advise. Thanks.

---

### Post by m83 on 2009-05-14
I solved it.

[LIST]
[*]Edit the file [FONT="Lucida Console"].gnome2/epiphany/mozilla/epiphany/pluginreg.dat[/FONT]

[*]find the lines that contain something like this:

```
/usr/lib/mozilla/plugins/nppdf.so:$
:$
1240483090000:1:5:$
The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.:$
Adobe Reader 9.1:$
```
[*] change the line [FONT="Lucida Console"]1240483090000:1:5:$[/FONT] to [FONT="Lucida Console"]1240483090000:1:4:$[/FONT] (notice that the 5 became 4).
[/LIST]

---

