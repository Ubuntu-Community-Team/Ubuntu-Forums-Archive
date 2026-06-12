---
title: "Prevent suspend/sleep using wol wake on lan"
date: 2012-10-31
forum: Desktop Environments
---

### Post by bilboubu on 2012-10-31
I want xbmc to suspend a machine after 30 mins of inactivity which it does. A tv server runs on this machine and I do not want it to suspend whilst it has clients connected.

At present I use a wake on lan to wake it up but the problem is that it still goes to sleep after the idle time even though I send continuous wol packets, the wol packets do wake it up again however.

Is there a way to reset the idle timer with a wol magic packet or is there some other way to do what I am after?

---

### Post by aromo on 2012-10-31
As you discovered, WOL packets won't prevent your TV server to go into suspend mode.  As it stands for Wake On-Lan will wake up an already suspended/hibernated/powered off computer.

My suggestion is, disable power management and run a background script that checks the status of network connections (e.g. netstat -t | grep ESTABLISHED assuming it's a TCP connection), and suspends the server (pm-suspend) after a pre-determined timeout.  With this approach you'd still be able to wake your server remotely with WOL.

---

### Post by bilboubu on 2012-10-31
Thanks I've found these for starters:
 
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2][http://www.linuxquestions.org/questions/linux-server-73/auto-suspend-for-my-home-server-730037/](http://www.linuxquestions.org/questions/linux-server-73/auto-suspend-for-my-home-server-730037/)
 
[http://aikar.co/2011/03/03/ubuntu-prevent-sleep-samba/](http://aikar.co/2011/03/03/ubuntu-prevent-sleep-samba/)
 
[http://www.pcmediacenter.com.au/forum/topic/42184-idle-network-traffic-script-to-suspend-bedroom-frontend/](http://www.pcmediacenter.com.au/forum/topic/42184-idle-network-traffic-script-to-suspend-bedroom-frontend/)
 
[http://forums.opensuse.org/english/get-technical-help-here/applications/471611-power-management-kicks-when-shouldnt-network-active.html](http://forums.opensuse.org/english/get-technical-help-here/applications/471611-power-management-kicks-when-shouldnt-network-active.html)
 
[http://ubuntuforums.org/showthread.php?t=2017336](http://ubuntuforums.org/showthread.php?t=2017336)
 
To my untrained eye not sure which looks best? There are no shares on this particular machine in use so base on smb access I dont think is an option.
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by aromo on 2012-10-31
First thing you need to do is define what means idle to you: no connection? or no network activity?

If you want to suspend after some time without an active connection, nestat -t|grep ESTABLISHED will do the trick.  If you want to suspend after a period of no network activity, then ethtool -S eth0|grep tx_bytes would work.

Once you define what for you will count as idle time, you create a script like this:
```
#!/bin/bash
if [ IS_IDLE ]; then
[INDENT]if [ -f /tmp/idle.tmp ]; then
[INDENT]rm -f /tmp/idle.tmp
pm-suspend[/INDENT]
else
[INDENT]echo 1 > /tmp/idle.tmp[/INDENT]
fi[/INDENT]
else
[INDENT]rm /tmp/idle.tmp[/INDENT]
fi

```
and add that script to your crontab every (30 minutes) to guarantee you have at least 30 minutes idle time before it suspends.

---

### Post by bilboubu on 2012-10-31
Excellent thank you, looking at the netstat out put I need to check for

tcp        0      0 htpc.local:9982         192.168.0.4:59455       ESTABLISHED

specifically 9982 with any 192.168.0.* client rather than just ESTABLISHED, is this possible?

---

### Post by bilboubu on 2012-10-31
So this:

```
#!/bin/bash
if [ netstat -t|grep "9982         192.168.0.*ESTABLISHED" ]; then
if [ -f /tmp/idle.tmp ]; then
rm -f /tmp/idle.tmp
pm-suspend
else
echo 1 > /tmp/idle.tmp
fi
else
rm /tmp/idle.tmp
fi
```

?

---

### Post by bilboubu on 2012-10-31
Actually thinking about it, no because I dont want it to suspend if I am watchin locally which it would with this, hmmmmm

---

### Post by bilboubu on 2012-11-01
Ok I think I have worked out what I need to grep for but I dont know how  :)

from the below output:
billy@htpc:~/bin$ netstat -t
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 htpc.local:40581        192.168.0.2:mysql       TIME_WAIT
tcp        0      0 htpc.local:50767        htpc.local:9982         ESTABLISHED
tcp        0      0 htpc.local:40575        192.168.0.2:mysql       TIME_WAIT
tcp        0      0 htpc.local:38226        192.168.0.:microsoft-ds ESTABLISHED
tcp        0      0 htpc.local:9982         htpc.local:50767        ESTABLISHED
tcp        0      0 htpc.local:40578        192.168.0.2:mysql       TIME_WAIT
tcp        0      0 htpc.local:38228        192.168.0.:microsoft-ds ESTABLISHED

I need to grep for 4 or more instances of port 9982 OR 192.168.0.*ESTABLISHED

edit
netstat -t|grep -P (9982){4,}  
netstat -t|grep -P 192\.168\.0\.

will do it, if either match dont suspend, how to script this?
Please assist.

---

### Post by bilboubu on 2012-11-02
I have this but I need to fix the ifs any advice?

```
#!/bin/bash
sleep 30


if [ `netstat -t | grep -c ":9982"` -ge 3 ]
then
      echo live tv
elif [ `netstat -t | grep -c "192.168.0.:microsoft-ds ESTABLISHED"` -ne 0 ]
then
      echo media playing
elif
cd ~billy/.hts/tvheadend/dvr/log
current_date=`date +%s`

for i in $( ls ); do
tmp_start=`cat $i | grep '"start":' | cut -f 2 -d " " | cut -f 1 -d ","`
tmp_stop=`cat $i | grep '"stop":' | cut -f 2 -d " " | cut -f 1 -d ","`

if [ $((tmp_stop)) -gt $((current_date)) -a $((tmp_start)) -lt $((current_date)) ]; then
 echo recording in progress
done
else
      echo pm-suspend
fi
fi
```

---

