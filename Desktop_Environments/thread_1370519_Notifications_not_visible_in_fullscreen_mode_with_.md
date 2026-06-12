---
title: "Notifications not visible in fullscreen mode with xfwm4 (Xfce window manager)"
date: 2010-01-02
forum: Desktop Environments
---

### Post by darthmob on 2010-01-02
I'm using xfwm4 as window manager on ubuntu 9.10 (so I guess it counts as a Xfce problem). What has been bothering me for quite a while is that notifications are not visible when applications run in fullscreen.

For example on my notebook Firefox always runs in fullscreen mode (it's only 12" so I need to use all the space I got ;-) ) and I never see when someone sends me a message over icq / msn. It's the same problem when watching videos in fullscreen with vlc.

Who knows a solution? Does the problem exist when running Xubuntu (with a full Xfce installation) as well?
Testing if it works is very easy. Simply enter the following command in a terminal, switch to a fullscreen application and wait.
```
sleep 3 && notify-send test
```
If there's no notification saying "test" visible after three seconds it doesn't work.

Thanks a lot in advance. :)

---

### Post by darthmob on 2010-01-03
*Giving this topic a gentle nudge* :KS

---

### Post by darthmob on 2010-01-07
Another bump. :KS

Come on guys, don't tell me no one uses Xfce!

---

### Post by McFlow on 2010-04-20
I'm using Xfce on Arch... but I am looking for that feature too!

---

### Post by kerry_s on 2010-04-20
i use a script that converts notify-send to zenity if you want to try that. you just name it notify-send & put it in /usr/local/bin

```

#!/bin/bash
zenity --info --text="$@"

```

---

