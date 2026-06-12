---
title: "Lost the update-notifier"
date: 2006-10-13
forum: Desktop Environments
---

### Post by jandi on 2006-10-13
I deleted by mistake the notification area.   After adding a new notification area, firestarter and checkgmail are back, but the update notifier isn't.  I've tried repeatedly removing and adding back the notification area.  I even removed the entire panel and created a new one - not intentionally, oops, but it didn't make any difference either.   I tried restarting my computer too, to no avail.  Update-notifier is running, however, it's nowhere to be seen in the notification area.

Any help would be greatly appreciated.

---

### Post by towsonu2003 on 2006-10-13
> **jandi said:**
> I deleted by mistake the notification area.   After adding a new notification area, firestarter and checkgmail are back, but the update notifier isn't.  I've tried repeatedly removing and adding back the notification area.  I even removed the entire panel and created a new one - not intentionally, oops, but it didn't make any difference either.   I tried restarting my computer too, to no avail.  Update-notifier is running, however, it's nowhere to be seen in the notification area.

Any help would be greatly appreciated.

maybe there is no update to notify? try running it from a terminal and watch its output too.

---

### Post by jandi on 2006-10-13
Interesting...

$ update-notifier

** (update-notifier:6170): WARNING **: already running?


$ sudo update-notifier
libnotify-Message: Unable to get session bus: Unable to determine the address of the message bus

** (update-notifier:6122): WARNING **: not starting because user is not in admin group


System monitor shows the update-notifier, status sleeping.

---

### Post by David Corrales on 2006-10-13
Did you reboot?

---

### Post by towsonu2003 on 2006-10-13
> **jandi said:**
> Interesting...

$ update-notifier

** (update-notifier:6170): WARNING **: already running?


just guessing:
```

killall update-notifier
update-notifier

```

also try 
```

killall gnome-panel    # it will come back :)

```

and restarting X (I think it was ctrl + alt + del)

PS. I still think there is no update to notify, so it doesn't show itself (which is supposed to happen).

---

### Post by dannyboy79 on 2006-10-13
I am having this same problem, can anyone help me? When I do a sudo aptitude update and then a sudo aptitude upgrade, all these packages want to be downloaded for upgrading. The little orange icon used to show up but now it doesn't anymore. Even when I go up to the top right side, it tells me that the update notifier is there. I have even gone into update settings and made sure that it is "smart" updating, which I think it will only update things that are meant for Dapper, not sure though? I also checked the box within synaptic that says, download all updates but don't install. which i would think that it would notify me (orange icon) that I have updates to apply but it's not working. Anyone help with this?

---

### Post by jandi on 2006-10-15
There are some updates left.  The icon was there with some updates pending before I deleted the notification area by mistake.

killall gnome-panel    

actually did the trick.

Which is quite odd, since rebooting the computer made no difference.

Ah well, the icon is back.  I'm happy now.

---

### Post by dannyboy79 on 2006-10-15
what exactly did killing the gnome panel do for you?? did you have to do gnome panel to open it again?? or would it be sudo gnome-panel?

---

### Post by NeoLithium on 2006-10-15
Killing the gnome panel simply stops the panel; and then linux will automatically restart the panel; (I think- With default configurations). You won't have to manually start anything up again. Think of it as a reset for part of your desktop :)

---

