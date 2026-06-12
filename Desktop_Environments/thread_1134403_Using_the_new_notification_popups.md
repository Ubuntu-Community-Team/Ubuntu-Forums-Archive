---
title: "Using the new notification popups"
date: 2009-04-23
forum: Desktop Environments
---

### Post by sygard on 2009-04-23
Hi!

I have a script i migrated from 8.10 to 9.04 where I use libnotify-send to inform the active user. In 9.04, this does not work anymore, or, it does work to some degree... If you install the libnotify-bin package, you can still notify the active desktop user, but not through the new notification system, but it pops up a message-window.

Now, how to I use the new notification system?

What is the equivalent command to 8.10's "notify-send" in 9.04?

Thanks !

---

### Post by sygard on 2009-04-24
Never mind, I found the solution.

It turns out I had some deprecated parameters in my notify-send string, making the notification show up as a dialog box.

After installation of libnotify-bin, the notify-send command worked perfectly!


/Sygard.

---

### Post by Tibuda on 2009-04-24
You already figured it out, but I think it is happening because you are displaying interactive notifications (with buttons). Those are supposed to be dialogs in the new system. See [https://wiki.ubuntu.com/NotifyOSD#Fallback%20alert%20boxes](https://wiki.ubuntu.com/NotifyOSD#Fallback%20alert%20boxes)

---

### Post by sygard on 2009-04-24
> **danielrmt said:**
> You already figured it out, but I think it is happening because you are displaying interactive notifications (with buttons). Those are supposed to be dialogs in the new system. See [https://wiki.ubuntu.com/NotifyOSD#Fallback%20alert%20boxes](https://wiki.ubuntu.com/NotifyOSD#Fallback%20alert%20boxes)

Handy page, thanks!

---

