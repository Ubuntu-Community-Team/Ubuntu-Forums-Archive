---
title: "Changed OpenGL settings, now desktop frozen"
date: 2014-08-05
forum: Desktop Environments
---

### Post by zalvera on 2014-08-05
Disclaimer: I'm on openSuse not Ubuntu but I believe this is a KDE  problem so I don't think that matters? I was fiddling with display  settings trying to fix a screen tearing issue and now when I try to log  in I end up with a frozen blank screen. I can't remember the original  setting but I remember I changed it to OpenGL 3.1. I'm able to log into  IceWM but can't access the KDE system settings from there, at least not  graphically. If anyone knows how I can restore this setting from the  terminal I'd be very grateful. 

(Is there such a thing as a  'reset all settings to default' button or command? This definitely won't  be the last time I screw up.)

EDIT: I renamed /.kde4 in my home directory but the problem persists. I'm able to log on with other accounts okay though. Where else could the settings be hiding?

EDIT2: Okay, figured out the setting. In Desktop Effects > Advanced I changed compositing type from XRender to OpenGL 3.1. Below that I changed Tear Prevention from Automatic to Full Scene Repaints. Here's hoping googling these sheds some light.

---

### Post by zalvera on 2014-08-05
Solved it! Replying in case anyone else needs it someday. In /home/[user]/.kde4/share/config there's a file called kwinrc. Under 'Compositing' there's a setting Enabled=true. Changed this to false and was able to log back in.

---

