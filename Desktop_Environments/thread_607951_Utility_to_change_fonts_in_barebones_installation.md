---
title: "Utility to change fonts in barebones installation"
date: 2007-11-09
forum: Desktop Environments
---

### Post by benton on 2007-11-09
Hi there,

I installed Gutsy's "command line system" from the alternate CD and then installed fluxbox. It's working fine but fonts in applications (firefox,leafpad,etc.) are too big for my taste.

My xorg.conf has only two lines in the "Files" section:

```
Section "Files"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi"
EndSection
```

So how can I change the font used for applications in this barebone system?

Regards,

-Benton

---

### Post by kerry_s on 2007-11-09
set your dpi in .Xdefaults> Xft.dpi: ?
stock i think the dpi is 100, so you might want to try 75.
don't forget to put> xrdb -merge ~/.Xdefaults < to your startup

---

### Post by benton on 2007-11-09
I did that and now X refused to run. No new errors or warnings, just the same old messages I see all the time when exiting X. Any ideas?

---

### Post by kerry_s on 2007-11-09
> **benton said:**
> I did that and now X refused to run. No new errors or warnings, just the same old messages I see all the time when exiting X. Any ideas?

my bag, did you add "&" to the end of the line in startup.

xrdb -merge ~/.Xdefaults &

---

### Post by benton on 2007-11-10
Well, X still refused to work that way, but I managed to solve it by moving 

```
xrdb -merge ~/.Xdefaults
```

from .xinitrc to fluxbox's startup file. Thay way I could startx X with 75dpi fonts. Sincere thanks for your help.

Not related but maybe worth mentioning: After the change Firefox seemed to be using smaller than 75dpi fonts though. Menus and dialogs were almost unreadable. Every other application was nicely set at 75dpi, so I replaced Firefox with Epiphany and now everything looks fine. Must be something in Firefox. Thanks again!

---

