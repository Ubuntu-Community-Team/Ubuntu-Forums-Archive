---
title: "fluxbox &amp; diff wallpapers"
date: 2005-07-31
forum: Desktop Environments
---

### Post by djpharoah on 2005-07-31
hi..im running fluxbox 0.9.13 (i think...whatever is the latste)

anyways i want to konw how to get different wallappers on each of the four different screens of the fluxbox WM.

anyone have any ideas? i googled it ..and found fluxspace..but not sure how well this works?

any ideas would be appreciated

djpharoah

---

### Post by dave9191 on 2005-07-31
Fluxspace is the only tool that I know of that will do this. I can't remember if I had trouble installing it or I never got round to trying to install it. 

An alternative is to bind your keyboard shortcuts to execute a command to change to your wallpaper and switch desktops. But that might be a messy solution. (so in the key binding file :ExecCommand fbsetgb -f /you/wall/paper && wmctrl -s DESKTOP_NUMBER). You need to have wmcrtl installed and this wont work changing desktops using the arrows on the toolbar. It might work nicely or it might be a pain switching desktops like this. Only one way to find out :)

Dave

---

