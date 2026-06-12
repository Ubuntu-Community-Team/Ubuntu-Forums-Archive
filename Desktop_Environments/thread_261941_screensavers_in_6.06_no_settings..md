---
title: "screensavers in 6.06 no settings."
date: 2006-09-20
forum: Desktop Environments
---

### Post by dragons on 2006-09-20
i have the 5.04 version of ubuntu, and loved all of the screensavers in it.  exspecially the engine one (where you can change from the different engines, such as jaguar, and so on). so i install the new 6.06, and it doesn't even have the options to change to the different engines.  i am new to this.  am i missing something?  and can the engine one be downloaded for windows also?  also does anyone out there play unrealtournament on ubuntu?  any help would be appreciated.  sorry for all of the questions.  thanks & have a great day.:confused:

---

### Post by Anduu on 2006-09-21
No you aren't missing anything...well you are actually....

The developers in their infinite wisdom have decided to make GnomeScreensaver the default for Dapper and have seen fit to remove any user control.

Never fear thoigh it is a rather simple matter to replace gnomescreensaver with XScreensaver and take control again.

See this how-to for details:
[http://www.ubuntuforums.org/showthread.php?t=195557](http://www.ubuntuforums.org/showthread.php?t=195557)

---

### Post by CatKiller on 2006-09-21
> **dragons said:**
> also does anyone out there play unrealtournament on ubuntu?

Yes. UT99, at least - my computer isn't up to the task of playing the later ones, although they will play natively too, AFAIK. It's relatively simple to get going.

[LIST=1]
[*]Get your 3D graphics working - you've probably already done this since you're asking about the pretty screensavers.
[*]Find either the ut-install-436.run or ut-install-436-GOTY.run scripts on the Internet, depending on which version you have - you can try [www.lokigames.com](www.lokigames.com), or search for the filenames to find a mirror site.
[*]type ```
sudo ./ut-install-436.run
``` into a terminal window to install the game.
[*]edit /usr/local/games/ut/ut so that the game can be found:```
sudo gedit /usr/local/games/ut/ut
```Replace >     # Is the awk/ls magic portable?
    if [ -L "$fullpath" ]; then
        fullpath="`ls -l "$fullpath" | awk '{print $11}'`"
    fiwith >     # Is the sed/ls magic portable?
    if [ -L "$fullpath" ]; then
        fullpath=`ls -l "$fullpath" |sed -e 's/.* -> //' |sed -e 's/\*//'`
    fi
[*]Type ```
ut
``` to run the game.
[/LIST]

It's a lot easier than it sounds.

---

