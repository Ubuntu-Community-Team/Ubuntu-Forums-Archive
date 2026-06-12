---
title: "playing with xrandr"
date: 2009-06-04
forum: General Help
---

### Post by scales on 2009-06-04
hi all.

i have an eee1000he and am working on hooking it up to an external monitor (1440x900).  I have set the virtual resolution to 2048 (since that is the max my vid card will allow) and as a result must stack the screens, 1024+1440=2464, so they fit.

I use the following command to get things working:
> xrandr --output LVDS --auto --primary --output VGA --auto --above LVDS
gconftool --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1

I have the laptop monitor set to be below the external one, and all works except for the fact that the menu bar likes to go to the bottom of the external monitor which is above my laptop screen.  I put that last line in the code to make the menu bar get onto the correct screen.  I tried to use that "--primary" for the same reason but no luck.  I also know that my desktop icons like to arrange/appear in the upper left most part so again, that would be on the external screen.

Is there any way to not have the icons or menu bar go onto that external screen?

Also, if i turn off the computer with the external screen on, the next time i start up my menu bar icons are all jumbled! can i fix this some how?  this problem doesnt happen if i disable the external screen before turning off....

---

