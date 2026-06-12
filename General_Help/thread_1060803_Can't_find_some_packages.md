---
title: "Can't find some packages"
date: 2009-02-05
forum: General Help
---

### Post by Nagora on 2009-02-05
I've installed Intrepid on a laptop to try it out. I've come from a background of using first RH and then Gentoo for about 10 years and there's a few packages I can't find.

The big one is TeX: I've searched through the add/remove program panel and I can't find anything that looks like an actual TeX install. Where is it hiding?

Next is mplayer and finally Opera. 

I did actually just go to the Opera website and install from there. When I did the system complained that Opera was available from an existing channel and I should use that. I broke out and looked (guessing that a "channel" was something to do with the categories in the add/remove panel) but I still couldn't see it anywhere, so I just went ahead and installed the Opera.com version. Where should I have seen Opera and what is a "channel"?

The only other thing bothering me at the moment is the inability to map the CapsLock key to be a Control key.

---

### Post by geirha on 2009-02-05
Add/Remove... only lists GUI applications. To search through all packages, try System -> Administration -> Synaptic package manager. [tetex-bin](apt:tetex-bin) may be the package you are looking for.

For the caps-lock key, go to System -> Preferences -> Keyboard. On the layout tab, select your layout and open the preferences window for that layout.

---

### Post by Nagora on 2009-02-05
> **geirha said:**
> Add/Remove... only lists GUI applications. To search through all packages, try System -> Administration -> Synaptic package manager. [tetex-bin](apt:tetex-bin) may be the package you are looking for.
That's great - TeX is indeed in there, although the system seems a bit over-enthusiastic about installing LaTeX as well. Mplayer too.

> For the caps-lock key, go to System -> Preferences -> Keyboard. On the layout tab, select your layout and open the preferences window for that layout.
Likewise. I had been on that panel but missed the entry.

Thanks.

---

