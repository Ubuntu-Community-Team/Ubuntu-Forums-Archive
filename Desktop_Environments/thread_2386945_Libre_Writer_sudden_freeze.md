---
title: "Libre Writer sudden freeze"
date: 2018-03-12
forum: Desktop Environments
---

### Post by Gnusboy on 2018-03-12
Hello
I was just using Libre Office Writer, editing some work and it suddenly froze. A little box popped up with this message:
LibreOffice document recovery
Due to unexpected error Libre Office crashed. blah. blah.
A smaller box opened with "In progress of saving"
But it isn't doing anything and it locked up starting at Mar 12 13:02 

I haven't tried rebooting or any way to make it restart because I definitely don't want top lose the work.
Here's the syslog from the start of the problem. It's now been over 25 minutes since it locked.

```

Mar 12 13:02:16 ranha-system dbus[805]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Mar 12 13:02:17 ranha-system systemd[1]: Starting Hostname Service...
Mar 12 13:02:17 ranha-system dbus[805]: [system] Successfully activated service 'org.freedesktop.hostname1'
Mar 12 13:02:17 ranha-system systemd[1]: Started Hostname Service.
Mar 12 13:02:17 ranha-system org.gtk.vfs.Daemon[1554]: ** (process:2066): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/1 (g-dbus-error-quark, 19)
Mar 12 13:02:17 ranha-system org.gtk.vfs.Daemon[1554]: message repeated 2 times: [ ** (process:2066): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/1 (g-dbus-error-quark, 19)]
Mar 12 13:02:17 ranha-system org.gtk.vfs.Daemon[1554]: ** (process:2066): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/1 (g-dbus-error-quark, 19)
Mar 12 13:04:18 ranha-system kernel: [36341.181209] CE: hpet increased min_delta_ns to 775230 nsec
Mar 12 13:04:18 ranha-system kernel: [36341.187193] CE: hpet increased min_delta_ns to 1162845 nsec
Mar 12 13:04:22 ranha-system kernel: [36345.159601] CE: hpet increased min_delta_ns to 1744267 nsec
Mar 12 13:08:36 ranha-system dbus[805]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Mar 12 13:08:36 ranha-system systemd[1]: Starting Hostname Service...
Mar 12 13:08:36 ranha-system dbus[805]: [system] Successfully activated service 'org.freedesktop.hostname1'
Mar 12 13:08:36 ranha-system systemd[1]: Started Hostname Service.
Mar 12 13:08:36 ranha-system org.gtk.vfs.Daemon[1554]: ** (process:2066): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
Mar 12 13:08:36 ranha-system org.gtk.vfs.Daemon[1554]: message repeated 2 times: [ ** (process:2066): WARNING **: send_infos_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)]
Mar 12 13:08:36 ranha-system org.gtk.vfs.Daemon[1554]: ** (process:2066): WARNING **: send_done_cb: No such interface 'org.gtk.vfs.Enumerator' on object at path /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
Mar 12 13:17:01 ranha-system CRON[8454]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```


OK I have attached a screenshot, if that will help. I just need to know if a reboot will cause the piece of work to disappear.
Thanks


And I'm trying to attach a screenshot of what I see, but now Firefox won't connect to allow the attachment. Something is definitely wrong.

---

### Post by #&amp;thj^% on 2018-03-12
Open another terminal and paste back the return of:
```
libreoffice --version
```

---

