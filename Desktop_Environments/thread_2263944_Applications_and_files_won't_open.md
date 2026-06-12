---
title: "Applications and files won't open"
date: 2015-02-04
forum: Desktop Environments
---

### Post by wg5o on 2015-02-04
I'm running Ubuntu 14.04.

WhenI try to open anapplication, the litttle progress wheel runs, and tics appear to indicate its open, but nothing is disptayed.  This condition seemed to davelope gradually, and now, I'm pretty much at a standsill.


Andy
San Antonio, TX

---

### Post by TheFu on 2015-02-04
What do the log files say?

---

### Post by wg5o on 2015-02-04
Sorry, how do I et the log files?

---

### Post by TheFu on 2015-02-04
There is a GUI way - I don't know that.
[http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) is how I do it. Works on every distro, with or without a GUI.

---

### Post by CantankRus on 2015-02-05
@** TheFu** FYI
The code block on that page won't run because of the type of quotes used around  **error|warning**.
```
sudo egrep -i [COLOR="#FF0000"]‘[/COLOR]error|warning[COLOR="#FF0000"]’[/COLOR] /var/log/*log
```
Probably how the blog software interprets single quotes.

---

### Post by wg5o on 2015-02-05
The system won't let me post the whole log. Here is the last bit:

```
 andy@Izzy:~$ /var/log/syslog:Feb  5 16:55:23 Izzy kernel: [   21.595721] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
> bash: syntax error near unexpected token `('
bash: syntax error near unexpected token `('
andy@Izzy:~$ andy@Izzy:~$ /var/log/syslog:Feb  5 16:55:51 Izzy NetworkManager[854]: <error> [1423176951.161083] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
bash: syntax error near unexpected token `('
andy@Izzy:~$ bash: syntax error near unexpected token `('
> andy@Izzy:~$ /var/log/syslog:Feb  5 16:55:51 Izzy dnsmasq[1812]: warning: no upstream servers configured
> bash: /var/log/syslog:Feb: No such file or directory
> andy@Izzy:~$ /var/log/Xorg.0.log:(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
> bash: syntax error near unexpected token `WW'
> andy@Izzy:~$ andy@Izzy:~$ sudo egrep -i ‘error|warning’ /var/log/*logsudo egrep -i ‘error|warning’ /var/log/*logsudo egrep -i ‘error|warning’ /var/log/*logsudo egrep -i ‘error|warning’ /var/log/*logsudo egrep -i ‘error|warning’ /var/log/*log
> warning’: command not found
```

---

