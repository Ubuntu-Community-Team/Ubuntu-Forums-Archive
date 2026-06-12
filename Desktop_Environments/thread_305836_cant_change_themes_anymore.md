---
title: "cant change themes anymore"
date: 2006-11-24
forum: Desktop Environments
---

### Post by llamapalooza489 on 2006-11-24
I just upgraded to edgy for dapper, and i'm stuck in a boring dark grey theme with default icons.  whenever i try to change the theme elements in the Theme Preferences nothing happens.  I'm not sure what other information to give, so if you need more just ask.  Thanks.

Edit: When i run gnome-theme-manager from the terminal i get this message:
```
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.ipc_key'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM dmix:Live
Window manager warning: Failed to read theme from file /usr/share/themes/metacity-1/metacity-theme-1.xml: Failed to open file '/usr/share/themes/metacity-1/metacity-theme-1.xml': No such file or directory

```

---

### Post by llamapalooza489 on 2006-11-24
anyone there?

---

### Post by al_sharpe on 2006-11-25
I also have the exact same four ALSA lines of error messages except
last word says nForce3 instead of Live and sound is not working
correctly

Al Sharpe

---

### Post by ronocdh on 2006-11-26
I can't use custom themes correctly, either. I can change window borders alright, and often I can see the difference between light and dark themes, but the buttons and contours of the windows won't change for custom themes. These are the same theme files I used in dapper, of course, and I've downloaded the most recent versions of them. =/

---

### Post by mcduck on 2006-11-27
try running 'gnome-settings-daemon', and if that solves the problem add it to your session (System/Preferences/Sessions/Startup Programs).

---

### Post by phormion on 2006-11-27
I think the error message is related to ALSA sound support - I'm also getting it when I try to test playback with ALSA (alsaplayer). On my computer, currently only oss sound output works (!). Here's another thread on this: 

[http://ubuntuforums.org/showthread.php?t=211218](http://ubuntuforums.org/showthread.php?t=211218)

This is really annoying, since it worked in Dapper and the upgrade to Edgy broke it. I regret voting that the upgrade to Edgy caused "little problems", this is quite bad.

---

