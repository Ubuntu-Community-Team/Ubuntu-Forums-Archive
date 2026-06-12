---
title: "Can't Customize Appearance Colors"
date: 2008-11-26
forum: Desktop Environments
---

### Post by RandomGameR on 2008-11-26
I have an odd problem.  I'm using Ubuntu 8.10 and I am incapable of changing the color of my themes.  No matter what theme I choose they are always a light blue with silver (the default Clearlooks colors).  For example if I switch to Crux it still has the squares but they're blue instead of purple.  

I am sadly not sure when this started happening but it was not originally this way when I first installed.  This clearly seems like it's not a hardware problem so I'm not sure what other relevant info to give.

Has anyone had this happen to them?  Does anyone have any suggestions on how to fix it?  I'm a relative newbie when it comes to linux' structure but I'm comfortable in a terminal.

---

### Post by nikgare on 2008-11-26
Are you able to change the colours via the Colours tab in the Customise Theme Dialogue box?

Does restting to default in this box help at all?

---

### Post by RandomGameR on 2008-11-30
When I go into that menu I see the defaults are selected for each theme.  I am able to change them to a different color, which will change the color and then freeze all of my applications and gnome-panel.  I am still able to switch desktops though it appears to peg my cpu quite a bit as the compiz effects become choppy and the mouse still moves around like normal.

I changed the color for clearlooks to red then switched themes and the new theme had red instead of blue.  Switching back and forth also caused a lock-up like described, though.  After restarting the colors are back to the default clearlooks ones again.

This is really odd.

update:

The selected theme and colors apply within any gui window run with sudo (i.e. synaptic package manager).  I tried to reinstall anything remotely theme related and I currently have uninstalled gnome-themes which made the appearance window claim that the current theme wouldn't look right due to relying on the uninstalled clearlooks.  The theme whose colors I'm locked into has been completely uninstalled and my themes in the hidden themes folder in my home directory deleted, but I am still locked into this color scheme.

---

### Post by RandomGameR on 2008-11-30
Update: My extremely clever and adorable boyfriend looked at his working install of ubuntu and compared what config files I had that he didn't.  When we deleted .gtkrc-2.0 from my home folder the themes suddenly started to work appropriately.  Anyone know what might have generated that file?

---

