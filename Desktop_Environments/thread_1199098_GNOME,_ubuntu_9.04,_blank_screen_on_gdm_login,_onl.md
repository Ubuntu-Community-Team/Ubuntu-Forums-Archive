---
title: "GNOME, ubuntu 9.04, blank screen on gdm login, only mouse"
date: 2009-06-28
forum: Desktop Environments
---

### Post by DROP on 2009-06-28
I am hoping that someone can help me out here, I am stumped on determining the cause to this problem.

I have a small computer lab running Ubuntu with a central LDAP authentication server, NFS mounted home directories, and libpam-ldap and libnss-ldap for authentication.

This issue which began only recently, is that certain users (seemingly random) are given a black background and only a mouse pointer that they can move around after logging in and it stays like that forever. If the user logs in with the failsafe Gnome session then the problem doesn't arise. This leads me to believe that it's one of the startup programs that's doing something funky.

I am also getting some strange permission denied messages from lsof, but I'm not sure what to make of them.

This is the output of the lsof for the specific user:
```
COMMAND     PID         USER   FD      TYPE DEVICE SIZE NODE NAME
gnome-key 16373 a***********  cwd   unknown                  /proc/16373/cwd (readlink: Permission denied)
gnome-key 16373 a***********  rtd   unknown                  /proc/16373/root (readlink: Permission denied)
gnome-key 16373 a***********  txt   unknown                  /proc/16373/exe (readlink: Permission denied)
gnome-key 16373 a*********** NOFD                            /proc/16373/fd (opendir: Permission denied)
pulse-ses 16385 a***********  cwd   unknown                  /proc/16385/cwd (readlink: Permission denied)
pulse-ses 16385 a***********  rtd   unknown                  /proc/16385/root (readlink: Permission denied)
pulse-ses 16385 a***********  txt   unknown                  /proc/16385/exe (readlink: Permission denied)
pulse-ses 16385 a*********** NOFD                            /proc/16385/fd (opendir: Permission denied)
ssh-agent 16457 a***********  cwd   unknown                  /proc/16457/cwd (readlink: Permission denied)
ssh-agent 16457 a***********  rtd   unknown                  /proc/16457/root (readlink: Permission denied)
ssh-agent 16457 a***********  txt   unknown                  /proc/16457/exe (readlink: Permission denied)
ssh-agent 16457 a*********** NOFD                            /proc/16457/fd (opendir: Permission denied)
dbus-laun 16461 a***********  cwd   unknown                  /proc/16461/cwd (readlink: Permission denied)
dbus-laun 16461 a***********  rtd   unknown                  /proc/16461/root (readlink: Permission denied)
dbus-laun 16461 a***********  txt   unknown                  /proc/16461/exe (readlink: Permission denied)
dbus-laun 16461 a*********** NOFD                            /proc/16461/fd (opendir: Permission denied)
dbus-daem 16463 a***********  cwd   unknown                  /proc/16463/cwd (readlink: Permission denied)
dbus-daem 16463 a***********  rtd   unknown                  /proc/16463/root (readlink: Permission denied)
dbus-daem 16463 a***********  txt   unknown                  /proc/16463/exe (readlink: Permission denied)
dbus-daem 16463 a*********** NOFD                            /proc/16463/fd (opendir: Permission denied)
start-pul 16465 a***********  cwd   unknown                  /proc/16465/cwd (readlink: Permission denied)
start-pul 16465 a***********  rtd   unknown                  /proc/16465/root (readlink: Permission denied)
start-pul 16465 a***********  txt   unknown                  /proc/16465/exe (readlink: Permission denied)
start-pul 16465 a*********** NOFD                            /proc/16465/fd (opendir: Permission denied)
pulseaudi 16466 a***********  cwd   unknown                  /proc/16466/cwd (readlink: Permission denied)
pulseaudi 16466 a***********  rtd   unknown                  /proc/16466/root (readlink: Permission denied)
pulseaudi 16466 a***********  txt   unknown                  /proc/16466/exe (readlink: Permission denied)
pulseaudi 16466 a*********** NOFD                            /proc/16466/fd (opendir: Permission denied)
pulseaudi 16475 a***********  cwd   unknown                  /proc/16475/cwd (readlink: Permission denied)
pulseaudi 16475 a***********  rtd   unknown                  /proc/16475/root (readlink: Permission denied)
pulseaudi 16475 a***********  txt   unknown                  /proc/16475/exe (readlink: Permission denied)
pulseaudi 16475 a*********** NOFD                            /proc/16475/fd (opendir: Permission denied)
gconf-hel 16481 a***********  cwd   unknown                  /proc/16481/cwd (readlink: Permission denied)
gconf-hel 16481 a***********  rtd   unknown                  /proc/16481/root (readlink: Permission denied)
gconf-hel 16481 a***********  txt   unknown                  /proc/16481/exe (readlink: Permission denied)
gconf-hel 16481 a*********** NOFD                            /proc/16481/fd (opendir: Permission denied)
gconfd-2  16484 a***********  cwd   unknown                  /proc/16484/cwd (readlink: Permission denied)
gconfd-2  16484 a***********  rtd   unknown                  /proc/16484/root (readlink: Permission denied)
gconfd-2  16484 a***********  txt   unknown                  /proc/16484/exe (readlink: Permission denied)
gconfd-2  16484 a*********** NOFD                            /proc/16484/fd (opendir: Permission denied)
```

and this is the output of ps aux: (UID=10006 is the problem user):
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3084  1884 ?        Ss   00:27   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   00:27   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   00:27   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   00:27   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   00:27   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   00:27   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   00:27   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   00:27   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   00:27   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   00:27   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   00:27   0:00 [khelper]
root        12  0.0  0.0      0     0 ?        S<   00:27   0:00 [kstop/0]
root        13  0.0  0.0      0     0 ?        S<   00:27   0:00 [kstop/1]
root        14  0.0  0.0      0     0 ?        S<   00:27   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S<   00:27   0:00 [kintegrityd/1]
root        16  0.0  0.0      0     0 ?        S<   00:27   0:00 [kblockd/0]
root        17  0.0  0.0      0     0 ?        S<   00:27   0:00 [kblockd/1]
root        18  0.0  0.0      0     0 ?        S<   00:27   0:00 [kacpid]
root        19  0.0  0.0      0     0 ?        S<   00:27   0:00 [kacpi_notify]
root        20  0.0  0.0      0     0 ?        S<   00:27   0:00 [cqueue]
root        21  0.0  0.0      0     0 ?        S<   00:27   0:00 [ata/0]
root        22  0.0  0.0      0     0 ?        S<   00:27   0:00 [ata/1]
root        23  0.0  0.0      0     0 ?        S<   00:27   0:00 [ata_aux]
root        24  0.0  0.0      0     0 ?        S<   00:27   0:00 [ksuspend_usbd]
root        25  0.0  0.0      0     0 ?        S<   00:27   0:00 [khubd]
root        26  0.0  0.0      0     0 ?        S<   00:27   0:00 [kseriod]
root        27  0.0  0.0      0     0 ?        S<   00:27   0:00 [kmmcd]
root        28  0.0  0.0      0     0 ?        S<   00:27   0:00 [btaddconn]
root        29  0.0  0.0      0     0 ?        S<   00:27   0:00 [btdelconn]
root        30  0.0  0.0      0     0 ?        S    00:27   0:00 [pdflush]
root        31  0.0  0.0      0     0 ?        S    00:27   0:00 [pdflush]
root        32  0.0  0.0      0     0 ?        S<   00:27   0:00 [kswapd0]
root        33  0.0  0.0      0     0 ?        S<   00:27   0:00 [aio/0]
root        34  0.0  0.0      0     0 ?        S<   00:27   0:00 [aio/1]
root        35  0.0  0.0      0     0 ?        S<   00:27   0:00 [ecryptfs-kthrea]
root        38  0.0  0.0      0     0 ?        S<   00:27   0:00 [scsi_eh_0]
root        39  0.0  0.0      0     0 ?        S<   00:27   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S<   00:27   0:00 [scsi_eh_2]
root        41  0.0  0.0      0     0 ?        S<   00:27   0:00 [scsi_eh_3]
root        42  0.0  0.0      0     0 ?        S<   00:27   0:00 [scsi_eh_4]
root        43  0.0  0.0      0     0 ?        S<   00:27   0:00 [scsi_eh_5]
root        44  0.0  0.0      0     0 ?        S<   00:27   0:00 [kstriped]
root        45  0.0  0.0      0     0 ?        S<   00:27   0:00 [kmpathd/0]
root        46  0.0  0.0      0     0 ?        S<   00:27   0:00 [kmpathd/1]
root        47  0.0  0.0      0     0 ?        S<   00:27   0:00 [kmpath_handlerd]
root        48  0.0  0.0      0     0 ?        S<   00:27   0:00 [ksnapd]
root        49  0.0  0.0      0     0 ?        S<   00:27   0:00 [kondemand/0]
root        50  0.0  0.0      0     0 ?        S<   00:27   0:00 [kondemand/1]
root        51  0.0  0.0      0     0 ?        S<   00:27   0:00 [krfcommd]
root       724  0.0  0.0      0     0 ?        S<   00:27   0:00 [kjournald]
root       858  0.0  0.0   2044   552 ?        S<s  00:27   0:00 /sbin/udevd --daemon
root      1483  0.0  0.0      0     0 ?        S<   00:27   0:00 [kpsmoused]
daemon    2043  0.0  0.0   1940   532 ?        Ss   00:27   0:00 /sbin/portmap
statd     2064  0.0  0.0   2004   824 ?        Ss   00:27   0:00 /sbin/rpc.statd
root      2144  0.0  0.0   1808   532 tty4     Ss+  00:27   0:00 /sbin/getty 38400 tty4
root      2145  0.0  0.0   1808   528 tty5     Ss+  00:27   0:00 /sbin/getty 38400 tty5
root      2152  0.0  0.1   6056  2616 tty2     Ss   00:27   0:00 /bin/login --       
root      2153  0.0  0.0   1808   528 tty3     Ss+  00:27   0:00 /sbin/getty 38400 tty3
root      2154  0.0  0.0   1808   528 tty6     Ss+  00:27   0:00 /sbin/getty 38400 tty6
root      2224  0.0  0.0   2204  1084 ?        Ss   00:27   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    2269  0.0  0.0   4908  1580 ?        Ss   00:27   0:00 /sbin/syslogd -u syslog
root      2292  0.0  0.0   1968   536 ?        S    00:27   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      2294  0.0  0.1   3636  2412 ?        Ss   00:27   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108       2317  0.0  0.1   6004  2148 ?        Ss   00:27   0:00 /bin/dbus-daemon --system
root      2470  0.0  0.0  10620  1744 ?        Ss   00:27   0:00 /usr/sbin/winbindd
root      2490  0.0  0.0  10620  1200 ?        S    00:27   0:00 /usr/sbin/winbindd
111       2517  0.0  0.2   9500  5148 ?        Ss   00:27   0:01 /usr/sbin/hald
root      2520  0.0  0.1  17576  2832 ?        Ssl  00:27   0:00 /usr/sbin/console-kit-daemon
root      2583  0.0  0.0   3328  1112 ?        S    00:27   0:00 hald-runner
root      2613  0.0  0.0   5176  1788 ?        S    00:27   0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3
root      2647  0.0  0.0   5188  1780 ?        S    00:27   0:00 /usr/lib/hal/hald-addon-cpufreq
111       2650  0.0  0.0   4852  1680 ?        S    00:27   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      2666  0.0  0.0   3556  1552 ?        Ss   00:27   0:00 /usr/sbin/bluetoothd
root      2699  0.0  0.0  14952  1764 ?        Ss   00:27   0:00 /usr/sbin/gdm
root      2700  0.0  0.2  18572  4396 ?        S    00:27   0:00 /usr/sbin/gdm
root      2728  0.0  0.1  16420  2692 ?        Ssl  00:27   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      2746  0.0  0.0   4280  1336 ?        S    00:27   0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      2748  0.0  0.1   7048  3120 ?        S    00:27   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
avahi     2752  0.0  0.1   5828  2324 ?        Ss   00:27   0:03 avahi-daemon: running [green.local]
avahi     2753  0.0  0.0   5696   912 ?        Ss   00:27   0:00 avahi-daemon: chroot helper
root      2780  0.0  0.1   6280  3012 ?        Ss   00:27   0:00 /usr/sbin/cupsd
root      2808  0.0  0.0   4324  1156 ?        Ss   00:27   0:00 /usr/bin/system-tools-backends
daemon    2881  0.0  0.0   1916   428 ?        Ss   00:27   0:00 /usr/sbin/atd
root      2909  0.0  0.0   3300   960 ?        Ss   00:27   0:00 /usr/sbin/cron
root      2934  0.0  0.0   3700  1748 ?        SNs  00:27   0:45 /usr/sbin/preload -s /var/lib/preload/preload.state -i
root      3007  0.0  0.0   1808   532 tty1     Ss+  00:27   0:00 /sbin/getty 38400 tty1
root      3013  0.0  0.0   2276  1040 ?        S    00:27   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
root      3084  0.0  0.0      0     0 ?        S<   00:27   0:00 [rpciod/0]
root      3085  0.0  0.0      0     0 ?        S<   00:27   0:00 [rpciod/1]
root      3089  0.0  0.0      0     0 ?        S<   00:27   0:00 [nfsiod]
root      3092  0.0  0.0      0     0 ?        S<   00:27   0:00 [lockd]
ntp       3163  0.0  0.0   4220  1228 ?        Ss   00:27   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 113:123 -g
root     15350  0.9  1.2  89532 26604 tty7     Ss+  13:01   0:45 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
10006    16373  0.0  0.1  11524  2304 ?        S    14:19   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
10006    16385  0.0  0.0   1872   528 ?        Ss   14:19   0:00 /bin/sh /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
10006    16457  0.0  0.0   4784   604 ?        Ss   14:19   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
10006    16461  0.0  0.0   6136   976 ?        S    14:19   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
10006    16463  0.0  0.0   5424  1176 ?        Ss   14:19   0:00 //bin/dbus-daemon --fork --print-pid 8 --print-address 10 --session
10006    16465  0.0  0.0   1872   512 ?        S    14:19   0:00 /bin/sh /usr/bin/start-pulseaudio-x11
10006    16466  0.0  0.1  18764  3356 ?        S    14:19   0:00 /usr/bin/pulseaudio --start
10006    16475  0.5  0.2  96120  5036 ?        Ssl  14:19   0:00 /usr/bin/pulseaudio --start
10006    16481  0.0  0.1  10724  3528 ?        S    14:19   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
10006    16484  0.3  0.2  10372  5224 ?        S    14:19   0:00 /usr/lib/libgconf2-4/gconfd-2
pearl    16774  0.6  0.1   5648  3028 tty2     S    14:20   0:00 -bash
pearl    16937  0.0  0.0   5636  2004 tty2     R+   14:20   0:00 ps aux
```

---

### Post by MaskedMarauder on 2009-07-04
I have the same problem.  I've gone over to KDE for now.  It  started after a recent routine package update.

I've also noticed that gnome-terminal can't work from KDE anymore.  The problem there is that gconfd doesn't start with the session.

---

### Post by DROP on 2009-07-04
> **MaskedMarauder said:**
> I have the same problem.  I've gone over to KDE for now.  It  started after a recent routine package update.

I've also noticed that gnome-terminal can't work from KDE anymore.  The problem there is that gconfd doesn't start with the session.

I believe it was after a package update for me as well. I couldn't think of any configuration that I had changed that would cause it. Out of curiosity are you also running an LDAP authentication with NFS home dirs?

My response that seems to be working so far, has been to just create new home directories for the affected users... kind of annoying, and it's totally neglecting the actual cause of the problem but I can't seem to figure out what the root cause is.

---

### Post by thomo5000 on 2009-08-05
I can confirm that we have the same problem with the same configuration, i.e.
LDAP authentication server; NFS home directories; libpam-ldap and libnss-ldap.

Users are NOT going to be happy about starting with new home directories. Any other ideas?

---

### Post by DROP on 2009-08-05
I looked through the affected user's home directory and I can't figure out what causes this. I'm not even really sure which process is hanging. More importantly I can't figure out what the user does to cause this to happen on their next login, or even if it's the user doing something.

It seems like disabling most of the start up applications might help sometimes, but sometimes it doesn't...

---

### Post by Keeper of the Keys on 2009-08-27
I'm having the same/similar problems to the ones sighted above, has anyone had any luck yet?

I observed the following things:
- I am only experiencing this problem with new users (ie. people starting with an empty homedir, or one that was filled by Ubuntu).
(However I only started using Ubuntu clients a few weeks ago and the first testcase for ldap/nfs did work fine even though it was also a new user... So I don't know if it's the same problem since you think it started a long time ago, but I do suffer from the same symptoms)

- I can start a gnome-session for the affected user with now problem from the terminal (as long as there is an X server running), and it will run well.

- However logging in from gdm just lands said user on a black/blank screen with only the mouse visible....

---

### Post by Keeper of the Keys on 2009-08-27
Another observation:
- Failsafe GNOME works

---

### Post by Keeper of the Keys on 2009-08-28
-Kick-
I have been trying to turn various startup scripts off but nothing seems to help...

Is there a way to see an strace of gdm starting? I am not fining it in the logs....

---

### Post by Keeper of the Keys on 2009-08-30
Another kick...

If this is not the right forum maybe a moderator/admin can move it to a forum with more people who know this subject matter.

It seems that if this issue really exists by more people this would be a major problem as it makes networked use of Ubuntu pretty problematic...

---

### Post by DROP on 2009-08-30
It definitely seems like a problem that should be affecting more people. From what you say it looks like your problem is exactly the same as what I described in the first post. I still can't seem to figure out what causes this to happen though. Should we file a bug report?

---

### Post by Keeper of the Keys on 2009-08-31
My workaround for now is using xfce/xubuntu...

It does very much sound like a bug that should be filed...

---

### Post by Keeper of the Keys on 2009-09-07
In my setup gnome has suddenly decided to work again I have no explanation as yet.
What I can say is that I switched from ldap-account-manager/phpldapadmin to gosa2 (and phpldapadmin) and in the process decided to just trash my old database as the new school year anyhow meant a totally new group of people (except for the small amount of staff).
So either the replacement of some library in the dist-upgrade did the trick or the ldap objects were lacking something gosa2 added....

---

### Post by PhilSat on 2009-09-07
Same here. Existing user (so no empty home-dir), all of the sudden no more GDM??

What to do?? Please help

---

### Post by Keeper of the Keys on 2009-09-09
Ok, it seems to be a bit more complicated than I originally assumed, a clean installed system I made yesterday failed on my test user yet I saw teachers succeed so I guess I'll have to investigate the differences in the homedir.

Phil, as I suggested above you may want to try installing xfce4 of kde4 and switching the session to these.
Also note we are discussing the failure in a network logon setting, if that is not your problem then you should either create a topic or find one that deals  with it as the solutions we may come up with here will most likely not help you.

---

### Post by DROP on 2009-09-09
> **Keeper of the Keys said:**
> Ok, it seems to be a bit more complicated than I originally assumed, a clean installed system I made yesterday failed on my test user yet I saw teachers succeed so I guess I'll have to investigate the differences in the homedir.

Phil, as I suggested above you may want to try installing xfce4 of kde4 and switching the session to these.
Also note we are discussing the failure in a network logon setting, if that is not your problem then you should either create a topic or find one that deals  with it as the solutions we may come up with here will most likely not help you.

I examined EVERYTHING in the home directory to try to find a difference between a working and non-working profile. It's hopeless...

---

### Post by thomo5000 on 2009-09-09
I found that installing libpam-ccreds and nscd fixed the problem in our environment. 

I just edited /etc/nscd.conf to cache credentials for 10 hours (longer then anybody's shift) like so:[INDENT][FONT=Courier New]positive-time-to-live   passwd          36000[/FONT]
[FONT=Courier New] positive-time-to-live   group           36000[/FONT]
[/INDENT]I have a feeling that nscd by itself would have fixed the problem, but I configured libpam-ccreds at the same time incase the LDAP server goes down. Our /etc/pam/common-auth now contains:[INDENT][FONT=Courier New]auth sufficient pam_unix.so[/FONT]
[FONT=Courier New] # Pam users members of local groups[/FONT]
[FONT=Courier New] auth required pam_group.so use_first_pass[/FONT]
[FONT=Courier New] # If LDAP is unavailable, go to next line.[/FONT]
[FONT=Courier New] auth [authinfo_unavail=ignore success=1 default=die] pam_ldap.so use_first_pass[/FONT]
[FONT=Courier New] auth [default=done] pam_ccreds.so action=validate use_first_pass[/FONT]
[FONT=Courier New] auth [default=done] pam_ccreds.so action=store use_first_pass[/FONT]
[FONT=Courier New] auth [default=done] pam_ccreds.so action=update use_first_pass[/FONT]
[/INDENT]Hope it helps!

Edited: 
oh I should have mentioned /etc/ldap.conf:
[INDENT][FONT=Courier New]bind_policy soft[/FONT]
[FONT=Courier New] bind_timelimit 5
[/FONT][/INDENT]

---

### Post by andriva on 2009-09-30
Folks,

I'm not sure if this has been solved, either way this worked for me.

Check in the /home/<user>/.pulse directory. It should contain a symlink named something like this.  666c385573d86d7895d493ec4aa2a86c:runtime

If you see a file that is not a symbolic link with a similar name delete it. Login again and the symbolic link should be recreated, and the desktop should load normally.

I spent all day on this -> not pleasing to have Pulse cripple the desktop from loading...

---

### Post by ludda512 on 2009-10-21
I don't know if this will help, but my problem was that I could log in right  after a fresh reboot, but after sometime of inactivity I would be able to login an ldap user, but the splash would not disappear and the screen would fade into black and a cursor.  No other buttons worked to restart xserver and such.  My logs indicated kdm:auth failure and kdm:session closed.  Nothing special, I did find that my nfs stopped responding.  I umounted all and logged in and it worked.

---

