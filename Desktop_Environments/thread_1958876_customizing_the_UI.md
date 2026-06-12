---
title: "customizing the UI"
date: 2012-04-15
forum: Desktop Environments
---

### Post by isnehadeep on 2012-04-15
i've downloaded the kernel api and have studying it. I want to know that is the api for GUI of  ubuntu desktop environment available for download? Plz help. I want to customize the unity and also the other UIs ,not by using any software but actual programing! A detailed assistance plz!

---

### Post by MG&amp;TL on 2012-04-15
Ubuntu's UI is called unity, you can get the source code (like any package) with:

```
apt-get source unity
```

or, if you want the cutting-edge version, 

```
bzr branch lp:unity
```

If you want the UI toolkit, look at gtk and libnux, both of which the source is available for.

---

### Post by isnehadeep on 2012-04-15
thanks. Looking forward to it.

---

