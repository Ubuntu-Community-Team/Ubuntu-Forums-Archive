---
title: "Help: application font problem (cannot be corrected through menu)"
date: 2007-03-12
forum: Desktop Environments
---

### Post by fsando on 2007-03-12
Situation:
This only happens in xgl not in normal gnome session.
Application fonts are not what they should be (a bit too big). This is NOT about **System > Preferences > Font**
Application Font is what is used in applications and in the panels.

Yesterday I did various things: I changed the screen resolution, then changed it back. I installed some extra fonts through Synaptics (this may or may not be significant)
After that Application font was far too big (14pt in stead of 10pt)  any change through the menu had no effect. All other font settings could be changed like before - this only affected Application Font.

I went through the forum and found that starting 'gnome-settings-daemon' explicitly would make the system responsive to changes to Application Font. I have put this in the startup menu so it is started automatically. Now the panel appears to act fully as before. Applications, though, seems to respond somewhat but not entirely. The font size in applications is just a tad bigger than in the panel - it appears to be not the exact same font actually. 

I believe that the way I start 'gnome-settings-daemon' is not the right way to do it but what else can I do? I have no idea what is going on.

What I would like to know is: 
1) What is the correct way to get 'gnome-settings-daemon' started?
2) Where do the panel (and the applications) get their default font settings from?
3) Where are the changes made through the menu stored?
I tried to find the settings by changing them and then searching for recently changed files without success.

---

### Post by fsando on 2007-03-13
bump

---

