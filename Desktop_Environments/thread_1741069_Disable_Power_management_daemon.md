---
title: "Disable Power management daemon"
date: 2011-04-27
forum: Desktop Environments
---

### Post by cccc on 2011-04-27
hi

I have Lucid Lynx with Gnome and Kernel 2.6.32 installed.
Which probelms can I get if I disable Power Manager (Power management daemon) from the startup?

BTW does ```
xset -dpms s off
```do the same thing like disable Power Manager in the Starup Applications or DPMS is just for the Monitor?

---

### Post by Buntumatic on 2011-04-27
[COLOR=Blue]xset -dpms off[/COLOR] will disable monitor sleep, useful if you watch video and do not want the screen blacked out.

---

### Post by Yellow Pasque on 2011-04-27
Some people have reported long logout times from Gnome when not running the power daemon. If you're not using a laptop, then I suggest just disabling it in the Startup Applications and seeing what happens. Monitor your CPU temp and frequency. If it's not downclocking at idle, control it with cpufrequtils.

I prefer the xfce power manager, which you can use with gnome.

---

### Post by Copper Bezel on 2011-04-27
Ditto - I'm using primarily Gnome services, but the power manager fails to launch sometimes and has caused me some other annoyances, so I've been using XFCE's without a hangup. Its menu behavior is annoying and it doesn't do battery health statistics, but I like that it appears in the Notification Area instead of the Indicator Area. (Terribly annoying to see my battery icon sitting in between my indicators for Tomboy and Dropbox.)

---

### Post by flyingAnt on 2011-04-28
Come in study:p

---

