---
title: "Change Focus / Window behaviour"
date: 2010-08-12
forum: Desktop Environments
---

### Post by damogran on 2010-08-12
Hi there, 

I got an old gnome 2.0 desktop here at work and I wanna change "window comes ins front" behaviour of the windows.

like on my other desktop (compiz) I have a window in front of another and can click the one behind without poping it up above the one in the front. to do so i have to press ALT or click the title bar. dunno how this is called but its a great thing in combination with the sloppy pointer. 

but the only options i could find are these 

-- snip --
gconftool-2 -a /apps/metacity/general
 auto_raise = false
 theme = Esco
 focus_mode = sloppy
 application_based = false
 titlebar_uses_system_font = true
 visual_bell_type = fullscreen
 titlebar_font = Sans Bold 10
 auto_raise_delay = 500
 num_workspaces = 7
 disable_workarounds = false
-- snap --

i bet there is another switch somwhere to set, but right now i cant find it. 

help much appreciated.

thanks in advance!

---

