---
title: "Keyboard layout code wrong after Breezy upgrade"
date: 2005-12-01
forum: Desktop Environments
---

### Post by Clouseau__ on 2005-12-01
Wow, first post after months of browsing these forums!

Hi everyone,

This is a little problem I have not been able to find a solution to.

I use Ubuntu in English but prefer my Keyboard layout to be 'Latin America'. After my upgrade to Breezy about a month ago, I wasn't able to type anything but numbers and after painfully using hex codes and the almighty character map, I was able to login and look at the Keyboard layout options and xorg.conf file, which was apparently unmodified (XkbLayout was 'la', which, as I understand, stands for Latin America). However, Gnome Keyboard layout seemed to have interpreted this as 'Laos' (!!!!) which, I assume, was the reason only numbers were being recognized.

I managed to set the layout to 'Spain' which is similar but not identical to 'Latin America' and have been using it since. If I try to edit my xorg.conf XkbLayout option back to 'la' and restart Gnome, I'll get the 'Laos' keyboard again.

Having searched extensively for XkbLayout options, It seems 'la' does stand for 'Latin America', so this is all just very confusing :(

This is not an urgent matter, but, would anyone know how to fix this?

Thanks a million in advance!

Clouseau__

---

### Post by ranf on 2005-12-01
I'd try `mx' (for Mexico).

---

### Post by Clouseau__ on 2005-12-01
ranf,

Thanks a lot for your reply! 

Just tried what you adviced, but it seems X doesn't recognize 'mx'. I get the following error message when logging to Gnome: 

> 

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd



The keyboard apparently defaults to english. Any ideas?

Again thanks a lot!

Clouseau__

---

