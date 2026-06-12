---
title: "Compiz/emerald makes non-KDE system tray icons float in the corner of my screen"
date: 2011-05-17
forum: Desktop Environments
---

### Post by soulspit on 2011-05-17
Hey everyone,

I've just done a fresh install of Natty Kubuntu and everything (well, mostly) was wonderful. Then I installed compiz, and some things became more wonderful and some things became less wonderful. One of the things that became less wonderful was the fact that all non-KDE system tray icons (Skype, VLC, etc but *not* Amarok or any default icons like wifi, volume, etc) no longer go into the system tray widget on my task bar. Instead, they all float, one on top of the other, in the upper left corner of my screen. They are always-on-top.

I can still click on them and use them, as long as I have only one so they don't obscure each other (e.g. if I open Skype then VLC, the VLC icon is on top of the Skype icon in the top left corner of the screen and I can't get to the Skype menu).

The only way I can get it to work is by closing the applications, killing compiz, running kwin, opening up the application again (whereupon the icon rests rightfully in the system tray), and then killing kwin and opening compiz again. Then the icons are in the right place. But any new programs opened continue to have their system tray icons floating up in the corner.

It's far from a critical problem, and kind of amusing, but it's also annoying and I'd like to figure it out, so any help would be appreciated!

---

### Post by lorebett on 2011-05-17
I've just upgraded my kubuntu to natty from maverik where I was using compiz... after upgrade compiz makes the kde desktop a mess, similarly to what you experienced...  I have to use kwin, since compiz does not seem to work... if I use compiz-fusion-icon to set emerald and compiz then all windows lack the title bars.

---

### Post by Copper Bezel on 2011-05-17
Well, the latter problem is due to Emerald not being compatible with the version of Compiz that ships with Natty, yet. So far as I know, it still has to be compiled from a git repository, _[like this]("http://ubuntuforums.org/showthread.php?p=10769035#post10769035")_.

That doesn't address this bizarre system tray behavior, of course, and I'm curious to see whether this problem has occurred for anyone else (although I don't use 11.04 or KDE, so I can't really offer any input on it.)

---

### Post by soulspit on 2011-05-17
Oh yes - I should have mentioned that I compiled Emerald from git, but those in the know, like Mr. Bezel, can figure this out :)

I'm certainly curious to see who else has this problem. One thing I hate about bugs like this, though, is that they're sort of difficult to describe, and hence difficult to Google for. Are my systray icons floating, or are they popping out, getting stuck, morphing into crippled mutant plasma widgets? We may never know.

---

### Post by kfoe on 2011-05-22
I'm having the same problem after updating to natty!I'm also having window focus issues when using alt-tab to switch between applications, it seems that when I type something it doesn't appear but after minimizing and maximizing the window again, everything is there which is very annoying. I tried switching to kwin but it seems to perform a lot slower than compiz.

---

### Post by Copper Bezel on 2011-05-22
The Alt+Tab problem may or may not be limited to the particular application switcher you're using - see [here]("http://ubuntuforums.org/showthread.php?t=1761437&highlight=ring+static+application+switcher").

I still have no hints on system tray the issue. I've seen parenting mucked up by restarting Compiz, such as my AWN panels having their outlines misplaced on the screen (piled up floating in the upper left) but only for applications run *before* running Compiz. Anything that causes the window to refresh (in my case, opening AWN's preferences dialog) fixes it. This problem running in exactly the opposite direction is completely baffling to me.

---

### Post by crutex on 2011-05-22
I have this same issue.  11.04, compiz, gtk app system tray icons are given their own window and do not appear in the system tray

This is extremely annoying :x

[IMG]http://i.imgur.com/Yk8Sw.jpg[/IMG]

:popcorn:

---

### Post by soulspit on 2011-05-26
Yep, that screenshot captures exactly what I have, except I'm using KDE and, fortunately, on mine there is no window decoration, it's just the icon, stuck in the very upper left corner. Presumably, I suppose, it could be related to the various other glitches I'm getting from KDE + compiz that may or may not ever be fixed, like a runner and an application launcher that keep losing focus, ceasing to update, etc.

Even if I knew exactly where to go, though, it's bearable enough that I'm having a hard time motivating myself to file a bug report and actually track down what could be going wrong.

---

