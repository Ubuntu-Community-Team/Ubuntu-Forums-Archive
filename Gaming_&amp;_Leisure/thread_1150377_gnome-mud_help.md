---
title: "gnome-mud help"
date: 2009-05-06
forum: Gaming &amp; Leisure
---

### Post by mystmaiden on 2009-05-06
I'm such a dinosaur - I still like text based games but coming from zmud to gnome-mud has left me sort of lost. Zmud does a lot of stuff for you. Can anyone tell me where to get some real basic help with gnome-mud (or a how-to for dummies!)  like setting up custom emotes with variables, etc? I found a forum but it seems to be for developers rather than users. 

What I am trying to do right now is just set up an emote that will have a pattern like

erun <person>

that would come out as :

E runs around Joe (or whatever other name you stick in there)

---

### Post by LinuxGamer on 2009-05-06
If you use Tintin I am pretty sure you can just import your zmud scripts and emotes..after looking around, you may also want to consider tiny fugue, as there is some decent documentation for that as well. I never really liked Gnome-mud because of the lack of docs.

---

### Post by mystmaiden on 2009-05-06
Thanks, LinuxGamer,  I have one question though, and this may  be a little silly - but what is Tintin?

---

### Post by Vadi on 2009-05-06
A terminal-based mud client.

I haven't done much stuff in gnome mud, but I do work on mudlet: [http://www.mudlet.org/](http://www.mudlet.org/) that I can help you with.

---

### Post by Grishka on 2009-05-06
> **mystmaiden said:**
> Thanks, LinuxGamer,  I have one question though, and this may  be a little silly - but what is Tintin?

tintin a powerful cli mud client. I'm not sure if that's what you want, but you can get it [from the repos]("apt://tintin++"). it's terminal-only, so if you need something more clickable, there are many better clients than gnome-mud. it's nice for it's simplicity, but not very powerful. try [kildclient]("apt://kildclient"), or [kmuddy](http://www.kmuddy.com/). or tintin's graphical equivalent, [ggmud]("http://www.ggsoft.org/ggmud/").

---

### Post by Vadi on 2009-05-06
no ggmud: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ggmud](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ggmud)

---

### Post by Grishka on 2009-05-06
> **Vadi said:**
> no ggmud: [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ggmud](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=ggmud)

ah, right. looks like I got it from [this PPA](https://launchpad.net/~frasten/+archive/ppa).

---

### Post by mystmaiden on 2009-05-07
I tried the link, Vadi, it doesn't seem to work.

---

### Post by Vadi on 2009-05-07
[http://www.mudlet.org/?](http://www.mudlet.org/?) works here...

---

### Post by mystmaiden on 2009-05-08
Oops was looking at the wrong link, I tried following the instructions on the page you gave me, Vadi, but I may be in over my head. I got this error :

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B8045AA69930E50

When I tried with Synaptic I got - 
mudlet:
 Depends: libpcrecpp0 but it is not going to be installed
 Depends: libqscintilla2-3 but it is not going to be installed
 Depends: libqt4-network (>=4.4.3) but it is not installable
 Depends: libqt4-webkit (>=4.4.3) but it is not installable
 Depends: libqtcore4 (>=4.4.3) but it is not installable
 Depends: libqtgui4 (>=4.4.3) but it is not installable

---

### Post by Vadi on 2009-05-08
Oh... sorry, your Qt version is too old, being on hardy :(

---

### Post by mystmaiden on 2009-05-08
Thanks for trying to help, Vadi. When I update, I'll try for mudlet again!

---

