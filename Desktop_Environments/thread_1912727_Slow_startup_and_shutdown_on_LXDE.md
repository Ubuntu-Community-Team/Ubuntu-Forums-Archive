---
title: "Slow startup and shutdown on LXDE"
date: 2012-01-21
forum: Desktop Environments
---

### Post by Lars Noodén on 2012-01-21
I'm using LXDE via Lubuntu on an old G4 and it runs absolutely great, once it's started.  

Starting is very slow, it takes about 8 or 9 minutes from power-on to being able to type.  Shutdown is also slow, it takes about 4 or 5 minutes from clicking shutdown until the machine actually powers off.  What can I edit or change to speed up these processes?

---

### Post by SteveDee on 2012-01-21
> **Lars Noodén said:**
> I'm using LXDE via Lubuntu on an old G4 and it runs absolutely great, once it's started...

I don't know what a G4 is, but as you are happy with the system once running, I suggest you take a look at the syslog to see what is taking its time when you start the system. The basic install does not include a log viewer but you can add: gnome-system-log via Synaptic.

Is the long delay just before the login screen, or does it also take a long time after loggin in?

---

### Post by Lars Noodén on 2012-01-21
( [G4](http://en.wikipedia.org/wiki/PowerPC_G4) is one of the PPC processors that Apple (and others) used to have before they downgraded to x86. ) 

The slowness is before the login screen.  Once it's time to log in, everything is fast.  Same with shutdown, everything is fast, until the actual shutdown process starts.

Edit: removed incorrect excerpt from syslog

---

### Post by oldrocker99 on 2012-01-21
I have noticed this too; logging off in XFCE takes 'forever.' I usually end my session with a 'sudo shutdown -r now' because it's faster than waiting for XFCE to log me off.:confused:

---

### Post by Lars Noodén on 2012-01-21
```

...
Jan 21 15:33:36 g4 kernel: [   20.537820] [drm] nouveau 0000:00:10.0: 64 MiB GA
RT (aperture)
Jan 21 15:33:37 g4 kernel: [   20.567843] [drm] Supports vblank timestamp cachi
ng Rev 1 (10.10.2010).
Jan 21 15:36:52 g4 bluetoothd[760]: HCI dev 0 up
Jan 21 15:36:52 g4 avahi-daemon[466]: Joining mDNS multicast group on interface
 eth0.IPv6 with address fe80::20a:95ff:fea0:1ca0.
...
Jan 21 15:36:55 g4 avahi: For more information, see http://avahi.org/wiki/Avahi
AndUnicastDotLocal
Jan 21 15:38:33 g4 kernel: [  219.515485] [drm] nouveau 0000:00:10.0: Setting d
pms mode 3 on TV encoder (output 2)
Jan 21 15:38:33 g4 kernel: [  244.030487] BUG: soft lockup - CPU#0 stuck for 23
s! [Xorg:896]
...


```

---

### Post by SteveDee on 2012-01-21
I guess you need to look at bluetooth & whatever the TV output relates to. Have you got some kind of TV card installed?

---

### Post by Lars Noodén on 2012-01-21
No, there is no TV or bluetooth.  So it's looking for somethings that are not present and should skip right away.  I'm not sure how to turn off looking for them.

---

### Post by SteveDee on 2012-01-22
> **Lars Noodén said:**
> No, there is no TV or bluetooth...

In the absents of any other suggestions I can only suggest you take a look here: [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

Also use googlebuntu to search: "g4 kernel"

---

