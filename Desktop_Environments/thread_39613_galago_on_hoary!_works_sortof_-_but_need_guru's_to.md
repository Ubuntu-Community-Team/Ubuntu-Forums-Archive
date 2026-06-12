---
title: "galago on hoary!? works sortof - but need guru's touch"
date: 2005-06-05
forum: Desktop Environments
---

### Post by puccaso on 2005-06-05
```
      
Ubuntu Hoary users can install packages through an apt feed. Append the  following to /etc/apt/sources.list: 

 deb [http://www.galago.info/apt/ubuntu](http://www.galago.info/apt/ubuntu) hoary/
deb-src [http://www.galago.info/apt/ubuntu](http://www.galago.info/apt/ubuntu) hoary/
  Then apt-get the necessary components. For example: 

 $ apt-get update  
$ apt-get install galago-daemon eds-feed gaim-galago gnome-presence-applet
  For the .NET components: 

 $ apt-get install libgalago-cil libgalago-gtk-cil
    

```

so i got it to install
and i see the presence aplet
but nothing happens?

has anyone got it to work? ie - give pressence

---

### Post by willrea on 2005-06-14
yeah, im having the same problem too. I was looking forward to see this in action.

---

### Post by willrea on 2005-06-17
It's just no the packages, even when compiled from cvs the applet still doesnt work

---

