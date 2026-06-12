---
title: "Samba Linux &lt;-&gt; WinXP + Crossover cable"
date: 2005-11-02
forum: Desktop Environments
---

### Post by jax2000 on 2005-11-02
I have set up a simple filesharing network between my WinXP and Linux boxes with 2 NIC ( ubuntu ) 1 NIC ( WinXP ) + Crossover cable... Everything works just fine but everytime I reboot my computer ( ubuntu ) I'll have to Deactivate/Activate my second NIC that connects these two machines with eachother. This is pretty annoying to do everytime I boot. Please help

---

### Post by everdred on 2005-12-05
I don't have a solution for you, but rather, a question... how did you get it working over a crossover cable? I'm able to connect to Windows shares using Samba over a more traditional LAN, but it simply won't work for me over my crossover cable (which definitely works in other cases, like XP -> XP).

---

### Post by Fireal on 2006-10-09
(Bump) This is a great question, anyone have a link?  I tried the same thing with no success.

---

### Post by acegolfer on 2006-10-31
Another bump. I'm trying connecting Ubuntu desktop with WinXP laptop using crossover cable. I tried switch/hub but failed.

---

### Post by dbott67 on 2006-10-31
Make sure that you've assigned static IP addresses to each NIC.  They also need to be on the same subnet:
  - XP: 192.168.1.100
  - UB: 192.168.1.101
The subnet mask on both should be 255.255.255.0
The gateway isn't required in this case, as there aren't any other computers to connect to.

Try pinging ***both IP addresses*** from ***both computers***:

```
ping 192.168.1.100
```
```
ping 192.168.1.101
```

This will verify that the local & remote IP addresses are reachable.

If you're still having issues, post the output of **ifconfig** (Ubuntu) and **ipconfig -all**(XP), as well as the output from the ping commands.

-Dave

---

### Post by chikin03 on 2007-10-16
<bump>

I have 2 wireless computers, and am trying to bridge them with a crossover cable  (client windows, server ubuntu) to share a disk.  Really, this is just a sharing a drive on the network.  How come this is so hard?!

I have Samba installed, and have tried to use gsambad to configure the sharing.  There are several problems that pop up, including: 

(gsambad:12589): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

and the fact that whenever I "activate" it goes back to deactivate in the next 10s.

I don't want to share homes, I just have a single computer with a static IP that I want to speed the connection to.

Right now, they are both in the same workgroup (MSHOME), but the windows cannot see the ubuntu computer, at all.

Here is my smb.conf:
```
[global]
netbios name = chikinkoop
server string = comment
workgroup = MSHOME
hosts allow = 192.168.0.0/24
printcap name = /etc/printcap
load printers = yes
printing = cups
cups options = raw
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
security = user
username level = 8
password level = 8
username map = /etc/samba/smbusers
add user script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
smb passwd file = /etc/samba/smbpasswd
encrypt passwords = yes
unix password sync = yes
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*\n
null passwords = no
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
interfaces = 127.0.0.1/8 192.168.0.0/24 
remote browse sync = 192.168.0.255 192.168.0.3 192.168.5
remote announce = 192.168.0.255 192.168.0.1 192.168.5
local master = no
os level = 33
domain master = no
preferred master = no
time server = no
domain logons = no
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
name resolve order = wins lmhosts bcast
wins support = no

wins proxy = no
dns proxy = no
preserve case = no
winbind use default domain = yes
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null

[Testing]
path = /media/disk-2
comment = testingasd
valid users = chikin
write list =
admin users = chikin
read only = no
available = yes

writable = yes
guest ok = no
public = yes
printable = no
share modes = no
locking = no
browsable = yes
```

Both computers can connect to the internet (and my router) via wireless.  For now, I have chosen to "bridge" the two connections on the windows computer, thinking the devices are sort of equivalent.  I can ping the static IP of the other computer.  Does anyone have any ideas?

---

