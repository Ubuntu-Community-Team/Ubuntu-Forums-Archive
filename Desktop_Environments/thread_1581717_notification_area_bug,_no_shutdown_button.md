---
title: "notification area bug, no shutdown button"
date: 2010-09-25
forum: Desktop Environments
---

### Post by ipey on 2010-09-25
my shutdown icon on notification area is suddenly gone. Nothing happens when I click it. technically, this doesn't trouble me since I can use shutdown button but I have to to know what to do when something has gone wrong with my system. so could anyone light the way? Many thanks.

this is the screenshot:
[IMG]http://ubuntuforums.org/picture.php?albumid=2028&pictureid=6769[/IMG]

---

### Post by sikander3786 on 2010-09-25
Refreshing the panels might solve the problem. Or a logout/login.

```

sudo killall gnome-panel

```

---

### Post by Dex73 on 2010-09-25
Restart may be in order or it could be a one time hiccup. It may stay if you right click and add to panel.

---

### Post by ipey on 2010-09-26
thanks for replying,

This problem persists even after I've restarted GDM or logged out/in for many times. Well, I'll just add shut down button to the top panel and ignore the bug.

---

### Post by marquinos on 2010-12-28
@ipey: You have the long bug here: [https://bugs.launchpad.net/ubuntu/maverick/+source/gnome-panel/+bug/439448](https://bugs.launchpad.net/ubuntu/maverick/+source/gnome-panel/+bug/439448)
This must be a "critical" bug :(

---

