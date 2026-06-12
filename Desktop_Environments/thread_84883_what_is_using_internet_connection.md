---
title: "what is using internet connection?"
date: 2005-11-01
forum: Desktop Environments
---

### Post by danpre on 2005-11-01
I use Ubuntu Breezy 5.10.
I have internet connection and use wifi.

Every 2-3 minutes something is using all internet bandwith for about 10-20 seconds (I use gkrellm monitor).

All programs are turned off.

How to check what is going on?

---

### Post by MrCheese on 2005-11-01
try [http://www.ubuntuguide.org/#firestarter]("http://www.ubuntuguide.org/#firestarter") and the following sections on how to secure your network. Check that you don't have any mail collection daemons (fetchmail for instance) running in the background or your mail client set to sync every few minutes.

---

### Post by danpre on 2005-11-01
[QUOTE=MrCheese]try [http://www.ubuntuguide.org/#firestarter]("http://www.ubuntuguide.org/#firestarter") and the following sections on how to secure your network. Check that you don't have any mail collection daemons (fetchmail for instance) running in the background or your mail client set to sync every few minutes.[/QUOTE]

No, I don't have any daemons, and my mail client and instant messenger are not running.

---

### Post by NewWithoutClue on 2005-11-01
Gkrellm has an option and/or a plugin that allows others ( you ) to connect to it and get system stats...
do a 'netstat -l -np -p' to show open ports and the files that own them ( look in tcp )

Regards,
Paul.

---

### Post by danpre on 2005-11-01
[QUOTE=NewWithoutClue]Gkrellm has an option and/or a plugin that allows others ( you ) to connect to it and get system stats...
do a 'netstat -l -np -p' to show open ports and the files that own them ( look in tcp )

Regards,
Paul.[/QUOTE]

output fot netstat -l -np -p is:

root@danpre:/home/danpre# netstat -l -np -p
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:68              0.0.0.0:*                          6217/dhclient3
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     8138     6572/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     8064     6525/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     10433    7290/dbus-daemon    @/tmp/dbus-DZ2grbisXu
unix  2      [ ACC ]     STREAM     LISTENING     8154     6585/hald           @/tmp/hald-local/dbus-M4eFBmcxHV
unix  2      [ ACC ]     STREAM     LISTENING     9528     6928/gdm            /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     9911     7003/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     10428    7286/ssh-agent      /tmp/ssh-jrDucg7245/agent.7245
unix  2      [ ACC ]     STREAM     LISTENING     10445    7298/esd            /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     10491    7300/xfce4-session  /tmp/.ICE-unix/7300

---

### Post by danpre on 2005-11-01
I have checked with IPTRAF

Statistics for wlan0:
There is almoust nothing for TCP but there is a lot of incoming activity for UDP.

---

### Post by l33tc0d34 on 2005-11-01
my web browser and email use the internet. maybe you too? i can't use now tho because i have a black screen after installing ubuntu linex. can u help?

---

### Post by NewWithoutClue on 2005-11-01
[QUOTE=danpre]output fot netstat -l -np -p is: root@danpre:/home/danpre# netstat -l -np -p Active Internet connections (only servers) Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name udp 0 0 0.0.0.0:68 0.0.0.0:* 6217/dhclient3 Active UNIX domain sockets (only servers) Proto RefCnt Flags Type State I-Node PID/Program name Path unix 2 [ ACC ] STREAM LISTENING 8138 6572/dbus-daemon /var/run/dbus/system_bus_socket unix 2 [ ACC ] STREAM LISTENING 8064 6525/acpid /var/run/acpid.socket unix 2 [ ACC ] STREAM LISTENING 10433 7290/dbus-daemon @/tmp/dbus-DZ2grbisXu unix 2 [ ACC ] STREAM LISTENING 8154 6585/hald @/tmp/hald-local/dbus-M4eFBmcxHV unix 2 [ ACC ] STREAM LISTENING 9528 6928/gdm /tmp/.gdm_socket unix 2 [ ACC ] STREAM LISTENING 9911 7003/X /tmp/.X11-unix/X0 unix 2 [ ACC ] STREAM LISTENING 10428 7286/ssh-agent /tmp/ssh-jrDucg7245/agent.7245 unix 2 [ ACC ] STREAM LISTENING 10445 7298/esd /tmp/.esd-1000/socket unix 2 [ ACC ] STREAM LISTENING 10491 7300/xfce4-session /tmp/.ICE-unix/7300[/QUOTE] i don't need/use dhclient3, unless someone knows how to stop it from running at boot...i just kill it 'killall dhclient3' ( be root ) you may need it, i admit that i have no clue of it true functions. ( my net works fine without it presence ) Paul. w00t


EDIT: Don't worry much about UDP. I will not explain here, i suggest you read up on internet protocals, to get a good idea of whats actually happening.

---

### Post by danpre on 2005-11-03
I have started EtherApe

Every time when my internet connection is so busy, I see a picture like on the screenshot.

My ip is 172.16.1.2, I don't have any idea what is 172.16.250.123

Any ideas?

You can see on the right bottom - there is gkrellm running - and wlan0 connection is full for the last few seconds

---

### Post by mips on 2005-11-03
[QUOTE=danpre]I have started EtherApe

Every time when my internet connection is so busy, I see a picture like on the screenshot.

My ip is 172.16.1.2, I don't have any idea what is 172.16.250.123

Any ideas?

You can see on the right bottom - there is gkrellm running - and wlan0 connection is full for the last few seconds[/QUOTE]

Well,  172.16.0.0 - 172.31.255.255 is a private address range, meaning it cannot come from the public Internet. So it is local to your LAN.

Something with address 172.16.250.13 is sending out broadcasts if i understand that diagram right, 172.16.250.255 is a broadcast address.

Somewhere on your local LAN is something with address 172.16.250.13, check your router, pc and any other device you might have connected.

---

### Post by danpre on 2005-11-03
[QUOTE=mips]Well,  172.16.0.0 - 172.31.255.255 is a private address range, meaning it cannot come from the public Internet. So it is local to your LAN.

Something with address 172.16.250.13 is sending out broadcasts if i understand that diagram right, 172.16.250.255 is a broadcast address.

Somewhere on your local LAN is something with address 172.16.250.13, check your router, pc and any other device you might have connected.[/QUOTE]

do you mean that 172.16.250.13, could be computer which is constantlly traing ping me or scan my ports? Could it be windows computer with virus?

I don't know any adresses in my network - I have internet access from cable tv, IP from dhcp. So I don't know what 172.16.250.13 is.

---

### Post by danpre on 2005-11-03
I have wrote to my InternetProvider.
Maybe they can solve this.

---

### Post by NewWithoutClue on 2005-11-03
Doesn't sound like broadcast packets at all; he said it stays active for about 10-20 seconds. Mine lasts for maybe 3 seconds.

Paul.

---

