---
title: "Banshee Notifications Via New Jaunty Notifications?"
date: 2009-06-11
forum: General Help
---

### Post by wpwend42 on 2009-06-11
I may be overlooking something obvious, but is there a way to get Banshee notifications (new song playing, etc) in Jaunty's new panel notifier?  I don't see any kind of option for doing this.  Thanks.

---

### Post by Tipped OuT on 2009-06-11
Doesn't look like Banshee does work with the new notification system, at this point.

---

### Post by wpwend42 on 2009-06-14
Ok, fair enough, I was just wondering.  I'm sure it will in an upcoming release.  That would be really neat.

---

### Post by NoPoChris on 2009-07-13
```
sudo apt-get install notify-osd
```

This worked for me, except it just shows the new song title and artist, there's no option to skip the song like there was with the old notifications.

Also, make sure notifications are enabled. Right click on the banshee notification area icon and check *Show Notifications*

---

