---
title: "How to auto-load console for a specific user?"
date: 2007-03-28
forum: Desktop Environments
---

### Post by Aceman87 on 2007-03-28
Hi

I have installed mpd and ncmpc on my ubuntu machine and I am really happy with them. However, I want to make them easier to access directly. Thus I made a new user named apropriately "Music", which then would load ncmpc at login (and mpd of course, but that is done readily).

I first tried using sessions startup manager to start up ncmpc straight away for "Music": 
```
gnome-terminal --full-screen --hide-menubar -x ncmpc
```

That didn't work out for some reason; so I tried:
```
gnome-terminal --full-screen --hide-menubar --window-with-profile=Music
```
And making the profile would run the command...but alas failure again.

Now I am thinking of somehow making "Music" login directly to a console (like what you get with ctrl + alt + f1, but without the second login procedure of course). I wouldn't need nautilus, gnome or anything besides a command promp and then mpd and ncmpc to start up for this user. Any ideas as to how to pull this off?

Thank you :)

---

### Post by curly_nostrill on 2008-01-15
Great Idea! coinkydinkily, I'm doing exactly the same thing.  See [*my post*]("http://ubuntuforums.org/showthread.php?t=664719&highlight=ncmpc") if you're still around.

---

