---
title: "Preventing last opened Windows and Programs from opening up on each reboot/shutdown"
date: 2012-04-23
forum: Desktop Environments
---

### Post by dzchimp on 2012-04-23
I've found that while on Kubuntu, even if I manually close each application/window before restarting/shutting down, they reopen after I login (after a reboot/shutdown). How can I disable this behaviour?

---

### Post by samigina on 2012-04-23
Go to system settings / startup and shutdown / session / and chose "Start with an empty session"

---

### Post by dzchimp on 2012-04-23
> **samigina said:**
> Go to system settings / startup and shutdown / session / and chose "Start with an empty session"

Thank you. Is there a file where these settings are saved and can be manually adjusted?

---

### Post by samigina on 2012-04-24
Hello.

I think this could be the config file for this settings: .kde4/share/config/ksmserverrc

In that directory you can find more config files.

Be careful! Just edit them if you know what are you doing!

Read more about ksmserever [here]("http://techbase.kde.org/KDE_System_Administration/Startup#ksmserver:_Session_Management_and_Autostart").

---

