---
title: "Amarok: Even after installing amarok-xine, can't choose any engine except arts &amp; null"
date: 2005-05-25
forum: Desktop Environments
---

### Post by draxinusom on 2005-05-25
Even after I installed amarok-engines, I can't choose to use the xine or gstreamer engines (they don't show up in amarok's engine dropdown).  I've tried installing only amarok-xine, to no avail; the dropdown still only show arts (which it complains about when I select), and the null engine.  Please help if you can; I would dearly love to be able to use amarok with the xine engine, as it freezes regularly if I try use the arts engine.

---

### Post by thechitowncubs on 2005-05-26
restart your comp

---

### Post by ludi on 2005-05-26
[QUOTE=draxinusom]Even after I installed amarok-engines, I can't choose to use the xine or gstreamer engines (they don't show up in amarok's engine dropdown).  I've tried installing only amarok-xine, to no avail; the dropdown still only show arts (which it complains about when I select), and the null engine.  Please help if you can; I would dearly love to be able to use amarok with the xine engine, as it freezes regularly if I try use the arts engine.[/QUOTE]
 Check if you have this packages installed in your system (without any errors):
amarok-arts
amarok-engines
amarok-xine
amarok-gstream

Check your sound settings on Control Center.

---

### Post by draxinusom on 2005-05-27
I restarted my comp and the engines appeared.  Thanks, all; didn't know that the magic rebooting trick worked in Linux, too.  :?

---

### Post by Sarojin on 2005-05-30
That's a bug in amaroK 1.2.3 and lower; 1.2.4 was released recently, but I suppose we'll have to wait until Breezy for it.

---

