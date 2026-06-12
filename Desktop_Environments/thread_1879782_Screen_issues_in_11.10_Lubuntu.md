---
title: "Screen issues in 11.10 Lubuntu"
date: 2011-11-12
forum: Desktop Environments
---

### Post by dajare on 2011-11-12
I have a set of screen oddities in Lubuntu 11.10. I don't know if they're related...

1. Window re-size: some apps (e.g. Mahjongg, Mines, and Tetris from the Gnome games collection) will not remember their size after being resized (others, like Klotski, are fine). This seemed to be the case for the GIMP but checking again just now, it seems to be "holding" after using the "Re-size" option from the app window's taskbar menu.

2. Sometimes (not always) the screen simply stays black after "waking up" from the screen saver. The cursor is visible and moves around, but ... just blackness otherwise.

3. On bootup, sometimes (I hate "sometimes" in these situations!) I get the "Lubuntu" splash screen, but usually I don't.

Is it possible these are related? It would be great to have resized windows "remembered", solid screensaver behaviour, and consistent display on bootup.

Thanks for any help with this!

---

### Post by amjjawad on 2011-11-12
> **dajare said:**
> I have a set of screen oddities in Lubuntu 11.10. I don't know if they're related...

1. Window re-size: some apps (e.g. Mahjongg, Mines, and Tetris from the Gnome games collection) will not remember their size after being resized (others, like Klotski, are fine). This seemed to be the case for the GIMP but checking again just now, it seems to be "holding" after using the "Re-size" option from the app window's taskbar menu.

2. Sometimes (not always) the screen simply stays black after "waking up" from the screen saver. The cursor is visible and moves around, but ... just blackness otherwise.

3. On bootup, sometimes (I hate "sometimes" in these situations!) I get the "Lubuntu" splash screen, but usually I don't.

Is it possible these are related? It would be great to have resized windows "remembered", solid screensaver behaviour, and consistent display on bootup.

Thanks for any help with this!


Hi and sorry for being late.

From LXTerminal, please run this command and post the output here:

```
sudo lshw -C display
```

Please wrap up the text (output) with code tags - this is how:

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---

### Post by dajare on 2011-11-12
Hi amjjawad - thanks for picking this one up. Here's the output....

```

[PCI (sysfs)]
 
 *-display
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:17 memory:d0000000-dfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff

```The machine is a Toshiba Satellite Pro A100 (FWIW). Any clues? These are issues I never had with Jaunty, just since the 11.10 Lubuntu Oneiric upgrade. Generally, the screen refresh (is that the right term?) seems much slower under Oneiric. Videos ran smoothly in 9.04, whereas now you seem to get 1 frame-per-second-ish.

I'm very glad I took the Lubuntu plunge, but hope to iron out this sort of wrinkle!

---

### Post by dajare on 2011-11-12
[Double post - sorry! Very flakey internet this evening. :confused: ]

---

### Post by Rodney9 on 2011-11-12
i still have the random glitch, one the this morning, first time in a week or two, that when I boot up I get just a black screen with the boot messages in top left corner. 

The odd thing is that the mouse works, but that's it , nothing else does, so all I can do is hold the laptops power button down until it powers down , then reboot.

The other even more random glitch I have is it gets the wrong resolution on start up, too small, this happened much more with Xubuntu, at least with Lubuntu there is the Monitor Settings.

These only happen on the laptop, never a problem with the desktop.

Curiously or maybe not, mine is also a Toshiba, even though I have Intel.

I have always blamed the laptop for the problems, it was a inexpensive model and I have seen others having problems with Toshiba's.

Rodney

```

 *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f2800000-f2bfffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f2100000-f21fffff
```

---

### Post by amjjawad on 2011-11-14
> **dajare said:**
> Hi amjjawad - thanks for picking this one up. 
Sorry again for being late but I'm not at my best these days. Will do my best but don't expect much from me today :)

> ```

[PCI (sysfs)]
 
 *-display
       description: VGA compatible controller
       product: RC410 [[COLOR=Red]**Radeon Xpress 200M**[/COLOR]]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=**[COLOR=Red]radeon [/COLOR]**latency=66 mingnt=8
       resources: irq:17 memory:d0000000-dfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff

```

One of my two test PCs, if I'm not wrong, it has the same Graphics Controller. I need to double check though. I can test or try to produce that but sometimes, it's a machine related more than a system related issue.

> The machine is a Toshiba Satellite Pro A100 (FWIW). Any clues? 
Don't have a laptop with Linux so not sure and can't tell from what were posted. Have you checked whether other users with the same hardware specifications have the same issues?


> These are issues I never had with Jaunty, just since the 11.10 Lubuntu Oneiric **upgrade**. 

Is this an upgrade or fresh new install?

---

### Post by amjjawad on 2011-11-14
> **Rodney9 said:**
> i still have the random glitch, one the this morning, first time in a week or two, that when I boot up I get just a black screen with the boot messages in top left corner. 

The odd thing is that the mouse works, but that's it , nothing else does, so all I can do is hold the laptops power button down until it powers down , then reboot.

The other even more random glitch I have is it gets the wrong resolution on start up, too small, this happened much more with Xubuntu, at least with Lubuntu there is the Monitor Settings.

These only happen on the laptop, never a problem with the desktop.

Curiously or maybe not, mine is also a Toshiba, even though I have Intel.

I have always blamed the laptop for the problems, it was a inexpensive model and I have seen others having problems with Toshiba's.

Rodney

```

 *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f2800000-f2bfffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f2100000-f21fffff
```

Hi Rodney,

How many time you got these two weird errors/issues? can you reproduce that or these are random weird issues?

Your Graphics Controller is different that the OP's controller.

Did you search for similar issues?

---

### Post by Rodney9 on 2011-11-14
Ah that's the problem, it happens totally random, I guess  in the last 3 weeks maybe 3 or 4 times only.

I turn the laptop on at least once a day.

I have seen others with similar problems, but never an answer. I think it's this laptop, not the OS.

Don't worry about me, look after yourself.


Rodney

---

### Post by amjjawad on 2011-11-14
> **Rodney9 said:**
> Ah that's the problem, it happens totally random, I guess  in the last 3 weeks maybe 3 or 4 times only.
If that's a bug, with this random behavior, it's a bit hard to find a fix, that in case it's a bug.
Sometimes, lots of weird things happen with me as well but once I log out and sometimes restart, everything back to normal. Usually, I don't turn the PC off and it stays on for 2-3 days so such issues might be because of what I'm doing. I'm kind of heavy user :P

> I have seen others with similar problems, but never an answer. I think it's this laptop, not the OS.

But it's good to know whether it's from the OS or the laptop :)
Those with similar problems, do they have exactly the same laptop and graphics controller?


> Don't worry about me, look after yourself.

I was unable to stay in bed so thought to do some activities. I'm slowing down big time :D

---

### Post by dajare on 2011-11-14
> **amjjawad said:**
> 

[QUOTE=dajare]These are issues I never had with Jaunty, just since the 11.10 Lubuntu Oneiric upgrade.

Is this an upgrade or fresh new install?[/QUOTE]

Sorry for the confusion: it's a fresh install. I wiped the Jaunty and started from a clean slate.

Definitely the screen refreshing (?) is noticeably slower in Oneiric Lubuntu that it was in Jaunty Ubuntu. A bit disappointed that it should be so, and certainly not a deal-breaker! Odd all the same, unless other developments in the underlying system mean that more demands are now placed on the display.

---

### Post by dajare on 2011-11-16
I'm still concerned about this one, and here's a bit more information:

- I have rarely seen (maybe once? twice?) the Lubunutu "splash screen" on bootup.

- screensavers are ... odd. Many of them do not work at all. These are the ones that seem to work "OK":

. Cubestorm
. Fiberlamp
. Fuzzy Flakes
. Noof
. Pipes

Is there something common to these that the rest of the set don't share? My favourite one is Atunnel :) but this, and most others, are either erratic and freeze the screen on exit, or won't operate at all.

It would be REALLY nice to see this sorted. (Reminder: my hardware configuration is in [post #3]("http://ubuntuforums.org/showpost.php?p=11451263&postcount=3").)

---

