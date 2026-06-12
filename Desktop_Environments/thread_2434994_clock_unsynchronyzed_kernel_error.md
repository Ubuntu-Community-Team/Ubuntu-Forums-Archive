---
title: "clock unsynchronyzed kernel error"
date: 2020-01-14
forum: Desktop Environments
---

### Post by lister171254 on 2020-01-14
Running the latest Ubuntu Desktop and after every boot I have to (re)start ntp due to the time being incorrect

The log shows

```
Jan 15 20:08:56 LeosHomePc1 systemd[1]: systemd-hostnamed.service: Succeeded.
Jan 15 20:08:59 LeosHomePc1 systemd[1]: Starting Network Time Service...
Jan 15 20:09:00 LeosHomePc1 systemd[1]: systemd-localed.service: Succeeded.
Jan 15 20:09:00 LeosHomePc1 ntpd[3296]: ntpd 4.2.8p12@1.3728-o (1): Starting
Jan 15 20:09:00 LeosHomePc1 ntpd[3296]: Command line: /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 129:135
Jan 15 20:09:00 LeosHomePc1 systemd[1]: Started Network Time Service.
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: proto: precision = 0.084 usec (-23)
Jan 15 20:09:00 LeosHomePc1 kernel: [  206.336786] audit: type=1400 audit(1579079340.163:44): apparmor="DENIED" operation="open" profile="/usr/sbin/ntpd" name="/snap/bin/" pid=3296 comm="ntpd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: leapsecond file ('/usr/share/zoneinfo/leap-seconds.list'): good hash signature
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: leapsecond file ('/usr/share/zoneinfo/leap-seconds.list'): loaded, expire=2020-06-28T00:00:00Z last=2017-01-01T00:00:00Z ofs=37
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: Listen and drop on 0 v6wildcard [::]:123
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: Listen and drop on 1 v4wildcard 0.0.0.0:123
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: Listen normally on 2 lo 127.0.0.1:123
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: Listen normally on 3 enp9s0 192.168.1.10:123
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: Listen normally on 4 lo [::1]:123
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: Listen normally on 5 enp9s0 [fe80::16da:e9ff:fec8:c682%2]:123
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: Listening on routing socket on fd #22 for interface updates
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: kernel reports TIME_ERROR: 0x41: Clock Unsynchronized
Jan 15 20:09:00 LeosHomePc1 kernel: [  206.451811] audit: type=1107 audit(1579079340.279:45): pid=1376 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/systemd1" interface="org.freedesktop.systemd1.Manager" member="GetDynamicUsers" mask="send" name="org.freedesktop.systemd1" pid=3305 label="/usr/sbin/ntpd" peer_pid=1 peer_label="unconfined"
Jan 15 20:09:00 LeosHomePc1 kernel: [  206.451811]  exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
Jan 15 20:09:00 LeosHomePc1 ntpd[3305]: kernel reports TIME_ERROR: 0x41: Clock Unsynchronized

```

I can manually start with
```
sudo service ntp restart
```
without any issues.

Thanks

---

### Post by CelticWarrior on 2020-01-14
Maybe you need to replace the CMOS battery.

---

### Post by logix2 on 2020-01-15
In case you dualboot Ubuntu with Windows, see this AskUbuntu answer for how to fix it and get the time to be in sync: [https://askubuntu.com/a/169384/817248](https://askubuntu.com/a/169384/817248)

---

### Post by lister171254 on 2020-01-15
I am dual bootin, but not sure that's the problem; why does restarting ntp manuall set the correct time?

Also, that post starts about 7 years ago.

I think that the folowing points to is the cause
```
an 15 20:09:00 LeosHomePc1 kernel: [  206.336786] audit: type=1400 audit(1579079340.163:44): apparmor="DENIED" operation="open" profile="/usr/sbin/ntpd" name="/snap/bin/" pid=3296 comm="ntpd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
```

Why is it using snapd for ntp?

---

### Post by raffaele.fusto on 2020-02-07
disable systemd-timesyncd
systemctl disable systemd-timesyncd

---

