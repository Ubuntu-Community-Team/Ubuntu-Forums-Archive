---
title: "Mono repository"
date: 2009-01-19
forum: General Help
---

### Post by Trzone on 2009-01-19
I installed the package moonlight-plugin-mozilla from this repository
[http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu)

And the plugin works, although it's not moonlight 2.0
It works on the firefox that is most up to date to the ubuntu repository
however it does not work for the 3.2a1pre version of firefox.
My question is how would i make the package work?
i'm familiar with the terminal!
Also, does anyone know how to get the moonlight 2.2 version or silverlight 2 compatible version for linux?
thanks!

---

### Post by directhex on 2009-01-20
> **Trzone said:**
> I installed the package moonlight-plugin-mozilla from this repository
[http://ppa.launchpad.net/directhex/ubuntu](http://ppa.launchpad.net/directhex/ubuntu)

And the plugin works, although it's not moonlight 2.0
It works on the firefox that is most up to date to the ubuntu repository
however it does not work for the 3.2a1pre version of firefox.
My question is how would i make the package work?
i'm familiar with the terminal!
Also, does anyone know how to get the moonlight 2.2 version or silverlight 2 compatible version for linux?
thanks!

There's no point in building packages with managed code (SL2) enabled yet. Support is simply too spotty to bother. When upstream pushes out a new tarball, then that's a different matter.

As for bleeding edge versions of Firefox, I've only tested against 3.0 (Intrepid) and 3.1 (Ubuntu MozillaTeam PPA). I imagine I need ANOTHER versioned xulrunner dependency for it - however, if it's not from a package, then it's likely to simply be a case of non-Ubuntu Firefox not looking in the right place for plugins (/usr/lib/xulrunner-addons/plugins on Ubuntu). The plugin symlink needs to be to /usr/lib/moon/plugin/libmoonloader.so

---

### Post by Trzone on 2009-01-20
Thanks! I created a link to /usr/lib/moon/plugin/libmoonloader.so and it worked

---

