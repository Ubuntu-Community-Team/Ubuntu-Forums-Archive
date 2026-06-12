---
title: "I need to lock down EVERYTHING on the desktop!"
date: 2010-04-21
forum: Desktop Environments
---

### Post by Old *ix Geek on 2010-04-21
How can I lock down everything on a user's desktop?  I don't want panels/widgets/icons/anything else to be added/deleted/moved/resized/etc.  I mean absolutely, positively LOCKED DOWN!!  It's Kubuntu 9.10.

---

### Post by wilee-nilee on 2010-04-21
> **Old *ix Geek said:**
> How can I lock down everything on a user's desktop?  I don't want panels/widgets/icons/anything else to be added/deleted/moved/resized/etc.  I mean absolutely, positively LOCKED DOWN!!  It's Kubuntu 9.10.

If this is because others change them set up accounts for them.

---

### Post by Old *ix Geek on 2010-04-21
> **wilee-nilee said:**
> If this is because others change them set up accounts for them.Thanks, but no. The user has their own computer--and they're constantly screwing it up! And I'm sick and tired of fixing it.  (That's a little harsh--it's my 86 year old mother, and I'm really proud of her for having PAINLESSLY switched to Linux from that god-awful piece of crap from Redmond she used to use. But the reality is that she's CONSTANTLY, inadvertently (because she doesn't bother to LOOK at what's happening!) adding/deleting/resizing panels/widgets/icons and everything else.  I'm tired of putting everything back the way I had it.)

---

### Post by Untitled_No4 on 2010-04-21
Right click on desktop or panel and choose Lock Widgets. Yes, this does not absolutely locks everything with a password forever, but if she's only deleting things because she clicked in the wrong place, at least this will be prevented (hopefully).

I would do something a little different though. Since all the desktop settings are saved in the .kde folder in your home directory, it's easy to "reset" a desktop by setting up the desktop as intended, then copying  .kde to another directory (e.g. .kde-backup) and then you'll be able to reset the desktop by overwriting .kde with .kde-backup. You can set up a script that runs at login and whatever she does she only has to log out and then back in to have everything reverted.

---

### Post by drreed on 2010-04-21
> **Old *ix Geek said:**
> Thanks, but no. The user has their own computer--and they're constantly screwing it up! And I'm sick and tired of fixing it.  (That's a little harsh--it's my 86 year old mother, and I'm really proud of her for having PAINLESSLY switched to Linux from that god-awful piece of crap from Redmond she used to use. But the reality is that she's CONSTANTLY, inadvertently (because she doesn't bother to LOOK at what's happening!) adding/deleting/resizing panels/widgets/icons and everything else.  I'm tired of putting everything back the way I had it.)


Hehehhe . . .  My 79yr-old mom is on Xubuntu, and she does the same stuff.

This should be an interesting case study for phd psychologists or something. I don't know how she does what she does, or why. Older people are wired different.:lolflag:

I'm in my 50's, is this what I have to look forward to?

---

### Post by Old *ix Geek on 2010-04-21
> **Untitled_No4 said:**
> Right click on desktop or panel and choose Lock Widgets. Yes, this does not absolutely locks everything with a password forever, but if she's only deleting things because she clicked in the wrong place, at least this will be prevented (hopefully).Been there, done that. You know what she does?  SHE right clicks, unlocks widgets, and has at it again! :D
> I would do something a little different though. Since all the desktop settings are saved in the .kde folder in your home directory, it's easy to "reset" a desktop by setting up the desktop as intended, then copying  .kde to another directory (e.g. .kde-backup) and then you'll be able to reset the desktop by overwriting .kde with .kde-backup. You can set up a script that runs at login and whatever she does she only has to log out and then back in to have everything reverted.I've tried restoring her .kde settings, but depending on WHAT she's screwed up, it doesn't necessarily solve the problem. For example, WHEN she deletes all her widgets (and, yes, she does this quite frequently...I still haven't figured out HOW!), and I put them all back, I have to set 'picture frame' back up (choose its photo directory, set its timing, randomness, appearance, etc.)...and then do that with 'LCD weather station' and everything else. ](*,)  See why I'm looking for an absolutely FOOLPROOF way of locking EVERYTHING down? :)

> **drreed said:**
> Hehehhe . . .  My 79yr-old mom is on Xubuntu, and she does the same stuff.

This should be an interesting case study for phd psychologists or something. I don't know how she does what she does, or why. Older people are wired different.:lolflag:You know, in the '80s when I started programming and administering *nix systems, things were SO MUCH EASIER to control.  My users COULDN'T screw things up like this.  GUIs are wonderful, beautiful things, but, DAMN!, they make life difficult. I literally have no idea how she does the things she does. I continually find myself saying, "Mom, I've never SEEN this before!"

> I'm in my 50's, is this what I have to look forward to?Me too, and me too. :confused:

---

### Post by 3Miro on 2010-04-21
Create another folder in /home or somewhere on another partition (say /home/mom_important). Then move Documents, Downloads and other important stuff there. Symlink from the regular /home/mom/Downloads to -> /home/mom_important/Downloads. For all intensive purposes, this will look like one folder to her. Then you can backup the entire /home/mom folder and restore it when needed. This should fix the problem for all widgets and all application settings.

Another idea would be to find the unlock widgets script and replace it with something that requires root password, i.e. change Unlock widgets to:
```
kdesudo cd / && Unlock-widgets
```

Actually I don't know exactly how KDE works, but something like this may work.

---

