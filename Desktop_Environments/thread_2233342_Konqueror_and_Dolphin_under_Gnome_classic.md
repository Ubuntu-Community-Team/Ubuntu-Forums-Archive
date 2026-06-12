---
title: "Konqueror and Dolphin under Gnome classic"
date: 2014-07-08
forum: Desktop Environments
---

### Post by thanuntu on 2014-07-08
Although I find Gnome classic the most useful desktop environment in the Ubuntu ecosystem, there are still some KDE apps I really cannot do away with. While KTorrent and Okular work as they are expected, I have a problem with Konqueror (Dolphin exhibits the same problem although I do not use it).

The pictures speak for themselves:
[ATTACH=CONFIG]254563[/ATTACH] (None selected)
[ATTACH=CONFIG]254564[/ATTACH] (Hover)
[ATTACH=CONFIG]254565[/ATTACH] (Selected)
[ATTACH=CONFIG]254566[/ATTACH] (Selected + hover)

When a selected file or directory is hovered with the cursor, its name disappears. I suppose this has something to do with the color profiles but I could not find anything that suggests a solution. I have also tried this on another machine with similar setup and the problem persists

Any suggestions?

System:
Ubuntu 64-bit (or 32-bit) with Gnome classic (gnome-session-fallback)
Konqueror 4.8.5

---

### Post by echotech2 on 2014-07-09
FWIW, I prefer Dolphin as a file manager.  Under Ubuntu 14.04 64-bit, Unity desktop the same thing happens.  No idea why.

---

### Post by ibjsb4 on 2014-07-09
I am on fallback and konqueror is a 189M download, so ouch, I will not be playing with that package :)

What I have found on my LXQt install is that gnome packages can render poorly.  There are some tweaks for this.  My guess is that the opposite holds true, QT apps in gnome can have problems. Although I did a search on this and did not get any hits.  Maybe your google-fu is better than mine.

---

### Post by thanuntu on 2014-07-09
No ibjsb4, your google-fu is just fine; I couldn't find anything either.

However, your reply suggests a structural problem that may not be easily resolved.

Alas, Konqueror, with its infinite panes and solid behavior, does not seem like a viable choice (don't let me get started on another anti-Nautilus rant!)

Probably SpaceFM is the closest match (and offers an "Up" button out of the box, thanks for nothing Nautilus!)

---

### Post by ibjsb4 on 2014-07-09
Maybe its time for you to setup a LXQt partition.  Even though its all still under development, I find QT4 quite stable and QT5 is just around the corner (source code is out).  We have till 2017 to figure it out :)

---

### Post by Frogs Hair on 2014-07-09
I found a post that stated installing qt4-qtconfig might help with adjusting KDE applications in Gnome. I installed and removed it just to look at it with no harm done.

---

### Post by ibjsb4 on 2014-07-11
Here's a thought ..

I was playing with themes this morning a it occured to me that this could apply to you.  Possibly you could find a theme that would resolve your problem.  Maybe metacity, maybe gtk.  You could then possibly use FrogsHair's idea and tweak it with the qt config package.

---

### Post by thanuntu on 2014-07-14
Thanks for these suggestions.

First of all a big THANKS to Frogs Hair for pointing out the solution:
I installed qt4-qtconfig, launched it and changed themes: Selecting Desktop Settings and GTK+ reproduced the previous behavior, but CDE, Cleanlooks, Motif, Plastique and Windows did the trick!! Hurray! I have Konqueror again!!
The only thing I needed to further tweak was the fonts (from bold italic to regular) and that was it!
Marking this as solved.

Also thanks to ibjsb4 for suggesting me to tweak the themes. BTW, LXQt seems like a nice DE (why would I need a special partition though?)

Finally, I believe in the value of reporting failed attempts so that others do not have to reproduce them:
I tried to tweak the KDE settings through the systemsettings package, but to no avail; the single characteristic I needed to change (i.e. the highlighted text color) did not respond, plus I ended up messing up my font antialiasing due to created .fonts.conf file (which I just deleted).

UPDATE 1: After further tests, I also had to tweak the tooltip text color (from white to black). Another point to note is that font settings have the tendency to revert to these defaults after each theme change.
UPDATE 2: From the themes that successfully correct this issue, only with the Windows theme do we get menu expansion with hovering. For the rest, when you click and expand a menu and proceed to the next one with the mouse, you have to re-click to expand them. Not what we are used to these days. So, Windows theme is the best replacement.

---

### Post by thanuntu on 2014-07-14
To make konqueror the default file manager (i.e. for opening the "Places"):
```
nano ~/.local/share/applications
``` and add the following:
```
[Desktop Entry]
Name=Open Folder
TryExec=konqueror
Exec=konqueror %U
NoDisplay=true
Terminal=false
Icon=folder-open
StartupNotify=true
Type=Application
MimeType=x-directory/gnome-default-handler;x-directory/normal;inode/directory;application/x-gnome-saved-search;
```

Then ctrl-x to save.

Then,```
 nano ~/.local/share/defaults.list
``` and add the following lines:
```
inode/directory=konqueror.desktop
x-directory/normal=konqueror.desktop
```
(solution inspired by [this]("https://help.ubuntu.com/community/DefaultFileManager#Manual_Method"))

---

