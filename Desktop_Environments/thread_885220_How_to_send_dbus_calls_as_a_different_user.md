---
title: "How to send dbus calls as a different user?"
date: 2008-08-09
forum: Desktop Environments
---

### Post by Nicolae on 2008-08-09
I need to send the following dbus call from the /etc/acpi/powerbtn.sh script:

/usr/bin/qdbus org.kde.ksmserver /KSMServer org.kde.KSMServerInterface.logout 1 2 0

However as the script is not run as my login user it doesn't work. I've tried using su -c and exporting the necessary environment variable in the script and still nothing. Anyone know how to pull this off, or another way to call KDE4's shutdown menu from the power button script?

---

### Post by trtr on 2008-10-19
/usr/bin/qdbus org.kde.ksmserver /KSMServer logout 1 2 0

---

