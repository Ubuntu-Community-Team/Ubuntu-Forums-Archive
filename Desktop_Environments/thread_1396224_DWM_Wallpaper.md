---
title: "DWM Wallpaper"
date: 2010-02-01
forum: Desktop Environments
---

### Post by sicpsnake on 2010-02-01
Granted DWM is a WM, and not a DE, I had no idea where to post this.

I used to use Awesome a long, long while ago, and while I don't exactly remember how, I know that setting the wallpaper was fairly simple. I am wondering, because I can't seem to get it right, how can I set a wallpaper on DWM? I am currently using fbsetbg to set it manually, but it always defaults back whenever I log out or restart. How can I set a wallpaper that will be there whenever I restart/log out? Thank you so much for the help, in advance.

---

### Post by mcduck on 2010-02-02
You'll probably have to add fbsetb to some startup script (I don't know if DWM has any of it's own, I haven't used it, but if not then ~/.profile should work).

I use Nitrogen to set wallpapers on my Openbox setup, and I've added Nitrogen's startup command to Openbox's startup.sh

---

