---
title: "After upgrade, X takes 2 tries to start"
date: 2006-06-17
forum: Desktop Environments
---

### Post by tchock on 2006-06-17
I did a big apt-get upgrade/dist-upgrade today and got an updated kernel, fglrx drivers & I think an updated Xorg. I boot to terminal, and I normally type startx to get into X. This .xinitrc had previously worked /w no problems:

```
#!/bin/sh 
gnome-volume-manager & 
gnome-settings-daemon & 
xscreensaver -nosplash &
eval `cat $HOME/.fehbg` &
gkrellm -w &
pypanel & 
#This prevents the panel from failing if it loads too fast 
if pgrep pypanel 
then exec openbox 
else pypanel && exec openbox 
fi
```

Now, however, I get into X and all I see is a desktop BG for about 5 seconds (no pypanel, no gkrellm), then it drops back to terminal. If I type startx again, it goes in and everything starts up normally. So, not critical, but my list of annoying quirks is growing steadily.

Any ideas? Even if just an idea of where I ought to start looking to investigate why it's doing this...


edit:
The only error it seems to give me after exiting is:

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining

Why I get this the first time & not the second is beyond me.

---

### Post by tchock on 2006-06-18
I understand if no one has any idea what is going on here, but I"m not sure what log files might contain information about what is going on... I've looked at Xorg.0.log, and it doesn't seem to contain anything out of the ordinary. Any other places I should be looking?

---

