---
title: "Help! first timer with ubuntu. can't install flash playe"
date: 2009-05-14
forum: General Help
---

### Post by UkeyBuntu on 2009-05-14
Hi. This is my first day trying out ubuntu and I've been having a lot of trouble installing everything! But my current problem right now is installing Adobe Flash Player. I've been trying to install "Adobe Flash Player Linux.deb" and when I get to the package installer and click Install I get an error message saying:
[B][I]
Could not Download all required fiiles
please check your internet connection or installation medium

details: Failed to lock /var/cache/apt/archives/lock[/I][/B]

[LEFT]I really need help. I don't know what to do or what this means. Thank you so much for the help.
[/LEFT]

---

### Post by oldos2er on 2009-05-14
Make sure no other package manager is running. Open a terminal, and run this command:
```
sudo apt-get update && sudo apt-get install flashplugin-nonfree
```
 This requires a working internet connection.

---

