---
title: "Strange reboot bug"
date: 2008-12-22
forum: General Help
---

### Post by eeliottheking on 2008-12-22
Hello, i am running Ubuntu 8.10 Intrepid, and i am experiencing an annoying but not critical problem.  Evertime I click the user icon at the top left that has my name on it and select either shutdown, or reboot, it sends me to the GDM login screen for some reason.  Any idea as to what could be creating this problem?

> everyone knows what im talking about right?  the bar in the upper left corner that comes in the normal GUI of Intrepid.  Normally it lets you switch users, logout, restart, etc.  whenever i click either restart or shutdown it send me back to the GDM screen.

---

### Post by eeliottheking on 2008-12-22
sorry to bump, but does anyone have a possible solution to this?

---

### Post by eeliottheking on 2008-12-22
sorry for another bump, but seeing how many posts this place gets id like to not let it get buried.

---

### Post by eeliottheking on 2008-12-23
Anyone got anything on this?

---

### Post by eeliottheking on 2008-12-23
bump again maybe

---

### Post by eeliottheking on 2008-12-23
bump again :)

---

### Post by eeliottheking on 2008-12-23
bump again?

---

### Post by eeliottheking on 2008-12-23
sorry for another bump.  am i asking at a bad time?

---

### Post by eeliottheking on 2008-12-24
everyone knows what im talking about right?  the bar in the upper left corner that comes in the normal GUI of Intrepid.  Normally it lets you switch users, logout, restart, etc.  whenever i click either restart or shutdown it send me back to the GDM screen.

---

### Post by iponeverything on 2008-12-24
I haven't heard of this issue before and from my digging around the condition seems pretty rare. 

Do Ctrl-Alt-F2 to open in a Vty, in the Vty do:
```

cd /var/log
sudo tail -vf syslog daemon.log messages kern.log debug > /tmp/debug.txt

```

Then do Ctrl-Alt-F7 to switch back to the GUI, try to shutdown.

After you pop up back to GDM do Ctrl-Alt-F2 to go back to your Vty.

Do Ctrl-c to kill your tail. Now do:

```
sudo dmesg >> /tmp/debug.txt

```

Then switch back to the GUI login and upload /tmp/debug.txt as an attachment with your next bump.

---

### Post by eeliottheking on 2008-12-24
thank you for helping!

alright, i did just as you said, but for some reason firefox wants to crash everytime i browse for debug.txt, so i just pastebin'd it instead

[http://pastebin.com/f3cb13de1](http://pastebin.com/f3cb13de1)

hope this helps.

---

### Post by eeliottheking on 2008-12-24
bump

---

### Post by iponeverything on 2008-12-25
it looks like for the dmesg part your only put one ">" instead of two ">>" so it didn't append and instead overwrote. 

try again.

---

### Post by eeliottheking on 2008-12-25
> **iponeverything said:**
> it looks like for the dmesg part your only put one ">" instead of two ">>" so it didn't append and instead overwrote. 

try again.

oops, my bad

[http://pastebin.com/f57ab191b](http://pastebin.com/f57ab191b)  -  hopefully a correctly done debug.txt  sorry to waste your time with the last one :(

---

### Post by iponeverything on 2008-12-25
check to see if console kit daemon is running.

```
ps uaxwww|grep console-kit
```

also post the output of:

```

dpkg -l |grep consolekit
uname -a

```

---

### Post by iponeverything on 2008-12-25
also post post the output of:

```
sudo ifconfig

```

need to see if your loopback device is missing.

---

### Post by eeliottheking on 2008-12-25
ps uaxwww|grep console-kit

```
eeliottheking@eeliottheking-cpu:~$ ps uaxwww|grep console-kit
root      5333  0.0  0.0  17480  2612 ?        Ssl  02:35   0:00 /usr/sbin/console-kit-daemon
1000     12880  0.0  0.0   3240   820 pts/0    S+   04:20   0:00 grep console-kit

```



dpkg -l |grep consolekit
```
eeliottheking@eeliottheking-cpu:~$ dpkg -l |grep consolekit
ii  consolekit                                 0.2.10-1ubuntu9                                      framework for defining and tracking users, s

```



uname -a
```
eeliottheking@eeliottheking-cpu:~$ uname -a
Linux eeliottheking-cpu 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

```




sudo ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:04:bb:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:222 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:852 (852.0 B)  TX bytes:852 (852.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:a5:7d:47  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:297698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:436363093 (436.3 MB)  TX bytes:16113431 (16.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-A5-7D-47-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by iponeverything on 2008-12-25
```
Dec 25 02:38:06 eeliottheking-cpu bonobo-activation-server (eeliottheking-6868): could not associate with desktop session: Failed to connect to socket /tmp/dbus-I4f1PMqmLz: Connection refused
```

I think that this is the issue. Though, I don't know cause. I'll look around a bit.

-- I dislike the auto inserting of the :) every time it this board sees a colon paren - very annoying.

---

### Post by iponeverything on 2008-12-25
see if dbus is running

```

ps uaxwww|grep dbus
env | grep -i dbus

```

Also try creating a new user on the system, give the user administrative privs --
reboot the machine, log in as the new user and see it will shutdown from that account.

System -> Administration -> Users and Groups

---

### Post by eeliottheking on 2008-12-25
ps uaxwww|grep dbus
```
108       5078  0.0  0.0   3176  1500 ?        Ss   02:35   0:03 /bin/dbus-daemon --system
1000      7041  0.0  0.0   3168  1540 ?        Ss   02:39   0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
1000      7042  0.0  0.0   3124   688 ?        S    02:39   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-session-manager
1000     21329  0.0  0.0   3240   820 pts/0    S+   09:22   0:00 grep dbus

```



env | grep -i dbus
```
eeliottheking@eeliottheking-cpu:~$ env | grep -i dbus
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-DZYgtry8fv,guid=1b78fb0344c72259cdb2918f495338a3
eeliottheking@eeliottheking-cpu:~$ 

```

will post new user results in just a second.

EDIT:  A new user with admin privileges is NOT able to restart.

---

### Post by iponeverything on 2008-12-25
I am running out of ideas..

Try to reinstall some of the packages in question..

```

sudo apt-get --reinstall install gdm
sudo apt-get --reinstall install dbus
sudo apt-get --reinstall install dbus-x11
sudo apt-get --reinstall install libpolkit-dbus2

```

then try a reboot..

---

### Post by eeliottheking on 2008-12-25
alright.  I re-installed all 4 apps, and i still have the same problem.

---

### Post by iponeverything on 2008-12-25
Barring a clean install, I am out of ideas.

---

### Post by eeliottheking on 2008-12-26
> **iponeverything said:**
> Barring a clean install, I am out of ideas.

alright, its only a small bug.  i can live with logging out and pressing the power button.  thanks for your time and help :)

---

