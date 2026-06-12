---
title: "Update notification applet"
date: 2011-09-15
forum: Desktop Environments
---

### Post by vatzec on 2011-09-15
Do you know of an applet (or a tray icon program) notifying of updates for GNOME? Having the update manager pop up all of a sudden can be distracting. There used to be such a thing in earlier releases of Ubuntu.

Thanks!

---

### Post by Frogs Hair on 2011-09-15
In the update manager settings > update tab ,  you can set to notify only .

---

### Post by Krytarik on 2011-09-15
> **Frogs Hair said:**
> In the update manager settings > update tab ,  you can set to notify only .
This doesn't prevent the Update Manager from popping up, but disabling the key "/apps/update-notifier/auto_launch" in "gconf-editor" does. Then you would get a notification icon in the panel, like you know it from earlier versions of Ubuntu.

Greetings.

---

### Post by Frogs Hair on 2011-09-15
> **Krytarik said:**
> This doesn't prevent the Update Manager from popping up, but disabling the key "/apps/update-notifier/auto_launch" in "gconf-editor" does. Then you would get a notification icon in the panel, like you know it from earlier versions of Ubuntu.

Greetings.

Strange , my update manager has never popped  , but I had been running a dock with no window list for a year prior to Unity . With Unity I have never seen it pop up .

---

### Post by mcduck on 2011-09-16
> **Frogs Hair said:**
> Strange , my update manager has never popped  , but I had been running a dock with no window list for a year prior to Unity . With Unity I have never seen it pop up .

It only pops up once per seven days (if there are updates available), and the counter resets on every update so if you install updates manually (through apt-get, synaptic or the update manager) once in a week you'll never see the update manager window pop up on it's own.

Security updates are an exception, of course, and they should cause the update manager to pop up as soon as it knows that such updates are available.

Anyway, +1 to Krytarik's suggestion. That's what I always do on my own Ubuntu systems. :)

(edit: the "notify only" option in Update Manager's settings tells it to notify about available updates as opposed to downloading & installing them automatically. So that's the default setting, and unless you change the gconf key yourself, the way it's going to notify you is by popping up the update window.)

---

### Post by vatzec on 2011-09-16
> **Krytarik said:**
> This doesn't prevent the Update Manager from popping up, but disabling the key "/apps/update-notifier/auto_launch" in "gconf-editor" does. Then you would get a notification icon in the panel, like you know it from earlier versions of Ubuntu.

Greetings.

Thanks! I'll see if this works.

> **mcduck said:**
> Security updates are an exception, of course, and they should cause the update manager to pop up as soon as it knows that such updates are available.

Hmm, I don't know, I think it's a matter of personal preference - I'd rather have the window never pop up automatically, and just show an icon on a panel, and perhaps a notification via libnotify. :)

---

### Post by nilarimogard on 2011-09-16
> **vatzec said:**
> Do you know of an applet (or a tray icon program) notifying of updates for GNOME? Having the update manager pop up all of a sudden can be distracting. There used to be such a thing in earlier releases of Ubuntu.

Thanks!

I think what you're looking for is [Update Manager Indicator]("http://www.webupd8.org/2011/09/update-manager-indicator-for-ubuntu.html").

---

### Post by colinwood07 on 2011-09-16
Thanks Dear 
I get solution of our problems in this forum...............

---

### Post by Frogs Hair on 2011-09-16
> It only pops up once per seven days (if there are updates available),  and the counter resets on every update so if you install updates  manually (through apt-get, synaptic or the update manager) once in a  week you'll never see the update manager window pop up on it's own.

I never see it because I have been Using Firefox daily /nightly builds for over a year .  Though the update manager  checks daily  I check for and install updates at start-up each morning .  ;):oops:

---

### Post by Krytarik on 2011-09-16
> **vatzec said:**
> and perhaps a notification via libnotify.
Yeah, it would do so also, forgot to mention this. Started doing so a while back, really nice!

---

### Post by vatzec on 2011-09-18
Thanks, everyone. "Update Manager Indicator" seems nice, but it displays the default "no icon" icon on my copy of Natty, at least when no updates are available. Setting the default update notifier not to "auto_launch" is also a cool solution. :)

---

