---
title: "Symlink breaks freenas share for QuiXplorer"
date: 2009-05-24
forum: General Help
---

### Post by jbraveman on 2009-05-24
I upgraded to 9.04 32 bit on a new machine (from 8.04 on an old dell).  I mounted my freenas shares (0.69) using cifs.  I created symlinks (right click on the mounted folders) on some of my shares.  When I tried to use Quixplorer 2.3 on freenas to browse those shares I got this error:

ERROR(S):
Disk1: Unable to read directory. 

When I delete the symlink, the shares are now browsable.
The shares are otherwise completely accessable with ubuntu and my vista machine with the links in place.  

It's only a problem with quixplorer, which is a problem becuase I use that program to move files between drives on the freenas.  It's much faster using the cifs/smb shares.

---

