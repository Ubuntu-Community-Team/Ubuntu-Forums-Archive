---
title: "no panels!"
date: 2010-03-30
forum: Desktop Environments
---

### Post by hammergil on 2010-03-30
my son has a profile on my laptop and somehow my 4 year old has successfully deleted every panel.  He now only has his desktop with the folders that were there and NO PANELS!  How do I get one back? Thanks!

---

### Post by bigsmitty64 on 2010-03-30
I'm no genius here by any means but, On mine I deleted (purpously)one panel, and now have no  option to delete the other one. Leading me to believe you can't delete both? Is it possible its just on autohide? if you position your curser all the way to the top edge does it show up?  If it does, right click/properties uncheck autohide. Hopefully it's this simple! Good luck.

---

### Post by hammergil on 2010-03-30
There are no panels and I checked for auto-hide...nothing.  Somehow this little guy got rid of all my panels.  Any other ideas?

---

### Post by bigsmitty64 on 2010-03-30
Maybe this will help?  Found it on this sight  [http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)


alt+F2  THEN  type "gnome-terminal" in the provided space, then click run

Then in terminal type:

[LEFT][COLOR=#FF0000]***gconftool &#8211; -recursive-unset  /apps/panel***[/COLOR]
[COLOR=#FF0000][B][I]
[/I][/B][/COLOR]
[COLOR=#FF0000]***no spaces between the 2 dashes!!!!!***[/COLOR]

[COLOR=#FF0000]******[/COLOR]
[COLOR=#FF0000][B][I]Then type:
 [/I][/B][/COLOR][/LEFT]
 [LEFT][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR][/LEFT]
 [LEFT][COLOR=#FF0000]***[FONT=Verdana]rm -rf ~/.gconf/apps/panel[/FONT]***[/COLOR]
[COLOR=#FF0000][B][I][FONT=Verdana]
[/FONT][/I][/B][/COLOR][/LEFT]
 [LEFT][FONT=Verdana]And  one more:
[/FONT]
[FONT=Verdana]
[/FONT][/LEFT]
 [LEFT][COLOR=#FF0000]***[FONT=Verdana]pkill gnome-panel[/FONT]***[/COLOR]
[COLOR=#FF0000][B][I][FONT=Verdana]
[/FONT][/I][/B][/COLOR][/LEFT]
 [COLOR=#FF0000][FONT=Verdana][COLOR=#000000]This should give you back your panels in there default settings. 
 [/COLOR][/FONT][/COLOR]

---

### Post by hammergil on 2010-03-30
yes, i saw that thread.  alt + F2 does nothing.

---

### Post by bigsmitty64 on 2010-03-30
is the F lock on, on the right side of the keyboard?

---

### Post by Dayofswords on 2010-03-30
what i did to reset panels was delete ~/.gconf/apps/panel folder

logout
login
fixed

---

### Post by hammergil on 2010-03-30
thanks all for trying to help.  I didn't want to delete any files b/c this was a problem for a user on my laptop, no problem with my profile.  so i just created another profile for my son and put him in the same group as his old user and gave read/write privileges to users of that group.  I then copied all his files over to his new profile, so we are set.  Thanks again

---

### Post by Dayofswords on 2010-03-31
> **hammergil said:**
> thanks all for trying to help.  I didn't want to delete any files b/c this was a problem for a user on my laptop, no problem with my profile.  so i just created another profile for my son and put him in the same group as his old user and gave read/write privileges to users of that group.  I then copied all his files over to his new profile, so we are set.  Thanks again

anything changed in home (~) doesnt after anyone else
all things said here should have fixed it

---

