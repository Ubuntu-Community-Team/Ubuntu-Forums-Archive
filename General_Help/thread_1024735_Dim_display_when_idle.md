---
title: "Dim display when idle"
date: 2008-12-29
forum: General Help
---

### Post by peppergrower on 2008-12-29
I'd like to change the timeout for the "dim display when idle" setting in the power management preferences.  Currently it dims my screen if I don't do anything for 30 seconds; where can I change it to be 1 minute instead, or perhaps 2 minutes?

Thanks,
Michael

---

### Post by namdung on 2008-12-29
> **peppergrower said:**
> I'd like to change the timeout for the "dim display when idle" setting in the power management preferences.  Currently it dims my screen if I don't do anything for 30 seconds; where can I change it to be 1 minute instead, or perhaps 2 minutes?

Thanks,
Michael

*System-->Preferences-->Screensaver*

---

### Post by adamvert on 2009-02-26
Open gconf-editor, go to apps > gnome-power-manager > backlight > idle_dim_time

---

### Post by danyim on 2009-05-07
> **adamvert said:**
> Open gconf-editor, go to apps > gnome-power-manager > backlight > idle_dim_time

You are a saint! Finally solved my issue with the "DIm when idle" going off too early.

---

### Post by dadgetboy on 2010-02-26
This is an old thread, I know; however I would like to thank you for the gconf-editor tweak. Thanks a lot! Also, the screensaver way would do the trick as well.

---

### Post by msrinath80 on 2010-06-25
I would also like to say thanks. Currently the 10 second limit in Lucid is ridiculous!

---

### Post by rduke15 on 2010-08-14
If you prefer copy/pasting commands instead of mousing around through menus you can also paste this into terminal:

```
gconftool --type int --set /apps/gnome-power-manager/backlight/idle_dim_time 120
```

This will set the idle_dim_time to 120 seconds.

To list everything defined by gconftool use this:

```
gconftool -R /
```

---

### Post by KC_GoldShine on 2010-12-15
> **adamvert said:**
> Open gconf-editor, go to apps > gnome-power-manager > backlight > idle_dim_time

Thank you very much!

---

### Post by Cenoforums on 2011-04-03
Thank you so much for this!

---

### Post by rwankar on 2011-11-02
Any idea how to do this in 11.10?

---

### Post by mcduck on 2011-11-02
> **rwankar said:**
> Any idea how to do this in 11.10?

Sure. it's pretty much the same as in previous versions, only difference being that the setting is stored in Gsettings/dconf instead of the old Gconf. Sstart by installing [dconf-tools]("apt:dconf-tools"). Then run dconf-editor, browse to *org.gnome.settings-daemon.plugins.power* and change the *idle-dim-time* to whatever you want. The value is in seconds.

Alternatively a way that doesn't require installing dconf-tools; pop open a terminal and run the following command, changing the time value to suit your taste of course:
```
gsettings set org.gnome.settings-daemon.plugins.power idle-dim-time 60
```

---

### Post by rwankar on 2011-11-02
Thanks. That worked. I had tried the gconf-editor option but gnome-power-manager does not show up in it.

Out of curiosity, why isn't something like this part of the "screen" page under settings? It is so confusing (gconf-editor, dconf-editor, gnome-tweaks, compiz-settings). How does one know where to change things? One would imagine that with gnome-3 and Unity etc life would be easier, not more difficult!

---

### Post by r_mano on 2011-11-14
Thanks for the tip. The move from gconf to dconf is sometime quite strange (there are still options in the two, you never know which one will be picked by which application --- or there is some way to know?)

> **rwankar said:**
> 
Out of curiosity, why isn't something like this part of the "screen" page under settings? It is so confusing (gconf-editor, dconf-editor, gnome-tweaks, compiz-settings). How does one know where to change things? One would imagine that with gnome-3 and Unity etc life would be easier, not more difficult!

Because the new philosophy is that your are not supposed to have a lot of knobs to touch, otherwise you will damage yourself. So options are getting hidden and hidden and then they disappear. As the "nice" global menu with focus-follow-mouse in unity (for which I fear the solution will be to ditch focus-follow-mouse). :(

The good news is that is Linux, and you can switch distribution, desktop, window manager when you feel that this is going too far. Till now I still find Ubuntu amazing, and thanks (also) to the help here, it's still my best option (although I am honestly thinking about going from Unity to Shell).

---

### Post by rwankar on 2011-11-15
> **r_mano said:**
> 
Because the new philosophy is that your are not supposed to have a lot of knobs to touch, otherwise you will damage yourself. So options are getting hidden and hidden and then they disappear. As the "nice" global menu with focus-follow-mouse in unity (for which I fear the solution will be to ditch focus-follow-mouse). :(

The good news is that is Linux, and you can switch distribution, desktop, window manager when you feel that this is going too far. Till now I still find Ubuntu amazing, and thanks (also) to the help here, it's still my best option (although I am honestly thinking about going from Unity to Shell).

Just take a look at the Unity Settings app (especially the Switcher and Experimental tabs) and tell me they won't damage me. Also take a look at "Bounce Keys" and "Slow Keys" settings under Accessibility Settings. It takes time to figure out what these will do. If you can have a UI for these, you sure can for "Dim Display". They even took away the font selection from the "Appearance" settings!

I've changed distributions before. That is an even bigger nightmare since there are differences in the names of applications (named on Fedora is bind9 on Ubuntu, httpd in Fedora is Apache2 on Ubuntu), their installation directories are different and how you configure startup services is different.

---

### Post by mcduck on 2011-11-15
> **rwankar said:**
> Thanks. That worked. I had tried the gconf-editor option but gnome-power-manager does not show up in it.

Out of curiosity, why isn't something like this part of the "screen" page under settings? It is so confusing (gconf-editor, dconf-editor, gnome-tweaks, compiz-settings). How does one know where to change things? One would imagine that with gnome-3 and Unity etc life would be easier, not more difficult!

Either because Gnome developers decided that it's not needed, or the more likely alternative, it's simply not done yet. Keep in mind that Gnome 3 is still quite new, and pretty much everything is written from scratch. So when you see a dialog with some features missing that used to be there, keep in mind that the dialog probably isn't the one with some features removed, it's a new one and some of the old features haven't even been coded into it yet.

What comes to gconf/dconf, in the future everything will use dconf, but right now it's still a question of each application's developers to make the change. Things are a bit complicated while everything is moving from Gnome 2 to Gnome 3, but likely

---

### Post by rwankar on 2011-11-15
First, let me say that I love Linux and this is not intended to be a bashing. I applaud the fact that several developers are toiling night and day to bring us free software. I am all for new things and have no issues with learning curves. For example, they replaced RhythmBox and F-Spot.

My objection is to introducing something that is not fully coded as the default. Secondly, you need to make it extremely easy for people to switch back to old stuff that was working perfectly. There are folks who love living on the edge. Let them play with the new stuff. The reason I updated from 11.04 was for updated drivers. Unfortunately, Linux always lacks behind in support due to non-cooperation from vendors. It is also hard to tell before an upgrade what issues you're going to face.

---

### Post by mcduck on 2011-11-15
> **rwankar said:**
> 
My objection is to introducing something that is not fully coded as the default. Secondly, you need to make it extremely easy for people to switch back to old stuff that was working perfectly.
It took Gnome 2 good 8 years to get some of the features people are now complaining to be missing from Gnome 3. And I don't think there even is such state as "fully coded" for a Linux desktop environment. ;)

What comes to switching back to old stuff, there are situations when doing that simply isn't possible, and the move from Gnome 2 to Gnome 3 is one of them. The two aren't compatible with each other, as one of the main reasons for move to Gnome 3 was that the developers needed a fresh start with a new design to fix many of the problems and limitations of the mess Gnome 2 had become over time.

---

