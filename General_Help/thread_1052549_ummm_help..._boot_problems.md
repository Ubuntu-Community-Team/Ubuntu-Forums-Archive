---
title: "ummm help... boot problems"
date: 2009-01-27
forum: General Help
---

### Post by theozzlives on 2009-01-27
K, I booted my computer that has my apache server on it and I get to the screen just before the login screen and I just get stuck at that circle. My web site is up and I can access my shares on my network. I booted from the live CD and ran fsck on all my ext3 partitions and it said their clean. I can hit ctrl+alt+F1 and log into the prompt but startx don't work. Please, I need to get this running, re-install is not an option.

---

### Post by jimv on 2009-02-04
I don't think that it just says "startx won't work".  There's an error there that should say why it's not starting...something like a missing module, or a version mismatch.

My bet is that you installed a kernel upgrade, and for whatever reason, it didn't install your video drivers.

---

### Post by theozzlives on 2009-02-05
I wish we could mark these things as   solved again, it was a problem with the logon screen I got from GNOME-Look.

---

