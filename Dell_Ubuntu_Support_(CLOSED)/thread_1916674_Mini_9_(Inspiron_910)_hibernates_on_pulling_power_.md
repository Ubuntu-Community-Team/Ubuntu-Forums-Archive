---
title: "Mini 9 (Inspiron 910) hibernates on pulling power cable"
date: 2012-01-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ugm6hr on 2012-01-28
Ubuntu 11.10 with Gnome 3 (Mint) on my Mini 9....
Found that whenever I pull the power cable, it estimates remaining time as about 5 minutes, despite being >95% charge.
This triggers Gnome 3's power management - which then hibernates the netbook immediately. I can prevent this by suspending or hibernating before the auto hibernation, and switching back on, but it shouldn't be necessary.

For anyone who is having the same problem - I found this:
[http://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value](http://askubuntu.com/questions/92794/how-to-change-critically-low-battery-value)
> Start dconf-editor.
Browse to org->gnome->settings-daemon->plugins->power.
Change the values of percentage-critical and percentage-action to the level you require.
And change use-time-for-policy to false
Or, as I did - in Terminal:
```
gsettings set org.gnome.settings-daemon.plugins.power percentage-critical 10
gsettings set org.gnome.settings-daemon.plugins.power percentage-action 9
gsettings set org.gnome.settings-daemon.plugins.power use-time-for-policy false
```
This appears to fix the problem

---

