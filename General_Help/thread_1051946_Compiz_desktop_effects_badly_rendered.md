---
title: "Compiz desktop effects badly rendered"
date: 2009-01-27
forum: General Help
---

### Post by alendrom on 2009-01-27
Hey everyone,

There seem to be a persistent desktop effect misrepresentation on my Ubuntu 8.10 (see attached screenshot).

My graphic card is Nvidia Quadro nvs120m. Driver version is 177. Tell me if you need more info.

Any advice is welcome.

Thanks in advance,

Alendrom.

---

### Post by gettinoriginal on 2009-01-27
Install emerald, it is a window decorator that renders better with compiz than gtk.
```
sudo apt-get install emerald
```
then do:
```
compiz --replace
```
```
emerald --replace
```

---

### Post by alendrom on 2009-01-29
Thanks!

How do you make Emerald the main render engine? The system seems to revert back to Compiz all the time.

Btw, can I also render AWN with Emerald?

Cheers,

Alendrom.

---

### Post by gettinoriginal on 2009-01-29
To simplify things, compiz is a window manager, emerald is a window decorator.  Go to CCSM, Window Decoration and in the command line type:
> emerald --replace
You can also install fusion-icon from synaptic, it is a little tool that allows you to control your window manager (compiz/metacity) and your window decorator (emerald/gtk) at the click of the mouse.

---

