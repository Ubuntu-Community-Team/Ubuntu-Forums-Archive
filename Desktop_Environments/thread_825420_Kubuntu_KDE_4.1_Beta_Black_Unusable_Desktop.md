---
title: "Kubuntu KDE 4.1 Beta Black Unusable Desktop"
date: 2008-06-11
forum: Desktop Environments
---

### Post by CFBauer on 2008-06-11
Hey, thanks for reading.

I recently installed the KDE 4.1 Beta alongside my existing Ubuntu Hardy setup using[ nixternal's repository ]("http://blog.nixternal.com/2008.06.05/hardy-kde-41-beta-1-completed/").

Everything was seemingly normal (not perfect, it was a beta and all) but it was about what one might expect.  After an update (unfortunately I don't remember what packages) my desktop began appearing all black.  The splash screen is viewable, along with some windows.  For instance, I originally thought the issue might be due to compiz loading by default, so I hit alt+f2 and ran "kwin --replace#".  It loaded kwin rather than compiz, and the alt+f2 window was viewable, but the desktop was still black.

I started out with linux and Mandriva 2007 with KDE, and had video memory issues with KDE then (nVidia GeForce 6200 LE).  It seems weird to have these issues since everything seemed fine at first, but I don't know.

Any suggestions would be rad.  Thanks again.

-Chris

---

### Post by CFBauer on 2008-06-12
shameless bump

---

### Post by irrdev on 2008-06-12
There's a 95% chance that this is a bug. After all, KDE 4.1 is just now in beta 1. Not only that, KDE uses an odd release numbering which which dictates that the first stable release of KDE 4 will be version 4.4 or 4.5. KDE 4.1 Beta 1 is therefore really a "Beta of a beta." If you seriously want to continue testing KDE 4.1, then I would simply do a desktop reinstall. Just remember not to install the software updates afterwards. ;)

---

### Post by Naegling23 on 2008-06-12
grrr, I've been having the same problem, I was hoping someone could help.

anyway, if you delete .kde4 in your home folder you can get it to work again.

of course this clears all of your settings.

---

### Post by CFBauer on 2008-06-12
> **irrdev said:**
> There's a 95% chance that this is a bug. After all, KDE 4.1 is just now in beta 1. Not only that, KDE uses an odd release numbering which which dictates that the first stable release of KDE 4 will be version 4.4 or 4.5. KDE 4.1 Beta 1 is therefore really a "Beta of a beta." If you seriously want to continue testing KDE 4.1, then I would simply do a desktop reinstall. Just remember not to install the software updates afterwards. ;)
I thought KDE 4.1 was supposed to be the stable release.

Anyway yes, I completely understand this is a beta.  I didn't not want to come across like I "expected" everything to be perfect.  I just want to let people know what issues I'm having in case they have any suggestions, or to confirm with other users that this issue is in fact a bug.

Or hopefully, if this information is useful to anyone, provide some feedback.

> 
grrr, I've been having the same problem, I was hoping someone could help.

anyway, if you delete .kde4 in your home folder you can get it to work again.

of course this clears all of your settings. 
I'll give it a shot.  This is a fresh install just for the fun of it.  Usually I'm an Ubuntu user, though I'll probably switch to KDE 4 full time when the time is right.

---

### Post by CFBauer on 2008-06-13
I did start fresh by deleting the /home/.kde4 directory, and everything is back to normal.  I hope this helps anyone with a similar issue, and will repost if I learn something new.

---

### Post by CFBauer on 2008-06-13
Goshdarnit, woudln't you know I installed gtk-qt-engine-kde4 and everything turned black again.  This doesn't necessarily mean gtk-qt-engine-kde4 is the culprit because I did not install it last time and I got the same issue.

---

### Post by danns on 2008-10-24
This has to do with compositing I believe.  If you go into .kde/share/config/kwinrc and set [compositing] Enabled=true to Enabled=false and then bounce out of KDE (probably have to hit ctrl-alt-backspace); log back in you should be good to go.

I noticed this problem when I tried to enable some desktop features.  Once I hit apply, the screen went black and kde4.1 was unusable.  I don't have this problem with the gnome desktop features or xfce4 compositing.  

I'm running an nvidia card too.

---

