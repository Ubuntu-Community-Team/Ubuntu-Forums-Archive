---
title: "Two icons for same application in Dash"
date: 2016-09-08
forum: Desktop Environments
---

### Post by Lars Noodén on 2016-09-08
I'm getting two icons in the Dash for the same application.  Unfortunately the two behave differently.  One gets the application running with no problem.  The other doesn't. 
If it's any help the wrong icon (and presumably .desktop file) get attached to The Launcher no matter how I launch the application. 

Attached is a screenshot of the problem of double icons.  In this case it is showing Jitsi.

How do I remove the wrong icon?

PS.  Uninstalling, even purging, the application and re-installing it has no effect.

---

### Post by vasa1 on 2016-09-08
> **Lars Noodén said:**
> I'm getting two icons in the Dash for the same application.  Unfortunately the two behave differently.  One gets the application running with no problem.  The other doesn't. 
If it's any help the wrong icon (and presumably .desktop file) get attached to The Launcher no matter how I launch the application. 

Attached is a screenshot of the problem of double icons.  In this case it is showing Jitsi.

How do I remove the wrong icon?

PS.  Uninstalling, even purging, the application and re-installing it has no effect.

Wont' you have two desktop files for jitsi in */usr/share/applications*? What do their *Exec=* lines look like? Maybe that may afford some clues?

---

### Post by Lars Noodén on 2016-09-08
> **vasa1 said:**
> Wont' you have two desktop files for jitsi in */usr/share/applications*? What do their *Exec=* lines look like? Maybe that may afford some clues?

I've tried removing all the .desktop files for Jitsi, for example, and not found any difference.  I've also tried changing the values in /usr/share/applications/jitsi.desktop to strange stuff just to see the changes but the changes don't show up.  So The Launcher is getting its icon and other info from somewhere else.  

However, the modified .desktop file is used by The Dash.  See the attached image.  The legitimate icon is labeled "jitsix" and has a CC icon.  So I can see which of the two icons is legitimate (the changed one) rather than relying on position.  Where is the illegitimate icon coming from?  It's the one that the Launcher is pulling in.

---

### Post by vasa1 on 2016-09-08
By any chance would the output of ```
which jitsi
``` or ```
locate jitsi
``` help? Their site points to the same download for Ubuntu and Debian :confused:

---

### Post by Lars Noodén on 2016-09-08
> **vasa1 said:**
> By any chance would the output of ```
which jitsi
``` or ```
locate jitsi
``` help? Their site points to the same download for Ubuntu and Debian :confused:

*which jitsi* shows the executable with full path : /usr/bin/jitsi
That executable works fine, except that the Launcher ends up with a lame icon.  If I launch from the shell, things are ok, if I launch from the Launcher, then jitsi can't find my accounts

*locate jitsi.desktop* shows only the one true desktop file : /usr/share/applications/jitsi.desktop
That's the one that can be modified as shown in the above post.

---

### Post by mc4man on 2016-09-09
take a look in /usr/local/share/applications & ~/.local/share/applications

---

### Post by Lars Noodén on 2016-09-09
> **mc4man said:**
> take a look in /usr/local/share/applications & ~/.local/share/applications

Thanks.  I checked.  I have no /usr/local/share/applications/ directory at all but looking in ~/.local/share/applications/ there were some files which I grepped for "jitsi"  One named "lib.desktop" was there and contained the wrong settings.  Removing it fixed the situation:  now the Dash shows only one icon, the correct one, for Jitsi, and when I bind it to the Launcher, it works as it should.

---

