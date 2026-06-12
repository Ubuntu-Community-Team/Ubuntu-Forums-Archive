---
title: "How do I make Tooltips work on the desktop? 20.04/LXQt"
date: 2021-07-14
forum: Desktop Environments
---

### Post by GhX6GZMB on 2021-07-14
I am not able to get Tooltips (mouse-over-icon) to work on the desktop.

It works in the Application Menu, eg, placing the mouse pointer over FeatherPad, a little pop-up saying "Text Editor" appears.
It also works in the bottom panel, where again placing the mouse over the FeatherPad icon gives a pop-up with "FeatherPad (Text Editor)".

But on my desktop icons a mouseover on FeatherPad gives a "FeatherPad" pop-up, which is pretty useless. Especially for new users who do not know the Lubuntu program names.

From my research, there are two fields in the .desktop files that are in play for the Tooltips.
The Menu and the Panel use *GenericName*, which is as it should be.
But the desktop seems to use *Name*, which is not what I want, I want *GenericName*.

Is there a Desktop setting or configuration file where that can be modified to fix this?

Thank You.

---

### Post by coley9225 on 2021-07-14
Hello ml9104. You can modify the name shown on your desktop icons in the /home/username/Desktop folder. Open you file manager, at the top, click tool, then open as root. Go to your Desktop folder and open it. That is all your desktop icon info. Rigt click on Featherpad and open with, well, Featherpad. You will see a spot with "Name=Featherpad'. You can change that to whatever you want, even 'write stuff' if that's what you want. To make it easy to associate 'Featherpad' with being a text editor, I would name it 'Featherpad text editor'. By doing it this way, if you add a desktop shortcut for another text editor, you'll know which is which. Make these changes in your /home/user file, not the / file, that will leave the default naming for any other users.  Do not change any thing else in the file. Save the changes. I don't remember if the changes are effective right away or if you will need to ;log out and back in, but that should be a way to solve you issue.

---

### Post by GhX6GZMB on 2021-07-14
I know all about renaming.
I'm talking about the mouseover tooltips that display a descriptive text about the application.
This works in the Application Menu and the Panel, but not on the Desktop. That's my issue.

---

### Post by westie457 on 2021-07-14
This may point you in the right direction.

[https://superuser.com/questions/513325/turning-off-tooltips-in-xfce](https://superuser.com/questions/513325/turning-off-tooltips-in-xfce)

---

### Post by GhX6GZMB on 2021-07-14
Thanks, westie457.
That's a step in the right direction, but unfortunately doesn't help for LXQt. Gnome configurations don't really fly, but it gives a hint on where to search.

---

### Post by GhX6GZMB on 2021-07-15
OK, no solution found. It seems to be a bug, on searching I've found references to the issue elsewhere.

I can live with it, but it's a shame when presenting Lubuntu to new users.

---

