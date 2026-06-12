---
title: "[SOLVED] Citrix 8 in Intrepid Ibex - libXaw.so.6 error"
date: 2008-12-30
forum: General Help
---

### Post by dsauxier on 2008-12-30
I've solved this myself, just posting to help others out: 

After running alien on an RPM of Citrix ICA Client ( Citrix version 8 )
I ran (from the command line so that I could see the errors) ```
/usr/lib/ICAClient/wfcmgr
``` 
Then, from the GUI, when trying to connect to any of my servers, I would get this error on the terminal : 

/usr/lib/ICAClient/wfica: error while loading shared libraries: libXaw.so.6: cannot open shared object file: No such file or directory

To fix this, I created a softlink : 

```
sudo ln -s /usr/lib/libXaw3d.so.6 /usr/lib/libXaw.so.6
```

---

### Post by Nico666 on 2009-10-06
Sos una maquina dsauxier!!

---

### Post by malapradej on 2011-09-23
Thanks for sharing. This has helped to set up my citrix app for UCL. 

> **dsauxier said:**
> I've solved this myself, just posting to help others out: 

After running alien on an RPM of Citrix ICA Client ( Citrix version 8 )
I ran (from the command line so that I could see the errors) ```
/usr/lib/ICAClient/wfcmgr
```Then, from the GUI, when trying to connect to any of my servers, I would get this error on the terminal : 

/usr/lib/ICAClient/wfica: error while loading shared libraries: libXaw.so.6: cannot open shared object file: No such file or directory

To fix this, I created a softlink : 

```
sudo ln -s /usr/lib/libXaw3d.so.6 /usr/lib/libXaw.so.6
```

---

