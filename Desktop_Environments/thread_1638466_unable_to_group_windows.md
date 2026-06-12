---
title: "unable to group windows?"
date: 2010-12-05
forum: Desktop Environments
---

### Post by DatBugler on 2010-12-05
I'm running Kubuntu 10.10 and for some reason I can't use tabbed windows. The options for tabbed windows appear to be configured correctly in KDE Settings, but the window menus don't have the option to group windows and the middle click drag doesn't do anything. I use the Bespin window theme, but I switched briefly to Oxygen and had the same problem. Suggestions?

---

### Post by inobe on 2010-12-05
it could possibly be the theme, note: switching themes sometimes requires a restart for some things to take affect.

i have kde 4.5.4 and grouping works fine with multiple themes.

---

### Post by DatBugler on 2010-12-05
Yeah, I rebooted after switching between Bespin and Oxygen. No dice. I am on KDE 4.5.1.

---

### Post by DatBugler on 2010-12-06
Any ideas I could try? I don't know my way around KDE under the hood at all, since I switched fairly recently, so any help would be most appreciated, even if it's just pointing me to a likely configuration file.

---

### Post by inobe on 2010-12-06
[http://www.youtube.com/watch?v=TCL_6YNgc8w](http://www.youtube.com/watch?v=TCL_6YNgc8w)

see if those settings work

---

### Post by DatBugler on 2010-12-06
I have precisely those settings enabled, and the "move window to group" item does not show up on my window menus. The middle click drag likewise has no effect. I have tried this under both Oxygen and Bespin, as noted.

---

### Post by inobe on 2010-12-06
then we must reset your desktop or we can upgrade it.

reseting the desktop will remove any settings you've made, that's the downside but you won't lose data.

an upgrade will take you to kde 4.5.4, kde 4.5 has something like 16,000 bug fixes, it's your choice, however if it's a settings issue then you upgraded without solving the problem and are forced to reset your desktop anyway.

---

### Post by DatBugler on 2010-12-06
Well it sounds like I've got nothing to lose by trying the upgrade route first. How do I go about that? I am up to date with the Ubuntu repositories.

Also is there a nice way to backup my KDE settings? I just made a copy of .kde and .kderc, but I didn't really look around to see if there's a tool for settings backup.

---

### Post by inobe on 2010-12-06
have a look here.

[http://ubuntuforums.org/showpost.php?p=10175304&postcount=4](http://ubuntuforums.org/showpost.php?p=10175304&postcount=4)

and here, this ones important.

[http://ubuntuforums.org/showpost.php?p=10175344&postcount=5](http://ubuntuforums.org/showpost.php?p=10175344&postcount=5)


btw i never backed up these settings, i only took the delete .kde folder route to reset, i never really needed to backup these settings.

you can start a thread just for that if you wish.

---

### Post by StephanG on 2010-12-07
Grouping windows is a feature that has been built into the Oxygen Window Decoration, and later Aurora.  So, if your using a different window decoration, it won't work.

NOTE:  The window decoration is NOT the same as the style that you choose under Appearances.

Its a little confusing since there is an Oxygen KDE Style and an Oxygen KWin decoration.  As well as both a Bespin KDE Style and a Bespin KWin decoration.

The KWin decoration is found in System Settings >> Workspace Appearance >> Window Decorations.

Just make sure that its set to either Oxygen, or one of the themes that use the Aurora engine.  (Aurora Themes have been integrated in 4.5, so its not immediately clear which are Aurora Themes.  But the majority should be.)  Bespin's Decoration is NOT an Aurora theme, so it won't support window grouping.

But if you are using a decoration that supports grouping, the only other alternative I can think of is upgrading and hoping that the issue is resolved.

Best of luck!

---

### Post by DatBugler on 2010-12-09
[QUOTE=StephanG]NOTE: The window decoration is NOT the same as the style that you choose under Appearances.[/QUOTE]
Aha! That was what I was missing. I feel like a doofus now.

---

