---
title: "WINE: Couldn't find a decent font"
date: 2004-12-03
forum: Gaming &amp; Leisure
---

### Post by halcyon on 2004-12-03
I've been trying to get WINE to work on my computer, I used the Package Manager to install it, and with apps that only use a console it works fine, but whenever I try to run something that actually has a GUI, with the wineconsole command it prints a bunch of gibberish and then gives me a "Couldn't find a decent font, aborting" error.

I don't currently have a Windows installation on this machine, and I don't really want to have to install one; given that, is there a way to fix this?

---

### Post by halcyon on 2004-12-03
Ok, never mind, solved that, but now when I try to run something I get "Could not load graphics driver 'x11drv'.  Make sure that your X server is running and that $DISPLAY is set correctly".

I have no idea what this means.

---

### Post by TravisNewman on 2004-12-04
if you're trying to use wine for games, you probably want to use Cedega. There's a thread in this section with CVS .deb packages.

If not, have you tried running the configuration for wine? If not....
man wine

---

### Post by halcyon on 2004-12-04
Yeah, I ran winesetup if that's what you mean, everything worked fine during that, and the man pages didn't reveal anything useful regarding this problem, at least not what I saw.

My X server should be loaded, if I have Gnome and things running, and I set my DISPLAY variable in ~/.wine/config to ```
;;"Display" = ":0.0"
```

I think that's right, so what's going on with WINE then?

---

