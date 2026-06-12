---
title: "Can't enable 3d effects!"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by tomsa on 2008-02-23
I have just installed gutsy on my gateway t-1625 laptop.  Its video card is an ATI Radeon x-1270.  I have enabled the restricted drivers (fglrx, I think).  When I try to enable 3D effects, I get the error "the Composite extension is not available".  I have already tried reinstalling the drivers.  when I run "compiz" in a termnal, I get the following output:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

I'm enough of a noob that I'm really just not quite sure what to do with this.  Can anyone please help me?

---

### Post by Afkpuz on 2008-02-26
You need to install xgl-server.  while your at it, install the compiz settings manager so you can tweak the effects.

```
sudo apt-get install xserver-xgl compizconfig-settings-manager 
```

---

