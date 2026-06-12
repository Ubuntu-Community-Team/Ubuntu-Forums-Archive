---
title: "Can't save settings in LiquidWeather"
date: 2005-11-06
forum: Desktop Environments
---

### Post by tiagobt on 2005-11-06
I compiled the latest version of SuperKaramba and installed LiquidWeather 8.6 (SKZ format). It works fine and I can make all the settings I want. The problem is that I can't save the settings using this new theme format. I created a link in KDE's autostart folder with the command:

```
superkaramba 'path_to_the_theme/lwp-8.6.skz'
```

The theme is started everytime I start KDE, but the settings return to default. Is there a way I can save them?

---

### Post by ltmon on 2005-11-06
Hi,

For autostarting liquid weather, don't bother with the autostart.  Just set it running and leave it there when you log out.

In your SystemSettings you should find a "Session Manager" dialog that allows you to fine tune this behaviour.

Possibly what happened is that you are getting multiple versions of LiquidWeather starting up because of this, and one is overwriting the other's settings?

Either that or you once started up LWP with "sudo" and the root user now owns the setting file and you have no permissions.

L.

---

### Post by tiagobt on 2005-11-07
Thanks again, Itmon! I just delete my autostart link, made all the settings I wanted in LiquidWeather, and restarted KDE without closing SuperKaramba. It worked like a charm!

---

