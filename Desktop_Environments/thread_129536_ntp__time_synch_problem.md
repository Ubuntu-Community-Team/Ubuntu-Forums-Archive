---
title: "ntp / time synch problem"
date: 2006-02-14
forum: Desktop Environments
---

### Post by msak007 on 2006-02-14
Ok so I'm a linux n00b, and I love Kubuntu. I've had a few issues that I've been able to resolve by googling or looking on the forum, but there's one driving me absolutely nuts that I can't find the answer to anywhere. I'm not sure when it started happening, but I didn't have this issue when I first installed Kubuntu about a month ago. But now anytime I try to synch my clock using the ntp servers, I get an error. These are the steps I'm taking to update the time:

Right-click on clock --> Adjust Date & Time --> Check the "Set date and time automatically:" --> hit OK or Apply

and I get the following error:

"Unable to connect to time server: pool.ntp.org"

I get this regardless of what server I choose with the error indicating the server I tried to connect to (I have several, including Public, north-america, etc.), but I can ping all of them with no problem.

I have already tried uninstalling / reinstalling ntp-server, ntp, ntpd, and editing my ntp.conf file. I have "pool.ntp.org" commented out, and the only server listed in the file is "ntp.ubuntulinux.org" but that is not in my list of servers to choose from in the drop-down box, so I have no idea where it's pulling the server info from. I've restarted the ntp server several times, and did a full reboot with no change. Can someone please tell me where else these server settings are stored, and why I'm unable to connect to any of them using the KDE Control Module clock settings? Thanks in advance to anyone that can help me out.

---

### Post by David Valentine on 2006-02-17
I'm having the exact same problem...

---

### Post by grsuisse on 2006-04-14
If you are like me your router has problems with IPv6. To overcome this for ntp you need to make a copule of changes.
First ntpdate is called at start up. Its configuration file is /etc/defaults/ntpdate. Adding -4 to the line NTPOPTIONS will force ntpdate to use IPv4. My file looks like this:
# servers to check.   (Separate multiple servers with spaces.)
#NTPSERVERS="pool.ntp.org"
NTPSERVERS="ch.pool.ntp.org"
#NTPSERVERS="ntp.ubuntulinux.org"
#
# additional options for ntpdate
#NTPOPTIONS="-v"
NTPOPTIONS="-u -4"

Note that I have also selected a server closer to me (ch.pool.ntp.org). To find a list of alternative servers go to the following [http://www.pool.ntp.org/]("http://www.pool.ntp.org/")

That should fix your problems at start up. 

There is also a daemon that runs during your session and regularly checks the time. This is turned on from the System menu under Administration - Time and Date. You need to tick the box and then select some servers close to you (you can also add the pool referred to above). 

The daemon ntpd also needs to be forced to use IPv4. To do this edit the file /etc/ntp.conf. On every line that starts with the word "server" you need to put  "-4" between the word "server" and the name of the ntp server.  My file looks like this:
# /etc/ntp.conf, configuration for ntpd

# ntpd will use syslog() if logfile is not defined
#logfile /var/log/ntpd

driftfile /var/lib/ntp/ntp.drift
statsdir /var/log/ntpstats/

statistics loopstats peerstats clockstats
filegen loopstats file loopstats type day enable
filegen peerstats file peerstats type day enable
filegen clockstats file clockstats type day enable


# You do need to talk to an NTP server or two (or three).
#server ntp.your-provider.example

server -4 ch.pool.ntp.org
etc.

---

### Post by rubengs on 2006-05-10
I tried this solution and was unable to solve the problem for KDE, I think KDE uses a different way to synchronize time with the servers than Gnome, the latter uses ntp-server to do it, and KDE uses a script that is equivalent to running this: 

> sudo /etc/init.d/ntp-server stop
sudo ntpdate pool.ntp.org
sudo /etc/init.d/hwclock.sh restart
sudo /etc/init.d/ntp-server start

If you run this commands you can have an efective synchronization, my solution was as simple to uninistall ntp-simple and ntp-server and doing this again: 

Right-click on clock --> Adjust Date & Time --> Check the "Set date and time automatically:" --> hit OK or Apply

Without this packages you can use this function, no problem ;) .

---

### Post by gauss on 2007-07-19
I have exactly the same problem as msak007 with Feisty Fawn/AMD64. I tried the IPv4 solution from grsuisse but it didn't seem to solve the problem. (Also, I have ntpdate only--not ntp). Here's what I get from the command line:

```
/usr/sbin# ./ntpdate-debian us.pool.ntp.org
Error : Servname not supported for ai_socktype
19 Jul 15:56:30 ntpdate[5873]: can't find host us.pool.ntp.org

Error : Servname not supported for ai_socktype
19 Jul 15:56:30 ntpdate[5873]: can't find host us.pool.ntp.org

19 Jul 15:56:30 ntpdate[5873]: no servers can be used, exiting
```

Any pointers would be gratefully received.

[EDIT] In frustration I installed *rdate* and get the *same* error.
```
~# rdate us.pool.ntp.org
rdate: Servname not supported for ai_socktype: pool.ntp.org 
``` so it must have something to do with networking. But my DNS works, I don't have other networking problems, and ntp is associated with port 123 in */etc/services*.
[/EDIT]

---

### Post by Tanjerine on 2007-10-09
> **rubengs said:**
> I tried this solution and was unable to solve the problem for KDE, I think KDE uses a different way to synchronize time with the servers than Gnome, the latter uses ntp-server to do it, and KDE uses a script that is equivalent to running this: 



If you run this commands you can have an efective synchronization, my solution was as simple to uninistall ntp-simple and ntp-server and doing this again: 

Right-click on clock --> Adjust Date & Time --> Check the "Set date and time automatically:" --> hit OK or Apply

Without this packages you can use this function, no problem ;) .

:KS this solution worked for me on gutsy. 'cept that in my case, it was .. 

```

sudo /etc/init.d/ntp stop
sudo /etc/init.d/ntp start

```

and not ntp-server. so i just uninstalled ntp. :)

---

