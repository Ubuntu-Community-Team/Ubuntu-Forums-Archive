---
title: "remote logging bug? (syslogd=&quot;-r&quot;)"
date: 2009-09-24
forum: Desktop Environments
---

### Post by configt on 2009-09-24
Once I enable remote logging (/etc/default/syslogd syslogd="-r"), my desktop starts to be behave very strange (hangs on commands).  I traced the problem using strace and ltrace.  Once I disable remote logging (/etc/default/syslogd syslogd="") the problem is resolved.  I am not DOS'ing myself, I just have one Cisco router sending about 5 messages per minute.

There is no indication in the logs as to why this happens.  If it was not for the fact that I realized the issue was reproducible whenever using sudo, or trying to login, or gksudo, etc., anything to do with authentication, I never would have realized the relationship between my syslogd configuration and the symptoms.

Here is what I found and how I found it:

After I change /etc/default/syslogd 'SYSLOGD="-r"', remote logging from  my Cisco works, BUT, the system would hang on many commands like simply  logging in, or using sudo: 

1) sudo -s (or su to root) 
2) strace sudo ls 
.. 
.. 
socket(PF_FILE, 0x80002 /* SOCK_??? */, 0) = 4 
connect(4, {sa_family=AF_FILE, path="/dev/log"...}, 110) = 0  sendto(4, "<85>Sep 21 11:53:05 sudo:  userna"..., 96, MSG_NOSIGNAL,  NULL, 0) = 9 

(hangs.... doesn't get past the above line for several minutes) 
.. 
.. 


3) ltrace sudo ls 
.. 
.. 
openlog("sudo", 0, 80)                           = <void> 
__vsnprintf_chk(0x7fff9ca54a60, 961, 1, 961, 0x41350a) = 70 
__syslog_chk(5, 1, 0x41352d, 0x7fff9ca54a60, 0x736c2f6e69622f3d) = 0x2490af0 

(hangs... doesn't get past the above line for several minutes) 
.. 
.. 


Once I change back to /etc/default/syslogd 'SYSLOGD=""' 

Everything is fine again. 


2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux


Does anyone else have this problem?  Or better yet, an explanation and reasonable solution?

Thank you.

---

