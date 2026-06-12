---
title: "kde issue - only wallpaper visible"
date: 2007-11-02
forum: Desktop Environments
---

### Post by sundar261 on 2007-11-02
When I log into kde session, I am able to see only the desktop wallpaper.  There is no panel or windows or desktop icons visible. When I do Alt+f1 I get the kmenu but once i select an application, only the wallpaper is displayed. 

I was able to work with kde for sometime.  I was trying to install and run screenlets on kde when I suddenly lost (only wallpaper display) the kde session.  I am also running compiz (not sure if it crashed).  compiz was running for atleast 10 days without any issues.

I tried to re-login/restart but the same result.  When I login I am able to see panel and all the desktop icons, then the screen goes blank and comes back with only the wallpaper.  Alt+tab does not work too.

When I login to gnome everything compiz+screenlets works well.

I am using gusty.  

-Sundar

---

### Post by overdrank on 2007-11-03
> **sundar261 said:**
> When I log into kde session, I am able to see only the desktop wallpaper.  There is no panel or windows or desktop icons visible. When I do Alt+f1 I get the kmenu but once i select an application, only the wallpaper is displayed. 

I was able to work with kde for sometime.  I was trying to install and run screenlets on kde when I suddenly lost (only wallpaper display) the kde session.  I am also running compiz (not sure if it crashed).  compiz was running for atleast 10 days without any issues.

I tried to re-login/restart but the same result.  When I login I am able to see panel and all the desktop icons, then the screen goes blank and comes back with only the wallpaper.  Alt+tab does not work too.

When I login to gnome everything compiz+screenlets works well.

I am using gusty.  

-Sundar

Hi you could try and remove compiz and see if that brings your desktop back 
```
sudo apt-get remove compiz compizconfig-settings-manager compiz-plugins compiz-fusion-plugins-extra 
``` Then you could try and reinstall. Hope this helps and good luck! :KS

---

