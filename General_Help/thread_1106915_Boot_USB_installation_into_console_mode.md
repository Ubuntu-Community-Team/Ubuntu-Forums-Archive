---
title: "Boot USB installation into console mode"
date: 2009-03-26
forum: General Help
---

### Post by iKevin on 2009-03-26
Hi All

I made a bootable USB Ubuntu thumbdrive using the menu pick from 8.10.  All went well and it works like a charm.  However, I have a quick question about modifying the USB installation.  I would like to boot straight into console -- no graphics.  I think this is what I need to do:

sudo update-rc.d -f gdm remove

Can anyone confirm that?  

Also, on the USB installation drive, the graphical mode autologs into some account. If I bring up a console, who do I login as and what password do I use? Or, does the console also go directly into the default account?

Thanks

---

### Post by skymera on 2009-03-26
System > Administration > Services

Untick GDM

---

### Post by iKevin on 2009-03-26
Thanks a bunch.  Since I am not home at the momement, will this leave me at a login prompt or will it autologin like the regular install session?

---

### Post by skymera on 2009-03-27
It will leave you in the command line.

you can start GUI at later time

---

