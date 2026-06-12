---
title: "[SOLVED] Problem with Nautilus"
date: 2008-08-30
forum: Desktop Environments
---

### Post by MojoMax on 2008-08-30
I tried to have Thunar as the default file manager so I put this in the terminal

```
sudo mv /usr/bin/nautilus /usr/bin/nautilus.real
sudo gedit /usr/bin/nautilus
```

But now my files won open how do I change this back 

thanks :)

---

### Post by suffe on 2008-08-30
I would guess

sudo mv /usr/bin/nautilus.real /usr/bin/nautilus

would do the trick. That is, unless you've done other things too in your attempt at installing Thunar.

---

### Post by gmxgeek on 2008-08-30
> **suffe said:**
> I would guess

sudo mv /usr/bin/nautilus.real /usr/bin/nautilus

would do the trick. That is, unless you've done other things too in your attempt at installing Thunar.

That should do the trick

---

### Post by MojoMax on 2008-08-30
> **suffe said:**
> I would guess

sudo mv /usr/bin/nautilus.real /usr/bin/nautilus

would do the trick. That is, unless you've done other things too in your attempt at installing Thunar.

Thanks that worked

---

