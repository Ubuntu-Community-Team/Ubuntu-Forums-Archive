---
title: "EasyUbuntu caused missing HELP"
date: 2005-11-29
forum: Desktop Environments
---

### Post by anil_robo on 2005-11-29
I installed EasyUbuntu on Breezy, and it didn't work. I uninstalled it, and since then some applications went missing:

[IMG]http://img224.imageshack.us/img224/5779/screenshot0gm.png[/IMG]

1. THere was no icon for "add applications"
2. There was no icon for HELP
3. The update manager was also uninstalled automatically

SOlution:
1. sudo apt-get install gnome-app-install
2. ?
3. sudo apt-get install update-notifier

PLease help

---

### Post by anil_robo on 2005-11-29
I booted through live  CD, because it has the help icon built-in.

I right clicked on HELP lifeboat icon, clicked on properties and saw the command. It was yelp.

so I typed in the following in a terminal window and pressed enter:

sudo apt-get install yelp

And help was there! :p

---

