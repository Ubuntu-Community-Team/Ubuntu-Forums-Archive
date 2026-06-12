---
title: "Problem with AWN"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by damonjablons on 2008-02-18
I tried installing AWN Curves, but I guess I did something wrong, so then I tried uninstalling it and reinstalling AWN.  Now when I try to do this, Synaptic Package Manager gives me the following error:

E: /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0

What I want to do is start fresh, and install AWN Curves.  Is this possible?  Or have I done serious damage?  Thanks in advance for the help.

---

### Post by amohanty on 2008-02-18
The libawn-bzr version is the bleeding edge (well almost) version of the libawn. You can have one or the other but not both. if you want to use the xxx-bzr versions, make sure that you remove all the default avant-* and *awn* packages and then install the debs.

If all else fails:
Fire up synaptic, do a search with anything with awn in the name, "completely remove it"
Do the same with anything that starts with avant. Start from scratch.

HTH
AM

---

### Post by damonjablons on 2008-02-18
i went ahead and completely removed everything to start from scratch, but now when trying to install awn curves, i still get an error.  i guess i'll move to that thread.

thank you for the help.

---

