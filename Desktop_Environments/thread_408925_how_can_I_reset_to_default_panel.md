---
title: "how can I reset to default panel?"
date: 2007-04-13
forum: Desktop Environments
---

### Post by slowness on 2007-04-13
I accidentally removed default applets from panel, including laptop battery applet, package notification applet. I tried panel->add to panel, but only colck and volumn control there, the battery icon there is way too ugly. can someone help me? Thanks.

---

### Post by slowness on 2007-04-14
I fixed it, put the steps here for people like me to google:

restart X, then in console:

gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

---

### Post by igor4u on 2007-04-19
Thank you!

---

### Post by Meserias on 2007-12-14
> **slowness said:**
> I fixed it, put the steps here for people like me to google:

restart X, then in console:

gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

Yes indeed this works perfectly on Ubuntu 7.10
Thank you. :guitar:

---

### Post by Lostincyberspace on 2007-12-14
Good thing.

---

