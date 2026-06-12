---
title: "Need fglrx for beryl?"
date: 2006-11-06
forum: Desktop Environments
---

### Post by FlakJacket on 2006-11-06
I would like to try Beryl on my Kubuntu 6.10 laptop, but it's kinda old with an IGP 340M.  This card isn't supported by fglrx.  What I haven't been able to find definitively is whether the installation of Beryl/XGL requires fglrx.  Thanks,

Flak

---

### Post by dbd on 2006-11-06
You do need to have some kind of 3d acceleration installed to use beryl. However there are many 3d drivers other than fglrx, so you may be able to use another one. You could try the radeon driver, but I don't think even that would offer full 3d support for your card, have a look here for info on installing that:
[https://help.ubuntu.com/community/RadeonDriver?](https://help.ubuntu.com/community/RadeonDriver?)

---

### Post by FlakJacket on 2006-11-06
How do I know if I have 3d acceleration for my card.  glxinfo says "direct rendering: yes" if that's any help.

Thanks

---

### Post by igknighted on 2006-11-07
if your video driver claims to support direct rendering, I would give it a shot and install the beryl packages and try to run it.  Worst thing that could happen is that it beryl wont start.  (note, do not try to set up an XGL session, just install the beryl packages and run beryl-manager from a console)

---

### Post by FlakJacket on 2006-11-07
Thanks alot for the quick replies!  I'm very happy, Beryl works without a hitch.  Thanks for the reassurance.

Flak

---

