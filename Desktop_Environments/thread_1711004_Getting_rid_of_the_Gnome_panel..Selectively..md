---
title: "Getting rid of the Gnome panel..Selectively."
date: 2011-03-20
forum: Desktop Environments
---

### Post by RKendron on 2011-03-20
I have a small problem.  I have one profile on my Ubuntu machine that I want to eliminate the gnome panel from.  When I use the gconf-editor I can change the panel key but it has no effect on my profile.  If I set the key as the default it kills the panel on all my other profiles but not on the one I set it from.   Anyone have any bright ideas on this?

I suppose I could just auto hide the one left offending panel but I truly wanted to get rid of it entirely.  It is irritating having it pop up when I get near the edge of the screen constantly.

---

### Post by Krytarik on 2011-03-20
Check if it is in "Startup Applications", I had that when I tried AWN, disabled it in "gconf", but all of a sudden it was in those instead.

---

### Post by RKendron on 2011-03-21
"Check if it is in "Startup Applications", I had that when I tried AWN,  disabled it in "gconf", but all of a sudden it was in those instead."

Good suggestion but it was not their.  What I did find out was that my "Save running applications on exit" was checked.  The problem is, I do not know how to get it to stop running the already saved applications when it last exited.  Even if you remove the check it keeps loading the last saved application on startup. Normally the solution would be to turn off the application and click the "save running applications now" button but the gnome panel will not shut off.  If you try to kill it in the system monitor it just response itself.  

I need another suggestion hear.  Any ideas on how to clear the auto loading of running applications on exit without actually turning off the application?

---

### Post by false truths on 2011-03-21
There is a way to do it, but it requires accessing every active profile on your computer to modify its startup applications.

```
gksudo nautilus /usr/bin
```

Find gnome-panel in that nautilus window, cut it with the context menu. Next, switch to /home and paste it in every profile's home folder (you will probably need root privileges for this).

Now, when you log out and back in, gnome-panel should be disabled. Another way to disable it at this point is with "killall gnome-panel" but that would waste time if you are going to switch to other profiles and activate it from them.
For the profiles you still want it to run on, start up the profile, open a terminal with ctrl+alt+t and type "~/gnome-panel". Open startup applications like normal and add an entry, with the command as "~/gnome-panel".

That will effectively make the gnome panel a user side application instead of a system side application. You have to repeat for every profile that you intend to use the gnome panels for, but so far I have found it to be the only way to completely disable gnome panels.

---

### Post by Krytarik on 2011-03-21
Just remove the contents of the directory "~/.config/gnome-session/saved-session".

---

### Post by RKendron on 2011-03-22
> **Krytarik said:**
> Just remove the contents of the directory "~/.config/gnome-session/saved-session".
Short sweet and to the point.  It worked like a champ!  No more Gnome Panel in only the profile I wanted to disable it in.  It was the auto save I am sure.  So to recap:

---

### Post by RKendron on 2011-03-22
I Forgot to say thank you VERY VERY much to all that took the time to reply to my request for help!

---

