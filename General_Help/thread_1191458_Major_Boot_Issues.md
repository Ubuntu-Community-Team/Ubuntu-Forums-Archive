---
title: "Major Boot Issues"
date: 2009-06-19
forum: General Help
---

### Post by trelichiban on 2009-06-19
So my installation of Xubuntu 9.04 has been giving me problems for the past month or so.  It runs on a laptop booting XP as well, and the recent problems have forced me to become almost exclusively dependent upon Windows.

The issue with my Jaunty Xubuntu is inconsistent and miserably frustrating.  It seems that whenever I boot it up, it glides right up to the login screen without a hitch.  And then once I log in to my only account (not 'root'), it all falls apart.  Gnome panels usually get loaded without contents.  The system hangs, causing the desktop icon graphics to load improperly and the mouse to freeze.  Sometimes the programs that should launch automatically don't (NetworkManager).  Half the time the system fails to make a successful boot.  Usually it just takes an unbearably long time.

I don't really know where to start with this.  Perusing the log files didn't yield anything that looked relelvant enough to post, and the latest boot went relatively swimmingly.  NetworkManager loaded, but the top panel contents on the left were mostly missing.

I know that this might be too vague an issue to solve, so I'm ready to do whatever necessary to find more data.  Thanks.

---

### Post by anystupidname on 2009-06-19
As a test initially, I would suggest creating a new user to see if the problem is the same when you login with the new user.

If yes, I don't have a suggestion for you besides reinstalling. (although a better option MAY exist, I just lack foo)

If the problem does NOT exist with the new user, you could try something like renaming the /home/brokeassuser/.gnome2 folder while logged in as the new user or root and then logging in with your original user. You'll lose some settings and panel placement and stuff but that is easily re-setup.

---

