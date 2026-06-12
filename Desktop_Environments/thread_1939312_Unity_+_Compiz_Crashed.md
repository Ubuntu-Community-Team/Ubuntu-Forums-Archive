---
title: "Unity + Compiz Crashed"
date: 2012-03-11
forum: Desktop Environments
---

### Post by krzheiyah on 2012-03-11
Good day,

I have installed a Azenis GTK+2 Theme for Natty. At first, it all worked fine. I browse on the web on how to enable opacity of dropdown boxes and other stuffs and I saw that Compiz could tweak the theme and so I downloaded it.

It came to my mind to enable some tweaks for my own and have my desktop rock n' roll. So I enabled Desktop Cube. I have no idea what Cubes are for so after enabling it and disabling the Desktop Wall, my Unity crashed in an instant! It has no System Bars, Application Bars, no Sidebars, as in nothing. Only my Wallpapers and my Mouse Pointer

I run on the terminal these codes

```
gconftool-2 --recursive-unset /apps/compiz-1
```
```
unity --reset
```

It worked like a charm! I also uninstalled CCSM and reinstalled it. Upon looking on my CPU, the page-load seemed to be high so I go to CCSM and "Enabled Default Settings"

After reboot, again, my Unity crashed

Any help on how to fix my Unity + Compiz like I have once in my fresh install?

---

### Post by Frogs Hair on 2012-03-11
This is a variation of the same commands I have used successfully . 

Reset Compiz

Code:
gconftool-2 --recursive-unset /apps/compiz-1 
 
Then, open another terminal window, and run:

Code:
unity --reset

If you remain without a desktop and only with a Nautilus bar at the
top of the screen, go back to the first terminal window, and run the following ,

Code:
ccsm

When the CCSM opens check the box with the Uity Plug-in . If all goes well Unity will return . Close the terminal even if you see a running process message .

---

### Post by krzheiyah on 2012-03-11
> **krzheiyah said:**
> Good day,

I have installed a Azenis GTK+2 Theme for Natty. At first, it all worked fine. I browse on the web on how to enable opacity of dropdown boxes and other stuffs and I saw that Compiz could tweak the theme and so I downloaded it.

It came to my mind to enable some tweaks for my own and have my desktop rock n' roll. So I enabled Desktop Cube. I have no idea what Cubes are for so after enabling it and disabling the Desktop Wall, my Unity crashed in an instant! It has no System Bars, Application Bars, no Sidebars, as in nothing. Only my Wallpapers and my Mouse Pointer

I run on the terminal these codes

```
gconftool-2 --recursive-unset /apps/compiz-1
```
```
unity --reset
```

It worked like a charm! I also uninstalled CCSM and reinstalled it. Upon looking on my CPU, the page-load seemed to be high so I go to CCSM and "Enabled Default Settings"

After reboot, again, my Unity crashed

Any help on how to fix my Unity + Compiz like I have once in my fresh install?
Thanks frog. This one's resolved

---

