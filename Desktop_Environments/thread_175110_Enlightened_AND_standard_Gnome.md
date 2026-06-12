---
title: "Enlightened AND standard Gnome"
date: 2006-05-12
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2006-05-12
I found this thread
[http://www.ubuntuforums.org/showthread.php?t=54476](http://www.ubuntuforums.org/showthread.php?t=54476)
about using Enlightenment as your window-manager rather than Metacity in a Gnome session. In the same thread somebody asked if one could have the choice at the start between standard and enlightened Gnome. I'm also interested on this, so I replied, and it took me two days before I realized I was posting in a Hoary forum :-k .
So I ask again here: did anybody find a method to have both gnome sessions available?
A friend of mine suggested I could create two distinct .gnome2/session files and have a look to the gdm scripts in order to to switch between them based on the choice you make at the start.
Actually gdm seems to launch some scripts, located in subfolders of /etc/gdm, whose names sounds like
PostLogin
PostSession
etc. so it seems I'm done. Actually no: it should not be too difficult to edit those scripts, but I can't find where the information about the possible session choices is stored. So I can't add a Enlightened Gnome session. Any ideas on this? (hope I was able to explain)
Thank you
Andrea

---

### Post by johnc4510 on 2006-05-12
At the log in screen, you should be able to click on session and choose between Gnome standard and Enlightenment

---

### Post by Nonno Bassotto on 2006-05-12
I know this, but I think I didn't explain well. I can log in into enlightenment, but I don't feel comfortable with it, so i don't use it. The only reason I have enlightenment installed is because the thread I pointed to shows how to use enlightenment as a window-manager in a gnome session. But this has a price, you don't have metacity anymore.
Now, what I would like to do is to have in the gdm say Gnome and EGnome sessions, and choose between them. This is not that simple, anyway, because you change window-manager by editing a gnome configuration file: you now would need the choice between two gnome sessions, which load different configuration files. As this is difficult to achieve, a simpler way to get this done would to switch between the two versions of that file with a script loaded by the gdm itself.
I hope this makes the things a bit more clear.
Thank you

---

### Post by stevea1210 on 2006-05-12
shot in the dark here.  If you built a new version of gnome from cvs, could it be installed to a  different location, and use that to launch the EGnome session?  I haven't tried this, just hypothisizing.

---

### Post by Nonno Bassotto on 2006-05-13
Thank you for your answer. I don't know if this would work, but if i understand well, I would have Gnome installed two times, which is quite a waste of space. More important, this way every setting would be lost, so I would have to apply every change twice, a bit too cumbersome, and I don't know if I would get into some conflict.
Anyway if I don't find a better method I could give this a try, hoping not to damage my system.

---

