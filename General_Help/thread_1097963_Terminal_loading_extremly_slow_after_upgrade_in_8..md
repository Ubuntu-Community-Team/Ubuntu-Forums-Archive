---
title: "Terminal loading extremly slow after upgrade in 8.04"
date: 2009-03-16
forum: General Help
---

### Post by Ostien on 2009-03-16
I have been running Hardy (8.04) for a while now and everything was fine.  I had been running KDE and wanted to try out Gnome to see if I like it.  Turned out I didin't really.  SO I went to:
[http://psychocats.net/ubuntu/purekdehardy](http://psychocats.net/ubuntu/purekdehardy)
and uninsalled all of Gnome and went back to the default programs for a Kubuntu install.  Went fine just had to re-install some things that got taken down in the massive uninstall such as Firfox, xchat, pidgin, gimp, etc.

However now loading a terminal is damn slow.  I use Kuake a lot and when I call it up it takes about a minute to load the shell and a bit after that before I can start typing.  This is the same with ANY terminal program.  Other programs such as Firefox and OpenOffice seem to take slightly longer to load.  There were some upgrades that went though so this may be some buggy upgrade.  Hate when that happens.

After browsing the forums for a bit a common solution seemed to be to remove all references to ipv6 from the /etc/host file.  I thought that may be the problem because I had a slowness issue before and that resolved it and thought my /etc/host got overwritten.  Nope still had me hosts file with all the ipv6 commented out.  Tried removing the lines completly and restarting to no avail.

Any ideas?  Also Don't know if this matters but an upgrade a while ago gave me a new kernel (2.6.24-23-386) and that didin't work out too well (X would not load) So I went back to using 2.6.24-22-386.

---

### Post by Ostien on 2009-03-17
UPDATE: This seems to also affect KdeSudo (it takes a long time to load and then when it does a while before I can start typing).  Also saving files in OpenOffice has the same issues and its slower on loading up then it used to be.

---

### Post by fieroboom on 2009-03-17
> **Ostien said:**
> UPDATE: This seems to also affect KdeSudo (it takes a long time to load and then when it does a while before I can start typing).  Also saving files in OpenOffice has the same issues and its slower on loading up then it used to be.

This sluggishness can happen sometimes if you don't have a $HOSTNAME variable set, or if your loopback doesn't come online. Since the machine is trying to communicate with itself, but doesn't know where itself is, it has to go find itself and bring it back to itself so that it can present you with what you want....;)

Whew...
Anyway, run these commands, copy the output from each one, and post them here:

```
ifconfig
hostname
cat /etc/hosts
```

This will show us 1) your interfaces, 2) your machine's hostname, and 3) what you have locally stored for a DNS cache.
:D
-Paul

---

### Post by Ostien on 2009-03-17
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:11:2f:de:4d:97
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fede:4d97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:232944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:331091528 (315.7 MB)  TX bytes:11265195 (10.7 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:475 errors:0 dropped:0 overruns:0 frame:0
          TX packets:475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:27624 (26.9 KB)  TX bytes:27624 (26.9 KB)

my hostname is:
ostien
and the contents of my /etc/hosts is:
127.0.0.1 localhost ostien

---

### Post by Ostien on 2009-03-19
shameless self bump

The output I pulled up seems, to me, to look in working order.  Is there some other explanation for this problem?  Its getting really annoying :/

---

### Post by Ostien on 2009-03-20
ANOTHER UPDATE:

okay so some progress was made with the help of pturing on the freenode #Ubuntu IRC chat

A workaround has been found not too pretty but it is functional.

went to a virtual tty terminal logged in and made a file .xinitrc with the line xterm.  Then ran startx -- :3 to get a blank x session with the xterm pulled up.  Ran 'startkde'

The original purpose was to see if there were any interesting messages in the xterm but what happened was it was working fast on this instance of kde.  It was running fast like it used to on everything from Kuake to kdesudo to Openoffice.

So while I was trying to find some error messages I found a workaround.  I still want to fix it so that I don't have to do this, that is start another kde session.

Hope this information will be useful and be able to point me in the right direction.

donno how long these links last for but here [http://paste.ubuntu.com/134064/](http://paste.ubuntu.com/134064/) is part of my /var/log/messages the many segfaults are worrying.

---

### Post by Ostien on 2009-03-20
LAST UPDATE:

Seems that the scim-bridge segfaults were the problem

```

Mar 19 23:50:48 toaster kernel: [ 1875.049849] scim-bridge[11071]: segfault at 53454741 eip b7e6b443 esp bfa24b70 error 4

```

seems scim was all out of wack technically speaking.  I found a bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/hardy/+source/scim-bridge/+bug/199592](https://bugs.launchpad.net/ubuntu/hardy/+source/scim-bridge/+bug/199592)
However all I did was reinstall the scim package and it worked like a charm.  Don't know about the other workarounds suggested.

---

