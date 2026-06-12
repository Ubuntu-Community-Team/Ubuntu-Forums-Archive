---
title: "Update Manager wierdness."
date: 2005-12-06
forum: General Help
---

### Post by carlosqueso on 2005-12-06
Hey all, I'm lovin' Ubuntu and really happy with the help I've gotten on the forums.  I've just got one little problem.  The update manager comes up and indicates that I have updates, but when I double-click, enter my password and choose install, it appears to start and then comes right back to the beginning screen without doing anything.  Apt-get and Synaptic work just fine, I was just wondering if this was a bug or something that I managed to break;) .  I don't mind using apt-get, but two-click updating might be nice.  If it is a bug, I'll go ahead and file it, I just didn't want to post a bug that was my fault.

---

### Post by carlosqueso on 2005-12-07
Since no one seems to know aything about this, I guess into bugzilla it goes....

---

### Post by Mr. Electric Wizard on 2005-12-07
I have gotten this also.
The way I "fixed" it was to go to the terminal and type:
sudo apt-get update
sudo apt-get dist-upgrade

This seems to fix the problem, at least gets the updates...:)

---

### Post by carlosqueso on 2005-12-07
yeah...I'm having no problem getting the updates...actually, I kinda like apt-getting it and watching all the stuff happen, but I just wanted to know if it was a bug or if I'm dumb and broke it.

---

