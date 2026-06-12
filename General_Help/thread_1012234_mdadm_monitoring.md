---
title: "mdadm monitoring"
date: 2008-12-15
forum: General Help
---

### Post by hgilbert on 2008-12-15
I am trying to set up mdadm so that it will send me an email message if my raid 1 array were ever to enter a degraded state.  I have configured postfix and verified that sendmail works.  Mail delivered to root is forwarded to my account.  If I enter the command 
```
mdadm --monitor /dev/md0 -t -1
```
then it prints the message: 
'mdadm: Monitor using email address "hunter" from config file'
and exits.  I do get an email in my local mail spool file.
However, if I instead enter
```
mdadm --monitor --scan -t -1
```
I get nothing - the program just quietly exits.  The init script located at /etc/init.d/mdadm calls mdadm at startup with the following command:
```
/sbin/mdadm --monitor --pid-file /var/run/mdadm/monitor.pid --daemonise --scan --syslog
```
I added the ' -t ' parameter to the startup script but still got nothing.  It seems that it will not send me a test message if I use ' --monitor --scan ' instead of ' --monitor /dev/md0 '.  My question is whether this is strictly related to the test message, or if it is not going to send me any messages at all unless I explicitly define the array to monitor.

Thanks,
Hunter

---

