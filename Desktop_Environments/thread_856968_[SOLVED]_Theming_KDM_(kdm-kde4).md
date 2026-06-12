---
title: "[SOLVED] Theming KDM (kdm-kde4)"
date: 2008-07-12
forum: Desktop Environments
---

### Post by ChameleonDave on 2008-07-12
I used to play around with different login-screen themes in KDE 3, but it doesn't really seem possible in KDE 4.

Has anyone managed to theme the latest version of KDM?  I don't mind if it involves a bit of hacking.

---

### Post by NikoC on 2008-07-12
I didn't think it is possible in kde4 via the 'regular' way yet (been doing some reading and I think it was mentioned somewhere that this is low priority for kde developers).

I did manage to change the wallpaper though on my hardy heron lappy: 
in the folder /usr/lib/kde4/etc/kde4/kdm is a file called backgroundrc
I (sudo) opened it with nano and changed the Wallpaper to a custom one...
Going to look for the login box settings later one ;)

Cheers.

---

### Post by ChameleonDave on 2008-07-12
I've been playing with /usr/lib/kde4/share/kde4/apps/kdm/themes/circles, which is the theme that comes with KDE 4 (though not enabled).

Inside, it looks the same as the inside of themes for KDE 3's KDM, but there must be some difference, because I can't get it to accept old themes.

I copied "circles" to "custom" and then started playing with it.  You can make a new background, colours, buttons, etc.  I feel confident that I could make a totally new theme based on that structure.

If I knew the differences between the requirements for the KDE 3 and 4 versions, I could automatically port old themes to the new KDM.

---

