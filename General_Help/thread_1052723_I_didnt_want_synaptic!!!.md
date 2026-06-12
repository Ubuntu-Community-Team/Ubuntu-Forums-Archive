---
title: "I didnt want synaptic!!!"
date: 2009-01-28
forum: General Help
---

### Post by mahela007 on 2009-01-28
I selected in and installed firefox on KDE. I have firefox but I also ended up with SYNAPTIC why?

---

### Post by halovivek on 2009-01-28
Could you please explain little more please?

---

### Post by mahela007 on 2009-01-28
> **halovivek said:**
> Could you please explain little more please?
The default package mangaement tool in kubuntu is not synaptic. However after I installed firefox synaptic was also there on my kubuntu system

---

### Post by ubuntu27 on 2009-01-28
I think that mahela007 has installed Kubuntu (KDE), and since kubuntu doesn't come with firefox, he installed it. And when he installed firefox, synaptic package manager also came with it.

So it seems firefox in Dependant on synaptic? I cannot confirm it right now.

---

### Post by jerome1232 on 2009-01-28
Certinaly doesn't seem to depend on synaptic
```
 apt-cache show firefox
Package: firefox
Priority: optional
Section: web
Installed-Size: 124
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: all
Source: firefox-3.0
Version: 3.0.5+nobinonly-0ubuntu0.8.10.1
[COLOR="Red"]Depends: firefox-3.0, firefox-3.0-branding[/COLOR]
Filename: pool/main/f/firefox-3.0/firefox_3.0.5+nobinonly-0ubuntu0.8.10.1_all.deb

```

Why not just remove synaptic then?

```
sudo apt-get autoremove synaptic
```

---

### Post by Jouke74 on 2009-01-28
I think you have to look a bit further down the tree. Firefox also comes with some functionality to install plugins like Flash. For that you probably need to have Synaptic. Might be nice to inform the (K)Ubuntu developers about this. Anyway, to remove Synaptic there is nothing in the way to use: sudo apt-get autoremove synaptic. Although I hope it does not remove Firefox as a dependency then :)

---

### Post by 3rdalbum on 2009-01-28
"Firefox-3.0" depends on "ubufox", which depends on "apturl", which depends on Synaptic. That's a fair ol' chain of dependencies, but Synaptic isn't going to cause any problems installed there. You'll probably like if if you give it a chance - it's a great package manager frontend.

---

### Post by OrangeCrate on 2009-01-28
You can just uninstall ubufox from Synaptic, and then uninstall Synaptic, and you'll be back to a pure KDE install.

ubufox's description:

> Ubuntu Firefox specific configuration defaults and apt support

Extension package for Firefox provides ubuntu specific configuration defaults as well as apt support for firefox plugins/extensions.

**You can uninstall this package if you prefer to use a pristine firefox install.**

---

### Post by OrangeCrate on 2009-01-28
<deleted duplicate post>

---

### Post by mahela007 on 2009-01-28
> **ubuntu27 said:**
> I think that mahela007 has installed Kubuntu (KDE), and since kubuntu doesn't come with firefox, he installed it. And when he installed firefox, synaptic package manager also came with it.

So it seems firefox in Dependant on synaptic? I cannot confirm it right now.
exactly
It's not that I don't like Synaptic though. I used to use ubuntu which had synaptic. Can I use synaptic to install stuff on KDE?

---

### Post by cb951303 on 2009-01-28
> **mahela007 said:**
> Can I use synaptic to install stuff on KDE?
of course! package management is desktop agnostic

---

