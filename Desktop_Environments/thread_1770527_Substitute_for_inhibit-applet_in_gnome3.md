---
title: "Substitute for inhibit-applet in gnome3?"
date: 2011-05-29
forum: Desktop Environments
---

### Post by kansasnoob on 2011-05-29
I've been fiddling with gnome3 quite a bit, several different variants, and something I've yet to find a solution for is a way to "inhibit" the screensaver and/or sleep features if watching a movie or such.

In gnome2 I'd always just add 'inhibit-applet' to the panel, but I've so far found no substitute in gnome3.

---

### Post by kansasnoob on 2011-05-30
bump

---

### Post by aabmas on 2012-01-10
bumb. I'm wondering this too for Debian Wheezy. I know Ubuntu has caffeine for Unity..

---

### Post by cybergalvez on 2012-01-10
what's wrong with Caffeine it installs and seems to work in gnome3, but then again I'm using ubuntu

---

### Post by kansasnoob on 2012-01-11
> **aabmas said:**
> bumb. I'm wondering this too for Debian Wheezy. I know Ubuntu has caffeine for Unity..

No idea how it would work in Debian, but Caffeine does have a .deb here:

[https://launchpad.net/caffeine](https://launchpad.net/caffeine)

---

### Post by aabmas on 2012-01-12
> **kansasnoob said:**
> No idea how it would work in Debian, but Caffeine does have a .deb here:

[https://launchpad.net/caffeine](https://launchpad.net/caffeine)

I tried installing from the .deb and then sudo apt-get install -f, but caffeine depends on python-appindicator which isn't in the repositories. So I tried install caffeine from source, same issue. Finally, I added the [https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa) ppa to my repositories and tried installing that way, but I got the same errors about python-appindicator. So, I tried installing python-appindicator from the .deb in the Ubuntu repos, but that had unresolvable dependencies too..

A quick note, I checked the Debian Unstable (Sid) repo for the dependencies and they weren't there either :(

If I had to guess, I don't think that that caffeine will work in Debian until Unity is ported to it... Any other thoughts/ideas?

UPDATE:

After installing caffeine and python-appindicator from debs, I was able to install the rest of the dependencies from the Debian Experimental repo (apt-pinning). HOWEVER, caffeine still doesn't work :/

---

### Post by kansasnoob on 2012-01-13
> **aabmas said:**
> I tried installing from the .deb and then sudo apt-get install -f, but caffeine depends on python-appindicator which isn't in the repositories. So I tried install caffeine from source, same issue. Finally, I added the [https://launchpad.net/~caffeine-developers/+archive/ppa](https://launchpad.net/~caffeine-developers/+archive/ppa) ppa to my repositories and tried installing that way, but I got the same errors about python-appindicator. So, I tried installing python-appindicator from the .deb in the Ubuntu repos, but that had unresolvable dependencies too..

A quick note, I checked the Debian Unstable (Sid) repo for the dependencies and they weren't there either :(

If I had to guess, I don't think that that caffeine will work in Debian until Unity is ported to it... Any other thoughts/ideas?

UPDATE:

After installing caffeine and python-appindicator from debs, I was able to install the rest of the dependencies from the Debian Experimental repo (apt-pinning). HOWEVER, caffeine still doesn't work :/

I've been so busy with Ubuntu Precise I haven't had time to play in Debian at all, in fact I was busy with non-puter stuff during the Oneiric dev cycle, so I'm now playing "catch-up" during Precise dev :(

That aside it's always been tougher to get Ubuntu apps to work in Debian than vice-versa.

---

