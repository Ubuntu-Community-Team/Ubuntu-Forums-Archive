---
title: "DCOP and other annoying things"
date: 2007-05-21
forum: Desktop Environments
---

### Post by slybob on 2007-05-21
I keep getting the error. "Couldn't connect DCOP signal. Won't receive any status notifications!". Also, my install of Kubuntu wont save any of the settings that I change relating to the desktop environment.

Any Ideas?

Thanks

Andy
**/var/log/acpid**
```
[Mon May 21 00:45:51 2007] logfile reopened
[Mon May 21 01:09:13 2007] received event "button/lid LID 00000080 00000001"
[Mon May 21 01:09:13 2007] notifying client 4009[0:0]
[Mon May 21 01:09:13 2007] notifying client 4347[106:110]
[Mon May 21 01:09:13 2007] executing action "/etc/acpi/lid.sh"
[Mon May 21 01:09:13 2007] BEGIN HANDLER MESSAGES
ERROR: Couldn't attach to DCOP server!
[Mon May 21 01:09:14 2007] END HANDLER MESSAGES
[Mon May 21 01:09:14 2007] action exited with status 1
[Mon May 21 01:09:14 2007] completed event "button/lid LID 00000080 00000001"
[Mon May 21 01:09:39 2007] received event "button/lid LID 00000080 00000002"
[Mon May 21 01:09:39 2007] notifying client 4009[0:0]
[Mon May 21 01:09:39 2007] notifying client 4347[106:110]
[Mon May 21 01:09:39 2007] executing action "/etc/acpi/lid.sh"
[Mon May 21 01:09:39 2007] BEGIN HANDLER MESSAGES
ERROR: Couldn't attach to DCOP server!
[Mon May 21 01:09:40 2007] END HANDLER MESSAGES
[Mon May 21 01:09:40 2007] action exited with status 1
[Mon May 21 01:09:40 2007] completed event "button/lid LID 00000080 00000002"
[Mon May 21 01:10:20 2007] received event "button/lid LID 00000080 00000003"
[Mon May 21 01:10:20 2007] notifying client 4009[0:0]
[Mon May 21 01:10:20 2007] notifying client 4347[106:110]
[Mon May 21 01:10:20 2007] executing action "/etc/acpi/lid.sh"
[Mon May 21 01:10:20 2007] BEGIN HANDLER MESSAGES
ERROR: Couldn't attach to DCOP server!
[Mon May 21 01:10:21 2007] END HANDLER MESSAGES
[Mon May 21 01:10:21 2007] action exited with status 1
[Mon May 21 01:10:21 2007] completed event "button/lid LID 00000080 00000003"
[Mon May 21 01:10:27 2007] received event "button/lid LID 00000080 00000004"
[Mon May 21 01:10:27 2007] notifying client 4009[0:0]
[Mon May 21 01:10:27 2007] notifying client 4347[106:110]
[Mon May 21 01:10:27 2007] executing action "/etc/acpi/lid.sh"
[Mon May 21 01:10:27 2007] BEGIN HANDLER MESSAGES
ERROR: Couldn't attach to DCOP server!
[Mon May 21 01:10:28 2007] END HANDLER MESSAGES
[Mon May 21 01:10:28 2007] action exited with status 1
[Mon May 21 01:10:28 2007] completed event "button/lid LID 00000080 00000004"
[Mon May 21 09:00:16 2007] received event "button/lid LID 00000080 00000005"
[Mon May 21 09:00:16 2007] notifying client 4009[0:0]
[Mon May 21 09:00:16 2007] notifying client 4347[106:110]
[Mon May 21 09:00:16 2007] executing action "/etc/acpi/lid.sh"
[Mon May 21 09:00:16 2007] BEGIN HANDLER MESSAGES
ERROR: Couldn't attach to DCOP server!
[Mon May 21 09:00:16 2007] END HANDLER MESSAGES
[Mon May 21 09:00:16 2007] action exited with status 1
[Mon May 21 09:00:16 2007] completed event "button/lid LID 00000080 00000005"
[Mon May 21 11:08:39 2007] received event "ac_adapter ACAD 00000080 00000000"
[Mon May 21 11:08:39 2007] notifying client 4009[0:0]
[Mon May 21 11:08:39 2007] notifying client 4347[106:110]
[Mon May 21 11:08:39 2007] executing action "/etc/acpi/power.sh"
[Mon May 21 11:08:39 2007] BEGIN HANDLER MESSAGES
[Mon May 21 11:08:39 2007] END HANDLER MESSAGES
[Mon May 21 11:08:39 2007] action exited with status 0
[Mon May 21 11:08:39 2007] completed event "ac_adapter ACAD 00000080 00000000"
[Mon May 21 11:08:39 2007] received event "battery BAT1 00000080 00000001"
[Mon May 21 11:08:39 2007] notifying client 4009[0:0]
[Mon May 21 11:08:39 2007] notifying client 4347[106:110]
[Mon May 21 11:08:39 2007] executing action "/etc/acpi/power.sh"
[Mon May 21 11:08:39 2007] BEGIN HANDLER MESSAGES
[Mon May 21 11:08:39 2007] END HANDLER MESSAGES
[Mon May 21 11:08:39 2007] action exited with status 0
[Mon May 21 11:08:39 2007] completed event "battery BAT1 00000080 00000001"
[Mon May 21 11:19:39 2007] received event "ac_adapter ACAD 00000080 00000001"
[Mon May 21 11:19:39 2007] notifying client 4009[0:0]
[Mon May 21 11:19:39 2007] notifying client 4347[106:110]
[Mon May 21 11:19:39 2007] executing action "/etc/acpi/power.sh"
[Mon May 21 11:19:39 2007] BEGIN HANDLER MESSAGES
[Mon May 21 11:19:39 2007] END HANDLER MESSAGES
[Mon May 21 11:19:39 2007] action exited with status 0
[Mon May 21 11:19:39 2007] completed event "ac_adapter ACAD 00000080 00000001"
[Mon May 21 11:19:39 2007] received event "battery BAT1 00000080 00000001"
[Mon May 21 11:19:39 2007] notifying client 4009[0:0]
[Mon May 21 11:19:39 2007] notifying client 4347[106:110]
[Mon May 21 11:19:39 2007] executing action "/etc/acpi/power.sh"
[Mon May 21 11:19:39 2007] BEGIN HANDLER MESSAGES
[Mon May 21 11:19:40 2007] END HANDLER MESSAGES
[Mon May 21 11:19:40 2007] action exited with status 0
[Mon May 21 11:19:40 2007] completed event "battery BAT1 00000080 00000001"

```

---

