---
title: "My Gnome died"
date: 2007-03-04
forum: Desktop Environments
---

### Post by JELO on 2007-03-04
Whelp I've been running for a few months and everything is fine desktop wise.  No trouble what so ever.  Today I put a dvd in and while I was watching it on VLC, I got busy doing some stuff and restarted gnome ctrl+alt+backspace.  Apparently this messed something up in gnome.  The only way I got back up was by going into a terminal and installing kde, which at first glance I already don't like.  Unfortunately I hadn't gotten around to doing a full backup.  I've tried failsafe gnome, etc.  I'm able to get to the log on screen, username/pass.  Then I get nothing but a tan screen, no logon sound, nothing.  I've tried uninstalling and reinstalling gnome via this
apt-get remove --purge gnome gnome-core gnome-desktop-environment
apt-get install ...................................................
At first I just tried apt-get remove --purge gnome
then apt-get install gnome
I'd really like not to have to do a full wipe and start over.
Thanks

---

### Post by ComplexNumber on 2007-03-04
go into failsafe and enter the following commands, one after the other:

mv .gconf .gconfOLD
mv .gnome2 .gnome2OLD
mv gconfd gconfdOLD
mv .nautilus .naultilusOLD (this one probably isn't necessary, but it won't do any harm)


then go back to the login screen and try going into gnoe again.

---

### Post by JELO on 2007-03-04
Thanks for the quick response.
I went into failsafe terminal, entered the commands.
It's still doing the same thing.  I went back and double checked to make sure they were all renamed after attempting to login to gnome again.  I found that the .nautilus didn't regenerate, the rest had though.
There's also a .gnome and a .gnome_private would those regen as well?

---

### Post by floke on 2007-03-04
Yep, should do.

---

### Post by JELO on 2007-03-04
Tried moving those and it's still not working.
You guys know of anything else I could try?

---

### Post by ComplexNumber on 2007-03-04
> **JELO said:**
> Tried moving those and it's still not working.
You guys know of anything else I could try?
that seems weird. effectively deleting those files above would give you a virtually new desktop. obviously, then, your personal settings are not at fault.

> 
There's also a .gnome and a .gnome_private would those regen as well?
gtk is for the old toolkit and gnome_private is always empty (at least, i've never known it to be otherwise).




i don't know what to suggest otherwise because its difficult to ascertain what exactly is wrong. i would have thought that it was something thats been corrupted in your personal settings. if i have a brainwave, i'll get back to you.

---

### Post by jpolaski on 2007-03-17
I'm having roughly the same problem with my system. I was changing the icon sets on my theme, and all of the sudden Gnome crashed. I was left with just the background. I tried a CTRL ALT BKSP reset, then after entering my info, I had an empty load bar. I tired the above steps, and it did indeed reset everything, but brought me back to an essentially blank screen (the background wouldn't even load) I'm a total newbie to this, and this is my main computer. \

PLEASE HELP!!!

---

