---
title: "Emerald - Window Title Fonts Too Small"
date: 2008-03-13
forum: Desktop Effects &amp; Customization
---

### Post by TygerFish on 2008-03-13
I've had this annoying problem with Compiz/Emerald for a while.  I'm running Gutsy on a Dell D610 that's been upgraded successfully from an original Feisty installation.

When I boot and log into GNOME, Compiz Fusion seems to work and Emerald loads its theme just fine, except the fonts of the window titles are too small.  (see first attached picture)  The command "emerald --replace" fixes it (see second attached picture), so I tried putting that in the GNOME session startup list.  That didn't work, so I tried "sleep 30 && emerald --replace" to make sure everything had had a chance to load up first, but that didn't seem to help, although it works just fine if run normally from the command line.

I'd rather not spend a lot of time tracking down the problem and completely reinstalling Compiz, since I'm planning on doing a full reinstall to clean out all my cobwebs once Hardy comes out.  Can anyone suggest a quick and dirty way that I can get Emerald to refresh after startup?

---

### Post by alan34 on 2008-03-13
Tried this in your System - Preferences - Sessions menu

compiz --replace -c emerald &

Or go System - Preferences - Emerald - Edit Themes - Title Bar and pick what font and size you want
(top right)

---

### Post by TygerFish on 2008-03-13
> **alan34 said:**
> Or go System - Preferences - Emerald - Edit Themes - Title Bar and pick what font and size you want
(top right)
This doesn't work for my problem... the setting in emerald-theme-manager is already the one I want, but it doesn't display correctly until I run "emerald --replace" or "compiz --replace" manually.

> **alan34 said:**
> Tried this in your System - Preferences - Sessions menu

compiz --replace -c emerald &
This doesn't seem to work as a startup command either... although when entered into the command line manually, it does correctly refresh Emerald like the other commands I mentioned above.

Thanks for the suggestions, though!

---

### Post by alan34 on 2008-03-14
I have attached a screenshot of my sessions command might be no help but ....
by the way if you pick session option tab you can save your running applications
when you log out but unfortunately they are not remembered when you shutdown.


If you are running gnome

To change the title font in the normal window, in a terminal

gconf-editor

click apps scroll down to and click metacity then click general in the window on the right will be titlebar_font double click to edit.

---

### Post by TygerFish on 2008-04-23
> **alan34 said:**
> I have attached a screenshot of my sessions command might be no help but ....
by the way if you pick session option tab you can save your running applications
when you log out but unfortunately they are not remembered when you shutdown.
[http://ubuntuforums.org/showthread.php?p=4768497#post4768497]("http://ubuntuforums.org/showthread.php?p=4768497#post4768497")

If you are running gnome

To change the title font in the normal window, in a terminal

gconf-editor

click apps scroll down to and click metacity then click general in the window on the right will be titlebar_font double click to edit.

Just for the record (i.e., people who come across this thread), that's what I did have in my sessions file and I tried manipulating the metacity font size setting, and neither fixed whatever problem I was experiencing.

I ended up upgrading to Hardy (which has created its own set of problems - [http://ubuntuforums.org/showthread.php?p=4768497](http://ubuntuforums.org/showthread.php?p=4768497)) so I apologize to anyone with similar problems that we'll never know what was causing my issues!

---

