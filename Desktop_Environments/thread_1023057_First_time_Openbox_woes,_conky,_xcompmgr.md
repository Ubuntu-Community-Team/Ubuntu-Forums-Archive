---
title: "First time Openbox woes, conky, xcompmgr"
date: 2008-12-27
forum: Desktop Environments
---

### Post by Mizutsuki on 2008-12-27
I have been trying to set up open box to my liking and I have come up with a series of questions:

Conky is disappearing if loaded with autostart.sh.  This only happens when the double_buffer setting is on, but when it's off the font of the text is different from the one I chose.  Is there a way to have conky load after everything else already has?  Also, conky disappears if I put the temperature over any further towards the corner in the following configuration:
```
alignment top_lef
double_buffer false
gap_y 0
gap_x 0
override_utf8_locale yes
use_spacer left
use_xft
xftfont sans:size=10
default_color 222222
default_shade_color 999999
background yes

TEXT
${goto 1215}${time %l:%M %P} 
${goto 1200}${cpugraph 20,75}
${goto 1200}${membar 10,39} ${memperc}%








































 ${battery} ${battery_time} ${goto 1170}${color ddedc0}${acpitemp} °C
```
So if I increase that final goto to 1171, the entire thing just disappears (though it doesn't seem to crash.)

On a different note: whenever I run xcompmgr from startup or from terminal, all windows disappear and the only thing that shows up is the cursor and a couple of letters for just a second and then they too get swallowed.  When I kill it, everything comes back.  On the suggestions from other threads I have added the composite extension to my xorg.conf, but to no avail.  The Xorg.0.log says that composite loaded succesfully, too.

This is a Dell Latitude X1 with an intel 915GMS chipset (GMA 900 graphics card.)

Thank you all very much.

---

### Post by Mizutsuki on 2008-12-28
Bump

---

### Post by cylux on 2008-12-28
Would you present your xorg.conf and Xorg.0.log please?

Edit: Also, are you using the autostart.sh for openbox? If so, post as well.

---

