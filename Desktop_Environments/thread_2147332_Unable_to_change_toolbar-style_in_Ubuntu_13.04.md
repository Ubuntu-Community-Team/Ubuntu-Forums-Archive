---
title: "Unable to change toolbar-style in Ubuntu 13.04"
date: 2013-05-21
forum: Desktop Environments
---

### Post by chraazy on 2013-05-21
I'm having some issue with rhythmbox not changing the toolbar style to match what I set it to in dconf-editor. I tried the steps mentioned [here]("http://ubuntuforums.org/showthread.php?t=1859526") but I am unable to get the toolbar in Rhythmbox to show only icons. No matter what I select in dconf-editor (org.gnome.desktop.interface/toolbar style) rhythmbox continues to show both icons and text. If I choose "both-horiz", nothing changes. Rhythmbox still shows icons on top of text. I'm using a fresh install of Ubuntu 13.04 and have tried rebooting and logging out/in after making changes. I was able to get the icon size to be small using the steps mentioned in the thread above, but that wasn't my priority. I would like to remove the text from the toolbar so it shows only icons. Rhythmbox is the only app having this issue, the toolbars in all other apps changed properly when I edited dconf. I don't really care about this in all apps, just rhythmbox. Using the rhythmbox-ui.xml file under /usr/share/rhythmbox I was able to remove the seperators from the rhythmbox toolbar, but removing text is what I'm really wanting to do here. Any suggestions?

---

