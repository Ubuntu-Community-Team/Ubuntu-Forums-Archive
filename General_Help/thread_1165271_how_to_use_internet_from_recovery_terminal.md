---
title: "how to use internet from recovery terminal"
date: 2009-05-20
forum: General Help
---

### Post by }SoC{phenix on 2009-05-20
On my desktop computer I have Ubuntu Hardy Heron, and for whatever reason, although it originally supported my NVIDIA card, it stopped using it, and now refuses to start gnome, leaving me with just recovery mode.  The computer needs an update in order to install the driver, but I can't get internet with the recovery root terminal.  I know that if I were to change runlevels (I think that's what they were called) I could get internet access, but I don't remember how to do so, and I'm not sure it would work.  Any suggestions on enabling the ethernet so I can run links and apt?

---

### Post by Titan8990 on 2009-05-20
/etc/init.d/networking start

---

### Post by Fixman on 2009-05-20
```
 init 3 
```

---

### Post by }SoC{phenix on 2009-06-04
Thanks a lot, I'll have to try those commands when I have a chance.

---

