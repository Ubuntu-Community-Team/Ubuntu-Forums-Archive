---
title: "Window borders disappear when clicked on"
date: 2009-01-26
forum: General Help
---

### Post by trikster_x on 2009-01-26
I am running hardy on a acer aspire one with 1 GB ram, 120 GB HDD, 1.6 GHz atom processor.

The problem I am having is with the emerald theme engine.  After I downloaded and ran fusionbuild to install the latest version of compiz fusion from git for me, emerald stopped working.  When I try to grab a window border to move the window, it disappears, like emerald just shut itself off.  I have to restart X to get the border to come back, but it disappears again as soon as I click anywhere on the border.  I have tried removing and reinstalling emerald with no luck.  Running emerald --replace in the terminal does nothing.  I have the command set in sessions and window decorator, so it isn't that I missed something on the setup.  Everything worked perfectly before using fusionbuild.  When I use the normal GTK windows, everything works how its supposed to.  Is there a conflict between emerald and the latest version of compiz that I should know about, or is the latest version of emerald just this unstable?


**I just got emerald to work again by removing the newer version of compiz and going with the version in the add/remove program on Hardy.  It would still be nice to get it to work with the newer compiz so I can use the deform cube plugin.  If any one has an idea, it would be appreciated.

---

### Post by gettinoriginal on 2009-01-26
Go to CCSM and under "window decoration" command, type "emerald --replace.

---

### Post by trikster_x on 2009-01-26
> **gettinoriginal said:**
> Go to CCSM and under "window decoration" command, type "emerald --replace.

If you read my first post entirely, you would have seen I did that already.  I wish it was that simple because I wouldn't have had to start a thread to fix the problem.....

I do have some more info, though.  It appears that I can't enable the visual effects at all with the latest version of compiz installed.  But when I removed it last night, and installed the original version I had, emerald worked fine and I could enable the normal and extra settings of visual effects.  So I am starting to think it is a problem with compiz not emerald.....

Any thoughts?

---

### Post by gettinoriginal on 2009-01-26
Just did some research on Fusionbuild, and notice that by the authors admission he is still working on it, and invites questions here:
[http://ubuntuforums.org/showthread.php?t=871165&page=3](http://ubuntuforums.org/showthread.php?t=871165&page=3)
and has a blog here:
[http://fusionbuild.wordpress.com/](http://fusionbuild.wordpress.com/)
Sorry I cannot be of more help, I'm basically a chicken and stick to stable stuff  :p

---

### Post by trikster_x on 2009-01-26
Thanks for that forum link.  I left a reply there, and will continue to update in this thread.  

It might be helpful to mention that when I first boot into Ubuntu, I can go to Preferences>Appearance>Visual Effects and extra is selected, but as soon as I try to click a border, none becomes selected.  When I try to select extra again, I get the message "Desktop Effects could not be enabled".

---

### Post by VeeDubb on 2009-01-27
Sounds like your home-spun compiz isn't working right.  (I know, stating the obvious)

Have you considered just going back to the compiz in the repos?

---

### Post by trikster_x on 2009-01-28
I actually did that.  But I kinda want the cube deformation plugin, which is not available to the version of compiz in the hardy repositories.  All the other newer plugins work with it though, so I will probably have to settle....

---

