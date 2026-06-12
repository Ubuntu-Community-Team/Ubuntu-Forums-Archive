---
title: "Boot hangs at Checking  battery state..."
date: 2009-02-01
forum: General Help
---

### Post by Ubun00btu on 2009-02-01
Running an upgraded system from 8.04 to 8.10
Desktop PC
Intel core Duo
9800 GTX+ x 2 
Evga mobo


Heron was running OK and I decided to upgrade (I don't know why, every single time I upgrade my system gets completely wrecked) to Ibex.  The upgrade process went well, except for one spurious message about nautlius that I figured would be no prob to fix after the upgrade was complete.

I reboot and the splash screen appears and it boots OK.  I install the Nvidia drivers in the hardware manager and then reboot.  Now the system hangs at:

```

*Checking battery state...
/dev/sda:
seting Advanced Power Management level to 0xfe (254)

/dev/sdc:
seting Advanced Power Management level to 0xfe (254)

                                                            [OK]

_
```


...and that's all folks.  It just sits there.

I've tried uninstalling/reinstalling xorg, xorg-server and dpkg'd xorg as well.  I've searched the forums and not found a solution.  I can get to the prompt using the ctrl alt F keys.

I'm at a loss.  Help please!

---

### Post by Ubun00btu on 2009-02-01
deleted...

---

### Post by halfshellheroes on 2009-02-02
I have the same problem on my dell inspiron 530, intel core2 quad. tried getting usplash to work and now i'm stuck.

* Starting GNOME Display Manager...                             [ OK ]
/etc/rc2.d/S30gdm: 108: /etc/init.d/usplash: not found
*Starting System Tools Backends system-tools-backends           [ OK ]
*Starting anac(h)ronistic cron anacron                          [ OK ]
*Starting deferred execution scheduler atd                      [ OK ]
*Starting periodic command scheduler crond                      [ OK ]
*Checking Battery state...                                      [ OK ]

---

### Post by halfshellheroes on 2009-02-02
ok i was able to login by hittinng ctrl+alt+f5 (i think it maybe f4 to f7)
that will ask you to login, type in your username and password, and then type in sudo gdm. that started the computer up for me

---

### Post by Ubun00btu on 2009-02-04
Problem solved for me.  Format.  Reinstall.  Update, reboot.  Backed up the config. Installed the 173 drivers instead if the 177. Reboot.  Working now.

Note to self, use a backup program for all personal data; so every time there's an "upgrade" I can just do a clean install instead of the usual headache of "why isn't this working anymore?"

---

### Post by LK_gandalf_ on 2009-02-18
I've just update my kernel from 2.6.27-11 to 2.6.27-12 as Kubuntu have notified me...and now when I reboot I have the same problem. checking battery state 0xfe 254.
I have a dell xps 1530, Kubuntu 8.10 64bit fresh installed, no upgrade from 8.04.

Luckily I have still the old kernel... I can't understand why they update so often the kernel, is it so necessary?
Linux should be stable, but indeed _from this point of view_ Windows and Mac are far away, it seems an empirical (sad) opinion.
I say, once you installed Mac or Windows I don't think there is the risk to have an unbootable system after an update. In Linux this is not rare.

---

