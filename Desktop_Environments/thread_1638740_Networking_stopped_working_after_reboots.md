---
title: "Networking stopped working after reboots"
date: 2010-12-06
forum: Desktop Environments
---

### Post by shadomic on 2010-12-06
I installed Ubuntu  10.04 through the Wubi installer (Funny, I installed it today and thought I would have gotten 10.10). I had a network connection and everything was working fine. I rebooted my coumputer a couple of times and then suddenly, I could not connect to the network and when I click the wireless/networking icon it says "Networking Disabled".

I reinstalled Ubuntu and the problem went away. After a few reboots the problem returned. I have tried restarting to see if it would come back as well as a few other things listed below. Any other suggestions would be appreciated.


Tried to restart networking via /etc/init.d/networking:
---

```
    amato@ubuntu:~$ sudo /etc/init.d/networking restart
     * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                             [ OK ]
```

Tried to stop and start it:
---

```
    amato@ubuntu:~$ sudo /etc/init.d/networking stop
     * Deconfiguring network interfaces...                                   [ OK ] 
    amato@ubuntu:~$ 
    amato@ubuntu:~$ sudo /etc/init.d/networking start
    Rather than invoking init scripts through /etc/init.d, use the service(8)
    utility, e.g. service networking start
    
    Since the script you are attempting to invoke has been converted to an
    Upstart job, you may also use the start(8) utility, e.g. start networking
    networking stop/waiting
```

Tried start networking:
---

```
    amato@ubuntu:~$ start networking
    start: Rejected send message, 1 matched rules; type="method_call", sender=":1.58" (uid=1000 pid=2241 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
    amato@ubuntu:~$ sudo start networking
    networking stop/waiting
```

Tried service networking restart:
---

```
    amato@ubuntu:~$ service networking restart
    restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.60" (uid=1000 pid=2248 comm="restart) interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))
    amato@ubuntu:~$ sudo service networking restart
    restart: Unknown instance: 
```



Here are the contents of my /etc/network/interfaces.
--

```
    auto lo
    iface lo inet loopback

I even tried to modify it to this (based on something I read, online, not sure if I was doing the right thing here). Tried everything again and no luck:

    auto lo eth0
    iface lo inet loopback
    
    iface eth0 inet dhcp
```

---

### Post by c00d on 2011-09-16
I know that this is a very old problem, but I have the same problem right now with my netbook ubuntu installation and I do not want to create a new thread. Problem described below:

Everything was working fine yesterday. Powered on my netbook today, and it can't find any wireless networks (pan0 interface working ok though).

The commands below give the answers below:

service networking restart 
restart: Unknown instance:

service networking start
networking stop/waiting

(same message if I try to start it through the /etc/init.d command)

Does anyone have a solution for this? I'm suspecting that the networking daemon is causing my wifi to fail but I'm not sure how I can start it.

Thanks in advance.


Edit: 
The command:
service networking status 
gives the same result:
networking stop/waiting

---

