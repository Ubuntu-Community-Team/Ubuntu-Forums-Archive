---
title: "Is it normal for my xorg.conf to be totally empty?"
date: 2009-02-13
forum: General Help
---

### Post by Dieseler on 2009-02-13
This is a brand new install, Opened it and there is nothing in it.
Intrepid 8.10.

---

### Post by insilico on 2009-02-13
Install a video driver first perhaps? e.g. Nvidia or ATI drivers

---

### Post by Dieseler on 2009-02-13
I have the openchrome installed as far as I know.

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

---

### Post by Alterax on 2009-02-13
Relax.  As it turns out, the latest version of Xorg has autoconfiguration, where it finds out what it can work with when it's initiated rather than depending on a file.

Anything you manually add to the file will override what xorg finds through autodetect.

---

### Post by Dieseler on 2009-02-13
Thats wonderful.
Thanks!
Solved.

---

