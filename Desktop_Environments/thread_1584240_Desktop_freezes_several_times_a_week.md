---
title: "Desktop freezes several times a week"
date: 2010-09-28
forum: Desktop Environments
---

### Post by s0c0 on 2010-09-28
I'm running Ubuntu 10.04 which was upgrade from a 9.x install.  I never had this problem on my 9.x install, but since the "upgrade" I experience my desktop freezing.  I'm not exactly sure how to troubleshoot this.

In looking at /var/log/messages the last entries I see before me having to a hard reboot are:
```

Sep 27 19:27:07 gingerk sudo: pam_sm_authenticate: username = [me]
Sep 27 19:27:07 gingerk sudo: pam_sm_authenticate: /home/me is already mounted
Sep 27 20:56:40 gingerk kernel: [102839.046817] operapluginwrap[26712]: segfault at 0 ip (null) sp bf9ce11c error 4 in libstdc++.so.6.0.13[110000+e9000]
Sep 27 20:56:40 gingerk kernel: [102839.077142] operapluginwrap[26723]: segfault at 0 ip (null) sp bf9e2d5c error 4 in libc-2.11.1.so[110000+153000]
Sep 27 20:56:40 gingerk kernel: [102839.134370] operapluginwrap[26746]: segfault at 0 ip (null) sp bfc7471c error 4 in libxcb.so.1.1.0[110000+18000]
Sep 27 20:56:40 gingerk kernel: [102839.181310] operapluginwrap[26768]: segfault at 0 ip (null) sp bff61eac error 4 in libX11.so.6.3.0[110000+119000]
Sep 27 21:25:09 gingerk sudo: pam_sm_authenticate: Called
Sep 27 21:25:09 gingerk sudo: pam_sm_authenticate: username = [me]
Sep 27 21:25:09 gingerk sudo: pam_sm_authenticate: /home/me is already mounted
Sep 27 22:17:05 gingerk sudo: pam_sm_authenticate: Called
Sep 27 22:17:05 gingerk sudo: pam_sm_authenticate: username = [me]
Sep 27 22:17:05 gingerk sudo: pam_sm_authenticate: /home/me is already mounted
Sep 28 08:02:32 gingerk rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="810" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

```

I've checked a few other logs but there is nothing that really stands out to me.  Any ideas?

---

### Post by s0c0 on 2010-09-28
Nevermind, I guess there is already a massive thread on this massive failure: [http://ubuntuforums.org/showthread.php?p=9902152](http://ubuntuforums.org/showthread.php?p=9902152)

Still any insight would be awesome.

---

