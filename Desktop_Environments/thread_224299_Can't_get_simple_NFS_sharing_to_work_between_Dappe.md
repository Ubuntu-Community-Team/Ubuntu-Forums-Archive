---
title: "Can't get simple NFS sharing to work between Dapper live cd boots"
date: 2006-07-27
forum: Desktop Environments
---

### Post by guuuug on 2006-07-27
I can't seem to get NFS working between two dapper live cd boots.

I did the following.

Server:
- Insert CD and boot dapper.
- Open terminal and ran 'ifconfig', returning 192.168.1.15 (DHCP).
- Went to System-Administration-Shared Folders. Window popped up and I selected 'NFS to share folders with Unix/Linux systems'.
- After installing was done, I clicked on the 'Add' button and selected /home/ubuntu as 'Path'.
- I clicked on 'Add host' and selected 'Hosts in the eth0 network', left 'Read only' unchecked and clicked 'Ok'. Clicked 'Ok' in the 'Share folder' window and clicked 'Ok' once again in the 'Shared folders settings' window.
- In the terminal I ran 'sudo /etc/init.d/nfs-kernel-server restart', 'sudo /etc/init.d/nfs-common restart' and 'sudo exportfs -ra'
- Next I checked if nfs was running with 'rpcinfo -p'

Client:
- Insert CD and boot dapper.
- Open terminal and ran 'ifconfig', returning 192.168.1.17 (DHCP).
- Went to System-Administration-Shared Folders, just to install all the NFS stuff.
- Closed the 'Shared folders settings' window, without adding folder shares
- In the terminal I ran 'sudo mkdir /local'
- I checked if the client could see the server nfs with 'rpcinfo -p 192.168.1.15'
- and then 'sudo mount 192.168.1.15:/home/ubuntu /local' which returned 'mount: 192.168.1.15:/home/ubuntu failed, reason given by server: Permission denied'

I've been trying to get NFS working for 2 days now and I just don't seem to get it right. Please help this eediot.

---

### Post by rouben on 2006-12-21
Would you mind posting a copy of the /etc/exports file on your NFS server? Thanks!

I'm thinking this might be a problem with the GUI application that you used to set up the NFS shares.

---

