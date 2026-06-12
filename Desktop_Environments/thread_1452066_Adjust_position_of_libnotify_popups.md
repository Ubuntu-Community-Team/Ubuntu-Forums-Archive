---
title: "Adjust position of libnotify popups?"
date: 2010-04-11
forum: Desktop Environments
---

### Post by isbura on 2010-04-11
More and more applications seem to be using libnotify for their pop-up notifications. While standardization is good, it's driving me mad that I can't find a way to move the location of the pop-ups.

I have a dual-monitor setup where I spend most of my time looking at my primary monitor but all notifications keep popping up slightly offscreen in the top-right corner of my second monitor (which is at a slightly lower resolution than the primary). So, not only are they way out of my line of sight but I can't even read them on the rare occasion I do happen to notice them.

My first instinct was to try and mouseover them and drag them to a new location. However, this simply causes them to vanish and reappear when I move the mouse off them again - very unintuitive behaviour!

After that, I tried searching through gconf-editor for some way to change the coordinates but couldn't find anything.

Does anyone know how/where to change their location? Ideally I'd like them to appear just below or above one of the GNOME panels, which seems like the logical place for them to be.

---

### Post by stilling on 2010-04-11
try and see this maybe can help you

[http://ubuntuforums.org/showthread.php?t=1378676](http://ubuntuforums.org/showthread.php?t=1378676)

---

### Post by isbura on 2010-04-11
Thanks for the link. None of the patches helped much, but you did point me in the right direction - I was searching for libnotify problems rather than the real culprit **notify-osd**.

After reading up on notify-osd, it seems part of the rationale behind it is that the position should explicitly *not* be under user control. I could live with that if the system was implemented well, but having notifications appear partially (or completely) off-screen on the wrong monitor suggests that it needs more work.

In the meantime I'm going to attempt to revert back to the old notification-daemon / notification-properties by following:

> **gradinaruvasile said:**
> U can revert to the older style notification by (commands in terminal):

1. Install the notification-daemon package:

```
sudo apt-get install notification-daemon
```

2. Rename the /usr/lib/notify-osd/notify-osd executable

```
sudo mv /usr/lib/notify-osd/notify-osd /usr/lib/notify-osd/notify-osd-original
```

3. Create a symbolic link:

```
sudo ln -s /usr/lib/notification-daemon/notification-daemon /usr/lib/notify-osd/notify-osd
```

4. Kill the original notification:

```
sudo killall notify-osd
```

5. Launch the new notification - press alt+F2, type /usr/lib/notify-osd/notify-osd

6. Test:

```
notify-send test test
```

With this older notification type u can use the notification-ptoperties tool to set the location of the notification pop ups

---

### Post by shimoda on 2011-03-15
Any advance on adjusting libnotify...?

Or the only solution is to replace it?

thanks!

---

### Post by Krytarik on 2011-03-15
> **shimoda said:**
> Any advance on adjusting libnotify...?

Or the only solution is to replace it?

How about this: [http://ubuntuforums.org/showthread.php?p=10115367](http://ubuntuforums.org/showthread.php?p=10115367)

Is the level of adjustability high enough in your case?

---

### Post by MestreLion on 2012-06-15
> **shimoda said:**
> Any advance on adjusting libnotify...?
Or the only solution is to replace it?
thanks!

You don't need to replace libnotify, the bug is in notify-osd, and a workaround was made there is a setting at dconf that changes the notify-osd behavior.

Look here for the steps:

[http://askubuntu.com/a/151542/11015](http://askubuntu.com/a/151542/11015)

(and, if it works for you, I would be glad if you upvote my answer)

---

### Post by Perfect Storm on 2012-06-16
Necromancing.


Thread closed.

---

