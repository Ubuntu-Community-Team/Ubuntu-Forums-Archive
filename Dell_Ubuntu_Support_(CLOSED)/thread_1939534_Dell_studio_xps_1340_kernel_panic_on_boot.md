---
title: "Dell studio xps 1340 kernel panic on boot"
date: 2012-03-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Wise Ferret on 2012-03-11
I use Precise Pangolin on Dell xps 1340 laptop (64 bit, nvidia-current).

Booting with the old oneiric kernel (3.0.0-16), all is fine. Booting with the new Precise kernel (3.2.0-18) leads to immediate kernel panic, with blinking caps lock key.

I updated /etc/default/grub and removed the "quiet" and "splash" parameters, and I can see a long list of error messages run across the screen. However, none of this is recorded to any of the logs in /var/log. all I get is ```
Mar 11 20:42:59 aku dhclient: DHCPREQUEST of 172.29.21.83 on eth1 to 132.64.253.10 port 67
Mar 11 20:42:59 aku dhclient: DHCPACK of 172.29.21.83 from 132.64.253.10
Mar 11 20:42:59 aku dhclient: bound to 172.29.21.83 -- renewal in 274 seconds.
Mar 11 20:43:43 aku kernel: Kernel logging (proc) stopped.
Mar 11 20:43:43 aku rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="785" x-info="http://www.rsyslog.com";] exiting on signal 15.
```
on syslog, and```
Mar 11 20:43:43 aku kernel: Kernel logging (proc) stopped.
```
on kern.log.

What can I do in order to uderstand what is going on, or even just gather sufficient information for a new bug?

---

### Post by djahma on 2012-04-27
I've experienced the exact same problem on the same computer model, after upgrading from Xubuntu 11.10 to 12.04. 
To sort that problem, I did sudo nautilus, went in /boot and removed references to kernel 3.2. Then I did update-grub and restarted the computer.
On startup, references to 3.2 were gone and my machine booted on 3.0 without any problem.
Finally I opened update manager to re-download the kernel 3.2, let it do the install and restarted. Et voilà! my machine now works perfectly fine under its brand new packages. Thank you Xubuntu

---

