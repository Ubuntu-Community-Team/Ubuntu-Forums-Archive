---
title: "[SOLVED] Radeon Mobility X1400 with Compiz"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by olieviya on 2007-09-14
I know other people have had help etc etc on the topic but I don't see anybody who has the same problem as me exactly so here I go:

I managed to get Compiz working, fully working with all the options being just fine by following this: [How-to]("http://blog.stephanbuys.com/2007/04/compiz-and-ubuntu-feisty-fawn-ati-x1400.html") it was perfect and exactly what I wanted except one problem: **the icons and the theme controls could NOT be changed ** and they were reverted to a default disgusting shade of dark grey and blue and the icons were gnome defaults (at least as far as I could tell by using the Theme options they could **not** be changed). And, it decided to revert to the default (I'm supposing) keyboard settings making my GB keyboard work like a USA one, but I just changed it so this was fixable.

This frustrated me so I tried the how-to on this website (first removing all I had previously done above to make sure I don't crap it all up): [here]("http://wiki.linuxfellaz.net/doku.php?id=ubuntu:compiz"). And this time it had the icons working correctly but Compiz just made my system hang after telling me about an [COLOR="Red"]error[/COLOR] that was something like: Expected list but got string or the other way around.

Any ideas would be much appreciated as now** I cannot go back to how it was** with the first how-to because the error remains.

Cheers!

---

### Post by Forlong on 2007-09-14
You are mixing two problems here.
> **olieviya said:**
> **the icons and the theme controls could NOT be changed ** and they were reverted to a default disgusting shade of dark grey and blue and the icons were gnome defaults
That is an issue of Xgl and would've been easy to solve by running
```
gnome-settings-daemon
```

But the error of the second guide might just be due to the repository you use - which is the same in both guides.
That's probably why you can't "go back".
You can post the output here and we can see, what we can do about it.

---

### Post by olieviya on 2007-09-16
> **Forlong said:**
> 
That is an issue of Xgl and would've been easy to solve by running
```
gnome-settings-daemon
```

Yay, just got it working again (by doing a fresh install of ubuntu), but running that doesn't seem to help, What reaction am I expecting to get after running that? All I got was some icons seemed to change but they don't change when I use the theme manager, I'm confused.
The main problem is the icons/themes are acting weird. I cannot change theme controls or icons or colours (where applicable) I can only change the window border. The preview in the theme manager (ie the image of what it should look like) does update though! By the way this behaviour occurs when I have Compiz working and when I don't. Any ideas?

I also have attached a screenshot to display what I mean - if I am being ambiguous. You can see in the screenshot that the current theme has not been applied at all.

Just wondering if could it have anything to do with the way the [How-to]("http://blog.stephanbuys.com/2007/04/compiz-and-ubuntu-feisty-fawn-ati-x1400.html") that I followed runs xgl? I have read [here]("https://help.ubuntu.com/community/CompositeManager/Xgl") that there are a few ways and it seems they aren't agreeing exactly on the one I'm using/the one from the how-to.



After experimenting a bit I have found a way this can be made to work, basically if I log in to a normal gnome without xgl and change the settings and then log out and log into the one with xgl that Compiz works on I can run the gnome-settings-manager and it will update the theme/icons/etc.

```
$ gnome-settings-daemon
Warning:          No symbols defined for <SYRQ> (keycode 92)
Warning:          No symbols defined for <II65> (keycode 101)
[...]
Warning:          No symbols defined for <I7D> (keycode 253)
Warning:          No symbols defined for <I7E> (keycode 254)
Warning:          No symbols defined for <I7F> (keycode 255)
xrdb:  "*Label.background" on line 243 overrides entry on line 170
xrdb:  "*Text.background" on line 249 overrides entry on line 211
xrdb:  "*Label.foreground" on line 255 overrides entry on line 171
xrdb:  "*Text.foreground" on line 261 overrides entry on line 212

** (gnome-screensaver:6842): WARNING **: screensaver already running in this session

```

What can I do to make this run at start-up and why was it not running since it seems to be included here (/usr/local/bin/startcompiz):


```

    #!/bin/bash # # Start beryl-manager within gnome-session # if (( `ps -A -o comm | grep -c '^Xgl$'` == "1" )); then DISPLAY=:1 gnome-settings-daemon & DISPLAY=:1 compiz --replace else echo "${0}: Error: compiz not launched. Xgl not running?" fi

```

PS: have also discovered that running gnome-settings-daemon as non-root is what makes it work, as root just makes it self-quit.

---

### Post by Forlong on 2007-09-17
I can't say anything about some How-To you used from the internet.
I only recommend using Method A from here: [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)


I know the guide could use a little troubleshooting section... I'm going to enhance it, when I'll find some time. I already did this [here](http://wiki.ubuntuusers.de/Xgl) but that's in german.

---

### Post by olieviya on 2007-09-18
I got it working basically I did a clean install of ubuntu followed the how-to and added gnome-settings-daemon to start up and it works like a charm :KS

---

