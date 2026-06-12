---
title: "dual head xrandr problems after upgrade to karmic"
date: 2009-12-15
forum: Desktop Environments
---

### Post by adamantivm on 2009-12-15
After upgrading to the Karmic Koala, my dual-monitor set-up, which I had working fine for a few releases back, suddenly stopped working as expected.

Before the upgrade, I was using the following commands to switch from single-screen to dual-head

```
xrandr --fb 1680x2048 --output LVDS --mode 1400x1050 --pos 140x998 --output VGA --mode 1680x1050 --pos 0x0
```

and back

```
xrandr --output LVDS --auto --output VGA --off
```

This is a set-up I ended up with that allowed me to work with an extended desktop on two monitors with desktop acceleration enabled , which used to limit the maximum virtual screen size to 2040x2048.

Now, if I use those xrandr commands, either nothing happens, or I get a fully ruined screen (mostly black) out of which the only path I find is to restart gdm from a text console.

Has anything changed around xrandr, perhaps compiz, in Karmic that could have caused this? Any hints on where to start looking for a solution, please?

---

### Post by adamantivm on 2010-01-06
My video card is an Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3

Any hints? Any tips as to how to start debugging? I don't ask for a solution here, just some pointers please

---

### Post by Ryders on 2010-01-21
Same problem here mate, except I'm running Intel Corporation 82Q35 Express Integrated Graphics Controller.. fresh setup.

Been digging for hours, no luck. Have you gotten anywhere?

Filed this;[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/510557](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/510557)

Cheers
Seb.

---

### Post by themtx on 2010-01-21
Intel chipset based device names changed somewhere in the 9.04->9.10 upgrade process for me as well - whether it's xorg itself or the intel drivers, I dunno...

Anyways, check xrandr -q for the correct NEW device names you should be using.  I had to update my xorg.conf accordingly once I found VGA and TMDS-1 had morphed into VGA1 and DVI1.

Hope this helps.

---

### Post by adamantivm on 2010-02-10
> **Ryders said:**
> Same problem here mate, except I'm running Intel Corporation 82Q35 Express Integrated Graphics Controller.. fresh setup.

Been digging for hours, no luck. Have you gotten anywhere?

Filed this;[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/510557](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/510557)

Cheers
Seb.

I haven't made any progress at all this. I tried different versions of the intel driver but only got worse results.

One question I wanted to ask you: I noticed you also found that the problem doesn't happen if you disable desktop effects but, ... even in that case, when you're running dual head with no effects, do all applications appear fine? In particular, have you tried using Open Office?

This is what happens to me with Open Office: [http://img129.yfrog.com/img129/3799/dddo.png](http://img129.yfrog.com/img129/3799/dddo.png)

---

