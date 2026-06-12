---
title: "updating errors"
date: 2009-01-26
forum: Desktop Environments
---

### Post by skydiving85 on 2009-01-26
hey i was wondering if anyone could help me decipher these updating errors i receive upon every update please see attached screen shot, thanks 
matt

---

### Post by gettinoriginal on 2009-01-26
Check System, Admin, Software Sources, and be sure that the first 4 boxes are checked, and Third Party should have all checked except CD.

---

### Post by skydiving85 on 2009-01-28
hey i check that, and all seems to be in order, could this be a compatibility issue, between heron and ibex?

---

### Post by gettinoriginal on 2009-01-28
Did you upgrade from Heron, or did you do a fresh install of Ibex ??
If you did, go to Software Sources, Third Party, and make sure they are all for intrepid, if they say hardy, edit them to read intrepid.
Then run this in terminal:
```
sudo apt-get update && sudo apt-get dist-upgrade
```

By the way, does your Software Sources, Updates say "normal releases" (it should) for intrepid, as it is not a LTR

---

### Post by skydiving85 on 2009-02-01
that worked to a certain extent but now i get this error ! 
see attached

---

### Post by theozzlives on 2009-02-01
Do you have dpkg, apt, or synaptic running?

---

### Post by skydiving85 on 2009-02-03
no they are not running as i update

---

