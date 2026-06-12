---
title: "Enlightenment Critical Problem"
date: 2006-11-20
forum: Desktop Environments
---

### Post by NaysNay on 2006-11-20
I installed Enlightenment and I chose that it edits my start up files so that it starts up automatically.
I restarted my computer, and I did not like it at all so I went to Synaptic, and marked all Enlightenment and it's libraries for complete removal. After rebooting, it said I cannot login and it gave me an error. I can only get on Failsafe GNOME. 
I use Ubuntu Dapper Drake

Please help me !!

Thanks a lot,

---

### Post by NaysNay on 2006-11-20
I got it answered on Launchpad.

How was it solved? (If anyone needs it for future reference)
All I did was go to System --> Preferences --> Sessions and under the "Startup Programs" tab, I removed the Enlightenment based stuff. I removed something called nm-applet --sm-disable
I only kept update-notifier, gnome-power-manager and gnome-volume-manager
I logged out and I logged in as a GNOME session successfully :)

---

