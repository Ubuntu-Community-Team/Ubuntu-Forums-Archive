---
title: "system -&gt; administration -&gt; services GUI won't load."
date: 2007-04-30
forum: Desktop Environments
---

### Post by xamox on 2007-04-30
For some reason when I try to run:
system -> administration -> services

or

system -> administration -> users and groups


I get a pop up box that says:
You are not allowed to access the system configuration.


if I run the command groups my user belongs to the following:
xamox adm dialout cdrom floppy audio dip www-data video plugdev lpadmin scanner admin


What's the dilly-o?

---

### Post by taurus on 2007-04-30
What's the output if you run this command from a terminal?

```
sudo aptitude update
```

---

### Post by xamox on 2007-04-30
```

Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Get:2 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://security.ubuntu.com feisty-security/universe Sources
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/universe Sources
Fetched 3B in 1s (2B/s)
Reading package lists...done


```

---

### Post by taurus on 2007-04-30
What happens if you run this from a terminal?

```
gksudo services-admin
```

---

### Post by xamox on 2007-04-30
This get's dumped in the terminal:

```

(services-admin:7497): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(services-admin:7497): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(services-admin:7497): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject

(services-admin:7497): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed

(services-admin:7497): Liboobs-CRITICAL **: oobs_session_get_platform: assertion `priv->connection != NULL' failed


```

And I get that pop up window that says I don't have access.

---

### Post by xamox on 2007-05-01
What is this dbus error? It seems I get an error when trying to shutdown too. I recently upgraded from 6.10 to 7.04 and then these problems occurred. Any suggestions?

---

### Post by seamus7 on 2007-05-03
I am having a similar problem now. When I go to System/Admin/Services the Servies window pops up but it is blank. I must use Force Quit. I get

(services-admin:17157): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I had just enabled lm-sensors through the Services window before this problem arose. I've gone into /etc/init.d/ and removed lm-sensors there but still the same problem with a frozen blank Services admin window.

???

---

### Post by xamox on 2007-05-03
Yeah, kind of sucks.

---

### Post by Malmsdoom on 2007-05-08
Hi, I have the same problem now, after i activated a checkbox in the services gui. Unfortunately i don't remember the service. Suggestions?

---

### Post by xamox on 2007-05-08
I have yet to find a solution, sorry.

---

### Post by thinkerisme on 2008-01-05
Finally I found one solution for this problem
It's because you shutdown dbus by some way 
So let's recover it!
thinkerisme@Linux:~$ sudo /etc/init.d/dbus restart
Password:
* Stopping System Tools Backends system-tools-backends [ OK ]
* Stopping network events dispatcher NetworkManagerDispatcher [ OK ]
* Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon [fail]
* Stopping network connection manager NetworkManager [ OK ]
* Stopping DHCP D-Bus daemon dhcdbd [ OK ]
* Stopping Hardware abstraction layer hald [ OK ]
* Stopping system message bus dbus [ OK ]
* Starting system message bus dbus [ OK ]
* Starting Hardware abstraction layer hald [ OK ]
* Starting DHCP D-Bus daemon dhcdbd [ OK ]
* Starting network connection manager NetworkManager [ OK ]
* Starting Avahi mDNS/DNS-SD Daemon: avahi-daemon [ OK ]
* Starting network events dispatcher NetworkManagerDispatcher [ OK ]
* Starting System Tools Backends system-tools-backends [ OK ]

Now go to service admin and check dbus&#65281;

---

