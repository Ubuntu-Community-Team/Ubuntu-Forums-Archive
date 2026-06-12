---
title: "Dual monitor window dragging problem"
date: 2009-04-22
forum: General Help
---

### Post by davidianstyle on 2009-04-22
I have an ATI Radeon 3450 graphics card with ATI's proprietary driver installed.

When I run:
```
$ sudo aticonfig --overlay-on=1
```

I get the following error:
```
Warning: Failed to set hardware overlay to head 1 immediately.
Using xorg.conf
Saved back-up to xorg.conf.fglrx-1
```

I can move my mouse back and forth between the two monitors but I cannot move windows back and forth...

Any ideas?

---

### Post by mshipman on 2009-04-23
If you have the monitors configured as two separate X-screens, then they are independent and moving windows between them is impossible. If you are using, say, Xinerama... then this shouldn't be an issue. Hope this helps!

---

### Post by davidianstyle on 2009-04-23
I'm not sure what that means...

Sorry, I'm a noob :(

---

### Post by Chaka_bum on 2009-07-06
> **davidianstyle said:**
> I'm not sure what that means...

Sorry, I'm a noob :(

I think you just need to enable Xinerama mode in Catalyst Control Center (on Display Options page).

---

