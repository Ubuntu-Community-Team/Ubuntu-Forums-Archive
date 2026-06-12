---
title: "Where's the gnome-wallpaper gone in E17?"
date: 2008-04-26
forum: Desktop Environments
---

### Post by darkmaster on 2008-04-26
Hallo everyone, I've got a really particular and weird problem here..I hope there are people able of helping me because this is strange.
I'm on Ubuntu Hardy right now. When I used Gutsy, after installing Enlightenment E17, logging into the session gave me the gnome-wallpaper in background. I mean, after the E17 wallpaper loaded the gnome wallpaper was not there anymore.. but right after logging with GDM, I could see the gnome wallpaper in background.

I'm not sure if that's because I used gnome-settings-daemon or not.. but I used it by the way, for icons, themes, etc.
Well, since the gnome wallpaper was somehow in background, I was able to use it for fake transparencies of the terminal, fbpanel, etc. I just had to set a gnome wallpaper equal to a screenshot of the same E17 wallpaper... I loved that feature.

Now in Hardy I notice that if I run Ubuntu in a gnome session it of course loads the wallpaper, if I do it in an E17 session, even running gnome-settings-daemon the gnome wallpaper is not there behind everything... so I do not have anymore my beloved fake transparency in gnome-terminal... now, why does it happens and how can I fix it, having the gnome-wallpaper be loaded when I log into E17?

I really hope someone out there is wise enough to be able and help me...

---

### Post by darkmaster on 2008-04-26
Update: I found that after launching nautilus in E17, the gnome wallpaper is setted in background.
Nautilus opens a fake desktop window when you opn it (to avoid this you should launch it with nautilus --no-desktop) and a normal browser window. When it crates the fake desktop window, it also settes the gnome wallpaper in background, so, if I killall nautilus, he gnome background remains there in background and the gnome-terminal displays transparency...

why does this happen? What's different from the previous Ubuntu version? Why is nautilus the one who handles this? And why in the previous version it was gnome-settings-daemon who took care of this? Does anyone know how can I find another way, maybe a command / script to be able to handle this background property of gnome without having to run nautilus at all?

---

