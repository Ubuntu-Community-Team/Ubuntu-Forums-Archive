---
title: "What's going on here? (pic)"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Joey French on 2005-12-11
So, i installed a theme from kde-look that screwed up my setup badly, and now I have little problems all over. I have since removed the theme, and tried to set everything back to default, but i still get stuff like this going on:
[Messed up...]("http://joeyfrench.com/images/problemsnapshot.png")
How can I get my system to go back to the default setup? This has been a royal pain to say the least, and my xfce desktop, as well as my kde desktop, even my firefox fonts and themes have been affected. Is there any way to go back to the original setup?

---

### Post by rosslaird on 2005-12-11
Generally, the hidden (dot) files for all the desktop environments track any tweaking that has been done to the defaults. There's a list somewhere on the forums (search for it) of which files specifically do what. But generally, when you remove them, things return to the defaults.

Ross

---

### Post by anil_robo on 2005-12-11
Alternatively, when you login to your session at bootup, click "sessions" button and select "GNOME-FAILSAFE". Then enter your username and password, and login. Your problem might be solved this way. It worked for me every time I have messed up my display! :) Please post the results here.

---

### Post by Joey French on 2005-12-11
[QUOTE=rosslaird]Generally, the hidden (dot) files for all the desktop environments track any tweaking that has been done to the defaults. There's a list somewhere on the forums (search for it) of which files specifically do what. But generally, when you remove them, things return to the defaults.

Ross[/QUOTE]

Man, I would love to know where these are located. Between making changes in kde, gnome and xfce lately, things are getting kinda screwy. If anyone can tell me how to "reset" my desktop managers I would be forever indebted.

I tried to login with gnome safe mode, to no avail.

---

### Post by rosslaird on 2005-12-11
I'm just looking at my home directory here. Some of the dot folders I've deleted in the past to get to the defaults are as follows:

.cache
.config
.gconf
.gconfd
.gnome (and all variants, such as .gnome2 and gnome_private))
.kde
.metacity
.nautilus
.qt
.xfce

Now, this is not an official list, and removing some of this may bork your system. But think about it: when you create a new user, none of these directories yet exist in the new user's home directory. They are created the first time you login to gnome or xfce or kde, and are dynamically re-created if you remove them. So removing them is generally the best way to start from scratch. But be cautious - back them up first.

Good luck.

Ross

---

### Post by Joey French on 2005-12-11
Hmmm. I will have to look into these. Anyone else have an opinion? Anyone wiped the slate clean by removing these files?

Thanks for the advice, rosslaird.

---

### Post by jasay on 2005-12-11
What I usually do is rename or move the folders rather than remove them.  It's like backing up and deleting in one step. :)

---

### Post by Joey French on 2005-12-12
So, I renamed all of the relevant folders woth an "_old" suffix and logged out. When I logged back in, I was greeted with a brand spankin' new brown Ubuntu "lagoon" desktop. I was like, "Nice, a clean sweep", but as soon as I opened Nautilus, the blacked out/striped file listing was still there. So, I put the old files back, and will wait for further advice.

It's nice to know how to reset your Ubuntu, though. If I ever screw up badly, I will use that.

---

### Post by rosslaird on 2005-12-12
I looked at the pic from your first post. You've probably tried this already, but make sure that under "System --> Preferences --> Theme" you've reverted all three tabs (I use the xfce window manager, so I don't get the gnome metacity options when I select this, so I can't tell you exactly what they're called, but it's something like Window Controls, Icons, and Window Decoration --though that last one doesn't sound right.

It sure looks like a theme problem to me. Try removing/renaming the .theme folder. Also look in /usr/share/themes/ and remove the offending theme (the one you downloaded).

Ross

---

