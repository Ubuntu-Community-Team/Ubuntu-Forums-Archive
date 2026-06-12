---
title: "NX Nomachine on alt port not working"
date: 2008-12-09
forum: General Help
---

### Post by elbeano on 2008-12-09
I can't connect to my nxserver on an alternative port from outside the LAN. What I did:

1. Setup NX nomachine on machine at work, using port 22.
2. Did a keygen to secure things a bit.
3. Set up my Hardy Heron computer at home to access work computer, including new key (used instructions from nomachines Administrator's guide). Worked great.
4. Changed the port on the work computer, edited files as follows:


[INDENT]Modify /usr/NX/etc/server.cfg

    * Change #SSHDAuthPort = "22"
    * To SSHDAuthPort = "2200"

Modify /usr/NX/etc/node.cfg

    * Change #SSHDPort = "22"
    * To SSHDPort = "2200"
[/INDENT]

After making changes, I can SSH into work computer from outside. I can SSH and use an nxclient inside the LAN. Outside, I have no access to nxserver.

---

### Post by elbeano on 2008-12-16
I decided to start from scratch with a new install to try to resolve this. That turned out to be less easy than I liked. I used: 

dpkg -r nxserver
dpkg -r nxnode
dpkg -r nxclient

Then I still needed to go in and manually delete files from my home folder and from \usr to complete the process. Otherwise, I still ended up with the client failing to connect. After restoring the computer to its "prior to nx" state, I managed to get things working. I connected all around with the default key (I highly recommend doing this first) then I managed with the newly generated key and doing a switch away from port 22.

The issue resulted from authentication failure within the NX software. SSH authenticated fine, but NX server adds to this by looking for the matching key.

---

