---
title: "Changing the default display manager"
date: 2005-07-27
forum: Desktop Environments
---

### Post by LazyIvan on 2005-07-27
Originally, I had gdm installed, and had problems after about a week where I was unable to log in, so I installed kdm in an attempt to get it working.  It did not fix the problem, but when it was fixed it began using kdm as the default display manager.  Does anyone know how to switch the default display manager back to gnome from kdm?

Thanks

---

### Post by Xian on 2005-07-27
From a teminal:

```
$ sudo dpkg-reconfigure kdm
```

---

### Post by jones_jj on 2005-07-27
Where do you get KDM when you do a Ubuntu install?  Do you have to do an apt-get to get KDM?  Thanks

---

### Post by LazyIvan on 2005-07-27
Thanks Xian, that fixed it right up.

As to installing KDM, I believe I just did it with an apt-get -i kdm, or you could do the same through the synaptic package manager and just search for kdm.  Sorry if that is too imprecise, but it is all I can remember doing since it has been at least a month since I installed it.

---

