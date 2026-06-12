---
title: "File manager fonts and window themes are not working after upgrade to Ubuntu 14.04."
date: 2014-04-18
forum: Desktop Environments
---

### Post by ghedum on 2014-04-18
The first thing I observed after upgrading to new Ubuntu 14.04 is that the fonts in the file manager (both the tree and the folder names) are not the default Ubuntu fonts, but something basic, not formatted. 
I decided to change the theme. Used Unity Tweak Tool, Ubuntu Tweak and Gnome Tweak tool - nothing helped.

Then I decided to install Mediterranean theme. Used Ubuntu tweak. It changes the GTK Theme, and even changed the font as it should be, but this time it doesn't change the Window theme. As a result, the window frame is square (see image attached).

I don't know what happens, but there's something wrong, maybe in the system settings, that messes up my themes. Maybe somebody can help me?

* It should be noted that I did the Log Off and Restart after the changes. So, it's not the solution.

---

### Post by Frogs Hair on 2014-04-18
Hello and Welcome

I don't know about the fonts , but from what I see at Gnome Look the Mediterranean  themes haven't been updated to GTK 3.10 yet . Some 3.8 themes will work and others wont or not completely. This has happened with every Gnome update since 3.0.

---

### Post by PJs Ronin on 2014-04-18
I have same problem as OP.   Some of my old themes work, others don't.   I'm even having issues with the newly updated Ambiance and Radiance themes that are supposedly tuned for 14.04.   Either way, I'd give it a month-ish so that theme devs and 14.04 can catch up with each other.

---

### Post by ghedum on 2014-04-18
I have restored the original Ambiance theme, and the fonts went back to the unformatted (non-Ubuntu, similar to Verdana). I don't know how to change them.
See attached the fonts styles: how it should be (left-side) and the one that appears by default.

---

### Post by Derek Karpinski on 2014-04-18
Same problem here.  Firefox has an ugly theme for a bit as well.  That seems to go away after a few seconds, but the small ugly fonts never go away.  Also, the Unity top panel has small ugly fonts.  Looks almost like GNOME shell fonts.

[ATTACH=CONFIG]252202[/ATTACH][ATTACH=CONFIG]252203[/ATTACH]

---

### Post by PJs Ronin on 2014-04-18
I do not believe that fonts should/do change when you change themes (I may be wrong).   Anyhow, to change to something you want open Unity Tweak Tool and go to the fonts section.   You can set anything you like here, but pay attention to the Appearance (anti-aliasing/hinting section) area.   If you're on an LCD monitor then you should set the same as I have.   I also find that the DejaVu Sans font is very clean and crisp.

---

### Post by Derek Karpinski on 2014-04-18
What I've found so far:

I installed and played around with Cairo Dock, logged back into unity, and some of the fonts were different.

So if I:

```
unity --replace
```

Now all the fonts/themes are back to normal.  But now Firefox won't start.  Even after reboot.

After a restart there is a definate time, 30 seconds or so, and you can 'watch' the theme changing, along with some of the fonts.

It's sad this is a LTS, I've never had these kind of problems before on a fresh install.

I wish I knew how to log compiz or unity's actions right after log in........can anybody help with that?  I'd like to file an official bug.

---

### Post by Derek Karpinski on 2014-04-21
If I reboot, and wait a few minutes before logging in, everything looks great. :confused:

Definately something going on.  Surprised its not that many people.......

---

### Post by nadro on 2014-06-16
I have the same problem with my Ubuntu 14.04.

BTW. Did you install Ubuntu on SSD? Maybe it's caused by too fast starting time...

---

### Post by emailme-t on 2014-06-21
So I just setup a brand new system - and noticed the font weirdness in Ubuntu right out of the gate.  I've installed unity-tweak-tool and downloaded a bunch of themes -- but when I change the theme, nothing happens.

I'm interested in Nadro's post -- as indeed, I did install the root onto a Corsair SSD.  Does anyone have any further info on problems with using an SSD for the root partition?

---

### Post by david310 on 2014-11-10
> **emailme-t said:**
> So I just setup a brand new system - and noticed the font weirdness in Ubuntu right out of the gate.  I've installed unity-tweak-tool and downloaded a bunch of themes -- but when I change the theme, nothing happens.

I'm interested in Nadro's post -- as indeed, I did install the root onto a Corsair SSD.  Does anyone have any further info on problems with using an SSD for the root partition?

Same here.

I've installed Ubuntu 14.04.01 in a VirtualBox machine. The virtual disk is stored in an external USB 3.0 HD. This installation is fine and stable. Themes and fonts configuration work perfectly in Unity Tweak Tool and Appearance menu of Ubuntu.

However, after installing Ubuntu in my "physical" machine (not a virtual machine), which has an SSD, a lot of bugs happen.
I can't change themes and font renderization configurations. Choosing a different theme (other than Ambiance), either in Unity Tweak Tool or Appearance (Ubuntu System Settings) menu, does nothing. Choosing different font hinting options in Unity Tweak Tool also does nothing.

I didn't have this problem in the past, in Ubuntu 10.04 version, before this aberration called "Unity" has been introduced.

---

### Post by Will_Moonen on 2014-12-14
Very similar to what I'm experiencing.

After replacing a traditional Seagate HDD with a Samsung SSD some strange things are happening.
The most annoying one is that the selected theme only works after a new login.
This behavior applies for every boot.

A clean install of Ubuntu 14.04.1 doesn't solve this.

---

### Post by waleedgplus on 2015-02-12
Same problem here, I replaced my old WD harddrive with WD 1TB 64MB CACHE CAVIAR BLACK, it boots really fast. compiz --replace brings back all the changes made with tweak tools, but on reboot they all disappears (Themes, Fonts and Icons).

---

### Post by rob-traderspit on 2015-05-09
I have the same issue, my workaround is to logout/login again after a reboot. 
My root disk is a SSD but I can't imagine, that this may be the reason for this nasty behaviour.

---

### Post by Himanshu_Amodwala on 2015-06-02
Guys I am also facing the same issue on Lenovo B320 AIO and I have a WD Caviar 1TB HDD. Still the issue persists.

---

### Post by korrosiv on 2015-10-21
I can confirm this issue. Fresh installed Ubuntu 14.04.3 64bit on SSD fails to load the icon/theme 50% of boots if autologin is enabled. With manual login everything is ok. Executing "killall nautilus && compiz --replace" seems to fix the issue when it happens. Looks like the boot is so fast something is not loaded properly. Any further information on this?

---

### Post by rob-traderspit on 2016-01-05
I have the same issue and searching for a solution since months. 
My first idea was, it's maybe theme related or I have destroyed/mixed the settings with tweaking the desktop with unity tweak tools and/or ccsm.

After a reboot, a lot of settings are blown away (font size, theme settings, fonts in conky etc) and the loaded theme in some GUIs looks like old fashion  '90s GTK style. I found out, that multiple  (in most cases 2-3) logout's/login's of the desktop session (not reboots) helps, what sound like a time out issue or something like that of the desktop service.

this post describes the same issue
[http://askubuntu.com/questions/628141/multiple-monitor-configuration-is-delayed-for-40-seconds-on-ubuntu-14-04-lts](http://askubuntu.com/questions/628141/multiple-monitor-configuration-is-delayed-for-40-seconds-on-ubuntu-14-04-lts)

Now, what I did is the same, waiting some (20..40) seconds before login into the desktop session and the theme and all the settings are fine.
but this can't be the final solution ...

My **[FONT=courier new]/var/log/Xorg.0.log[/FONT]** shows, that (in my case) after ~24s the initialization its ready (my interpretation) and from that it works fine

[FONT=courier new][    23.757] (II) XKB: reuse xkmfile /var/lib/xkb/server-11E5xxxxxxxxxxxxxxxxxxxxx.xkm
[ **   23.792**] (II) intel(0): resizing framebuffer to 3840x1080
[ 23.792] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI1 using pipe 0, position (0, 0), rotation normal, reflection none
[ 23.824] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 1, position (0, 0), rotation normal, reflection none
[ 23.840] (II) intel(0): switch to mode 1920x1080@60.0 on HDMI2 using pipe 1, position (1920, 0), rotation normal, reflection none[/FONT]

Can anyone confirm, that waiting of at least 40s before login to the desktop session "solve" the described problem ?

---

