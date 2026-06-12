---
title: "wine + starcraft = bad"
date: 2005-02-03
forum: Gaming &amp; Leisure
---

### Post by RastaMahata on 2005-02-03
I recently installed wine to try out starcraft and warcraft 3.

Surprisingly enough, starcraft ran slow, and warcraft3 was a breeze...

i tried the nice -n 20 thing, but the sound was choppy, without it, it ran damn slow.

Why is an old game running worse than a new one? I also tried cedega cvs, same problem... is there something screwing starcraft or something? also, worms armageddon runs damn slow...

What's wrong?! will this be fixed in warty? or soon enough?

---

### Post by jdodson on 2005-02-03
[QUOTE=RastaMahata]I recently installed wine to try out starcraft and warcraft 3.

Surprisingly enough, starcraft ran slow, and warcraft3 was a breeze...

i tried the nice -n 20 thing, but the sound was choppy, without it, it ran damn slow.

Why is an old game running worse than a new one? I also tried cedega cvs, same problem... is there something screwing starcraft or something? also, worms armageddon runs damn slow...

What's wrong?! will this be fixed in warty? or soon enough?[/QUOTE]

it is not a warty problem, it is a wine/cedega problem.

the next version of ubuntu might contain a new version of wine that fixes the issue.

---

### Post by Botsinge on 2005-02-03
I've had the same problem with StarCraft a couple of months ago, if I remember corretly you have to disable "Accelerated Interprocess Communication" to get it to run smooth.

---

### Post by RastaMahata on 2005-02-03
where could I find that option?

---

### Post by Botsinge on 2005-02-04
If you're running Cedega it's the third option from the end in properties for the shortcut.

In ordinarie Wine I don't really know, I can't find it (at least in my config). In my Cedega-config the option is located under Wineserver and is called:

```
[Wineserver]
"SHMWineserver" = "N"
```If it's of any help.

EDIT: The options I'm talking about is from the Cedega GUI Point2Play.

---

### Post by RastaMahata on 2005-02-05
[QUOTE=Botsinge]If you're running Cedega it's the third option from the end in properties for the shortcut.

In ordinarie Wine I don't really know, I can't find it (at least in my config). In my Cedega-config the option is located under Wineserver and is called:

```
[Wineserver]
"SHMWineserver" = "N"
```If it's of any help.

EDIT: The options I'm talking about is from the Cedega GUI Point2Play.[/QUOTE]

Nope, didnt work! :(

---

### Post by HaloGray on 2005-02-10
Sorry for the slight thread revival, but I got Starcraft running pretty smooth by disabling the mouse catcher option in /home/username/.wine/config

It also allows things to run in windowed mode and still capture keyboard commands.

Find:
"DXGrab" = "Y"

Replace with:
"DXGrab" = "N"

Hopefully it improves for you.

FYI - I'm using straight wine, which I configured with ease thanks to winetools.  I'm not using winex/cedega and have no suggestions for those who are.

I'm using wine version: 20050111-1

---

### Post by RastaMahata on 2005-02-12
[QUOTE=HaloGray]Sorry for the slight thread revival, but I got Starcraft running pretty smooth by disabling the mouse catcher option in /home/username/.wine/config

It also allows things to run in windowed mode and still capture keyboard commands.

Find:
"DXGrab" = "Y"

Replace with:
"DXGrab" = "N"

Hopefully it improves for you.

FYI - I'm using straight wine, which I configured with ease thanks to winetools.  I'm not using winex/cedega and have no suggestions for those who are.

I'm using wine version: 20050111-1[/QUOTE]
 I suppose winetools is apt-gettable?

---

### Post by Kebabji on 2005-10-10
try setting the winecfg to 16 bit res instead of the default (for me at least) 24. it speeds up sc quite fast.

---

