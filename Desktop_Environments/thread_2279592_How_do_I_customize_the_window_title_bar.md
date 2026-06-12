---
title: "How do I customize the window title bar?"
date: 2015-05-24
forum: Desktop Environments
---

### Post by greg83 on 2015-05-24
Today I decided to customize my Ubuntu a bit and I have encountered a problem I cannot fix. I want to make the window title bar transparent, I have found some older forum posts in which I have seen that you could, in fact, do that in older versions of Ubuntu but it isn't working out for me and some other people in 14.04 I may be doing it wrong, if so, please correct me.

Here is what I want to make tansparent if I didn't specify clearly (pardon me): [http://imgur.com/K4mAOV7](http://imgur.com/K4mAOV7)
Here is how I want it to be: [http://ubuntuhandbook.org/wp-content/uploads/2013/08/transparent-panel-titlebar.jpg](http://ubuntuhandbook.org/wp-content/uploads/2013/08/transparent-panel-titlebar.jpg)

It would also be nice if you could tell me how to customize that bar's height and color in addition to the transparency.

Thank you. :)

---

### Post by Frogs Hair on 2015-05-25
Hello and Welcome

The Ubuntu hand book title-bar transparency tutorial worked up through 13.10 and I find nothing new so far.

 [http://ubuntuforums.org/showthread.php?t=2226867](http://ubuntuforums.org/showthread.php?t=2226867)

You might want look into Emerald which offers transparent window decoration and has been updated for 14.04 +.
[http://www.ubuntuupdates.org/package/webupd8/trusty/main/base/emerald](http://www.ubuntuupdates.org/package/webupd8/trusty/main/base/emerald)

Themes: [http://gnome-look.org/index.php?xcontentmode=103](http://gnome-look.org/index.php?xcontentmode=103)

---

### Post by v3.xx on 2015-05-25
Ubuntu (Unity) has built in limitations, sounds like you hit on one.  As far as I know, this does not apply to any of the ubuntu flavors (X, Lu, Mate and so on).  You may want to look at your options.

Good luck

---

### Post by Copper Bezel on 2015-05-25
Well, might not need to go that far, as Frogs Hair is saying. The change is only in Compiz (and consistent with Compiz's increasing focus on core features of the Unity experience over bells and whistles, which isn't necessarily a bad thing.) If Emerald is being updated and still jives with Compiz / Unity, it'd get the job done without completely switching desktops or window managers. (And definitely check out the transparent menu panel and dash color setting tweaks in the Unity plugin, too, or the Opacity, Brightness, and Saturation plugin to make menus or dialogue boxes slightly transparent, if you dig that on KDE and Mac.)

---

### Post by grahammechanical on 2015-05-25
Install CompizConfig Settings Manager (CCSM) from the Ubuntu software centre. Open CCSM and go to the section Ubuntu Unity Plugin. And under the general tab reduce the panel opacity from 1.000 to 0.0100 or even 0.000. We do not get complete transparency. But it is close enough and it does also alter the look of the text in the panel.

By the way, do not be tempted to untick the box labelled Enable Ubuntu Unity Plugin because that will break the desktop. We need to first install an alternative desktop.

This works on Ubuntu Wily Werewolf (15.10). I have just tried it.

Regards.

---

### Post by Copper Bezel on 2015-05-25
That's the menu panel. The setting used to be inherited by the window titlebar, but now they're separate (as they should be) and there's no control for the titlebars themselves. (But that new switch to turn the menu panel opaque when a window is maximized, so everything matches up? *Delicious*. = D)

---

