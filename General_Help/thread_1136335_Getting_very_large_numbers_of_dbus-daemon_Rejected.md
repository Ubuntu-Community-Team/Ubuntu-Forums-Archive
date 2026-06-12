---
title: "Getting very large numbers of dbus-daemon: Rejected send message"
date: 2009-04-24
forum: General Help
---

### Post by MechaMechanism on 2009-04-24
SOLVED

I am getting a very large number of the message below in the log file.  Do I need to be worried?  Is something not working right or did I set up Ubuntu incorrectly.  Is there a way to turn the message off if it turns out to be harmless.
```
Apr 24 21:13:02 dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.38" (uid=1000 pid=4357 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.247" (uid=1000 pid=2409 comm="/usr/lib/firefox-3.0.9/firefox "))
```

---

### Post by jsjuni on 2009-05-03
How did you solve it? I'm getting a "rejected send message" every time DHCP renews a lease--3572 times in yesterday's auth.log file.

---

### Post by MechaMechanism on 2009-05-03
> **jsjuni said:**
> How did you solve it? I'm getting a "rejected send message" every time DHCP renews a lease--3572 times in yesterday's auth.log file.You have to make a filter.

Example, you will need to modify this for your machine.
```
^\w{3} [ :0-9]{11} [._[:alnum:]-]+ dbus-daemon: Rejected send message, [0-9]+ matched rules; type="method_call", sender=":[0-9.]+" \(uid=[0-9]+ pid=[0-9]+ comm="/usr/lib/indicator-applet/indicator-applet --oaf-a"\) interface="org.freedesktop.DBus.Properties" member="Get" error name="\(unset\)" requested_reply=0 destination="[0-9:.]+" \(uid=0 pid=[0-9]+ comm="/USR/SBIN/CRON "\)\)
```The filter is located at /etc/logcheck.

---

### Post by magicke on 2009-05-20
So, all these error-like messages are harmless and can be ignored then? Thats how I understood your solution to all those messages.

peace ^^

---

### Post by MechaMechanism on 2009-05-21
Yes they are harmless.  The log filtering turns out not to have worked but oh well, 9.10 will probably have less noise.

---

### Post by Unhban on 2009-05-21
Pardon me for being a newb, but I've suddenly started to get these messages on U9.04, surely there's something wrong!

Unh.

---

### Post by MechaMechanism on 2009-05-21
You mean you had 9.04 for a while and previously did not receive the messages but now have started to receive them.  The messages are only generated in the Gnome desktop, not when you are logged out or only logged in on one of the tty1-6.

---

### Post by maximevaillant on 2009-05-21
I can confirm I'm seeing the same errors filling up the /var/log/auth.log only when opening a gnome session. These messages do not appear when starting an ssh session or a tty1-6 console session. 

There is an open bug for this issue :

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/346513](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/346513)

---

### Post by Johnny B on 2009-08-02
script to clean auth.log
> #!/bin/bash
# clean auth.log
# run as root/sudo
cat /var/log/auth.log | grep -v "/usr/lib/indicator-applet/indicator-applet --oaf-a" > /tmp/auth.002
mv /tmp/auth.002 /var/log/auth.log
#chmod 640 /var/log/auth.log

---

