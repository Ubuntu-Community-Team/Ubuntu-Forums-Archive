---
title: "compiz wont load on ubuntu 11.10 with Ati card"
date: 2012-01-01
forum: Desktop Environments
---

### Post by Sietse on 2012-01-01
Hi people,

I am trying for a while now to get compiz running on classic-gnome desktop session in ubuntu 11.10

Card: Ati Radeon HD 5700 series (fglrxinfo)
Os: Ubuntu 11.10
Desktop: gnome (classic version).

When i wanna load compiz its says:
compiz (core) - Fatal: No composite extension
compiz (composite) - Error: initScreen failed
compiz (core) - Error: Couldn't activate plugin 'composite'
compiz (core) - Error: Plugin 'composite' not loaded.

compiz (core) - Error: InitPlugin 'opengl' failed
compiz (core) - Error: Couldn't activate plugin 'opengl'
compiz (core) - Fatal: No composite extension
compiz (core) - Fatal: No composite extension

My xorg.conf was generated with aticonfig so i think xorg.conf is a problem not having loaded all the needed extensions for compiz.

What changes should i make to the xorg.conf file to get compiz running? Or somebody have other tips? Dont reply with links to guides because i have read them all and not found the solution to my problem.

---

