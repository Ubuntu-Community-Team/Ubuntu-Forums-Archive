---
title: "How do I turn off screensaver in fresh XFCE?"
date: 2007-09-20
forum: Desktop Environments
---

### Post by cmp1988 on 2007-09-20
Hello, I recently did a fresh install of XFCE from the repos, and I can't seem to adjust my screensaver or power options.  How would I go about doing that?  Under Settings Manager, the Screensaver button doesn't appear.

---

### Post by Hero of Time on 2007-09-23
I'm having the same problem. I use Xubuntu Gutsy tribe 5, and somehow the mcs-manager plugin isn't installed and I can't seem to find it. When I click apps > settings > screensaver settings, I get the error "no such plugin 'screensaver'". I installed a few other screensavers, but I can't run them if I can't open the screensaver options.

---

### Post by durt on 2007-09-23
> **Hero of Time said:**
> When I click apps > settings > screensaver settings, I get the error "no such plugin 'screensaver'". I installed a few other screensavers, but I can't run them if I can't open the screensaver options.

Same problem here. I think that may be trying to access the GNOME screensaver settings. Try installing xscreensaver.

---

### Post by Hero of Time on 2007-09-24
> **durt said:**
> Same problem here. I think that may be trying to access the GNOME screensaver settings. Try installing xscreensaver.
That's just the problem. With or without xscreensaver installed, I get the same error. I checked the 'shortcut' that calls for the settings, it's xfce. Checking it's command, it's 'xfce-settings-show screensaver'. For keyboard settings, it's 'xfce-settings-show keyboard'. So obviously, the command parameter is unknown.

---

### Post by SoloSalsa on 2007-09-29
I just noticed this today.  xsaver settings has been with Xubuntu all along; I can't believe they've left it out now.  It was still present in tribe 4.

How can I point this out to developers?  We really should have xscreensaver settings included.  Is it worth starting a Launchpad report?

---

### Post by meist3r on 2007-10-20
I had the same problem after I installed Xubuntu Gutsy on my Thinkpad today. The screensaver settings just wouldn't show up. Then I did:

```
sudo aptitude reinstall xfce4-mcs-plugins xfce4-mcs-manager xscreensaver
```

It replaced the files with later ones (though no version change apparently). And now everything works like a charm (like I was used to).

---

### Post by rrwo on 2007-12-09
The problem is that Xfce is looking for the xscreensaver configuration utlity, called xscreensaver-demo.  You can fix this by screating a short script in /usr/bin called xscreensaver-demo that launched gnome-screensaver-preferences.

---

