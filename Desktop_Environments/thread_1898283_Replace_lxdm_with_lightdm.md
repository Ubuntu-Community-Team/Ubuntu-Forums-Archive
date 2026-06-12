---
title: "Replace lxdm with lightdm?"
date: 2011-12-21
forum: Desktop Environments
---

### Post by Drezliok on 2011-12-21
I tried to just install lightdm and select it as my main login app. But it won't load up.

I beleive I am missing a step to getting this to work. Any ideas?

Fresh install on a IBM Thinkpad T30 I salvaged. Lubuntu works!!

Thankyou for your time.
Drezliok

---

### Post by gil76mg on 2011-12-21
Hello,

i've the same problem with lightdm.

When loading LIGHTDM i have a black screen and i must re-install lxdm to go back to the graphical use.

If someone have solutions can you help us?

---

### Post by kerry_s on 2011-12-21
i don't think lt works with lxde yet, that's why it wasn't included. check over on there site it was mentioned somewhere.

---

### Post by Drezliok on 2011-12-21
> **kerry_s said:**
> i don't think lt works with lxde yet, that's why it wasn't included. check over on there site it was mentioned somewhere.

I checked out the launch pad, no info on it not working with lxde. but I did find this.

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

So I tried 
```


dekthor@ThinkTANK:~$ sudo dpkg-reconfigure lightdm
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing

```

---

### Post by Drezliok on 2011-12-21
Looking further into it, I want Xubuntu's lightdm login.

---

### Post by Drezliok on 2011-12-23
bump

---

### Post by Farinet on 2012-01-12
I think that might be a (L)Ubuntu problem: I've running lightdm as display manager with LXDE under Debian wheezy (on a Powermac) without any problem.

---

