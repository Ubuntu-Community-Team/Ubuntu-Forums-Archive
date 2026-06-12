---
title: "Themes - Trusty"
date: 2014-04-24
forum: Desktop Environments
---

### Post by PJs Ronin on 2014-04-24
In my saucy partition, I can use gnome-tweak-tool and/or ubuntu-tweak-tool to change themes.   I can set the 'window theme' to a specific theme and see the top part of an app's window change to that new theme.   I can set the 'gtk theme' to another theme and watch as an app's window's internals change to that theme.   I believe this is as it should be.

I cloned this install to a new partition and then updated it to trusty.  Now, when I use gtt or utt to change themes, changing the 'gtk theme' works for most of my installed themes but it doesn't matter what I select for the 'window theme', nothing changes.

I tried a fresh install of trusty into a new partition, installed gtt and utt and again could not change the 'window theme'.

I also cloned my saucy instal into a new partition and updated it to utopic but again can only change the 'gtk theme'... although this does not surprise me.

Is anyone else having theme probs with trusty?   Any ideas how I can get trusty to accept changes to 'windows theme'?

---

### Post by jbaerboc on 2014-04-24
I've been using gtk3 themes from gnome-look.org and the unity-tweak tool to then change the themes. I did note that I couldn't change the window theme separate from the "controls" scheme but the gtk3 theme i have changes both for me to my liking so I roll with it.

---

### Post by PJs Ronin on 2014-04-25
ty jbaerboc.

I've always found that within the unity-tweak-tool there is no option to seperate the windows theme from the gtk theme.   You get the same theme on both sides of the coin, which may not necessarily be a bad thing.   However, in ubuntu-tweak-tool and gnome-tweak-tool you can theme window and gtk individually.   Atm I'm rolling with the new Radiance theme, however the font in the top panel becomes unreadable if the panel is set with transparency.

---

### Post by Frogs Hair on 2014-04-25
Use GTK 3.10 themes and I have noticed that in 14.10 The Gnome Tweak Tool has become more specific the Gnome sessions rather than Unity. Ubuntu Tweak was updated for  14.04 according to launchpad . 

Edit : Ubuntu Tweak doesn't allow for septate title bar selection on my installation . 


[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

---

### Post by grumblebum2 on 2014-04-25
In unity, compiz no longer uses the gtk-window-decorator.
Decorations are provided by the unity plugin to be able to show in app menus.

The best I can do in 14.04 is to set a custom panel colour using **gtk-theme-config**,
which is also picked up by the unity window decorations.

---

### Post by PJs Ronin on 2014-04-25
ty ty ty ... for a moment I thought I was going nuts.

---

### Post by Frogs Hair on 2014-04-26
The application menu can be now be set to be visible  in the title bar rather than the top panel and I think this changed settings that were previously available because the title bar is now part of global menu system.

See Appearance > Behavior

---

### Post by PJs Ronin on 2014-04-26
ty Frogs Hair.

The setting you mentioned is the one I prefer and the one I always set.   There's just so much going on with themes and the display properties of the top panel atm that are making my system look real 'dated'.   Hopefully, things will pick up over the next month or two.   I don't want to mark this as [solved] just yet so will let it hang and keep an eye on Trusty's progress.

---

### Post by Frogs Hair on 2014-04-26
There are not alot of Gnome 3.10 themes yet and Noobslab has a list that can be installed via a PPA if you wish , just install Unity Tweak from the software center and you'll find some customization options as well as theme changing.

---

