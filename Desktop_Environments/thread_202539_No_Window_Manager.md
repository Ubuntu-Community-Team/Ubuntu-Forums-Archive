---
title: "No Window Manager"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Donnut on 2006-06-23
Hi.  I've been searching through the forums for days now,  I have no window manager after I tried installing XGL before first installing fglrx.  The "file" menu always overlaps my hotbar, alt-tab doesn't work, and no windows show up in the notification area.   Also, the minimize and close button-bar just isn't there.  I accidentily logged in as root and everything works right.  What Is this?  Please Help!

---

### Post by Third Thoughts on 2006-06-23
Try changing your session when you login. At the login in screen click the gear wheel in the bottom left. There should be an item to select session. Select either the GNOME session, or if that doesn't work, the Safe GNOME session. Maybe once you get in you can trouble shoot further.

~Andrew S.

PS What do you mean, accidentily logged on as root. Did you make a special root account?

---

### Post by Donnut on 2006-06-23
I am in the failsafe session right now, everything works.  But I can't just stay in failsafe gnome canI?
BTW. No, I just hit startx at recovery mode.

---

### Post by Third Thoughts on 2006-06-23
[QUOTE=Donnut]I am in the failsafe session right now, everything works.  But I can't just stay in failsafe gnome canI?[/QUOTE]

It's probabaly not the best thing to do. See if you have a file in your home directory called .gnomerc. If you do, post the contents. If you don't, then create it and add the line 
```
export WINDOW_MANAGER="/usr/bin/metacity"
```
That should make gnome use metacity on startup.

> 
BTW. No, I just hit startx at recovery mode.

Oh, I didn't know about that trick. When I wanted to startx from recovery mode I always used gdm and then logged in. I'll have to remember that for the future. Thanks :p 

~Andrew S.

---

### Post by Donnut on 2006-06-25
Well, that didn't do it, I think it may have something to do with startup scripts, as when I get into recovery mode and it doesn't run them, I don't have too bad a problem.  Could that be it and how to rebuild them?

---

### Post by Third Thoughts on 2006-06-27
I'm with you on it being the statup scripts, and I thought having a gnomerc file would fix that, but apparently I'm wrong :(. I'm not sure of how to rebuild the scripts. I don't see anything in my home directory that talks about window managers, so I'm kind of at a loss.

~Andrew S.

---

### Post by Donnut on 2006-06-27
Tnx, I think I can fix it, by removing xgl-compiz, I altered the startup scripts quite a bit.  Note to anyone reading this, ALWAYS install good video drivers first, it's a big deal.

---

### Post by Donnut on 2006-06-29
Thx for your help.  I fixed it by putting in the code: metacity --replace.
Thanks everybody!

---

