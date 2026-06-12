---
title: "how can I enable the new notification system in ubuntu 9.04?"
date: 2009-04-25
forum: Desktop Environments
---

### Post by self.python on 2009-04-25
I just upgraded to ubuntu 9.04, and the new notification system does not seem to be enabled by default. How can I enable it?

---

### Post by gettinoriginal on 2009-04-25
Right click your panel where you wish notifications to be and select "add to panel", then choose "notfication area".  :P

---

### Post by markitoxs on 2009-04-25
You just need to add to the panel the notification area.

---

### Post by self.python on 2009-04-25
thanks for replying, but I meant this:

[http://www.markshuttleworth.com/wp-content/uploads/2008/12/jaunty904_notifications_example1_web_092.swf](http://www.markshuttleworth.com/wp-content/uploads/2008/12/jaunty904_notifications_example1_web_092.swf)

---

### Post by organicanagram on 2009-04-26
try looking for notify-osd in the synaptic package manager, and installing it. if you want to revert, ubuntu currently uses notification-daemon.
or, in a terminal:
```

sudo apt-get install notify-osd

```

---

