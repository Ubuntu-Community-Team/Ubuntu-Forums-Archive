---
title: "[SOLVED] GUI don't start after upgrading to 8.10"
date: 2008-11-07
forum: Desktop Environments
---

### Post by micile on 2008-11-07
Hello,

something very strange happens after upgrade to 8.10 that I haven't find in any other post

On my PC I've had installed both Kubuntu-desktop (for my use) and Edubuntu-desktop (gnome based for my childrens).

I then upgraded to 8.10 from my kde session and all was terminated with success.

But at the restart, soon after the KDM login, I only see a terminal windows: neither kde nor gnome start.

If in this terminal I input "startkde" soon both( !!!!) kde and gnome (never seen before!) start and work very well.
Yes I've at the same time the two gnome bars with their buttons and the kde bar with its, while the desktop is the kde one (plasma).

I've tried to solve the problem by uninstalling compiz and reinstalling kubunt-desktop without any success...

hope in u !!!!!!!! pls

Micile

---

### Post by pseudosupport on 2008-11-07
have you trie ctrl+alt+f7 or f8 (I forget which one works in kde) to see if the gui interface comes on? If that doesn't work you might be stuck starting the desktop manager through the given command line.

---

### Post by micile on 2008-11-07
When I launch  startkde  both the KDE and the GNOME start at same time.

I'll try the ctrl+alt+f7 as I'll be near my PC and will post the results.

Anyway I afraid this wouldn't solve the problem as I would like to login through a login manager (kdm, gdm, or whatever) and then get the desktop manager started automatically.
thanx

---

### Post by stinger30au on 2008-11-07
i was just reading about this at the nvidia forums, you need to install the beta drivers to fix it



[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

---

### Post by micile on 2008-11-07
I've got a ATI Radeon graphic card.
Everything have worked ok up to the 8.04... the disaster come with the upgrade to 8.10

To be sure I've already uninstalled the compiz and disabled every desktop effect. without any success.  :cry:

---

### Post by pseudosupport on 2008-11-07
try checking your sessions in preferences and see what's set there; then, if everything looks kosher, log out and select options if your splash screen is displayed. From there, select session and either kde or gnome from the list displayed. I'm thinking that it's trying to load both on startup, so maybe this will help.

---

### Post by pseudosupport on 2008-11-07
What I mean by checking your session is to look for duplicates. ie: Make sure it's not starting two splash screens.

---

### Post by micile on 2008-11-10
thanks Pseudosupport, could u pls give me some directions?  I don't know how to check my sessions preference...

To complete the infos: I see the kdm splash and login windows, in the preferences I can even choose between kde and gnome, but whatever I select there is no behavior change.
thanx

---

### Post by pseudosupport on 2008-11-10
It's been quite a while since I used kde, and even then I never used kubuntu; so, I'm not quite sure how to do it in that. I believe MEPIS had it under utilites in the kicker, so I'd check for something like that. In Gnome it's under System>Preferences>Sessions. That'll display everything running on startup. I hope I'm not misinterpreting your question for directions.

---

### Post by micile on 2008-11-10
thank u very much!
that's ok! I can use this command since I got gnome and kde working...
I'll check that this evening as I'll be at home and post it.
ciao

---

### Post by toallpointswest on 2008-11-10
> **micile said:**
> I've got a ATI Radeon graphic card.
Everything have worked ok up to the 8.04... the disaster come with the upgrade to 8.10

To be sure I've already uninstalled the compiz and disabled every desktop effect. without any success.  :cry:

I think I ran into similar problems with the upgrade. What I noticed was that the upgrade switched out the fglrx driver with the new opensource radeon driver which works surprisingly well... once it's properly configured in /etc/X11/xorg.conf

I'll post mine when I get home and we'll see if it helps you.

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        Option          "AccelMethod"    "EXA"  #either XAA or EXA. "XAA" is the default and safe choice
        Option          "ColorTiling"    "on"
        Option          "AccelDFS"       "true" #seemed to speed things up using EXA acceleration
        Option          "TripleBuffer"   "true" #This *might* help if you use something like Beryl and have slow video playback.
        Option          "DMAForXv"       "true" #This can speed up movie playback but can in rare cases case instability

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Extensions"
        Option          "Composite"     "Enable"
EndSection

```

---

### Post by micile on 2008-11-24
Hello all.
After a period I had to stay far away from my PC, I finally solved that screwed problem.

As I intended to search for problems into Xsessions file, I found it missing in the /bin/kde4/kdm directory. 
Something wrong should have happened during the upgrade to 8.10.
Luckily the old /bin/kde3/kdm files were not removed.
So I just copied all the files from /kde3/kdm to the /kde4/kdm and the magic was done...
thanks u all 
Micile

---

