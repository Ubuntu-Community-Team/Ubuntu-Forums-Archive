---
title: "Firefox Beta 2"
date: 2006-09-20
forum: Desktop Environments
---

### Post by MaXiMuS-D on 2006-09-20
I can't find a way to remove FF from Ubuntu. I want to install the beta 2 and I don't want to keep the old FF.

Thanx in advance!

---

### Post by Paul41 on 2006-09-20
You can remove it in Synaptic. Just search for Firefox, mark it for removal then apply the changes.

---

### Post by effoff on 2006-09-20
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

...may help out if you want to do a system install that will be recognized by the menu system and APT. It keeps the older Firefox "in hibernation" as a backup. If you use that method, you willhave to use firefox as admin for a minute or two (gksudo firefox) from time to time if you want to use the auto update function of the fox when you know one is available.

---

### Post by MaXiMuS-D on 2006-09-20
That's the point, when I mark it for removal in Synaptic, it tries to remove -
firefox firefox-gnome-support gnome-app-install ubuntu-desktop yelp

Is this just FF associated stuff or does it have an impact on other packages? I was suspicious, so I asked.

---

### Post by Paul41 on 2006-09-20
I recently removed ff that was installed in the repositories (and therefore those packages) to install version 1.5.0.7 and haven't had any problems yet.

---

### Post by RAOF on 2006-09-21
> **MaXiMuS-D said:**
> That's the point, when I mark it for removal in Synaptic, it tries to remove -
firefox firefox-gnome-support gnome-app-install ubuntu-desktop yelp

Is this just FF associated stuff or does it have an impact on other packages? I was suspicious, so I asked.

**yelp** is the help-browser thing.  It uses an embedded Firefox engine (Gecko), and so depends on the Firefox in the repositories.

**gnome-app-install** is the thing marked "add or remove programs" in the menu.  It also uses an embedded Gecko engine.

**ubuntu-desktop** is just a convinience package, so that you can install "ubuntu-desktop" and be guaranteed to have the default Ubuntu software installed.  It doesn't actually contain anything.

---

### Post by puppy on 2006-09-21
A big note of caution - Firefox Beta 2 is, what it says, a beta version and is very likely to break the majority of your extensions and themes... just to make you aware. I tried it out and went straight back to 1.5.0.7!

---

### Post by MaXiMuS-D on 2006-09-21
Well, it seems to run okay on XP. And I don't have many extensions except AdBlock and Browser Sync.

So Yelp stops working and add/remove programs stops working? I seem to have Mozilla installed, do these 2 always use the SAME engine provided by FF?

Anyways, I have no use for Yelp, but is this add/remove programs the Synaptic package manager? If yes, then I'd rather wait for the final release of FF. Otherwise, to hell with it.

---

### Post by Paul41 on 2006-09-21
Synaptic package manager still works.

---

### Post by CaveRat on 2006-09-21
> **puppy said:**
> A big note of caution - Firefox Beta 2 is, what it says, a beta version and is very likely to break the majority of your extensions and themes... just to make you aware. I tried it out and went straight back to 1.5.0.7!

If you had installed the Nightly Tester Tools: [http://users.blueprintit.co.uk/~dave/web/firefox/buildid/index.html](http://users.blueprintit.co.uk/~dave/web/firefox/buildid/index.html) you would have been able to use most if not all your extensions. I installed Gecko 2.0b2 about two weeks ago and have not had a single problem with it. The standard Firefox install seemed to drag it's feet even with IPV6 disabled. Now since you cannot uninstall the default Firefox installation or any other default program install without also uninstalling your desktop, you can simply use the Alacarte Menu Editor in Applications/Accessories to hide the programs you do not want to see. Just go down through the list and uncheck them.

---

