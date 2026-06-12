---
title: "Unable to authenticate on login after reinstalling lightdm"
date: 2022-01-09
forum: Desktop Environments
---

### Post by makem2 on 2022-01-09
I uninstalled lightdm and reinstalled it. Following that, when I try to login I get a failure to authenticate error and the only way to get access is via VT (ctrl+alt+f4) and then 'startx'.

I am using an xfce desktop in Ubuntu 21.10.

journal:

[https://paste.ubuntu.com/p/TdrpY45Syh/](https://paste.ubuntu.com/p/TdrpY45Syh/)

Dmesg:

[https://paste.ubuntu.com/p/F5vTbwggrb/](https://paste.ubuntu.com/p/F5vTbwggrb/)

Any suggestions how to solve this please?

Edit:
/etc/lightdm/lightdm.conf.d:
```

  GNU nano 5.6.1                                                                                   /var/log/apport.log                                                                                            
ERROR: apport (pid 4127) Sun Jan  9 22:49:43 2022: called for pid 3948, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 4127) Sun Jan  9 22:49:43 2022: executable: /usr/bin/xfce4-session (command line "xfce4-session")
ERROR: apport (pid 4127) Sun Jan  9 22:49:43 2022: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 4127) Sun Jan  9 22:49:43 2022: debug: session gdbus call:
ERROR: apport (pid 4127) Sun Jan  9 22:49:43 2022: wrote report /var/crash/_usr_bin_xfce4-session.1000.crash
ERROR: apport (pid 4446) Sun Jan  9 22:50:30 2022: called for pid 4273, signal 11, core limit 0, dump mode 1
ERROR: apport (pid 4446) Sun Jan  9 22:50:30 2022: executable: /usr/bin/xfce4-session (command line "xfce4-session")
ERROR: apport (pid 4446) Sun Jan  9 22:50:30 2022: gdbus call error: Error: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

ERROR: apport (pid 4446) Sun Jan  9 22:50:30 2022: debug: session gdbus call:
ERROR: apport (pid 4446) Sun Jan  9 22:50:30 2022: apport: report /var/crash/_usr_bin_xfce4-session.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS

```

lightdm log:

[https://paste.ubuntu.com/p/Tc7kTZsb4F/](https://paste.ubuntu.com/p/Tc7kTZsb4F/)

---

