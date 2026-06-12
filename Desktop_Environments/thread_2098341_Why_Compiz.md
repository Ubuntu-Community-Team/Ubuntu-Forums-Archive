---
title: "Why Compiz?"
date: 2012-12-26
forum: Desktop Environments
---

### Post by Lloydb39 on 2012-12-26
Compiz, which I don't understand and didn't even know I had, has caused me to have to do a complete re-install of Ubuntu 12.04 (during which I lost my address book and favorites.) Do I need this dog? Can't I just remove it, using software manager? As far as I can tell all it does is make 3D pictures, which I don't need or want. Barring that, should I get CCSM, which I gather is a way of controlling it? I've read wikis and whatnot and still don't understand what this thing is or why I need it.

---

### Post by Lampi on 2012-12-26
I assume "unity 3d" needs compiz? Can you login unity 2d (same unity, but 3d effects disabled)?

---

### Post by stinkeye on 2012-12-26
Compiz is the window manager used in the Ubuntu session.
Unity is a plugin for compiz.
ccsm allows you to change settings in compiz.

As **Lampi** said, in 12.04 you can login to the unity2d session which uses Metacity as the window manager.

In 12.10 and onwards, if you want to use unity you will have to use compiz as the 2d session using Metacity is no longer supported.

2 handy commands to know when using compiz in 12.04 are
To reset unity to default settings
```
unity --reset
```

and to reload compiz
```
compiz --replace
```

---

### Post by Lloydb39 on 2012-12-26
Thank you both. That helps. I'll try to figure out whether I'm in Unity2 or 3 and how to change from one to the other. Even after I re-installed, Compiz crashed again and I chose to leave it closed. Don't know what effect that will have but everything seems to be working for now.

---

### Post by stinkeye on 2012-12-26
> **Lloydb39 said:**
> Thank you both. That helps. I'll try to figure out whether I'm in Unity2 or 3 and how to change from one to the other. Even after I re-installed, Compiz crashed again and I chose to leave it closed. Don't know what effect that will have but everything seems to be working for now.
You can choose your session at the login screen by clicking on the icon to the right of your user name.

---

### Post by Mopar1973Man on 2012-12-26
> **Lloydb39 said:**
> Compiz, which I don't understand and didn't even know I had, has caused me to have to do a complete re-install of Ubuntu 12.04 (during which I lost my address book and favorites.) Do I need this dog? Can't I just remove it, using software manager? As far as I can tell all it does is make 3D pictures, which I don't need or want. Barring that, should I get CCSM, which I gather is a way of controlling it? I've read wikis and whatnot and still don't understand what this thing is or why I need it.

Like stinkeye has shown the picture of you could load a different desktop like LXDE, or KDE... Then switch over to it. Like myself I'm running LXDE and very happy with it compared to Unity.

---

