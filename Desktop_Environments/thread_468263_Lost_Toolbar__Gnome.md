---
title: "Lost Toolbar  Gnome"
date: 2007-06-08
forum: Desktop Environments
---

### Post by Cushie on 2007-06-08
Ubuntu 7.04 new install, Gnome desktop. All my top and bottom toolbars disappeared. 

I have tried several suggestions from earlier posts with no success except I did backup the xorg.conf which I managed to reinstate after an abortive attempt to reconfigure xserver-xorg.
Tried 'killall' and then  'gnome-panel' but got no sensible response,  I have run the 'recovery' mode and 'fsck' . So now I'm back to virtually a blank Ubuntu desktop with Firefox and File browser running fortunatly allowing me outside communication. 

Right clicking on screen only allows me to change the background.  I can get nothing else.  I can get some sort of terminal using Ctl Alt F1. and can login to #.
(Incidently I can change session to KDE desktop after a reboot).

This is about my fifth installation of Ubuntu after previous foul-ups and would want to avoid starting another if possible.  There comes time when when patience wanes.
I would appreciate any further assistance

---

### Post by yabbadabbadont on 2007-06-08
Boot into your normal Gnome session.  (the one without the panels)  Hit Alt-F2.  In the run dialog that pops up enter, "gnome-panel" without the quotes, and hit enter.  That should have started one for you.  Now you can right click on that panel and add another one if you want.  Be sure to go to System->Preferences->Sessions and save your session so that the panels will show up the next time you login.

---

### Post by Cushie on 2007-06-08
Alt F2 does nothing.  Ctl Alt F2 get to a black screen with the $ prompt.
'gnome-panel' offers --help but I get no clue from the help.
Then tried the same as # prompt with same result.  So how do I run a 'gnome-panel' command maybe with some parameters?

---

### Post by yabbadabbadont on 2007-06-08
At the command prompt, search all the hidden directories in your home directory for files that contain the word, "session", in them.  Rename or remove those files then logout and back in.

Edit: You'll need to us the "-a" option with ls in order to see the hidden files and directories.

---

### Post by Cushie on 2007-06-10
I don't know how to use search in the terminal.  I tried the File Browser Search and it came up with nothing ( suspect it is not functioning)  So the I looked manually and found the following in my /Home/myname  Folder:

/.gconf/apps/gnome-session

/.gnome2/session

/nautilus/several saved sessions

/.xsession-errors

Do you believe this to be sufficient? Then I could delete them.


As a separate try could I remove the Gnome desktop complete and the reinstall?

Your help appreciated before another complete reinstall.

---

### Post by Cushie on 2007-06-10
Fine business!
Deleted:-

.gconf
.gnome
.gnome2

in /home/myname folder and all seems back to normal.

Is this Rocket Science?  Where is 'Goback' 'Restore'?
help appreciated yabbadabbadont

Cheers   :D

---

### Post by cedarmark on 2008-06-17
> **yabbadabbadont said:**
> At the command prompt, search all the hidden directories in your home directory for files that contain the word, "session", in them.  Rename or remove those files then logout and back in.

Edit: You'll need to us the "-a" option with ls in order to see the hidden files and directories.


Hi, 

I am a complete novice with the same problem, please can you assist me how to do a search for files?

Chris

---

