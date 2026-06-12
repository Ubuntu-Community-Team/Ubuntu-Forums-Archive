---
title: "Ubuntu 9.04 Package Manager Problem"
date: 2009-05-04
forum: General Help
---

### Post by billfreeboy on 2009-05-04
Well, I've been struggling to upgrade to 9.04 and I've done it, but during the cleaning up process, someone took out all my plugs even the power cord to plug in my new Power Mac G4 even though a power cord came with it. :mad: Now the package manager never works. I can't install any Debian Packages, or Add/Remove any software. Is there any way to fix this?

---

### Post by geirha on 2009-05-04
Have you tried running ```
sudo dpkg --configure -a
``` in a terminal?

---

### Post by skymera on 2009-05-04
```
 sudo apt-get update 
```

Run that, then try and install something.

---

### Post by billfreeboy on 2009-05-05
> **geirha said:**
> Have you tried running ```
sudo dpkg --configure -a
``` in a terminal?

Thanks. The text that came up was...
```
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

---

### Post by albinootje on 2009-05-05
> **billfreeboy said:**
> Thanks. The text that came up was...
```

ldconfig deferred processing now taking place
```

After that do a :
```

sudo apt-get -f install

```
and everything might be just fine again.

---

### Post by billfreeboy on 2009-05-06
:KS Thanks! Now it's able to work again.:guitar:

---

