---
title: "Screensaver is disabled but still activates"
date: 2021-04-05
forum: Desktop Environments
---

### Post by hikariws on 2021-04-05
I had installed Xubuntu on a VM and am leaving it opened with Firefox on my router's overview page. I'd like to keep it opened to watch how it goes while I'm doing other stuff, but after some time the screensaver activates and screen turns black.

I had already gone on Screensaver Preferences and disabled both screensaver and lock screen, but it's still activating.

Am I missing something?

---

### Post by &amp;KyT$0P# on 2021-04-06
What version of Xubuntu?
If Xubuntu 20.04, does [this]("https://ubuntuforums.org/showthread.php?t=2443777&p=13958886&viewfull=1#post13958886") help?

---

### Post by Tadaen_Sylvermane on 2021-04-07
Xubuntu has a minor issue of having multiple screensaver / power management things and some the gui isn't available. I'm not sure if the gnome-screensaver is actually active. The only way I found to eliminate this problem was a purge of all of them. For a vm that wouldn't be a problem at all.

```
apt search screensaver | grep installed
```

That is how I chased them down and kicked them out.

---

