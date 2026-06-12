---
title: "Blank screen must power off"
date: 2010-05-02
forum: Desktop Environments
---

### Post by DaleEMoore on 2010-05-02
Everything runs fine for several days then the monitor goes blank and I have to cycle power to bring it back. It's been idle sometimes, and in other instances it's been right in the middle of me typing an Open Office document...

/var/log/messages shows this around one:

```
Apr 26 23:32:13 eno-desktop kernel: [   15.248147] type=1505 audit(1272342733.185:5):  operation="profile_load" pid=690 name="/usr/share/gdm/guest-session/Xsession"
Apr 26 23:32:13 eno-desktop kernel: [   15.251240] type=1505 audit(1272342733.185:6):  operation="profile_replace" pid=693 name="/sbin/dhclient3"
Apr 26 23:32:13 eno-desktop kernel: [   15.251884] type=1505 audit(1272342733.185:7):  operation="profile_replace" pid=693 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Apr 26 23:32:13 eno-desktop kernel: [   15.253917] type=1505 audit(1272342733.189:8):  operation="profile_replace" pid=693 name="/usr/lib/connman/scripts/dhclient-script"
Apr 26 23:32:13 eno-desktop kernel: [   15.276161] type=1505 audit(1272342733.213:9):  operation="profile_load" pid=694 name="/usr/bin/evince"
Apr 26 23:32:13 eno-desktop kernel: [   15.285270] type=1505 audit(1272342733.221:10):  operation="profile_load" pid=694 name="/usr/bin/evince-previewer"
Apr 26 23:32:13 eno-desktop kernel: [   15.293227] type=1505 audit(1272342733.229:11):  operation="profile_load" pid=694 name="/usr/bin/evince-thumbnailer"
Apr 26 23:32:13 eno-desktop kernel: [   15.395194] type=1505 audit(1272342733.331:12):  operation="profile_load" pid=699 name="/usr/lib/cups/backend/cups-pdf"
Apr 26 23:32:13 eno-desktop kernel: [   15.395968] type=1505 audit(1272342733.331:13):  operation="profile_load" pid=699 name="/usr/sbin/cupsd"
Apr 26 23:32:13 eno-desktop kernel: [   15.512837] type=1505 audit(1272342733.449:14):  operation="profile_load" pid=700 name="/usr/sbin/tcpdump"
Apr 26 23:32:25 eno-desktop pulseaudio[1064]: ratelimit.c: 2 events suppressed
Apr 26 23:33:01 eno-desktop pulseaudio[1238]: ratelimit.c: 4 events suppressed
Apr 27 07:53:23 eno-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="286" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr 28 07:44:18 eno-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="286" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr 29 07:53:12 eno-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="286" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr 30 08:00:55 eno-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="286" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May  1 07:55:41 eno-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="286" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
May  1 10:25:01 eno-desktop kernel: [384784.281084] grep[17854]: segfault at ffaca604 ip 0037a899 sp bfaca468 error 7 in ld-2.11.1.so[36d000+1b000]
May  1 10:41:37 eno-desktop kernel: [385780.479643] wget[17875]: segfault at b7fc637d ip b7548e85 sp bfaa70cc error 4 in libc-2.11.1.so[b74cf000+153000]
May  1 17:11:06 eno-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
May  1 17:11:06 eno-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="508" x-info="http://www.rsyslog.com"] (re)start
May  1 17:11:06 eno-desktop rsyslogd: rsyslogd's groupid changed to 102
May  1 17:11:06 eno-desktop rsyslogd: rsyslogd's userid changed to 101
May  1 17:11:06 eno-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
```

Any thoughts you have are very much appreciated,
Dale E. Moore

---

### Post by DaleEMoore on 2010-05-02
This is Ubuntu 10.04.

---

### Post by DaleEMoore on 2010-05-03
Just happened--after only 10 min of work on internet. Ctrl-Alt-F1 had no impact, still have a black screen.

---

