---
title: "What Happens When the &quot;Leave&quot; Buttons are Pressed?"
date: 2011-07-11
forum: Desktop Environments
---

### Post by Atomic Fusion on 2011-07-11
What is done (scripts executed?) when "Shutdown", "Hibernate", "Sleep", etc. are pressed in the KDE menu?
I'm looking to hook into this, so that I can add custom actions.

---

### Post by ankspo71 on 2011-07-11
Hi,
I think this is the command you are looking for:
```
qdbus org.kde.ksmserver /KSMServer org.kde.KSMServerInterface.logout -1 -1 -1
```

Source:
[http://askubuntu.com/questions/1871/how-can-i-safely-shutdown-reboot-logout-kde-from-the-command-line](http://askubuntu.com/questions/1871/how-can-i-safely-shutdown-reboot-logout-kde-from-the-command-line)
also see: [http://api.kde.org/4.4-api/kdebase-workspace-apidocs/libs/kworkspace/html/namespaceKWorkSpace.html#ebd506f19067a1ae1c00ae4b8f2d7c03](http://api.kde.org/4.4-api/kdebase-workspace-apidocs/libs/kworkspace/html/namespaceKWorkSpace.html#ebd506f19067a1ae1c00ae4b8f2d7c03)
Hope this helps

---

### Post by Atomic Fusion on 2011-07-11
Thanks for the reply.
Do you know how I could hook into this action? Is there any easy way to monitor dbus events? (I know almost nothing about it.)

---

