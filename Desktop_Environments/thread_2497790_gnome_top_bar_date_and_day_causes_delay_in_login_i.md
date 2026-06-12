---
title: "gnome top bar date and day causes delay in login in if system time is set to autosync"
date: 2024-05-17
forum: Desktop Environments
---

### Post by vidyadhara on 2024-05-17
I have a fresh install of ubuntu 22.04. 

uname -a

Linux <computername> 6.5.0-35-generic #35~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue May  7 09:00:52 UTC 2 x86_64 x86_64 x86_64 GNU/Linux



I installed gnome-tweaks to set the background wall paper. Then I also attempted to set the week day and date. These promptly show up in the top bar.
But when I attempt to login again, the dash takes several seconds. Perhaps even 30 to 40 seconds on occasion. 

I created another account, deleted my original account and recreated it.

now it logs in quickly. 

But when i set the  date and day again on the top bar, it starts delaying the login once more.

If i remove the automatic date and time in settings, it logs in quickly again. 

Looks like that is definitely the problem.

Something in either gnome tweaks that forces a date time sync when logging in if that particular detail is added to the top bar.

And I was unable to find how to add tags after I posted this message. If someone can find that and add the appropriate tags, I'll be obliged.

---

### Post by MAFoElffen on 2024-05-18
Why? Without doing that, without that Gnome option enabled, what does this show?
```

sudo timedatectl status
sudo timedatectl timesync-status

```

---

### Post by vidyadhara on 2024-05-19
my desktop is gnome.

i turned off the time autosync in gnome settings and did this in gnome terminal.

vidyadhara@ryzen5600lin:~$ sudo timedatectl status
               Local time: Sun 2024-05-19 13:02:30 IST
           Universal time: Sun 2024-05-19 07:32:30 UTC
                 RTC time: Sun 2024-05-19 07:32:30
                Time zone: Asia/Kolkata (IST, +0530)
System clock synchronized: yes
              NTP service: inactive
          RTC in local TZ: no



vidyadhara@ryzen5600lin:~$ sudo timedatectl timesync-status
Failed to query server: Unit dbus-org.freedesktop.timesync1.service not found.

I see the same response to the second command for several attempts.

I checked this page for fixing the problem.

--
[https://bbs.archlinux.org/viewtopic.php?id=288227](https://bbs.archlinux.org/viewtopic.php?id=288227)
--

did the following commands.

systemctl start systemd-resolved.service

and

systemctl enable systemd-resolved.service

both exit with status 0 (assuming that means successful).

But still 

sudo timedatectl timesync-status
Failed to query server: Unit dbus-org.freedesktop.timesync1.service not found.

---

### Post by MAFoElffen on 2024-05-19
Here is my output for those
```

mafoelffen@Mikes-B460M:~$ sudo timedatectl status
               Local time: Sun 2024-05-19 09:42:36 PDT
           Universal time: Sun 2024-05-19 16:42:36 UTC
                 RTC time: Sun 2024-05-19 16:42:36
                Time zone: America/Los_Angeles (PDT, -0700)
[COLOR=#ff0000]System clock synchronized: yes
              NTP service: active
[/COLOR]          RTC in local TZ: no
mafoelffen@Mikes-B460M:~$ sudo timedatectl timesync-status
[COLOR=#ff0000]       Server: 185.125.190.56 (ntp.ubuntu.com)
Poll interval: 34min 8s (min: 32s; max 34min 8s)
[/COLOR]         Leap: normal
      Version: 4
      Stratum: 2
    Reference: B7A08584
    Precision: 1us (-25)
Root distance: 1.006ms (max: 5s)
       Offset: -11.337ms
        Delay: 163.959ms
       Jitter: 6.656ms
 Packet count: 1513
    Frequency: -11.282ppm

```
I asked for that output to see if the system had time sync turned on, and what by. The second command would check where from, and the pooling interval. I also use Gnome as a desktop. But I don't set the datetime sync through Gnome. That is just a duplication to me.

Here is yours:
```

vidyadhara@ryzen5600lin:~$ sudo timedatectl status
Local time: Sun 2024-05-19 13:02:30 IST
Universal time: Sun 2024-05-19 07:32:30 UTC
RTC time: Sun 2024-05-19 07:32:30
Time zone: Asia/Kolkata (IST, +0530)
[COLOR=#ff0000]System clock synchronized: yes
NTP service: inactive
[/COLOR]RTC in local TZ: no

```
So it says it is syncronized, but not through NTP...

I have to do a few errands, I'll get back to this a bit later.

EDIT: While running out the door... Please post the results of this so we can see where it is going to... But important that you post the output within CODE Tags!
```

systemctl status systemd-timesyncd --no-pager -l

```

---

### Post by vidyadhara on 2024-05-20
as i said earlier,  i turned off time sync in gnome settings to get faster login. That is what this seems to be reporting. 

```

vidyadhara@ryzen5600lin:~$ sudo systemctl status systemd-timesyncd --no-pager -l[sudo] password for vidyadhara: 
&#9675; systemd-timesyncd.service - Network Time Synchronization
     Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; disabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:systemd-timesyncd.service(8)


```


Now i turned it on and did the same thing again,

```

vidyadhara@ryzen5600lin:~$ sudo systemctl status systemd-timesyncd --no-pager -l
[sudo] password for vidyadhara: 
&#9679; systemd-timesyncd.service - Network Time Synchronization
     Loaded: loaded (/lib/systemd/system/systemd-timesyncd.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2024-05-20 10:34:39 IST; 13s ago
       Docs: man:systemd-timesyncd.service(8)
   Main PID: 4677 (systemd-timesyn)
     Status: "Initial synchronization to time server 185.125.190.57:123 (ntp.ubuntu.com)."
      Tasks: 2 (limit: 38318)
     Memory: 1.4M
        CPU: 52ms
     CGroup: /system.slice/systemd-timesyncd.service
             &#9492;&#9472;4677 /lib/systemd/systemd-timesyncd

May 20 10:34:39 ryzen5600lin systemd[1]: Starting Network Time Synchronization...
May 20 10:34:39 ryzen5600lin systemd[1]: Started Network Time Synchronization.
May 20 10:34:39 ryzen5600lin systemd-timesyncd[4677]: Initial synchronization to time server 185.125.190.57:123 (ntp.ubuntu.com).



```

the login lags even if i remove the day and date from the top bar, but for a shorter period. If I include them (through gnome-tweaks), it lags much longer.



[B]The lagging is off and on even with the time sync turned off. not entirely clear that it is the problem. But the lag is consistent with sync turn on.
[/B]

p.s.
I have a second account with time sync turned off. That too is acting funny.  very long lag after login. It seems to be taking longer than two minutes to get to working condition.

This is practically a fresh installation.

I have an NVidia gt 1030 graphics card and the system is using the nvidia 535 driver. I don't understand enough about the free / non free versions of this driver. Nouveau is the free version if I am not wrong. And that is a mess with two displays atleast for this hardware.

The last attempt a couple of weeks ago to try several different drivers destroyed my installation and I had to reinstall the OS.  

I have an old asus laptop that is running ubuntu 22.04 quite well for the past couple of years.

I think I want to try 24.04 on my newer ryzen box.

There maybe some linux distribution that works better than this for the gt1030 card.

Probably I am attempting too many things to be able to report any particular detail with sufficient fidelity.

Thanks a ton for the help so far.

---

### Post by vidyadhara on 2024-05-21
I installed ubuntu 24.04 over the earlier 22.04. And I installed gnome-tweaks. set a background picture and centered it. That crashed the desktop.

The OS was still running so I logged into tty2 and created a new user, cleaned out the old user and recreated it. It is working ok as of now.

Looks like something is really broken in gnome-tweaks.

---

