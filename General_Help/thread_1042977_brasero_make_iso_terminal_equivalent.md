---
title: "brasero make iso terminal equivalent"
date: 2009-01-18
forum: General Help
---

### Post by alphaniner on 2009-01-18
Does anyone know what command line & options brasero uses when writing a data project to iso with 'increased windows compatability'?  Or how to find out?  It always works for me, but I need to do it through the terminal.  As I understand it is just a front end for mkisofs or genisoimage.  I have tried to figure those out but I always end up with borked isos.  Thanks.

---

### Post by HalPomeranz on 2009-01-18
I'm not exactly certain what Brasero is doing, but when I use mkisofs on the command-line I always use the "-J" (Joliet) and "-r" (generate SUSP and RR records like "-R" and also squash UID/GID values) options.  This yields an image that works quite well across Linux/Windows/Mac.

---

