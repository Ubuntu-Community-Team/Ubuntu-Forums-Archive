---
title: "kubuntu network widget"
date: 2006-12-10
forum: Desktop Environments
---

### Post by Carandol on 2006-12-10
I've switched from Ubuntu to Kubuntu, but I sadly miss the little monitor icon that sits on the toolbar and flashes to show incoming and outgoing internet activity. Is there a similar thing for Kubuntu?

---

### Post by RHTopics on 2006-12-10
**knetdockapp** is a KDE application for monitoring network status and activity.

It is located in the universe repository.

I believe this is what you are looking for.

---

### Post by Carandol on 2006-12-10
Cool! Exactly what I was looking for. Now (I know this is a stupid question, but I've forgotten), how do I get it to load automatically on boot?

---

### Post by RHTopics on 2006-12-10
It does seems odd that the application does not have an option in its Settings to have it autostart.

So to have knetdockapp startup upon login, copy **/usr/share/applications/kde/knetdockapp.desktop** to **/home/*"your user id here"*/.kde/Autostart/knetdockapp.desktop**

---

