---
title: "Where did speaker graphic go on Jaunty?"
date: 2009-06-07
forum: General Help
---

### Post by egruber on 2009-06-07
I upgraded to Jaunty on my IBM T40.  On the prior release, raising and lowering the volume using the laptop keys brought up a graphic of a speaker showing the adjustments.  The graphic would fade in a couple of seconds.  

Since the upgrade, the keys still adjust the volume, but there is no graphic.  And setting 'mute' does not show on the speaker icon, either. So it is hard to tell if mute is on or not.  Any ideas what happened?  Do I have to set something?  Thanks!

---

### Post by fooman on 2009-06-07
check that the "notify-osd" package is installed.  open a terminal and run this command:

```
sudo apt-get install notify-osd
```

hope that helps.

---

### Post by egruber on 2009-06-08
It came back and said I already had the newest version, so I guess that wasn't it.  Any other suggestions?  Thanks!

---

