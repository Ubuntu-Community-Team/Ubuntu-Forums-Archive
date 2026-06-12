---
title: "Notifications going downhill?"
date: 2010-01-09
forum: Desktop Environments
---

### Post by candlerb on 2010-01-09
I've been an Ubuntu user since Dapper. Now I have Karmic on my desktop, I can't help thinking that things have moved backwards in terms of notifications.

(1) When a software update was available, you used to get a persistent icon in the notification bar (*). Now you get a pop-up straight into update-manager; if you dismiss it, then you have no further notification that an update is needed, as far as I can tell. I have found myself getting weeks behind as a result.

(2) When someone sent me a message in Pidgin which I hadn't read, I used to get a flashing icon in the status bar. Now with Empathy, the envelope icon changes from white to grey. Not exactly stand-out, is it? (**) If someone sends me a message while I'm "away", when I return that's all the notification I see.

Anybody else feel the same? And are there some simple workarounds I can apply? Going back to Pidgin is easy enough, but I can't find an "Add to panel..." option which would give me the update icon back.

Thanks,

Brian.

(*) I have Xubuntu Karmic on my laptop, and it still works this way, fortunately.

(**) Empathy is annoying for other reasons too, like not always scrolling received messages into view, so the response appears 'below the horizon'. But that's another thread.

---

### Post by mister_playboy on 2010-01-09
I used these instructions to revert 9.04's "updates available" to the previous behavior, I assume it works on 9.10:

[http://chrisjohnston.org/2009/change-the-way-ubuntu-904-notifies-you-of-updates](http://chrisjohnston.org/2009/change-the-way-ubuntu-904-notifies-you-of-updates)

Can't help with Empathy as I am a Pidgin user.

---

### Post by candlerb on 2010-01-12
Well that certainly stopped the pop-ups - but now I have no notification at all that upgrades are required. If they're there, I have to check for them manually. What I want is the arrow or exclamation mark icons which used to appear in the status bar.

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnome-screensaver
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,186kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by mister_playboy on 2010-01-14
> **candlerb said:**
> Well that certainly stopped the pop-ups - but now I have no notification at all that upgrades are required. If they're there, I have to check for them manually. What I want is the arrow or exclamation mark icons which used to appear in the status bar.

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnome-screensaver
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,186kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?

I get the exclamation mark in the status bar... sorry that it didn't work on 9.10.

---

