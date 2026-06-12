---
title: "Add Launcher to Open a File"
date: 2017-04-21
forum: Desktop Environments
---

### Post by mrkeef on 2017-04-21
I recently switched over from Unity to Gnome.

Everything mostly works OK except there is one thing that I can't work out. I regularly open a particular file in Libre Office and in unity I had a .desktop file in ~/local/applications. This showed up in the launcher and worked as expected.

I can't get the same result in Gnome. I can't work out how to add it to Favourites so it appears on the dock. If I open the file and click "Add to Favourites" it just creates a launcher for Libre Writer without opening the file.

I can create a shortcut on the desktop using the .desktop file, and this works fine. 

Thanks

Keith

---

### Post by monkeybrain20122 on 2017-04-22
I think there is/was a bug in gnome (or maybe a feature, you never know with gnome) In my Fedora 24 partition (gnome 3.20) I had the same problem with some third party packages and self made .desktop files. Just can't add them to the dock. This happened rather randomly, some worked, some didn't with no apparent pattern. Not sure about Fedora 25 (gnome 3.22). Switched to kde there.

---

### Post by mrkeef on 2017-04-22
OK. Thanks for that. Disappointing if it's true. 

I might have to make the leap to KDE if this gets too annoying :)

---

### Post by monkeybrain20122 on 2017-04-22
There is a gnome-extension called simple dock. If activated it creates a dock at the bottom and disables the gnome dock. Maybe it would work It is easy to install a second dock but AFAIK there is no easy way to disable the default one, this extension does that, that's why I suggest it. [https://extensions.gnome.org/extension/815/simple-dock/](https://extensions.gnome.org/extension/815/simple-dock/)

---

### Post by mc4man on 2017-04-24
It's possible to add custom .desktops to gnome-shell's dock thru dconf-editor. By and large they'll work ok though if the launcher or launcher quicklist calls an app that has it's own .desktop then that desktop icon will show up when it's running.
Definitely 'low rent' compared to the unity dock or plank or docky or Apple's..

---

### Post by mrkeef on 2017-04-25
Thank you mc4man! I worked my way through dconf-editor until  I found the right section.

---

