---
title: "Unity settings overriden on startup, load from file?"
date: 2013-10-10
forum: Desktop Environments
---

### Post by lastlion on 2013-10-10
New install for Ubuntu 12.04 LTS.  Been using it since it came out but did a clean install (after several problems with 13.04 upgrade attempt).  I'm tweaking unity theme settings and get it just how I want to look but on next boot some of the changes are lost, like the color/transparency on dash and launcher.

It looks like very briefly my custom setting will be loaded but then is overridden, however my eyes could be playing tricks on me. 

 Any way to have a terminal command run that loads my settings from a file so I don't have to manually apply them?

---

### Post by mc4man on 2013-10-10
If by color you mean a custom background color then that's broken in 12.04, will only last for the session. (the one set in ccsm > unityshell plugin
I provide a repaired unity build thru a ppa that fixes both use of custom color & the use of black as a custom color in this ppa
[https://launchpad.net/~mc3man/+archive/color-fix](https://launchpad.net/~mc3man/+archive/color-fix)

page has links to both bugs, check & see if that's what's affecting you

---

### Post by lastlion on 2013-10-10
Yeah.  When I reboot I can see my setting briefly then it reverts.  I installed your package (thanks) and it's still happening.

Also, and possibly unrelated, I can't reboot.  I can power all the way down and back up just fine but reboot just leads me to a purple screen.

---

### Post by lastlion on 2013-10-10
Well, after several reboots it's now remembering the settings.  That's odd, but my issue is resolved.

---

### Post by mc4man on 2013-10-10
I just logged into 12.04 so as to give you a screen

Where & how are you making these changes?
Screen shows in ccsm, in this case am using black with medium opacity. This setting sets the  color of Dash Home icon, the launcher & the color & opacity of the Dash itself.

Also using some transparency for both the panel & launcher.

As far as the panel > the opacity of the panel is slightly broken starting in 12.04 on 2 fronts - 
1. doesn't go linear from around 0.3000 to 0.0000. At 0.0000 it's totally trans, from 0.0000 or so to 0.3000 nothing much changes
2. the opacity of the panel can affect the opacity of quicklists in the launcher, it shouldn't but it sometimes does.

If you think the ppa builds are causing you issue or non effective then 
To revert the ppa -
install ppa-purge
```
sudo ppa-purge ppa:mc3man/color-fix
```

---

### Post by lastlion on 2013-10-14
Thanks Mc4man, but it seems to remember my settings now.  I gave up hope but after several reboots it just worked.  

I do have another issue however, which I have [submitted another thread for]("http://ubuntuforums.org/showthread.php?t=2180631").  

The greeter lags, it shows a malformed purple screen for a couple of seconds before displaying my background with login prompt.  It looks like a bug trying to render the greeter screen or something.

I do have dual monitors...but I've had dual monitors on another install of 12.04 without this issue (though that one had auto login).

---

