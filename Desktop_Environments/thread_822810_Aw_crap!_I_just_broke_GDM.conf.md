---
title: "Aw crap! I just broke GDM.conf"
date: 2008-06-08
forum: Desktop Environments
---

### Post by joebrueske on 2008-06-08
I think I broke the GDM.conf file. I was editing it with Vi using the recovery mode from GRUB. The main reason I was doing this was because the Network-Manager was broken, so I replaced it with a different program (lost my network connection of course), edited the interfaces files to auto detect the eth port (this is because Ubuntu didn't see the port as configured).
My session wouldn't load so I was going to add root login to GDM with Vi. I think I might have uncommented something because GDM won't load now. :( I'm running the "repair broken packages" function under root right now. So we'll see if it works. If not, does anyone have any ideas what I can do?!

Thanks!
Joe

---

### Post by ibutho on 2008-06-08
Its usually a good idea to backup important files before making any changes. One option would be to reinstall gdm e.g.
```
apt-get remove --purge gdm
apt-get install gdm

```

---

### Post by joebrueske on 2008-06-08
Well that was an easy fix! I do so enjoy my lighting fast internet. Now, to get the stupid wired connection going again!

---

