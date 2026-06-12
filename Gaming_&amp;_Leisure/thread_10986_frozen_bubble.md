---
title: "frozen bubble"
date: 2005-01-13
forum: Gaming &amp; Leisure
---

### Post by jstam1941 on 2005-01-13
i see frozen bubble in the files on my computer but don't have a clue as to how to
start it. any help would be appreciated

---

### Post by fng on 2005-01-13
You probbably installed frozen bublle without restarting X.
There is no icon in the games sub-menu.
Applications -> Run application ... -> typ in : 'frozen-bubble' and hit Run.

You can also restart X and there should be an icon in the Applications -> Games menu.

---

### Post by jstam1941 on 2005-01-13
i am new at ubuntu. i have a program called frozen-bubble-data at usr/share/games
but i don't know how to start it. it may even be the wrong program. any help will be
appreciated.

---

### Post by Dylanby on 2005-01-14
Assuming that you have the game installed...

Left click on "Applications"
Scroll down to "Games"
Right click in "Games", select "Entire menu" => "Add new item to this menu"

This will give you a little dialog that says "Launcher Properties"
Under "Basic" fill out these fields =>

Name: Frozen-Bubble
Comment: Pop out the bubbles!
Command: frozen-bubble

Click "Icon" & scroll down & select "frozen-bubble-icon-48x48.png"

One thing, on my system to get sound in Frozen-Buuble I have to kill esd.

Go to "Applications" => "System Tools" => "System Monitor"
There you can view the offending process & kill it!

---

### Post by garyfitz on 2005-01-14
Thanks Dylanby

You solved two of my problems
Frozen Bubble sound and
adding a menu item.

---

### Post by ptepper on 2005-10-31
I just tried your tip on adding things to the Gnome apps menu, I don't get an option in entire menu to add a launcher. Is that something you have to enable somewhere?

---

### Post by ubuntu_demon on 2005-10-31
[QUOTE=ptepper]I just tried your tip on adding things to the Gnome apps menu, I don't get an option in entire menu to add a launcher. Is that something you have to enable somewhere?[/QUOTE]

You are posting in an old thread aimed at warty. The current version of ubuntu is breezy. Which version of Ubuntu do you have ? warty,hoary or breezy?

In hoary you have to install smeg to edit the gnome menu (see the projects section on this forum). In breezy smeg is installed by default.

frozen-bubble is available from universe so make sure to have the universe repository enabled in your /etc/apt/sources.list Go here for information how to do this :
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

I you are running breezy I suggest you install frozen bubble by clicking on "add applications" and finding you way in the easy software installation tool.

You can install frozen bubble also manually by : 
$sudo apt-get install frozen-bubble

---

