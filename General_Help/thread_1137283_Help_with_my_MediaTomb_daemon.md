---
title: "Help with my MediaTomb daemon"
date: 2009-04-25
forum: General Help
---

### Post by 68pontiac on 2009-04-25
I have MediaTomb installed on Jaunty and have it configured to serve up to my PS3 over my wireless network. Everything works fine (except mp4 streaming which I understand is Sony's problem) but I can't seem to get MediaTomb to start as daemon on startup. I installed the mediatomb-daemon package from Synaptic and have an entry in my "Startup Applications" for mediatomb -d but it still doesn't start up. I read somewhere that there's an issue with MediaTomb trying to start before Network Manager configures but can't recall how to work around it. Can you guys help me out?

---

### Post by sstakes1 on 2009-04-25
The Startup applications start up only when you log into a session. However, I believe that Mediatomb when installed from the repos will start itself as a daemon. Perhaps, /var/log/mediatomb.log may contain more information.

---

### Post by 68pontiac on 2009-04-25
This is the last entry from the mediatomb.log file:
```
2009-04-25 09:18:15    INFO: Loading configuration from: /etc/mediatomb/config.xml
2009-04-25 09:18:15    INFO: Checking configuration...
2009-04-25 09:18:15    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2009-04-25 09:18:15    INFO: Setting metadata import charset to ANSI_X3.4-1968
2009-04-25 09:18:15    INFO: Setting playlist charset to ANSI_X3.4-1968
2009-04-25 09:18:15    INFO: Configuration check succeeded.
2009-04-25 09:18:16   ERROR: main: upnp error -117
2009-04-25 09:18:16   ERROR: upnp_cleanup: UpnpUnRegisterRootDevice failed
```

I'm not the smartest Linux guy around but I'm sure the last two errors are my problem. How can I fix this?

---

### Post by 68pontiac on 2009-04-26
Okay, I solved my own problem with a little sleuthing. I determined the error(s) were because MediaTomb was starting before my WLAN had connected to my router. I wrote a tiny script that delayed MediaTomb from starting immediately and then pointed the Startup Session to the script. :)

```
#/bin/bash
sleep 20 && mediatomb -d
```

---

