---
title: "wifi-radar doesn't work???"
date: 2005-10-24
forum: Desktop Environments
---

### Post by daller on 2005-10-24
Hi There,

In Hoary I installed wifi-radar from the repositories, and it worked great!

Now when i start wifi-radar, and tries to connect, it stalls at "please wait"

Gives this output in konsole:

Error : unrecognised wireless request "default"
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 903, in connect_profile
    connect_to_network( ssid, connect_status_window )
  File "/usr/sbin/wifi-radar", line 296, in connect_to_network
    os.kill( int(open(DHCP_PIDFILE, mode='r').readline()), signal.SIGTERM )
ValueError: invalid literal for int():

Any suggestions?

---

### Post by daller on 2005-11-09
I don't know whats wrong! - but it works in dapper...

---

### Post by speedybits on 2005-11-17
I'm having the exact same problem with Wifi-radar in Breezy. In the GUI, it just says "Working, please wait". My ESSID is "shwashwa". 

This is what happens when I run 'sudo wifi-radar' from the terminal and select "shwashwa" and then press the connect button:

Error : unrecognised wireless request "shwashwa"
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 903, in connect_profile
    connect_to_network( ssid, connect_status_window )
  File "/usr/sbin/wifi-radar", line 296, in connect_to_network
    os.kill( int(open(DHCP_PIDFILE, mode='r').readline()), signal.SIGTERM )
ValueError: invalid literal for int():


Please help! By the way, Breezy is amazing...I'm completely hooked!

---

### Post by bkaiser on 2006-01-04
sorry to bring up a months old topic, but I got exactly the same problem with wifi-radar. ```
wifi-radar -d
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1796, in ?
    connect_to_preferred()
  File "/usr/sbin/wifi-radar", line 188, in connect_to_preferred
    connect_to_network( ssid, None )
  File "/usr/sbin/wifi-radar", line 296, in connect_to_network
    os.kill( int(open(DHCP_PIDFILE, mode='r').readline()), signal.SIGTERM )
ValueError: invalid literal for int():

```
I have to ifdown and ifup the interface manually. But then it will get a IP by my DHCP and will work properly. I have no clue what is happening here. btw: I use a madwifi card with Ubuntu 5.10.

---

### Post by bedge on 2006-01-11
Still broken....
I tried the dapper version too, same thing, so it most be one of the libs that wifi-radar demends on:

0 #> apt-cache policy wifi-radar
wifi-radar:
  Installed: **1.9.4-0ubuntu7**
  Candidate: 1.9.4-0ubuntu7
  Version table:
 *** 1.9.4-0ubuntu7 0
        200 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
        100 /var/lib/dpkg/status
     1.9.4-0ubuntu6 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages

---

### Post by animacide on 2006-02-08
I've been having this same problem for a few days now, and I've found a solution.  I guessed there was something wrong with one of the PID files for dhcp from the traceback, so i just did this:

```
sudo rm /var/run/dh*
```

and magically it worked again.  Hope this helps.

---

