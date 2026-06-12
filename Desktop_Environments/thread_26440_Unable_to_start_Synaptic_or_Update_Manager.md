---
title: "Unable to start Synaptic or Update Manager"
date: 2005-04-12
forum: Desktop Environments
---

### Post by SpacedOut on 2005-04-12
My apologies in advance if this is a simple question, I did search the forums to no avail.

Whenever I try to start the Synaptic Package Manager I get the "Unable to get Exclusive Lock" error, and whenever I try to start the Ubuntu Update Manager, it starts, but when I try to refresh I get an "Another Package Manager is Running" error.

This happens even after a fresh restart. I'm a complete newbie, so any help is appreciated.

---

### Post by Xian on 2005-04-13
Open your system monitor from the Gnome panel menu and look for any running processes that have to do with synaptic or even perhaps terminal windows that are starting up on login. It seems that you have a program like that loading each session. Kill anything that appears APT related and then try again.

---

### Post by SpacedOut on 2005-04-13
Actually, I had already checked, and there are NO processes running related to apt-get or anything.... Any other suggestions?

---

### Post by Flaystus on 2005-09-29
I'm pertty much getting the same problem when I goto "add application" and click on advanced.

I'm just trying to get VLC installed.

---

### Post by SilentCacophony on 2005-09-29
Are you two running updated Breezy? If so, it may have broken something...

Anyway, I'll offer a couple of ideas. Is your update-notifier (next to volume on the top bar) working correctly? I'm guessing it could interfere as well if it has a problem.

Also, you could try logging out of ubuntu to the gdm prompt, press ctrl-alt-F2 and log into a console, and try apt-get or aptitude from the commandline there. That might get rid of the conflict temporarily.

---

### Post by Flaystus on 2005-09-30
[QUOTE=SilentCacophony]Are you two running updated Breezy? If so, it may have broken something...
Anyway, I'll offer a couple of ideas. Is your update-notifier (next to volume on the top bar) working correctly? I'm guessing it could interfere as well if it has a problem.
Also, you could try logging out of ubuntu to the gdm prompt, press ctrl-alt-F2 and log into a console, and try apt-get or aptitude from the commandline there. That might get rid of the conflict temporarily.[/QUOTE]

update-notifier is not running on mine, at least its now showing up right now as there are no updates. As far as running one of those mentioned from a command line. I don't know how. :oops:

---

### Post by pichtik on 2005-10-05
My synaptic manager told me when I started it that I have interrupted some update and should run
[FONT="Lucida Console"]dpkg --configure -a[/FONT]
so I opened terminal and run
[FONT="Lucida Console"]sudo dpkg --configure -a[/FONT]
and this error message dissapeared :D

---

