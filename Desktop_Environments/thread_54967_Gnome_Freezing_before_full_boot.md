---
title: "Gnome Freezing before full boot"
date: 2005-08-06
forum: Desktop Environments
---

### Post by jyank on 2005-08-06
Kind of an odd situation here.

I have been using ubuntu for a few weeks now without any trouble, today being no different.  About 30 minutes ago, I noticed somethings were generally going a bit slugish (in gnome) and some of the permissions were acting up.  I couldn't save anything into home, or even load programs unless I was in root.  So, I decided to retart X, but when I tried to get back on, after initially giving my username and password, gnome freezes up.  This is even before the ubuntu sign comes up, etc.  I also tried failsafe gnome, but it did the same thing.  I did a total shutdown and rebooted, but still the same.

Right now I was able to get in using fluxbox.  So, it seems as if its a problem with gnome.

Is there something that could be causing this?  I didn't do anything tonight that I would think would tinker with these settings other than messing with cedega/wine for a bit, but that was it.

EDIT: tried it again and this time was more patient.  After a while of sitting there ( the mouse i can move but thats it) the screen flicks black and takes me back to the login screen.

EDIT 2: I went back to the login in screen and did control shift F1 and logged in. Did sudo su, killall gdm and startx under root.  Gnome started up so the problem must lie within something done with my user account.

---

### Post by jyank on 2005-08-07
quick bump, still not able to get on gnome with my normal user account

---

### Post by wsanders on 2005-08-07
I'm having this same problem; just noticed it today. Any help would be appreciated.

---

### Post by varunus on 2005-08-07
That's really strange that you would have this problem.

Try a failsafe GNOME login from GDM.  Does this let you get into GNOME?

Another thing:  Can you try typing sudo init 1 into a failsafe xterm and then typing init 2 once you go down to single user?  Sometimes, GNOME can leave weird processes running...

One thing you could try (If you're willing to lose all your GNOME settings) is to delete the .gnome2 folder in your home folder.  (Dont think this causes any lasting damage...i don't think so, at least.  google around a bit first.)

---

### Post by jyank on 2005-08-08
I figured out the problem yesterday.  Some how my permissions got changed around for my /home/jyank(user) account.  I logged in under fluxbox went into sudo nautilus and noticed the permissions on the /home/jyank folder were set that the owner and group was root.  

I switched them back to what they should be, owner-jyank group-users and it booted up fine.  No clue how it got changed in the first place, but as long as I didn't lose my theme that I almost have perfected, I don't care :)

---

