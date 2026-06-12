---
title: "Update manager &quot;could not download all repository indexes&quot;"
date: 2009-01-02
forum: General Help
---

### Post by tegnoto89 on 2009-01-02
Couldn't get the following things:

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs



The thing is, I think that it's not letting me download the other updates after I get this message.  The only button I can press is "check" again.

---

### Post by wolfen69 on 2009-01-02
it is telling you that if you want to add a cd as a software source, you need to:```
sudo apt-cdrom
``` then do ```
sudo apt-get update
```

---

### Post by donkyhotay on 2009-01-02
As mentioned previously it is attempting to download/install repositories from the cdrom, however I seriously doubt you actually want to do that. Make certain the install disc is not in the drive then check your software sources are set for online servers.

---

