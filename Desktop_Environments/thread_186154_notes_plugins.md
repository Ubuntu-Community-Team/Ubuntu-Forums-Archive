---
title: "notes plugins ?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by IdoMcFly on 2006-06-01
Hi,

is there any sticky notes plugin for xfce?

---

### Post by encho on 2006-06-02
There is, but it's not in the repos at the moment. It was there but had some compatibility issues and was removed. I guess it will be there in backports as soon as edgy is out.

---

### Post by IdoMcFly on 2006-06-02
oh I see :)

So I'm trying to compile it myself but the configure gives me that:
```

checking for xfce4-panel-1.0 >= 4.1.90... Package xfce4-panel-1.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `xfce4-panel-1.0.pc' to the PKG_CONFIG_PATH environment variable No package 'xfce4-panel-1.0' found
configure: error: Library requirements (xfce4-panel-1.0 >= 4.1.90) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

I have xfce4-panel and xfce4-panel-dev installed.

---

### Post by encho on 2006-06-03
Same happened here, I never had any luck compiling them. Guess we'll have to wait :) Or if anyone knows the trick?

---

### Post by Tamihania on 2006-06-05
[quote=encho]Same happened here, I never had any luck compiling them. Guess we'll have to wait :) Or if anyone knows the trick?[/quote] 
You can try xfce4-xfapplet-plugin which gives you possibility to take advantege of Gnome's applets(sticky notes!) in xfce ;)

It's possible to "grab" it from here:

[http://gauvain.tuxfamily.org/repos/]("http://gauvain.tuxfamily.org/repos/")

...I use also tomboy notes - very good ones - possible to acquire from repository (Synaptic) 

Enjoy :D 

tami

EDIT: I am using also extension to Firefox: Google Notebook (easy to get if you are a gmail user ;)...

---

### Post by IdoMcFly on 2006-06-13
the problem with this solution is the sticky notes can't be hidden

---

