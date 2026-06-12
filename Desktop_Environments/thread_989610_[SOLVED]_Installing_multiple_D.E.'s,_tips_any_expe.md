---
title: "[SOLVED] Installing multiple D.E.'s, tips? any expected problems?"
date: 2008-11-21
forum: Desktop Environments
---

### Post by slinkey1981 on 2008-11-21
So I have been using GNOME for a while now. But keep hearing about how much quicker that xfce is, how nice KDE4 looks and was wondering "Why not try them all"

So, is it really best to do the whole Synaptic, search "KDE" and let it run with it like that, (KDE and XFCE packages are 224MB when selecting the "KDE4" and "XFCE" package names along with dependencies) or to download the "kubuntu-desktop" and "xubuntu-desktop" which is (surprisingly) 205MB?

I have a lot of KDE apps already (amarok, Konsole.. generic stuff) and just want to know which way would be least painful.

I have the cd Install of Ubuntu 8.04 (with all updates), and am not looking to upgrade to 8.10.

Any advise on this situation would be greatly appreciated.

---

### Post by mrboojive on 2008-11-22
I would probably suggest the kubuntu-desktop and xubuntu-desktop packages. Those will give you the Ubuntu customized KDE and XFCE. If you just install KDE or XFCE it will give you everything that comes with those DEs, including a bunch of stuff you might not want if you're just checking them out.

I noticed one time when I installed XFCE instead of xubuntu-desktop that it didn't have very useful default settings (panels didn't show up and such). You might also need to install xubuntu-default-settings (or kubuntu-default-settings) if you just install the DEs.

On the other hand, if you install the -desktop packages, that will change your usplash boot up screen to say Xubuntu or Kubuntu instead of Ubuntu (but that's easy to change around). Also, you'll want to follow these instructions if you later want to uninstall the -desktop packages: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome).

---

