---
title: "Changing network preferences in XFCE"
date: 2006-03-01
forum: Desktop Environments
---

### Post by fxgogo on 2006-03-01
I am using the XFCE desktop ontop of the server installation of Ubuntu. I want to set up two different wireless configurations for work and home. It was easy to do in Gnome, but how do I do it in XFCE?

Thanks.

---

### Post by earobinson on 2006-03-01
what program did you use in gnome, you should be able to use the same program in xfce

---

### Post by fxgogo on 2006-03-01
I would presume it is aswell, but it is not listed in any of the menus and I don't know the program name to call in a terminal. Any ideas?

---

### Post by taurus on 2006-03-01
Could it be

```

sudo system-config-network

```

---

### Post by Ramses de Norre on 2006-03-01
I would like such a program too, but never really searched for it.
Does you need to install system-config-network? 
apt-get doesn't find it.

---

### Post by fxgogo on 2006-03-13
No that does not do it, but I think this is going in the right direction. We just need the right name of the program to call. I would assume it is installed in the server install and is not part of gnome, but that might be a might 'assume'.

---

### Post by 5-HT on 2006-03-13
[quote=fxgogo]No that does not do it, but I think this is going in the right direction. We just need the right name of the program to call. I would assume it is installed in the server install and is not part of gnome, but that might be a might 'assume'.[/quote] 
What about 'network-admin' ?

I believe it's part of the 'gnome-system-tools' package, but could possibly be part of 'gnome-control-center'.

That GUI applet is definitely a GNOME utility though, so it shouldn't be installed if you did a base install and added XFCE.

Apart from the GUI, and having to install all those GNOME libs if you don't want to, you could also just edit /etc/network/interfaces to your liking.

'man interfaces' will bring up the manual for explaining the syntax and options of the file.

HTH

---

### Post by fxgogo on 2006-03-14
> That GUI applet is definitely a GNOME utility though...
Ok, that clears a lot up 5-HT, thanks. I was assuming too much. I will try your idea of editing the 'interfaces' file. I was not sure where the config files were kept, so that helps me a lot thanks.

---

