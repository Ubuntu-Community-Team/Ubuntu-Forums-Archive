---
title: "Panel Apps"
date: 2011-05-05
forum: Desktop Environments
---

### Post by Electric_Bubble on 2011-05-05
Can I still access the panel apps in unity? I used to love the whether predictions and a specially the power inhibitor app! Its seems to be impossible to customize the panel nowadays? I'v try'd caffeine as replacement for the inhibitor app, but it doesn't work in 11.04...

---

### Post by Copper Bezel on 2011-05-05
The Unity panel does offer somewhat less configurability, as it's relatively new and separate program written internally (that is, by Ubuntu rather than Gnome developers) and with a different set of goals.

The weather indicator just doesn't come by default anymore and can be installed with the command 

```
sudo apt-get install indicator-weather
```

and it can be run from the Dash or set as a Startup Application (managed by the program Startup Applications, which you can also launch from the Dash.)

Caffeine actually *should* work in 11.04 and within Unity. Is the problem that it (1) fails to install, (2) fails to appear in the panel, or (3) fails to inhibit sleep when run?

---

### Post by Electric_Bubble on 2011-05-05
Thanks, is there a command to install the power inhibitor? I would love to watch some flash vids without the power savings jumping on :-)

Thanks for the help, too bad unity has these major growing pains :-(

---

### Post by Copper Bezel on 2011-05-05
Yeah, it's fairly rough, since it's only been a full release for a week now.

Like I said, the powersave inhibitor, so far as I know, is gone, and I think Caffeine is the better bet. What problem did you have with it?

---

### Post by Electric_Bubble on 2011-05-05
i can install it but it doesn't appear to run. Same in terminal, it gives no feedback whatsoever...  I think i'm gonna use natty in classic mode until unity matures :-).

---

### Post by Copper Bezel on 2011-05-05
Nothing wrong with that option. = ) But is the powersave inhibitor a system tray applet? If so, you should be able to reenable it in Unity via [_this guide_]("http://www.webupd8.org/2011/04/how-to-re-enable-notification-area.html").

Point of fact, you might need to do the same with Caffeine. If you run System Monitor, is caffeine's daemon running?

---

