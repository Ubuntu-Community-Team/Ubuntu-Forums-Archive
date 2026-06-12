---
title: "I think I broke X.org and I can't fix it"
date: 2006-11-01
forum: Desktop Environments
---

### Post by Ninjajebus on 2006-11-01
Forgive me, I'm a noob.

I apt-get updated to Kubuntu Edgy, and things were working wonderfully, but I saw all this talk about aiglx, emerald, and beryl. I wanted to be like one of the cool kids so I followed one of the many guides that are floating around. I got as far as the point where I was supposed to start beryl, when the frame around my console window disappeared and everything locked up.

I rebooted, and couldn't get to the login screen. I am used to having problems with my Nvidia drivers, so I went to my xorg.conf file, and low and behold changing the driver to "nv" did not work, "vesa" does not do the trick either. I cannot get into X using what little tricks I know. 

So far I've tried to edit xorg.conf, rolled it back to a previous version, and purged all of beryl and it's related files. I don't know what to try next. ](*,) 

Please Help!!!

Thanks in advance!

---

### Post by taurus on 2006-11-01
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by JediSpam on 2006-11-01
don't worry man. i've done it before and i'm sure most people have done it lol

---

### Post by Ninjajebus on 2006-11-01
Thanks for your help, that and a sudo nvidia-glx-config enable did the trick.

Woot! taurus rock!:mrgreen:

---

### Post by taurus on 2006-11-01
> **Ninjajebus said:**
> 
Woot! taurus rock!:mrgreen:

:-$

---

