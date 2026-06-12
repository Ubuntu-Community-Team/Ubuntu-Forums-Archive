---
title: "acpi shutdown with lightdm running"
date: 2012-05-03
forum: Desktop Environments
---

### Post by laroche on 2012-05-03
With the new 12.04LTS release and lightdm running (nobody logged in), if you press
Ctrl-Alt-Del or run "virsh shutdown <guest>" in a virtualized environment, the acpi
event is sent to acpid.

acpid is configured in /etc/acpi/events/powerbtn to run the shell script
/etc/acpi/powerbtn.sh. "pidof x $PMS" then find gnome-settings-daemon to
be running and just exits.

Removing "gnome-settings-daemon" from this script or just running
"shutdown -h now" instead of this script both cure this problem.

best regards,

Florian La Roche

---

