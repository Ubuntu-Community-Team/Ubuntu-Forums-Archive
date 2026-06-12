---
title: "Remove the ugly menu arrow[EASY WAY]"
date: 2009-07-02
forum: Desktop Environments
---

### Post by basiix on 2009-07-02
We will be editing some [COLOR=Red]system[/COLOR] files so you'll need to get permissions for a folder. You can [COLOR=Blue]ch-mod[/COLOR] or just type [COLOR=Blue]gksudo nautilus[/COLOR] in terminal to open the Nautilus in root.
Then just follow the next steps:

1. Navigate to the following folder:
[COLOR=Red]/usr/share/themes/YOUR THEME/gtk-2.0/Images/Arrows[/COLOR]

a. Replace [COLOR=Red]YOUR THEME[/COLOR] with whatever theme you are using at the moment or navigate thru the themes folder and find yours. 

b.If your using a custom theme go to your Home folder, hit CTRL+H to show hidden files and find the folder named .themes and find the right theme your using in there.

2. In the [COLOR=Red]Arrows[/COLOR] folder just find two pictures usually named [COLOR=Red]down-arrow.png[/COLOR] and [COLOR=Red]down-arrow-dark.png[/COLOR]. Usually the first two ones.
    Once you find them just [COLOR=Red]DELETE[/COLOR] both.

3. That should do it. You can follow the same steps for other themes.

a. Now you can just logout, reboot or whatever is easier for you.

b. You can also type [COLOR=Blue]killall gnome-panel[/COLOR] in terminal and that'll reset gnome for you.

Good luck!
If you have any questions, just ask!

---

### Post by philcamlin on 2009-07-02
good to know

---

### Post by sdlynx on 2009-07-02
what is the ugly arrow...?

---

### Post by philcamlin on 2009-07-02
i know

---

### Post by basiix on 2009-07-02
This arrow:

[IMG]http://i40.tinypic.com/28mid1v.png[/IMG]

Bottom left of the logo...I believe the standard ubuntu themes don't have it but custom one's do. It's annoying to some people and so far recompiling gnome without the arrow was the only way everyone knew how to get rid of it, but the other way seems easier and faster.

---

