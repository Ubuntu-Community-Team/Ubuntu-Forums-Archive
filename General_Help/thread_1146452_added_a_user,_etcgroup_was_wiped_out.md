---
title: "added a user, /etc/group was wiped out"
date: 2009-05-02
forum: General Help
---

### Post by jhodges on 2009-05-02
Hi, I'm using Intrepid 64-bit.. yesterday I tried adding a user using the gui users/groups interface. After adding the user, I soon found that I was no longer in the sudoers file. I managed to get myself back in there, but found that all of the groups that were in /etc/group are gone. looking at the password file, I find that all the system users are now in "nogroup" instead of the group that they should be in.

So this has caused quite a few problems - intially I couldn't start gdm and was getting a number of other errors on startup, which I resolved by adding those groups manually, but there are still some issues - notably, I can't get the network to work at all. 

Is there anyway I can restore to previous group settings easily without having to track down and fix each problem one at a time? Any general advice besides "don't use the users and groups gui?"

Thanks, Jesse

---

### Post by unutbu on 2009-05-02
Can you use sudo now?
How many users did you create? 
What were there names? (The order in which they were created is important, so try to recall that too if you can).

I might be able to recreate a basic /etc/group and /etc/gshadow files for you...

---

### Post by jhodges on 2009-05-02
I can sudo now.

I added one user / one group (splunk:splunk)

---

### Post by unutbu on 2009-05-02
Please post the output
```
awk 'BEGIN{FS=":"}{print $1,$3}' /etc/passwd
```

---

### Post by jhodges on 2009-05-02
yeah, that's not looking too likely. I've been at it for 30 minutes now, no luck. As I said, the network isn't working, and I tried a flash drive - which is recognized but won't open - I tried burning a cd with the info and got some vague errors. 

If it's really necessary I'll copy it by hand, let me know.

---

### Post by unutbu on 2009-05-02
If you boot from a LiveCD, you can make the following repairs from there. You might find that a bit easier, since more programs should work as expected. If you that it that way and mount your Linux partition at /mnt, then you'll need to edit /mnt/etc/group and /mnt/etc/gshadow...

Here are basic /etc/group and /etc/gshadow files. Depending on what additional packages you've installed (like exim4 or mysql-server), there might be other groups that should be here but aren't. That was the purpose of the awk command -- to hint at what extra groups should be added. Nevertheless, making your /etc/group and /etc/gshadow look like this should help:

/etc/group:
```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:splunk
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:splunk
fax:x:21:
voice:x:22:
cdrom:x:24:splunk
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:splunk
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:
nvram:x:105:
messagebus:x:106:
fuse:x:107:
polkituser:x:108:
ssl-cert:x:109:
lpadmin:x:110:splunk
crontab:x:111:
mlocate:x:112:
ssh:x:113:
avahi-autoipd:x:114:
avahi:x:115:
netdev:x:116:
gdm:x:117:
haldaemon:x:118:
admin:x:119:splunk
pulse:x:120:
pulse-access:x:121:
pulse-rt:x:122:
saned:x:123:
splunk:x:1000:
sambashare:x:124:splunk

```
```

sudo chmod 644 /etc/group
sudo chown root:root /etc/group
```


/etc/gshadow:
```
root:*::
daemon:*::
bin:*::
sys:*::
adm:*::splunk
tty:*::
disk:*::
lp:*::
mail:*::
news:*::
uucp:*::
man:*::
proxy:*::
kmem:*::
dialout:*::splunk
fax:*::
voice:*::
cdrom:*::splunk
floppy:*::
tape:*::
sudo:*::
audio:*::pulse
dip:*::
www-data:*::
backup:*::
operator:*::
list:*::
irc:*::
src:*::
gnats:*::
shadow:*::
utmp:*::
video:*::
sasl:*::
plugdev:*::splunk
staff:*::
games:*::
users:*::
nogroup:*::
libuuid:!::
syslog:!::
klog:!::
scanner:!::
nvram:!::
messagebus:!::
fuse:!::
polkituser:!::
ssl-cert:!::
lpadmin:!::splunk
crontab:!::
mlocate:!::
ssh:!::
avahi-autoipd:!::
avahi:!::
netdev:!::
gdm:!::
haldaemon:!::
admin:!::splunk
pulse:!::
pulse-access:!::
pulse-rt:!::
saned:!::
splunk:!::
sambashare:!::splunk
```
```

sudo chmod 640 /etc/gshadow
sudo chown root:shadow /etc/gshadow
```

---

### Post by jhodges on 2009-05-07
I attempted to munge together the groups file based on what you posted plus what my /etc/passwd file contained, but am still having the same issues. If you don't mind, can you recommend a group file based on this?

```
root 0
daemon 1
bin 2
sys 3
sync 4
games 5
man 6
lp 7
mail 8
news 9
uucp 10
proxy 13
www-data 33
backup 34
list 38
irc 39
gnats 41
nobody 65534
dhcp 100
syslog 101
klog 102
messagebus 103
hplip 104
avahi-autoipd 105
avahi 106
haldaemon 107
gdm 108
jesse 1000
libuuid 109
pulse 110
polkituser 111
saned 112
landscape 113

```

---

### Post by unutbu on 2009-05-07
Okay, it has finally occurred to me that /etc/password holds the correct group id numbers.
For example, both your system and mine share this line in common:

```
man:x:6:**12**:man:/var/cache/man:/bin/sh
```

The 12 is man's group id. More generally, the number in the 4th column of the colon-separated list is the group id. So /etc/group should contain

```
man:x:12:
```

and /etc/gshadow should contain
```

man:*::
```

This may not be perfect but it should bring you closer to a working system.

Note: You might have a few entries in /etc/password that have very high group id numbers:
```

sync:x:4:65534:sync:/bin:/bin/sync
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
sshd:x:114:65534::/var/run/sshd:/usr/sbin/nologin
```
Ignore these. They do not have corresponding entries in /etc/group nor /etc/gshadow.

---

### Post by jhodges on 2009-05-08
everything seems to be in order now with the groups and gshadow, but it didn't fix the networking issue. I wonder if something else got changed? Also my computer now calls itself localhost.localdomain, so it does seem like something in the network got reset.

---

### Post by unutbu on 2009-05-08
The machine's hostname is configurable by editing /etc/hostname.
Also edit /etc/hosts so that hostname is an alias for 127.0.0.1. 

Does the machine recognize your network interface card (NIC)? An indication of that would be if the lights on the NIC start blinking during boot time.

If you get lights, it means a reasonable driver for your NIC is installed.

The next step is to configure /etc/network/interfaces. There are GUIs for this, e.g. Network Manager and wicd. Or you can just edit /etc/network/interfaces directly. If you are having problems here, describe what choice you've made (Network Manager, wicd or manual edit, and if you are going for a DHCP or static connection). Post /etc/network/interfaces too.

The third step is to check /etc/resolv.conf. It must supply the IP address of a domain name server. Depending on your situation and ISP, this might just be the IP of your router. For example,
```

nameserver 192.168.1.1
```

The fourth step is to reboot, because I've found (at least for my setup), the configuration files must be in place at the time of boot in order for the NIC to work.

If, after reboot, the NIC still does not work, also post the output of 
```

ifconfig
route
```

And if you are using wireless, also post:
```
iwconfig   
iwlist scan  
```

---

### Post by jhodges on 2009-05-09
Well, there are some differences in the config and what, for example the live cd configs, but it seems that the main difference is that with the liveCD I can connect to the correct network (AirHodges) and with my regular install i can't, as the network manager applet is gone. It might just be that I need to tell it to connect to the proper network, though when I look at the network config, the airHodges connection is configured and set to auto-connect.

---

### Post by jhodges on 2009-05-09
there's evidence in syslog files that it keeps trying to start the networkManager applet

for example I see these every 2 minutes :

```
syslog.0:May  7 21:17:02 thor-lx64 NetworkManager: <info>  Trying to start the supplicant... 
syslog.0:May  7 21:17:02 thor-lx64 NetworkManager: <info>  Trying to start the system settings daemon...
```

here's more detail:

```
May  7 21:17:02 thor-lx64 NetworkManager: <info>  Trying to start the supplicant...
May  7 21:17:02 thor-lx64 NetworkManager: <info>  Trying to start the system settings daemon...
May  7 21:17:03 thor-lx64 vmnetBridge: RTM_NEWLINK: name:ath0 index:4 flags:0x00001003
May  7 21:17:03 thor-lx64 vmnetBridge: Can't remove interface ath0 4 (does not exist).
May  7 21:17:03 thor-lx64 vmnetBridge: RTM_NEWLINK: name:ath0 index:4 flags:0x00011003
May  7 21:17:03 thor-lx64 vmnetBridge: Can't remove interface ath0 4 (does not exist).
May  7 21:17:03 thor-lx64 vmnetBridge: RTM_NEWLINK: name:ath0 index:4 flags:0x00011043
May  7 21:17:03 thor-lx64 vmnetBridge: Started bridge ath0 to virtual network 0.
May  7 21:17:03 thor-lx64 kernel: [ 2783.058412] /dev/vmnet: open called by PID 6040 (vmnet-bridge)
May  7 21:17:03 thor-lx64 kernel: [ 2783.058430] /dev/vmnet: hub 0 does not exist, allocating memory.
May  7 21:17:03 thor-lx64 kernel: [ 2783.058441] /dev/vmnet: port on hub 0 successfully opened
May  7 21:17:03 thor-lx64 kernel: [ 2783.058451] bridge-ath0: can't bridge with ath0, bad header length 88
May  7 21:17:03 thor-lx64 kernel: [ 2783.058455] bridge-ath0: enabling the bridge
May  7 21:17:03 thor-lx64 kernel: [ 2783.058458] bridge-ath0: can't bridge with ath0, bad header length 88
May  7 21:17:03 thor-lx64 kernel: [ 2783.058460] bridge-ath0: interface ath0 is not a valid Ethernet interface
May  7 21:17:03 thor-lx64 kernel: [ 2783.058467] bridge-ath0: attached
May  7 21:17:04 thor-lx64 vmnetBridge: RTM_NEWLINK: name:ath0 index:4 flags:0x00001043
May  7 21:17:04 thor-lx64 vmnetBridge: Can't add interface ath0 4 (does exist).
May  7 21:17:04 thor-lx64 vmnetBridge: RTM_NEWLINK: name:ath0 index:4 flags:0x00001003
May  7 21:17:04 thor-lx64 vmnetBridge: Stopped bridge ath0 to virtual network 0.
May  7 21:17:04 thor-lx64 kernel: [ 2784.353328] bridge-ath0: enabling the bridge
May  7 21:17:04 thor-lx64 kernel: [ 2784.353337] bridge-ath0: can't bridge with ath0, bad header length 88
May  7 21:17:04 thor-lx64 kernel: [ 2784.353340] bridge-ath0: interface ath0 is not a valid Ethernet interface
May  7 21:17:04 thor-lx64 kernel: [ 2784.353448] bridge-ath0: detached
May  7 21:17:11 thor-lx64 vmnetBridge: RTM_NEWLINK: name:ath0 index:4 flags:0x00001003

```

---

### Post by unutbu on 2009-05-10
Perhaps try using this guide to setup the connection
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by jhodges on 2009-05-14
Thanks for all your help. I eventually was able to get it all working again by copying /etc/group, /etc/shadow, /etc/gshadow, and /etc/passwd from the live cd, then switching the ubuntu user for myself. 

Everything appears to be working fine now.

---

