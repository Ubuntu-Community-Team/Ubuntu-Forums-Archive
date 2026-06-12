---
title: "System won't boot stops at mounting root filesystem"
date: 2006-07-13
forum: Desktop Environments
---

### Post by mooseman089 on 2006-07-13
Alright I have a 1tb ubuntu backup server (4x 250gb sata seagate drives) its mobo is a ECS Nforce4-A754 I came down to the basement to check on everything yesterday and when I moved the mouse it wouldn't take the monitor out of standby like normal but when on my windows box I was able to vnc in but it was obvious something was defiently wrong (besides the fact the monitor didnt work) like my sensors applet in my gnome panel wasnt showing the 4 drives with their temps like it normally does and the connection keep dropping so I eventually got it to ssh in and did a reboot but that didn't work. I went down there it was doing something crazy (i dont remember the messages) so this time I rebooted and i stayed there to watch and on the second item (mounting root filesystem) it never went further and starting doing that crazying thing that defiently seemed to related to the sata drives. Right now I have the system running a knoppix 3.9 live cd (I know there is newer verisons but 5.0.1 doesn't even seem to see all the drives) and the ubuntu live cd didn't work I'm trying to burn critical files to dvds (this is the backup server) but I can't move big files like /var/log/auth.log and stuff but I did look at syslog and its filled with 
```
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Primary device added
ata1: command 0x35 timeout, stat 0x58 host_stat 0x21
nv_sata: Primary device added
nv_sata: Primary device removed
nv_sata: Secondary device added
nv_sata: Secondary device removed
``` it keeps going with that loop and I have checked all cables but I did notice knoppix won't mount drive 3 but the main drive (drive 2, don't ask why its drive 2) appears to be visible and im still checking but if there is corruption it doesn't seem very extreme
Any ideas on what in the world could be going on or what happened?

---

### Post by mooseman089 on 2006-07-14
Does anybody have an idea on what could have happened or if there is a way to get ubuntu to boot again? I also noticed I can't seem to get knoppix to connect to my network at all and considering that error in the syslog's about nv_sata my first idea is something went wrong with my mobo. I was also wondering if there is a way to list the whole contents of a directory and all its subdirectorys so I would have a file list of the drives and a way to see all the programs I downloaded and installed with synaptic so I can get them again once I reinstall ubuntu
Edit: I just noticed that the /proc folder is totally empty is that normal or could that be part of the problem?

---

