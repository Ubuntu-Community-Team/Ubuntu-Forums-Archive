---
title: "Problem possibly with Xorg or Windows Manager"
date: 2014-11-11
forum: Desktop Environments
---

### Post by lama2p0 on 2014-11-11
Ok so, my laptop kind of freezes, once in a while.. By kind of, I mean mostly freezes.. Sound can still be heard, and I can still alt+ctrl+F1-F7.. Sometimes I still even have a cursor to move. It seems just the screen freezes..

This problem occurs mostly when trying to Alt+Tab or change volume level. And also seems only when something is Fullscreen, like a game.

Other things to note that might be related, some tasks start slowly(such as files/nautilus), sometimes my environment hangs for a few seconds to upwards a minute while loading or exiting applications. 

When this happens, shutdown doesn't go through properly, hangs at shutdown screen, and am forced to shutdown via button. I use '$ sudo halt now' to shutdown after this happens.

This problem doesn't always occur, and sometimes the conditions are different.


Ubuntu Gnome 14.04.1
My laptop: [http://www.msimobile.com/level3_productpage.aspx?id=454](http://www.msimobile.com/level3_productpage.aspx?id=454)

---

### Post by tgalati4 on 2014-11-11
Check the status of your hard disk:

```
sudo smartctl -a /dev/sda
```

Then check your log files:

```
more /var/log/syslog
```

and

```
more /var/log/Xorg.0.log
```

---

### Post by lama2p0 on 2014-11-11
smartctl command isn't found..

syslog: [http://tny.cz/ee8da9e0](http://tny.cz/ee8da9e0)
Xorg.0.log: [http://tny.cz/33a4ab69](http://tny.cz/33a4ab69)


I'm not sure what to look for in these..

Is it Bumblebee causing this?? I see a lot of (WW) and (EE) from Bumblebee.

---

