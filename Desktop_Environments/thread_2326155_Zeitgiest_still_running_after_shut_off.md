---
title: "Zeitgiest still running after shut off?"
date: 2016-05-28
forum: Desktop Environments
---

### Post by DigiAngel on 2016-05-28
Hrmm....zeitgeist is shut off, yet I see:

```
May 28 19:41:21 gamebox gnome-session[1403]: ** (zeitgeist-datahub:2452): WARNING **: zeitgeist-datahub.vala:212: Error during inserting events: GDBus.Error:org.gnome.zeitgeist.EngineError.InvalidArgument: Incomplete event: interpretation, manifestation and actor are required

2452  0.0  0.1 543968 20136 ?        Sl   18:22   0:00 zeitgeist-datahub
2459  0.0  0.0   4508   716 ?        S    18:22   0:00 /bin/sh -c /usr/lib/x86_64-linux-gnu/zeitgeist/zeitgeist-maybe-vacuum; /usr/bin/zeitgeist-daemon
2463  0.0  0.0 405728  6792 ?        Sl   18:22   0:00 /usr/bin/zeitgeist-daemon
2470  0.0  0.0 310996 10736 ?        Sl   18:22   0:00 /usr/lib/x86_64-linux-gnu/zeitgeist-fts

```

Any way to really shut off this feature?  Thanks.

---

### Post by CantankRus on 2016-05-28
You may like to say how you shut it off.

---

### Post by DigiAngel on 2016-05-29
Just went to System Settings -> Security & Privacy -> Files & Applications and set it to off as well as unchecked all the boxes.

---

### Post by buzzingrobot on 2016-05-29
Log out and log back in, or reboot, then check with System Monitor to see if the Zeitgiest process is active.

Unchecking it in System Settings should prevent it from launching in future sessions but it does not terminate current active processes.

---

### Post by DigiAngel on 2016-05-29
Thanks....however it's been set like that since I did the upgrade....I think the filesystem shows zeitgeist still updating files up to the minute:

```
-rw------- 1  53K May 21 08:33 activity.sqlite
-rw------- 1  32K May 29 05:44 activity.sqlite-shm
-rw------- 1 684K May 29 05:44 activity.sqlite-wal
drwxr-xr-x 2 4.0K May 28 18:22 fts.index
```

Interesting...

---

### Post by CantankRus on 2016-05-29
I don't think just turning off recording of "file and application usage" turns off the zeitgeist processes.
You could uninstall zeitgeist-core and zeitgeist-datahub but then you lose functionality of the unity dash.
[**_[COLOR="#B22222"]Why Zeitgeist Is Not Evil[/COLOR]_**]("http://www.omgubuntu.co.uk/2012/08/is-zeitgeist-spying-on-you")

---

### Post by DigiAngel on 2016-05-29
Thanks @CantnkRus...I guess I'll just leave it be for now...and thanks for the link that was very helpful.

---

