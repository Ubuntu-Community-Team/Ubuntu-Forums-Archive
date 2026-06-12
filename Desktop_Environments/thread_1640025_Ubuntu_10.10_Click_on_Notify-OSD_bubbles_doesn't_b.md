---
title: "Ubuntu 10.10: Click on Notify-OSD bubbles doesn't bring the related app to front"
date: 2010-12-07
forum: Desktop Environments
---

### Post by iFrodo on 2010-12-07
I was expecting that notify-OSD bubbles behavior to bring the app displaying the notification, when you click on them.

But in my case, when the mouse pointer enters the bubble, it fades out a little, and when I click on it, nothing happens.

Is that normal? Why doesn't a click bring the related app to front?

---

### Post by mcduck on 2010-12-07
That's how it's supposed to work. The notification bubbles fade away if you move the mouse over them, allowing you to see (and click) whatever is behind the bubble.

If there's an icon related to the notification, then clicking on the icon would bring the app to foreground.

---

### Post by tom4everitt on 2010-12-07
It is so by design actually. They are supposed to be as non-interfering as possible. From Launchpad 

> 
The freedesktop.org Desktop Notifications Specification provides a standard way for applications to display pop-up notifications. These are designed to make you aware of something, without interrupting your work with a window you must close.

Notify OSD presents these notifications as ephemeral overlays, which can be clicked through so they don't block your work. It queues notifications, to prevent them from flooding your screen. And as well as handling standard notification updates, Notify OSD introduces the idea of appending &#8212; allowing notifications to grow over time, for example in the case of instant messages from a particular person.

Link: [https://launchpad.net/notify-osd](https://launchpad.net/notify-osd)

There might be a way to change the behavior, I don't know.

EDIT: Seems like I was too slow :)

---

### Post by debray6379 on 2010-12-22
is there a way to turn these off,edit timing and/or placing of the bubbles.

this really is not the type of thing I like on my desktop and although I understand why it's there I wish I could turn it off or at least change it or move it in some way so it is not so annoying to me.

thank you in advance.

---

### Post by stinkeye on 2010-12-22
> **debray6379 said:**
> is there a way to turn these off,edit timing and/or placing of the bubbles.

this really is not the type of thing I like on my desktop and although I understand why it's there I wish I could turn it off or at least change it or move it in some way so it is not so annoying to me.

thank you in advance.
You can edit various settings with a patched NotifyOSD package.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/10/tweak-notifyosd-notifications-in-ubuntu.html[/COLOR]_**]("http://www.webupd8.org/2010/10/tweak-notifyosd-notifications-in-ubuntu.html")

---

