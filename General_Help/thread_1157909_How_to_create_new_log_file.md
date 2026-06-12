---
title: "How to create new log file ?"
date: 2009-05-13
forum: General Help
---

### Post by belbo on 2009-05-13
Hi

I am trying to log sensord output to a separate log file. I added the following lines to my /etc/syslog.conf file (as per the sensord man page) -

              *.info;...;local4.none;local4.warn  /var/log/messages
              local4.info                        -/var/log/sensors

The man page explains the effect of these lines as follows -

The first line ensures that regular sensor readings do not clutter &#8216;/var/log/messages&#8217;; we first say &#8216;local4.none&#8217; to eliminate informational messages; then &#8216;local4.warn&#8217; to enable warnings and above. The second line says to log all regular sensor readings to &#8216;/var/log/sensors&#8217;; the leading        hyphen  &#8216;-&#8217;  means  that this file is not flushed after every message.

I then restart the system monitor with -

sudo /etc/init.d/sysklogd restart

And get the following message,

* Restarting system log daemon.
chown: cannot access `/var/log/sensors': No such file or directory

So I create the file -

sudo touch /var/log/sensors

I restart the system log again and all appears ok, ie no error message as before.

 * Restarting system log daemon...                                       [ OK ]

However, the file remains blank, ie nothing is logging.

I restart sensord (with sensor logging every 5s and alarm logging every 30min) and system log again, but still /var/log/sensors remains blank.

sudo /etc/init.d/sensord restart -i 30m -l 5s

sudo /etc/init.d/sysklogd restart


Also, trying to open /var/log/sensors from the system log application in the ubuntu menus tells me it isn't a log file.

I check the permissions of the file and they are root:root. I see that the permissions of syslog are syslog:adm as are a number of other log files. So I change the permissions of the file -

sudo chown syslog:adm /var/log/sensors

Restart sensord and restart syslog again, but

still the file remains blank and the system log application tells me it is not a log file.

Please help ! How do I get logging to occur in the /var/log/sensors file ?

Thanks

---

### Post by belbo on 2009-05-13
Bump. Can anyone help re why my logfile (details below) is not being written to and is not recognised as a log file ?

---

