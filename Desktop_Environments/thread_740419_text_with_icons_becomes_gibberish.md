---
title: "text with icons becomes gibberish"
date: 2008-03-30
forum: Desktop Environments
---

### Post by johnnyhop on 2008-03-30
Its strange and silly, a bit annoying as well.  Since recently when I log out and remained logged out long enough for the monitor to time out past screen saver and shut off, the text associated with the log in screen icons would turn into tall skinny rectangles resembling a bar code but with constant width.  When clicking the users icon the correct user name would appear in the user name window and the password below would show asterisk's as typed.  Upon login the same effect was below the desktop icons and the start menu's text was likewise.  After about a minute the text below the icons reverts to normal one at a time after moving the mouse cursor over the icons.  Then the start menu returns to normal after the third click of the "K" KDE logo start menu icon.  The condition is subject to coming back in time.  Applications work more ok except links in the web browser--Firefox, haven't checked Konqueror.  A full restart has corrected this condition until log off and Kubuntu shuts off monitor.

Added after more monitoring of the symptoms:  The problem isn't related to KDE turning the monitor off as originally suspected.  It appears to be more related to the time lapse since the reboot.  Clamscan was run in home, no infections detected.  Also after time passes the symptom will occur upon passing the mouse pointer over the desktop icons then once all icons have the corrupted text, passing the mouse pointer the icons restores normal text.  A toggling effect.

OK two weeks have passed and I've a little more to note.  The symptoms mentioned above only appear after a logout.  When logging in after a reboot or a console login the condition does not occur.  I was experimenting with /dev/MAKEDEV trying to make a block device for the ZIP100 to work, not really sure what I was doing before the first occasion of the symptoms.  But alas dabbling with Kubuntu 8.04 beta discovered the ZIP100 to mounted with no problem "out of box."  Hopefully the 4/24 upgrade we're anxiously awaiting will correct the problem, otherwise if no one has any ideas, I'll do a full format and reinstall.

---

