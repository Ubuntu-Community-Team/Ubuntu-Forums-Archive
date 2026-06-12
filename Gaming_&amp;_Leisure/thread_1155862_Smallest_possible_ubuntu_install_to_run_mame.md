---
title: "Smallest possible ubuntu install to run mame?"
date: 2009-05-11
forum: Gaming &amp; Leisure
---

### Post by iscariot on 2009-05-11
Can someone give me a list of what I can/can't remove to run mame under ubuntu?  I'm trying to get something booting FAST and if I can even remove xorg that'd be great.

---

### Post by Bölvaður on 2009-05-11
mame?

Well you could check the dependancies of that and remove everthing else... that should cover it. But you can also reprogram your kernel to be forced to boot in 2 seconds and remove unnecessary code from it like... sendmail

---

### Post by anjilslaire on 2009-05-11
Do a bare server install with no exta services to get a bare minimum install, without X. Then, do
```

sudo apt-get install xmame-x

```

and see where that gets you.

---

### Post by iscariot on 2009-05-11
Bare server install?  Like off the alternate install cd?

---

### Post by Warpnow on 2009-05-11
> **iscariot said:**
> Bare server install?  Like off the alternate install cd?

Yes.

---

### Post by iscariot on 2009-05-11
This seems easier said than done.  I've tried to install jaunty twice from the install cd and all that happens is that it gets most of the way through the alternative install and then asks for jaunty release 20090420.1.  What does that mean?

---

### Post by anjilslaire on 2009-05-11
Actually, I was referring to the actual Server release, which has no GUI. I believe the alternate CD is just a text installer, but you end up with a full gnome desktop.

Server release:
[http://www.ubuntu.com/getubuntu/download-server](http://www.ubuntu.com/getubuntu/download-server)

Just elect not to install any extras like LAMP. You don't need Apache, MySQL or PHP...

---

### Post by iscariot on 2009-05-11
IT installed but I think I need to install a framebuffer.  How do I install it?

---

