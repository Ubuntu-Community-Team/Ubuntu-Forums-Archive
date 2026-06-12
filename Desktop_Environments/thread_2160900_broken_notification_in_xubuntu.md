---
title: "broken notification in xubuntu"
date: 2013-07-08
forum: Desktop Environments
---

### Post by tr4rex on 2013-07-08
hi, i have xubuntu installed on laptop. notifications works fine, just like in picture
 [IMG]https://lh5.googleusercontent.com/_1QSDkzYY2vc/TbqXvpgI6fI/AAAAAAAAENg/BjEUJ5hJEts/xubuntu-firefox-notifications.png[/IMG]
after some time i tried i3wm ([http://i3wm.org](http://i3wm.org)), but after i returned to xfce, notifications became broken in xubuntu. and now the look like this
[IMG]http://i.cubeupload.com/tjmhVX.png[/IMG]
do you have any ideas how to fix it?

---

### Post by Toz on 2013-07-09
Is xfce4-notifyd running?
```
ps -ef | grep notif
```

Go to Settings Manager -> Notifications. Which theme is selected? Try changing the theme to see if it helps.

---

### Post by tr4rex on 2013-07-09
yes, the notification is running

```
sergey    2358     1  0 22:07 ?        00:00:01 update-notifier
sergey    2508  2322  0 22:07 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libsystray.so 12 27263017 systray Notification Area Area where notification icons appear 

```
whatever theme and location i choose, the blue rectangle remains on the same position

---

### Post by Toz on 2013-07-09
That's not the notification daemon. You should get:
```

$ ps -ef | grep notif
toz       2428  2332  0 Jul04 ?        00:00:02 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libsystray.so 4 29360173 systray Notification Area Area where notification icons appear 
**[COLOR="#FF0000"]toz       7091     1  0 13:04 ?        00:00:01 /usr/lib/x86_64-linux-gnu/xfce4/notifyd/xfce4-notifyd[/COLOR]**

```

Maybe try running that executable to see if it fixes the problem. If the file doesn't exist, it is part of the **xfce4-notifyd** package.

---

### Post by tr4rex on 2013-07-10
if i try to re-run **[COLOR=#FF0000]xfce4-notifyd,[/COLOR]** then i get message that "another xndaemon is running". i have not found this daemon in services list [http://pastebin.com/ditrdf80](http://pastebin.com/ditrdf80)

---

### Post by Toz on 2013-07-10
Do you have **notify-osd** installed?

Can you post back all of your running processes:
```
ps -ef | grep $USER
```

Looks like another notification daemon is running.

---

### Post by tr4rex on 2013-07-10
i have not notify-osd installed. after installation notifications works fine. thx!

---

### Post by homburg on 2013-10-24
I had to remove (and kill) */usr/bin/dunst* to solve this exact problem.

---

### Post by mreq on 2014-01-26
> **homburg said:**
> I had to remove (and kill) */usr/bin/dunst* to solve this exact problem.

That did the job for me as well, thanks!

```
sudo apt-get purge dunst
```

---

