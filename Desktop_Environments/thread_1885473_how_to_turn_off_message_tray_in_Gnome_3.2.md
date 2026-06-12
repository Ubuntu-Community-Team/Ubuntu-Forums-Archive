---
title: "how to turn off message tray in Gnome 3.2?"
date: 2011-11-23
forum: Desktop Environments
---

### Post by cortman on 2011-11-23
I tried to post about this earlier, but my terms weren't accurate and created some confusion.
I'd like to know how, if possible, to remove the message tray from Gnome 3.2 This would be the auto-hide bar on the bottom. I think I can move the messages and notifications to the top panel, which I will do, but I'd also like to eliminate the possibility of mousing over the bottom right corner and bringing it up, if possible... Anyone have any ideas?

---

### Post by Frogs Hair on 2011-11-23
You can disable notifications under the user name on the top right . I don't know about removing the bottom panel reveal though . In my case the whether  clipboard , and Mailnag  icons appear there .

---

### Post by cortman on 2011-11-23
Turning off notifications on the top bar didn't change it, unfortunately... There surely has to be a way to do it. I find it very annoying especially that whenever I connect or disconnect from a network, or insert an external drive it pops up and will not autohide until I acknowledge the notification by clicking it and then waiting for several minutes (ok, seconds) until it disappears.

---

### Post by Frogs Hair on 2011-11-23
```
sudo apt-get remove notify-osd
```

This should remove all notification pop-ups . Logout/in may be required .

---

### Post by cortman on 2011-11-23
Thanks for the tip, but unfortunately it doesn't seem to work. I logged out/in, and inserted a USB flash drive and the notification popped right up.
I had hoped there was some way to do it, but it may just be one of those things that stays broken... Maybe I should research writing my own extension script.

---

