---
title: "Finch runs a lot of processes"
date: 2009-01-14
forum: General Help
---

### Post by wilson47 on 2009-01-14
Hello,

I just noticed that finch runs way too many subprocesses for my taste. It climbs up to well over a few hundred. Here is 
a relatively small example: 
```

init-+-NetworkManager-+-dhclient
     |                `-{NetworkManager}
     |-acpid
     |-atd
     |-avahi-daemon---avahi-daemon
     |-console-kit-dae---63*[{console-kit-dae}]
     |-cron
     |-cupsd
     |-dbus-daemon
     |-dd
     |-exim4
     |-5*[getty]
     |-hald---hald-runner-+-hald-addon-acpi
     |                    |-hald-addon-cpuf
     |                    |-hald-addon-dell
     |                    |-hald-addon-inpu
     |                    `-2*[hald-addon-stor]
     |-klogd
     |-login---bash---screen---screen-+-bash---w3m---sh---sensible-editor---nano
     |                                |-bash---pstree
     |                                `-finch---178*[{finch}]
     |-nm-system-setti
     |-syslogd
     |-system-tools-ba
     |-udevd
     `-wpa_supplicant

```
It seems like a new  subprocess is started for every single message... Is this a bug?

---

