---
title: "change from kdm back to gdm"
date: 2005-05-26
forum: Desktop Environments
---

### Post by eko291 on 2005-05-26
Hi All.  Yesterday, I installed kubuntu-dekstop and was given the option to change my login manager to KDM.  I did so and found that I really preferred GDM.  Is there a way to change my login manager back to GDM?

Mark

---

### Post by SSTwinrova on 2005-05-26
Complete guess, but possibly "dpkg-reconfigure gdm"??

---

### Post by dolny on 2005-06-20
Hm... I'm not sure. Is this a proper way? Can anybody tell me how to switch back to GDM ? I use KDE but imho KDM sucks compared to GDM.

---

### Post by afonic on 2005-06-20
[QUOTE=dolny]Hm... I'm not sure. Is this a proper way? Can anybody tell me how to switch back to GDM ? I use KDE but imho KDM sucks compared to GDM.[/QUOTE]
 If you have not removed Gnome just click on the Session button under your login box before you login and select Gnome.

---

### Post by dolny on 2005-06-20
I don't want to use Gnome. I just want to use GDM (login screen) because it looks cooler than KDM.

---

### Post by Xian on 2005-06-20
[QUOTE=dolny]Hm... I'm not sure. Is this a proper way? Can anybody tell me how to switch back to GDM ? [/QUOTE]
The method mentioned earlier is the correct "debian" way.

```
$ sudo dpkg-reconfigure gdm
```

---

