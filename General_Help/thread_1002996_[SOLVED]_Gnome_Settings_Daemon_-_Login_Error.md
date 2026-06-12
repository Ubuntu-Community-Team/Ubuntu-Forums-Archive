---
title: "[SOLVED] Gnome Settings Daemon - Login Error"
date: 2008-12-05
forum: General Help
---

### Post by rampageoberon on 2008-12-05
I randomly got a strange error on booting my PC. It happens everytime I have to login and takes a good 10 minutes to load the desktop. This is the error I get.

```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

On trying to run gnome-settings-daemon from terminal I get the following error and I can't think what could have caused it and how to fix it. Reinstalling dbus (from a forum post) did not help either.

```
** (gnome-settings-daemon:7298): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:7298): WARNING **: Could not acquire name
```

Many thanks in advance

---

### Post by rampageoberon on 2008-12-08
Okay I found a solution to my particular case. There are several other posts with alternate solutions depending on what the cause can be.

In my case it was the rules for Internet Connection Sharing which caused the problem. I applied the rules from [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) and my PC apparently did not like the following rule (in section Configure NAT) with 'dmesg' giving errors such as 'MASQUERADE: lo ate my IP address'

```
$sudo iptables -A POSTROUTING -t nat -j MASQUERADE
```

So I added a condition to check source ip's which fixed things.

```
$sudo iptables -A POSTROUTING -t nat -s xxx.xxx.xxx.xxx -j MASQUERADE
```

cheers

---

