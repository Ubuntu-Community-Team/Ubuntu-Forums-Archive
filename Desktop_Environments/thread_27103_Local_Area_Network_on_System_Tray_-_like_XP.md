---
title: "Local Area Network on System Tray - like XP"
date: 2005-04-14
forum: Desktop Environments
---

### Post by vvu on 2005-04-14
Anyone know how I can get the LAN icon on the system tray, just like in XP/2000?  I would like to see real time activity/icon on my system tray, thanks.

---

### Post by doclivingston on 2005-04-14
Right click on the panel -> Add to Panel... -> Network Monitor

---

### Post by ikhwani on 2005-04-15
Hi,
Add a universe repository to your /etc/apt/sources.list, normally by uncommenting a line like this:
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

Then install knemo. This program runs as a KDE service (Control Center - KDE Component - Service Manager)
To configure knemo, open Control Center - Internet & Network - Network Monitor

---

### Post by NTolerance on 2005-04-15
I've got the KNemo service started and I've added my interfaces to it, but I can't find out to how to add it to the system tray.  It's not in the list of apps that come up when you select "add to panel".

---

### Post by philipacamaniac on 2005-04-15
[QUOTE=NTolerance]I've got the KNemo service started and I've added my interfaces to it, but I can't find out to how to add it to the system tray.  It's not in the list of apps that come up when you select "add to panel".[/QUOTE]

Log out, and log back in. It goes to your tray automagically.

---

### Post by Takis on 2005-04-16
[http://knetstats.sourceforge.net/](http://knetstats.sourceforge.net/) 

Absolutely brilliant, this duder is awesome.

---

### Post by void_false on 2005-04-16
How about using GKRELLM?

---

### Post by Nano on 2005-04-16
I use netspeed to monitor the up and downloading speed at everytime.
It's a simple applet you can add to gnome.

---

