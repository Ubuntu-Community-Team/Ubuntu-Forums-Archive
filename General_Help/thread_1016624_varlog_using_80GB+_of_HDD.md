---
title: "/var/log using 80GB+ of HDD"
date: 2008-12-20
forum: General Help
---

### Post by blakjesus on 2008-12-20
I recently noticed that i had a lot less free space on my hard drive recently without adding anything to my hard drive. I ran the disk usage analyzer tool and found out that that the directory /var/log is using up 83GB of hard drive. Why is it so large?

I attached a screenshot from nautilus to show the files involved.

What is causing these files to be so large and how can i safely either shrink them or get rid of them?

---

### Post by cdtech on 2008-12-20
I would, at least, read the tail of those logs to see if anything unusual is going on.
```
cat /var/log/syslog.0 | tail -n 40
```
This will show you the last 40 lines of the log.

You can install "logrotate" to help with the administration of your log files:
```
sudo apt-get install logrotate
```

> The logrotate utility is designed to simplify the administration of log files on a system which generates a lot of log files. Logrotate allows for the automatic rotation compression, removal and mailing of log files. Logrotate can be set to handle a log file daily, weekly, monthly or when the log file gets to a certain size. Normally, logrotate runs as a daily cron job. [http://packages.ubuntu.com/dapper/logrotate](http://packages.ubuntu.com/dapper/logrotate)

---

### Post by ibuclaw on 2008-12-20
There have been reported problems with Intel Wireless Cards on the new kernel. Where the syslog applet is flooded with too many calls, and so just bloats the log files with a lot of error messages.

To confirm this, can you post the tail of the files?

```
tail -n30 /var/log/syslog
```

And you may see something like this:
[QUOTE=https://answers.launchpad.net/ubuntu/+question/49115]
Oct 26 16:42:40 marla kernel: [20204.022488] =======================
Oct 26 16:42:40 marla kernel: [20204.028145] bad: scheduling from the idle thread!
Oct 26 16:42:40 marla kernel: [20204.028149] Pid: 0, comm: swapper Tainted: P 2.6.27-7-generic #1
Oct 26 16:42:40 marla kernel: [20204.028151] [<c037c3f6>] ? printk+0x1d/0x1f
Oct 26 16:42:40 marla kernel: [20204.028155] [<c0122b8a>] dequeue_task_idle+0x2a/0x40
Oct 26 16:42:40 marla kernel: [20204.028157] [<c012107f>] dequeue_task+0xcf/0x130
Oct 26 16:42:40 marla kernel: [20204.028160] [<c012112a>] deactivate_task+0x1a/0x30
Oct 26 16:42:40 marla kernel: [20204.028163] [<c037ca13>] schedule+0x4b3/0x790
Oct 26 16:42:40 marla kernel: [20204.028166] [<c01028cd>] cpu_idle+0xbd/0x140
Oct 26 16:42:40 marla kernel: [20204.028169] [<c037a651>] start_secondary+0x9d/0xcc
[/QUOTE]

Best thing to do is delete them and reboot.

Then maybe look into setting up a logrotate scheme, or a stop the logging of some services.

Regards
Iain

---

### Post by blakjesus on 2008-12-20
```
cat /var/log/syslog.0 | tail -n 40
```
Didn't work, it just sat there blank.

Although
```
tail -n30 /var/log/syslog
```
Resulted in this:

```
Dec 20 11:08:37 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 20 11:08:37 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 20 11:08:37 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 20 11:36:58 Station -- MARK --
Dec 20 11:54:47 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 20 11:54:47 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 20 11:55:23 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 20 11:55:23 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 20 12:16:58 Station -- MARK --
Dec 20 12:36:58 Station -- MARK --
Dec 20 12:39:55 Station avahi-daemon[5119]: Files changed, reloading.
Dec 20 12:39:55 Station avahi-daemon[5119]: No service file found in /etc/avahi/services.
Dec 20 12:39:56 Station avahi-daemon[5119]: Got SIGTERM, quitting.
Dec 20 12:39:56 Station avahi-daemon[5119]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Dec 20 12:39:57 Station avahi-daemon[10963]: Found user 'avahi' (UID 110) and group 'avahi' (GID 121).
Dec 20 12:39:57 Station avahi-daemon[10963]: Successfully dropped root privileges.
Dec 20 12:39:57 Station avahi-daemon[10963]: avahi-daemon 0.6.23 starting up.
Dec 20 12:39:57 Station avahi-daemon[10963]: Successfully called chroot().
Dec 20 12:39:57 Station avahi-daemon[10963]: Successfully dropped remaining capabilities.
Dec 20 12:39:57 Station avahi-daemon[10963]: No service file found in /etc/avahi/services.
Dec 20 12:39:57 Station avahi-daemon[10963]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.100.
Dec 20 12:39:57 Station avahi-daemon[10963]: New relevant interface wlan0.IPv4 for mDNS.
Dec 20 12:39:57 Station avahi-daemon[10963]: Network interface enumeration completed.
Dec 20 12:39:57 Station avahi-daemon[10963]: Registering new address record for fe80::216:eaff:feb9:436a on wlan0.*.
Dec 20 12:39:57 Station avahi-daemon[10963]: Registering new address record for 192.168.1.100 on wlan0.IPv4.
Dec 20 12:39:57 Station avahi-daemon[10963]: Registering HINFO record with values 'X86_64'/'LINUX'.
Dec 20 12:39:58 Station avahi-daemon[10963]: Server startup complete. Host name is Station.local. Local service cookie is 2693818336.
Dec 20 12:56:58 Station -- MARK --
Dec 20 13:16:58 Station -- MARK --
Dec 20 13:36:58 Station -- MARK --
```

---

### Post by cdtech on 2008-12-20
Thats strange, your post shows "syslog.0" as the culprit not "syslog"

---

### Post by blakjesus on 2008-12-20
Ok im going to check out logrotate like you suggested. But is it ok to delete the log files?

Oh and i tried doing
```
tail -n30 /var/log/syslog
```
instead because the first command you asked about didn't work and it gave me this:


```
Dec 19 01:58:28 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 19 01:58:28 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 19 01:58:43 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 19 01:58:43 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 19 01:58:44 Station anacron[8226]: Anacron 2.3 started on 2008-12-19
Dec 19 01:58:44 Station anacron[8226]: Normal exit (0 jobs run)
Dec 19 01:58:44 Station anacron[8255]: Anacron 2.3 started on 2008-12-19
Dec 19 01:58:44 Station anacron[8255]: Normal exit (0 jobs run)
Dec 19 01:58:44 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 19 01:58:44 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 19 01:58:44 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 19 01:58:44 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 19 01:58:44 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 19 01:58:44 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 19 01:58:44 Station kernel: [ 3558.600777] CPU0 attaching NULL sched-domain.
Dec 19 01:58:45 Station kernel: [ 3558.600784] CPU1 attaching NULL sched-domain.
Dec 19 01:58:45 Station kernel: [ 3558.632548] CPU0 attaching sched-domain:
Dec 19 01:58:45 Station kernel: [ 3558.632553]  domain 0: span 0-1 level MC
Dec 19 01:58:45 Station kernel: [ 3558.632555]   groups: 0 1
Dec 19 01:58:45 Station kernel: [ 3558.632557]   domain 1: span 0-1 level NODE
Dec 19 01:58:45 Station kernel: [ 3558.632559]    groups: 0-1
Dec 19 01:58:45 Station kernel: [ 3558.632561] CPU1 attaching sched-domain:
Dec 19 01:58:45 Station kernel: [ 3558.632563]  domain 0: span 0-1 level MC
Dec 19 01:58:45 Station kernel: [ 3558.632564]   groups: 1 0
Dec 19 01:58:45 Station kernel: [ 3558.632566]   domain 1: span 0-1 level NODE
Dec 19 01:58:45 Station kernel: [ 3558.632567]    groups: 0-1
Dec 19 01:58:49 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 19 01:58:49 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 
Dec 19 01:58:49 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_full (No such file or directory) 
Dec 19 01:58:49 Station cpufreqd: get_class_device_attribute: couldn't open /sys/devices/LNXSYSTM:00/device:00/PNP0C0A:00/power_supply/BAT0/energy_now (No such file or directory) 

```

---

