---
title: "Where are the &quot;system icons&quot; and &quot;other icons&quot; directories hiding?"
date: 2008-11-11
forum: Desktop Environments
---

### Post by Nesnej Trick on 2008-11-11
After upgrading to KDE4 along with intrepid I found that kooldock was working sub-optimally. Since I'm fairly used to having a dock, I installed the Cairo-dock instead.

Theming it has proven a bit of a challenge though. I simply cannot find the Adept of Firefox icons, no matter where I look. Sure enough, they and others show up in either "system icons" or "other icons" if I change the icon in a KDE menu, but I can't find the actual files. Where are they hidden? :confused:

---

### Post by fabounet on 2008-11-12
for the dock, you can define the icons' set in the "Icons" tab of the config.

---

### Post by Nesnej Trick on 2008-11-15
I know that. What I was asking was which directory the default icons for different programmes are located in. Logic tells me these should be /usr/share/icons and /usr/share/pixmaps, but for some reason a great deal of icons (adept, amarko, openoffice) are nowhere to be found in either directory. They show up in the menus though, so they have to be _somewhere_, right? I'd like to know where this somewhere is, because currently my dock contains a lot of question marks.

---

### Post by BubbaFett on 2009-10-31
I had the same problem with wbar when switching from Jaunty to Karmic

Dolphin- tools find files- named:*.png (look in file:/, include subfolders, show hidden files) returned !*17010*! files.

adept:?
Firefox: /usr/share/pixmaps/firefox-3.5.png or 
             /usr/share/pixmaps/firefox-installer.png
Amarok: file:///usr/share/icons/hicolor/128x128/apps/amarok.png
Open Office: /usr/share/icons/hicolor/48x48/apps/openofficeorg3-startcenter.png

Hope this helps

---

