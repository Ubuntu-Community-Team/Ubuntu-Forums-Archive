---
title: "Uninstalling Xubuntu or Lubuntu from Ubuntu 11.04"
date: 2011-09-27
forum: Desktop Environments
---

### Post by rajeshrestha on 2011-09-27
I installed Xubuntu from Terminal (sudo apt-get install xubuntu-desktop).

After trying new desktop enviornment, I still want to use ubuntu exclusively. I want to remove Xubuntu from my ubuntu system. 

If anybody could help me with this I would be grateful. 

I tried to remove all new applications from software center but not useful. I also tried sudo apt-get remove xubuntu desktop command in terminal. I am very very new user. Thankx in advance.:D

---

### Post by nothingspecial on 2011-09-27
Here you go

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Krytarik on 2011-09-27
Now, after you removed the meta-package "xubuntu-desktop", run this command to hopefully get rid of the packages it pulled upon its installation:
```
sudo apt-get autoremove
```Hope it works!

If it doesn't, follow *nothingspecial*'s advice.

---

