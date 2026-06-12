---
title: "remove kubuntu usplash"
date: 2008-10-23
forum: Desktop Environments
---

### Post by Flynn555 on 2008-10-23
ok i put kubuntu kde 4 on my machine and hated it.  i removed it with:

```

sudo apt-get remove kde-desktop
sudo apt-get autoremove

```

but the usplash screen is still showing up.
its not that big of a deal just annoying :confused:

note: i dont think that the above code completely removed kde4 
can anyone help?

---

### Post by swisscow on 2008-10-23
try:

```
sudo update-alternatives --config usplash-artwork.so
```

then

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

