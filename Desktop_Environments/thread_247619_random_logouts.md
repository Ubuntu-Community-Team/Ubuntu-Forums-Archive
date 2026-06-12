---
title: "random logouts"
date: 2006-08-30
forum: Desktop Environments
---

### Post by hellfried on 2006-08-30
i have been experiencing random automatic logouts for the past few days. first i lose audio playing flash animations and youtube videos then when my pc is idling it automatically logs out and i have to relog in again. the worse part is all the downloads that i am doing using firefox dies too and i have to start all over again. this is frustrating as i am downloading images of other linux distros and they are huge. 
many other posters in this forum have said to look at the files in /var/log but what i am i supposed to be looking for?!
i am running dapper on a pc that has 1G of ram and a pentium d cpu.


updated:
i poked around in /var/log and this could be the problem. i really am not sure but could anybody care to comment?


Aug 31 10:13:20 localhost gconfd (hellfried-5197): GConf server is not in use, shutting down.
Aug 31 10:13:20 localhost gconfd (hellfried-5197): Exiting
Aug 31 10:22:22 localhost gconfd (hellfried-17784): starting (version 2.14.0), pid 17784 user 'hellfried'
Aug 31 10:22:22 localhost gconfd (hellfried-17784): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 31 10:22:22 localhost gconfd (hellfried-17784): Resolved address "xml:readwrite:/home/hellfried/.gconf" to a writable configuration source at position 1
Aug 31 10:22:22 localhost gconfd (hellfried-17784): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug 31 10:22:22 localhost gconfd (hellfried-17784): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 31 10:22:22 localhost gconfd (hellfried-17784): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 31 10:22:25 localhost gconfd (hellfried-17784): Resolved address "xml:readwrite:/home/hellfried/.gconf" to a writable configuration source at position 0
Aug 31 10:35:03 localhost kernel: [17196935.996000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.4 DST=239.255.255.250 LEN=129 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=8008 DPT=1900 LEN=109 
Aug 31 10:35:05 localhost kernel: [17196937.524000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.4 DST=239.255.67.250 LEN=185 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=32977 DPT=16680 LEN=165 
Aug 31 10:35:21 localhost kernel: [17196953.644000] Inbound IN=eth0 OUT= MAC= SRC=192.168.1.4 DST=239.255.67.250 LEN=160 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=UDP SPT=32977 DPT=16680 LEN=140 
Aug 31 10:52:16 localhost -- MARK --



something in the 3rd line just doesn't seem right. the reason for saying so is that in other entries before this it just says:

Aug 31 06:54:06 localhost gconfd (root-10175): GConf server is not in use, shutting down.
Aug 31 06:54:06 localhost gconfd (root-10175): Exiting
Aug 31 06:54:57 localhost gconfd (root-10395): starting (version 2.14.0), pid 10395 user 'root'

---

