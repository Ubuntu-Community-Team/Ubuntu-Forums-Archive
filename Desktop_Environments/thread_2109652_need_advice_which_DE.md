---
title: "need advice: which DE?"
date: 2013-01-28
forum: Desktop Environments
---

### Post by finite9 on 2013-01-28
Ive got Ubuntu 12.10 Server installed on my server.  I use it as a real server, not a desktop, and it's specified as such, hardware wise.  Since I got a nexus pad, I dont use my laptop that much, so I want to have a DE on my server that's low on resource usage and dependencies, extremely fast, but has a lot of features.

I'm a long time Gnome user.  I've never used any other DE really apart from a brief stint with KDE on Ubuntu 5.10 which I didn't like, and still don't.  Please don't turn this into a flame war... I just personally don't like KDE, and im not willing to try it.

I originally like Gnome3 but have gone off it because the "features" are not worth the performance degredation for me.  As such, im also averse to Unity for the same reason, and I think KDE is just way too confusing, and I just don't agree with the "everything and the kitchen sink" approach.

I tried:

Openbox & Fluxbox: Too featureless and sparse for me thanks.
LXDE: Not enough features, and standard stuff I expect to be thee just isn't, but extremely fast.
XFCE: Currently using this, seems ok, but I can't find some things that I've gotten used to in Gnome 2, like standard configuration items in the 'control panel'...

In XFCE, 

How to I add themes?
How do I add icon themes?
How do I add ability to tie in to my encrypted home folder?  At the moment it refuses to show the contents.
Is there a keyring manager?
Are there _any_ accessibility option, like High Contrast theme?  I can't find this.

Can I get everything from Universe repo without having to resort to downloads from the Net?  Im a strong supporter of getting as much as possible from the official Canonical repos for compatibility reasons.


After giving up on Gnome 3, I want something that's really fast again, and doesn't get in the way of my applications, but I feel like im going down the road of creating my own specific DE by choosing my own file manager, my own keyring manager, my own themes etc etc etc, that I personally have to meticoulously 'package'.  I never had to think about all the separate apps before, but now I feel like im having to do that to get a DE that I like.  Has anyone else gone down this route?  What was your experience?

I'm not willing to try Mate because although it seems to fit the bill, im scepticle about them being able to hold that fork afloat in the long run, and that it won't get security updates like the major DEs do.

Has anyone tried Cinnamon?  Im less sceptical of this, because although it's a PPA, it's built on Gnome, so the security updates to gnome will trickle thorugh to Cinnamon, and there is less for Cinnamon to add/maintain than for the Mate team.

---

### Post by ajgreeny on 2013-01-28
> **finite9 said:**
> Openbox & Fluxbox: Too featureless and sparse for me thanks.
LXDE: Not enough features, and standard stuff I expect to be thee just isn't, but extremely fast.
XFCE: Currently using this, seems ok, but I can't find some things that I've gotten used to in Gnome 2, like standard configuration items in the 'control panel'...

In XFCE, 

How to I add themes?
How do I add icon themes?
How do I add ability to tie in to my encrypted home folder?  At the moment it refuses to show the contents.
Is there a keyring manager?
Are there _any_ accessibility option, like High Contrast theme?  I can't find this.

Can I get everything from Universe repo without having to resort to downloads from the Net?  Im a strong supporter of getting as much as possible from the official Canonical repos for compatibility reasons.
You say you want something lightweight, but then say that the lightweight DEs are too sparse and featureless for you.

I think you will have to accept some sort of compromise, but what that may be will have to be your choice.  However to answer some of the queries about XFCE yu should gho to [http://xfce-look.org/](http://xfce-look.org/) where you will find lots of themes and icon sets.

I can not help with encryption as I have never used it, and therefore have no experience, nor am I sure about a keyring manager, though you may find some help on that by searching **xubuntu keyring manager** in [www.googlubuntu.com]("http://www.googlubuntu.com").

All the settings in a similar control-centre to gnome, are in the menu **Settings->Settings Manager** which should give you most of what you want, I think.

PS: for something totally different have a look at E17, the DE of Bodhi Linux.

---

### Post by black veils on 2013-01-28
copy the themes (whether it be for window manager or general) into /usr/share/themes

copy icon themes into /usr/share/icons

if i were you, i would either use xfce, or if needing something lighter, i would say lxde is the most usable.. just add certain packages to give my functions, or learn to edit a couple of text files and forget anything else. you need to compromise or find a way.

and yes you can get all or most things from the included repositories, you will probably want to enable the **canonical partners** repository in **software sources** >> **other software** tab.

i created a list of applications as a general system compilation, its long, but if you want to consult it, i can PM it to you. the idea being: lighter, easier to use, yet functional.

---

### Post by ibjsb4 on 2013-01-28
What about Gnome Classic?

I build it without all the bloat.  Nautilus fills the bill for me.

```
sudo apt-get install lightdm gnome-terminal synaptic && sudo apt-get install --no-install-recommends gnome-session-fallback
```

And from there, build to taste.

A couple of things.

Recent changes in the fallback package seem to make it not necessary to install without recommends.  I have not done a build with the new repackage, so I really don't know for sure.  The old package would dump on you without the no-recommends.

The panel background color needs to be change after the install so you can see the menu.  Its black on black at the start.

This for me is like the old gnome2.

[http://packages.ubuntu.com/precise/gnome-session-fallback](http://packages.ubuntu.com/precise/gnome-session-fallback)

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by LewisTM on 2013-01-28
The keyring manager for (X)Ubuntu is package **seahorse**. You can get more window manager themes from packages **xfwm4-themes** and **murrine-themes**. I agree Xfce is easily the best compromise for you. 

As for encryption, I'm sure it's possible and Google will give you answers if nobody in this forum chimes in.

Cheers!

---

### Post by ACubed10 on 2013-01-29
I use Ubuntu 12.10 and always install cinnamon right away.  I love it!  here's a screenshot of it :guitar:

---

### Post by ryanleesipes on 2013-01-29
> **ACubed10 said:**
> I use Ubuntu 12.10 and always install cinnamon right away.  I love it!  here's a screenshot of it :guitar:

ACubed10 has a point, for your use case Cinnamon is probably one of the better choices.

---

### Post by finite9 on 2013-01-29
thanks for the replies.  I think i'll keep trying to get xfce the way I want it, as it seems to give the best balance for me.

I am interested in Cinnamon, but it's still going to drag the Gnome bloat with it.  Not that my server can't handle it, but im mainly looking for the least dependencies.  If I come across lots of stuff that I can't easily get to work in xfce then I might just give cinnamon a try.

I can't find any high contrast accessibility setting in xfce, but I suppose I can fix that by getting a relevant theme?  anyway, high contrast usually forces firefox into high contrast mode which is just bad bad bad.

---

### Post by ACubed10 on 2013-01-30
> **finite9 said:**
> thanks for the replies.  I think i'll keep trying to get xfce the way I want it, as it seems to give the best balance for me.

I am interested in Cinnamon, but it's still going to drag the Gnome bloat with it.  Not that my server can't handle it, but im mainly looking for the least dependencies.  If I come across lots of stuff that I can't easily get to work in xfce then I might just give cinnamon a try.

I can't find any high contrast accessibility setting in xfce, but I suppose I can fix that by getting a relevant theme?  anyway, high contrast usually forces firefox into high contrast mode which is just bad bad bad.
well when you install cinnamon you choose at the login screen what DE you want..So I believe it only uses one at a time.  I could be wrong

---

### Post by finite9 on 2013-01-31
i've been reconfiguring a lot of stuff in xfce, and one thing I notice is that there are more options that I appreciate being there, that were never available in Gnome.  It's just a shame that they seem a bit randomly placed, which is what Gnome tries to address, I believe, but it's frustrating with Gnome that they remove options that I really like.

Got x11 cursors working and icon themes, and even found a setting to lauch Gnome application compatibility on startup, which was a bonus.

However...Im having trouble with 2 things:

If memory serves me, installing a "theme" sets window decorations in the window manager AND sets the gtk/xfce colour theme, but I want to control them individually.

In Gnome 2, the window manager was Metacity and the colour themes handled by gtk themes (on gnome-look.org).

But how do I add window decoration themes for xfwm? and does xfce use gtk window colour themes??  or is it another package that they use instead of gtk?

Also, how do I customise lightdm-gtk-greeter?  I've set my own background, but I want to customise the placement of the login box and the other controls.  Are there themes for this?

---

### Post by black veils on 2013-01-31
those themes are handled differently and have the relevant settings in the settings manager, in **appearance** and **window manager**.

both window themes and window contents (gtk) themes are put into /usr/share/themes, the window manager will be the **xfwm** folder within each one.

get them from:
window manager [http://xfce-look.org/index.php?xsortmode=high&page=0&xcontentmode=420&PHPSESSID=282c3ab192721924e8f7a5390cebd0b0](http://xfce-look.org/index.php?xsortmode=high&page=0&xcontentmode=420&PHPSESSID=282c3ab192721924e8f7a5390cebd0b0)
window contents (gtk) only a few work with both gtk2 and gtk3, so stay with stuff like the default, which is greybird, and then there is a modern version from 12.10, there is ambience from [http://www.ravefinity.com/p/download-ambiance-radiance-themes-for.html](http://www.ravefinity.com/p/download-ambiance-radiance-themes-for.html), mint have their own mint z and mint x themes. maybe bluebird and something else, but i dont like those.
[http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=167](http://gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=167)

---

