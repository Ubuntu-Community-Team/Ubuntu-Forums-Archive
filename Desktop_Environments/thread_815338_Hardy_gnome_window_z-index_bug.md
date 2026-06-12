---
title: "Hardy gnome window z-index bug"
date: 2008-06-01
forum: Desktop Environments
---

### Post by Blednik on 2008-06-01
Greetings.

Some time ago I updated my 7.10 ubuntu box to the latest, 8.04 (Hardy). Ever since the update I've been getting this strange bug in gnome with bringing selected windows to front. 

The problem is that whenever I click an inactive window like the gedit window behind my firefox, it won't become top-most. Instead, it will stay behind firefox. The window does gain focus because I can see the color change of the border on the top of the window where the window name is located. Ironically, this bug does not happen when clicking the window by its top border.

Here's a quick screenshot:
[[IMG]http://img263.imageshack.us/img263/8107/screenshotys7.th.png[/IMG]](http://img263.imageshack.us/my.php?image=screenshotys7.png)

I suspect it has something to do with compiz settings, but I am not sure.
Any ideas?

---

### Post by Blednik on 2008-06-07
bump

---

### Post by Schalken on 2008-06-07
Hmmm, I might know what it is.

Install compizconfig-settings-manager if you haven't already.

Then go to System > Preferences > Advanced Desktop Effects Settings, then "General Options" at the top, then the "Focus & Raise Behavior" tab and make sure "Raise On Click" is checked.

If that doesn't work, there must be some other sort of other program or configuration at play.

---

### Post by Blednik on 2008-06-07
Yes, that fixed it. Thanks. I wonder how it got disabled in the first place.

I have something to report about Ubuntu's default window decorator. There have been reports that nVidia GeForce 8 series are having trouble giving smooth window animations. This is due to a power saving feature that lowers the frequency of the GFX card clock and so decreases performance. The results are choppy window animations.

However, I noticed that it mostly seems to happen with ubuntu's default window theme (Human). After I changed the theme to Clearlooks, the choppy animations were gone. Can someone confirm this?

Also, after customizing the Clearlooks theme a bit, I had another problem with Nautilus, where dragging a file for about one second caused my X11 to crash and restart to the login screen. I've traced the problem to my Clearlooks theme. The crash doeesn't happen with Human theme.

---

### Post by Schalken on 2008-06-07
I get the choppy animations on my 8400M GS as well. However, changing the window decoration or GTK theme doesn't make much difference.

It seems the first few frames of an animation are choppy, as the chip is in a low-clock speed power-saving state, then the graphics card realises it needs to step up its clock rate and the animation is smooth from there on. I think this feature is called "PowerMizer" and can be disabled in your xorg.conf. *investigates*

---

### Post by Blednik on 2008-06-07
Oh? I've been running the nVidia settings window where the powermizer shows the card frequency and it does not increase at all on my laptop. It stays on the lowest setting even when windows are being animated. There was some console command (glxinfo?) that increased the frequency of the card to its max for a while. While at max, the anims played very smoothly.

What I am trying to say is that I'm getting smooth animations with certain window themes (Clearlooks) while the GFX card is on its lowest power mode all the time. The Human theme on the other hand gives more lagged animations with the same power settings. I am using GeForce 8600M GT.

---

