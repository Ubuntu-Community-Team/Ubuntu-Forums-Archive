---
title: "Gstreamer update help"
date: 2009-06-08
forum: General Help
---

### Post by Frogging101 on 2009-06-08
I needed to install a newer version of gstreamer, I downloaded the latest tarball from the gstreamer site. I compiled and installed it. Now there are two copies of gstreamer, one from synaptic, one from the main site, this is causing problems. how do I remove the synaptic one? If I just into synaptic and 'remove', it will remove vital packages such as 'ubuntu-desktop' I don't know what to do.

The version I got is not in synaptic, in case you were wondering.

---

### Post by Frogging101 on 2009-06-08
Why does it seem that I'm the only one without almost immediate replies?

---

### Post by Soul-Sing on 2009-06-08
Using synaptic uninstalling gstreamer it will remove vital packages such as ubuntu-desktop. Thats correct.
There was not a .deb available of this new gstreamer version?
(in karmic repos. for instance?)

---

### Post by Frogging101 on 2009-06-08
Exactly, how do I do it WITHOUT uninstalling those vital packages?

---

### Post by Soul-Sing on 2009-06-08
> **Frogging101 said:**
> Exactly, how do I do it WITHOUT uninstalling those vital packages?

many programm's depend on gstreamer, imho you have to find a .deb if this new version, otherwise your left with a "cripple" system. which gstreamer version-number is it?

---

### Post by Frogging101 on 2009-06-08
0.10.23, and there is no .deb on their site. have a look: [http://gstreamer.freedesktop.org/src/gstreamer/](http://gstreamer.freedesktop.org/src/gstreamer/)

---

### Post by Soul-Sing on 2009-06-08
: [https://launchpad.net/ubuntu/karmic/hppa/gstreamer-tools/0.10.23-1](https://launchpad.net/ubuntu/karmic/hppa/gstreamer-tools/0.10.23-1)

---

### Post by Frogging101 on 2009-06-08
Wrong architecture, hppa.

---

### Post by Soul-Sing on 2009-06-08
: [http://packages.ubuntu.com/zh-tw/karmic/libdevel/](http://packages.ubuntu.com/zh-tw/karmic/libdevel/)

---

### Post by Frogging101 on 2009-06-08
so... which package would I want? I don't know if it makes a difference, but why are you giving me results from karmic? I think the package is libgstreamer0.10-dev. Is that it?

---

### Post by Soul-Sing on 2009-06-08
> **Frogging101 said:**
> so... which package would I want? I don't know if it makes a difference, but why are you giving me results from karmic?

1) Why do you want this new version of gstreamer? The only thing  like/want to make clear is that you need an (ubuntu) .deb.

2) I'am only trying to be helpful, thats all.

---

### Post by Frogging101 on 2009-06-08
Thank you for all of your help. I was just wondering about the karmic thing because I wanted to learn more. I want the new version because I needed to install farsight, for aMSN. You have been very helpful, and now my problem is solved. Thank you!

---

