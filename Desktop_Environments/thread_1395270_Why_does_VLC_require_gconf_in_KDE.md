---
title: "Why does VLC require gconf in KDE"
date: 2010-01-31
forum: Desktop Environments
---

### Post by Mustache Villain on 2010-01-31
I'm just curious as to why this happens. Is this a general requirement for installing VLC on GNU/Linux or is this Ubuntu/Kubuntu specific, only? I find it strange that the Qt application would need gconf.

---

### Post by Zorael on 2010-01-31
Likely it depends on x which depends on y which recommends gconf. Thus it gets installed at the same time as per the new defaults; to treat recommends as dependencies when selecting packages to install.

Try telling your package manager to stick to the old behavior ("recommends are optional").
```
$ sudo aptitude install vlc --without-recommends
$ sudo apt-get install vlc --no-install-recommends
```

It's possible to create a rule in **/etc/apt/apt.conf.d** to make the old behavior the default, but I don't know the specifics.

---

### Post by Mustache Villain on 2010-01-31
> **Zorael said:**
> Likely it depends on x which depends on y which recommends gconf. Thus it gets installed at the same time as per the new defaults; to treat recommends as dependencies when selecting packages to install.

Try telling your package manager to stick to the old behavior ("recommends are optional").
```
$ sudo aptitude install vlc --without-recommends
$ sudo apt-get install vlc --no-install-recommends
```It's possible to create a rule in **/etc/apt/apt.conf.d** to make the old behavior the default, but I don't know the specifics.

That's fantastic, I can minimize the installation! Thanks for being so informative.

---

