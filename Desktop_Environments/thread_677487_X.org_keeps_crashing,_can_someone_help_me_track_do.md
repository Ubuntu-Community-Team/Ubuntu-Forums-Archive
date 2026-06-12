---
title: "X.org keeps crashing, can someone help me track down why?"
date: 2008-01-24
forum: Desktop Environments
---

### Post by enigma_0Z on 2008-01-24
X keeps randomly crashing on me. Without warning, X will just stop running (as if I had CTRL-ALT-Backspace'd) and GDM will reload.

I am running Compiz on nVidia Hardware, and haven't had an issue like this on this hardware until recently. I can't, however, figure out what is going on.

I've checked /var/log/Xorg.log.0.old, as well as dmesg and there is nothing that seems to indicate what would have caused the crash.

Has anyone experienced this, and does anyone know of where I may find information on my system as to what is causing the problem? Thanks.

---

### Post by katiad on 2008-01-27
Are you running anything specific each and every time it crashes? How often does this happen? When you say it crashes, does it dump you back to the GDM screen all on its own each time, or does it freeze, forcing you to ctrl-alt-backspace? Have you tried running without Compiz to see if the problem duplicates itself even without that?

When researching a similar problem (X kept crashing and freezing, sometimes every few days, sometimes multiple times a day) I was advised to do a memory test when booting up the computer (have memtest run), which, on my machine, found nothing.  Turned out it was my graphics card - on a whim, I'd swapped it with the one I had in my windows box, and X has ran perfectly ever since. However, the half-dead graphics card then fried XP. :mad: Not so cool. Definitely was the card, though - closer inspection revealed obvious physical damage to the card itself.

So... there's some things to look into - if you can't narrow down a software problem, check the hardware. Either memory problems or graphics cards can cause X to freeze up or crash randomly. I spent months seeking out a software solution, assuming that for whatever reason, linux just hated me. Should've checked that the hardware was good first, I guess. *palmface*

---

### Post by enigma_0Z on 2008-01-28
> **katiad said:**
> Are you running anything specific each and every time it crashes? How often does this happen? When you say it crashes, does it dump you back to the GDM screen all on its own each time, or does it freeze, forcing you to ctrl-alt-backspace? Have you tried running without Compiz to see if the problem duplicates itself even without that?

No, haven't tried running w/o compiz yet, that'll probably be my next step--compiz also seems to be crashing regularly (much more regularly that X, but not repeatable)

As far as symptoms, here's what happens: I'm using the computer and X dies (I think I do see compiz die first, because if I have a terminal open it loses transparency), and then almost instantly the screen goes black. Half a second and the nVidia splash screen comes up and then I'm at GDM's login screen. It acts like I Ctrl-Alt-Backspace'd but I didn't.

> **katiad said:**
> When researching a similar problem (X kept crashing and freezing, sometimes every few days, sometimes multiple times a day) I was advised to do a memory test when booting up the computer (have memtest run), which, on my machine, found nothing.  Turned out it was my graphics card - on a whim, I'd swapped it with the one I had in my windows box, and X has ran perfectly ever since. However, the half-dead graphics card then fried XP. :mad: Not so cool. Definitely was the card, though - closer inspection revealed obvious physical damage to the card itself.

Well, it's a laptop. I suppose I could log into Vista and just run it for a while to see if I have stability problems, but it's vista basic (no compositing), so probably wouldn't be a very good test.

> **katiad said:**
> So... there's some things to look into - if you can't narrow down a software problem, check the hardware. Either memory problems or graphics cards can cause X to freeze up or crash randomly. I spent months seeking out a software solution, assuming that for whatever reason, linux just hated me. Should've checked that the hardware was good first, I guess. *palmface*

Hmm... I will try memtest as advised. I recently switched to gnome, so as far as I can tell it could be one of:

Gnome
Compiz
Metacity
Hardware

... But I have found one way to reliabliy reproduce it: CTRL-ALT-F1 (or similar) and run:

```
DISPLAY=:0 metacity --replace
```

That produces output similar to "X lost connection to server" blah blah and some numbers referring to the socket and display

What I think I'll do first is disable compiz's crashhandler plugin, as I think that metacity is   causing me grief--when compiz launches metacity on crash. I'll do some more testing and see what happens, and possibly open another thread/bug report if that is the case.

---

### Post by Nythain on 2008-01-28
oooh, oooh, ooh, my money's on Compiz... never had much luck in the ways of "stability" with it, always thought it was just me :P

---

