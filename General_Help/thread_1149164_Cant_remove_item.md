---
title: "Cant remove item"
date: 2009-05-04
forum: General Help
---

### Post by RedSingularity on 2009-05-04
I am trying to remove the xorg-driver-fglrx from my system because i no longer use the ATI graphics card.  When i chose remove or completely remove in synaptic i get this:

```
E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2

```

---

### Post by ptn107 on 2009-05-05
try
```

sudo aptitude reinstall xorg-driver-fglrx && sudo aptitude remove xorg-driver-fglrx
```

---

