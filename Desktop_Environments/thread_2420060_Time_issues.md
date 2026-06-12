---
title: "Time issues"
date: 2019-05-29
forum: Desktop Environments
---

### Post by xendistar2 on 2019-05-29
(Taken from my previous post where I posted multiple questions and advised not to........)

After a Fresh install of xubuntu 19.04, my clock is one hour slow, 1fallen suggested

[QUOTE=1fallen]

Use timedatectl

```
sudo timedatectl set-timezone <timeszone>
```

Examples:

Timezone as EST

```
sudo timedatectl set-timezone EST
```

Timezone as UTC

```
sudo timedatectl set-timezone UTC
```

Listing all valid Timezones

```
timedatectl list-timezones
```

This command is perfect for automation scripts since it doesn't require any user interaction while compared to any given answer based on dpkg-reconfigure tzdata[/QUOTE]

Having followed those suggestions, this is my end result

```
mit@andora:~$ sudo dpkg-reconfigure tzdata

Current default time zone: 'Europe/London'
Local time is now:      Wed May 29 21:03:01 BST 2019.
Universal Time is now:  Wed May 29 20:03:01 UTC 2019.


 
```

My clock seem to be stuck UTC time

---

### Post by #&amp;thj^% on 2019-05-29
Your using "systemd" now >>"timedatectl " is the tool to use.
Have a look:
```
**timedatectl  status**
               Local time: Wed 2019-05-29 14:44:20 MDT
           Universal time: Wed 2019-05-29 20:44:20 UTC
                 RTC time: Wed 2019-05-29 14:44:20
                Time zone: America/Denver (MDT, -0600)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: yes

```

---

### Post by xendistar2 on 2019-05-29
> **1fallen said:**
> Your using "systemd" now >>"timedatectl " is the tool to use.
Have a look:
```
**timedatectl  status**
               Local time: Wed 2019-05-29 14:44:20 MDT
           Universal time: Wed 2019-05-29 20:44:20 UTC
                 RTC time: Wed 2019-05-29 14:44:20
                Time zone: America/Denver (MDT, -0600)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: yes

```

Ok, looking at the bottom two lines in my output compared to yours would suggest that my NTP service is inactive

```

mit@andora:~$ timedatectl status
               Local time: Wed 2019-05-29 21:51:03 BST
           Universal time: Wed 2019-05-29 20:51:03 UTC
                 RTC time: Wed 2019-05-29 20:51:03
                Time zone: Europe/London (BST, +0100)
System clock synchronized: yes
              NTP service: inactive
          RTC in local TZ: no

```

but if I look at the satus of ntp

```
sudo service ntp status
[sudo] password for mit: 
&#9679; ntp.service - Network Time Service
   Loaded: loaded (/lib/systemd/system/ntp.service; enabled; vendor preset: enab
   Active: active (running) since Wed 2019-05-29 19:36:23 BST; 2h 15min ago
     Docs: man:ntpd(8)
 Main PID: 19673 (ntpd)
    Tasks: 2 (limit: 4915)
   Memory: 2.8M
   CGroup: /system.slice/ntp.service
           &#9492;&#9472;19673 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 122:130


May 29 21:42:02 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c
May 29 21:43:06 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c
May 29 21:44:13 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c
May 29 21:45:18 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c
May 29 21:46:25 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c
May 29 21:47:31 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c
May 29 21:48:37 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c
May 29 21:49:43 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c
May 29 21:50:48 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c
May 29 21:51:55 andora ntpd[19673]: Soliciting pool server 2001:67c:1560:8003::c


```

That says it is running???

Think its time to go back to wind up clocks !!

---

### Post by #&amp;thj^% on 2019-05-29
> **xendistar2 said:**
> 

Think its time to go back to wind up clocks !!
Right??:lolflag:
To start automatic time synchronization with remote NTP server, type the following command at the terminal.

```
# timedatectl set-ntp true
```

To disable NTP time synchronization, type the following command at the terminal.

```
# timedatectl set-ntp false
```
You have been fun, I've enoyed it. ;)

---

### Post by xendistar2 on 2019-06-11
My Apologise, I have been busy and ill so I have put up with PC clock being an hour slow, but I am back now and my clock is still refusing to budge from being an hour behind, this is what I have currently

```

mit@andora:~$ timedatectl
               Local time: Tue 2019-06-11 21:14:38 GMT
           Universal time: Tue 2019-06-11 21:14:38 UTC
                 RTC time: Tue 2019-06-11 21:14:38
                Time zone: GMT (GMT, +0000)
System clock synchronized: no
              NTP service: inactive
          RTC in local TZ: no

mit@andora:~$ sudo systemctl status ntp
&#9679; ntp.service - Network Time Service
   Loaded: loaded (/lib/systemd/system/ntp.service; enabled; vendor preset: enabled)
   Active: inactive (dead)
     Docs: man:ntpd(8)

mit@andora:~$ sudo systemctl restart ntp.service
mit@andora:~$ sudo service ntp status
&#9679; ntp.service - Network Time Service
   Loaded: loaded (/lib/systemd/system/ntp.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2019-06-11 21:07:11 GMT; 21s ago
     Docs: man:ntpd(8)
  Process: 4336 ExecStart=/usr/lib/ntp/ntp-systemd-wrapper (code=exited, status=0/SUCCESS)
 Main PID: 4356 (ntpd)
    Tasks: 2 (limit: 4915)
   Memory: 3.1M
   CGroup: /system.slice/ntp.service
           &#9492;&#9472;4356 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 122:130


Jun 11 21:07:11 andora ntpd[4356]: Listen normally on 2 lo 127.0.0.1:123
Jun 11 21:07:11 andora ntpd[4356]: Listen normally on 3 enp0s25 192.168.1.133:123
Jun 11 21:07:11 andora ntpd[4356]: Listen normally on 4 lo [::1]:123
Jun 11 21:07:11 andora ntpd[4356]: Listen normally on 5 enp0s25 [fdcc:f6ed:237c::5b2]:123
Jun 11 21:07:11 andora ntpd[4356]: Listen normally on 6 enp0s25 [fdcc:f6ed:237c:0:cdf9:76dc:bfeb:8eb
Jun 11 21:07:11 andora ntpd[4356]: Listen normally on 7 enp0s25 [fdcc:f6ed:237c:0:7e74:4a1b:930c:dbc
Jun 11 21:07:11 andora ntpd[4356]: Listen normally on 8 enp0s25 [fe80::d56a:b06a:9117:3bf0%2]:123
Jun 11 21:07:11 andora ntpd[4356]: Listening on routing socket on fd #25 for interface updates
Jun 11 21:07:11 andora ntpd[4356]: kernel reports TIME_ERROR: 0x2041: Clock Unsynchronized
Jun 11 21:07:11 andora ntpd[4356]: kernel reports TIME_ERROR: 0x2041: Clock Unsynchronized


mit@andora:~$ sudo netstat -pl | grep ntp
udp        0      0 andora.lan:ntp          0.0.0.0:*                           4356/ntpd           
udp        0      0 localhost:ntp           0.0.0.0:*                           4356/ntpd           
udp        0      0 0.0.0.0:ntp             0.0.0.0:*                           4356/ntpd           
udp6       0      0 andora:ntp              [::]:*                              4356/ntpd           
udp6       0      0 andora:ntp              [::]:*                              4356/ntpd           
udp6       0      0 andora:ntp              [::]:*                              4356/ntpd           
udp6       0      0 andora.lan:ntp          [::]:*                              4356/ntpd           
udp6       0      0 ip6-localhost:ntp       [::]:*                              4356/ntpd           
udp6       0      0 [::]:ntp                [::]:*                              4356/ntpd 


```

My Time zone is Europe\London

Any suggestions?

---

### Post by #&amp;thj^% on 2019-06-11
Ok I'm enjoying this less now, you took to long. :lolflag: (Jokingly)
well now that you have it up and running use:
```
sudo timedatectl set-timezone Europe\London
```
Sometimes it takes a reboot to see any change.
And for fun only:
```

echo "Setting TimeZone..."
export tz=`wget -qO - http://geoip.ubuntu.com/lookup | sed -n -e 's/.*<TimeZone>\(.*\)<\/TimeZone>.*/\1/p'` &&  timedatectl set-timezone $tz
export tz=`timedatectl status| grep Timezone | awk '{print $2}'`
echo "TimeZone set to $tz"
```

This will query geoip.ubuntu.com from the server once it is started on the new network (the script checks for connectivity first course) and then sets the server's timezone based on the response.

The** "wget -q0 -" **tells wget to output only the results to stdout which is then piped to the **$tz variable.**
One of these just has to work for you. ;)

Hope it helps someone!

---

### Post by xendistar2 on 2019-06-12
> **1fallen said:**
> Ok I'm enjoying this less now, you took to long. :lolflag: (Jokingly)
well now that you have it up and running use:

I only took along time because my clock is slow :-P

OK Timezone set to Europe\London and ...................................my time is still 1 hour out :(

BUT, when I rebooted the PC, on the sign on screen the time was showing as correct, but as soon as I login the clock displays the time as an hour out

---

### Post by xendistar2 on 2019-06-13
Eureka, I found the issue.............

When I checked with timedatectl it would give me the Time zone as Europe\London

If I checked the time settings on XFCE it would give me Europe\London

But if you right click on the clock in the panel and select properties

The Time in that window was showing UK\London as the timezone

Changed that to Europe\London and now my time is correct.

While the timezone setting was set to UK\London while factually correct it was not a timezone that XFCE understood and it was easy to miss it.

It seems very strange that the time and date module in XFCE setting (which was showing the correct timezone Europe\London) is not the only place where you can adjust the time & date, the right click properties on the clock really should be linked to the time and date module in XFCE setting so that there is only the one location other wise you can end up in the issue I had where one set of settings is blocking the other set of settings

---

