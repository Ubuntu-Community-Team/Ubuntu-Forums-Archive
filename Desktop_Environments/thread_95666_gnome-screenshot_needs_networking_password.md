---
title: "gnome-screenshot needs networking password?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by aysiu on 2005-11-27
If I create a bookmark for something networked (my wife's Powerbook or some FTP site) in Nautilus, all of a sudden, every time I try to use gnome-screenshot, a dialogue pops up telling me I need the username and password for my network. 

Once I either cancel that dialogue or answer its questions, the gnome-screenshot actually works (appears--takes a screenshot). 

If I delete the bookmark, this no longer happens.

Is there a way around this? Is this a bug? I don't remember whether this happened in Hoary or not. Has anyone else experienced this?

---

### Post by manicka on 2005-11-27
I got asked once to always allow access to the keyring and then it doesn't happen again.

---

### Post by gw90se on 2005-11-27
What folder is it trying to save to by default?

---

### Post by aysiu on 2005-11-27
[QUOTE=gw90se]What folder is it trying to save to by default?[/QUOTE] Gnome-screenshot? My desktop, which I should definitely have write-permission to.

In any case, regardless of whether I type in the password or hit cancel, the screenshot will happen and save. What's weird is that the dialogue pops at all in the first place, especially since it happens for only gnome-screenshot and not any other application.

---

### Post by aysiu on 2005-11-27
[QUOTE=manicka]I got asked once to always allow access to the keyring and then it doesn't happen again.[/QUOTE] That was worth a try, but it didn't work for me. Did you have that happen for gnome-screenshot?

---

### Post by manicka on 2005-11-30
[QUOTE=aysiu]That was worth a try, but it didn't work for me. Did you have that happen for gnome-screenshot?[/QUOTE]
yes, gnome-screenshot

---

### Post by aysiu on 2005-11-30
I've just taken networked stuff off my bookmarks.
If I'm the only one experiencing this problem, it's probably not a bug report. Maybe I configured things badly...

---

### Post by trevorv on 2005-11-30
I can't check it right now, but I think I had the same problem a couple of months ago, bookmarking an FTP site. Whenever I tried to browse to a file with the Open dialogue of certain programs, it would ask for the password.

In the end I just deleted the bookmarks, I never got around to asking for help or filing a bug.

---

### Post by welsh_spud on 2005-11-30
Your not alone. This happens to me when I try to take a screenshot. My bookmark is my dads Windows box which I use for storage.

---

### Post by arpunk on 2005-11-30
Thats weird, i have 2 ftp servers on my bookmarks and gnome-screenshot doesnt ask me for password, and i dont have gnome keyring enabled for my ftps :???:, im using Breezy.

---

### Post by manicka on 2005-12-02
hmmmm, I hadn't thought about this one for  few days until I went to take a snapshot of an app and there it was asking for passwords again after starting a new session. This looks more like some sort of strange bug.

---

### Post by kanem on 2005-12-19
This bug started with Breezy. And still exists in Dapper. I suspect it's because bookmarks are now places in all gtk open/save dialogs. I filed a bug about it [here](http://bugzilla.gnome.org/show_bug.cgi?id=315420). Maybe it will get the developers attention if someone confirms it.

---

