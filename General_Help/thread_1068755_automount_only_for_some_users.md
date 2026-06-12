---
title: "automount only for some users?"
date: 2009-02-13
forum: General Help
---

### Post by firfin on 2009-02-13
Hi,

I currently have a line in my /etc/fstab to automatically mount a samba share using smbfs. I need this in order to enable firefox (and other non-gvfs-aware programs) usage of the share. 
[COLOR="DarkOliveGreen"]This construction works,[/COLOR] of course it would be better if each user could  just have some links and bookmarks to the needed shares in Nautilus. Unfortunately this doesnt seem possible, at least in a way so that firefox can make use of it. Please, please, correct me if I'm wrong!

This however causes a problem for me. Now [COLOR="Sienna"]the 'guest session'- user can also access[/COLOR] the files on the share. 
[B]
Is there a way to prevent this?[/B]

Or is there a way to automatically mount devices depending on which user logs in?


Line in fstab:
//fileserver/server    /media/fileserver   smbfs   defaults        0       0

---

### Post by firfin on 2009-02-23
I have rephrased my question here:

[http://ubuntuforums.org/showthread.php?t=1067994](http://ubuntuforums.org/showthread.php?t=1067994)

Anybody who can help out with this?

---

