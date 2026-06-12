---
title: "Why don't Ubuntu update my programs"
date: 2006-09-12
forum: Desktop Environments
---

### Post by Amorphous_Snake on 2006-09-12
I noticed that Firefox is still 1.5.0.5 and not .0.6, the same goes to VLC player which is 0.8.4 not .5.

VLC is installed through Automatix. I tried reinstalling it through there, but still 0.8.4.

What's wrong?

---

### Post by Viskovitz on 2006-09-12
[SIZE="2"]Nothing's wrong! It's just that the program version in the Ubuntu repositories isn't always the latest available (I don't know exactly why). Maybe they have to check that the new version is stable enough (or worth upgrading). Can someone tell the reason?

You can check that your programs are all up-to-date by typing in a terminal:

```
sudo apt-get update
``` to update your repos

```
sudo apt-get upgrade
``` to upgrade all your programs[/SIZE]

---

