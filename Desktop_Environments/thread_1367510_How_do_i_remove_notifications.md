---
title: "How do i remove notifications?"
date: 2009-12-29
forum: Desktop Environments
---

### Post by GmAz on 2009-12-29
On my screen shot below, I get notifications from time to time and I can't stand them.  How can I get rid of them.  The notification is located in the upper right corner.

[IMG]http://dl.dropbox.com/u/1376995/grrr.png[/IMG]

---

### Post by Mahngiel on 2009-12-29
Right-click on it, and "remove from panel"

---

### Post by GmAz on 2009-12-29
Not the icons on the upper panel.  I updated my screenshot because it may have been confusing.  I circled what I want gone.  Oh, and when you mouse over it, it disappears until you move the mouse again.

I guess its part of libnotify, but annoying as hell on a netbook.

---

### Post by Mahngiel on 2009-12-29
aah, gotchya. ya, that thing IS quite annoying. i'll be payint attention to this thread myself. love the singature btw. truly funny.

---

### Post by drs305 on 2009-12-29
I think this is what you are looking for, since you mention libnotify:

Turn off:
```
sudo chmod -x /usr/lib/notify-osd/notify-osd
```
or rename the service:

```
sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled 
```

---

### Post by GmAz on 2009-12-29
Ok, I ran each of those commands and now my netbood interface won't come back up.  i can open firefox using Alt-F2, but I can't get my interactive desktop back.  i undid the renaming of the service, but what is the command to undo the chmod -x command?

---

### Post by drs305 on 2009-12-30
> **GmAz said:**
> Ok, I ran each of those commands and now my netbood interface won't come back up.  i can open firefox using Alt-F2, but I can't get my interactive desktop back.  i undid the renaming of the service, but what is the command to undo the chmod -x command?
Sorry it didn't work for your netbook.

```

sudo chmod +x /usr/lib/notify-osd/notify-osd
```

---

