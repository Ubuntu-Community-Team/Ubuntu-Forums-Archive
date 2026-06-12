---
title: "[SOLVED] GDesklets Launches Blank Window"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by jusmurph on 2007-06-28
I installed via synaptic.

When ever i click to launch the program, all i get is a blank window called gdesklet shell, which after 15 or so seconds goes grey, another 15 it closes itself.

Can anyone help here?

---

### Post by jusmurph on 2007-06-29
Ok when i tried to launch it via terminal it said it failed to connect to the daemon and nothing appeared.

---

### Post by ubonetu on 2007-07-01
Same

7.04 Dell Inspirion 1501 ATI 200m

---

### Post by super.roz on 2007-07-06
I have the same problem.  Any solution yet?

My log file has the following:
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[07/05/07-22:57:17]===
Could not import tiling module!

---

### Post by super.roz on 2007-07-06
There are more details and a workaround posted here:
[https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103)

---

### Post by jusmurph on 2007-07-09
> **super.roz said:**
> There are more details and a workaround posted here:
[https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103](https://bugs.launchpad.net/ubuntu/+source/gdesklets/+bug/110103)

Cheers, i will have to have a look when i get home.

---

### Post by samkline on 2007-07-14
same.

i'm using an amd athlon 64 x2

---

### Post by jusmurph on 2007-07-15
> **samkline said:**
> same.

i'm using an amd athlon 64 x2

At the link above there is a deb file. Someone mentions below to extract i think the lib folder and just move that. It worked for me.

---

