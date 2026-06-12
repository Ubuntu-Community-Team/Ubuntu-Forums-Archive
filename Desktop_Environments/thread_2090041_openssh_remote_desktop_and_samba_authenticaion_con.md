---
title: "openssh remote desktop and samba authenticaion conflict?"
date: 2012-12-01
forum: Desktop Environments
---

### Post by hawaiiman on 2012-12-01
Server is 10.04 with gnome package added. Running samba file server, apache webpage host, and openssh. I can access the server with Bitvise ssh client from my home windows7 machine. I have xterm and sftp functioning well, but can't get the remote desktop feature to go. The log shows a good connection , then 
`server rejected our attempt to open a remote 
desktop client-2-server connection from 127.0.0.1:49705 to 
192.168.1.10:3389, sent:0, received:0'
Interestingly, when I first got the ssh client running I was able to get the remote desktop up after installing xrdp package on the server. All was going well in this first session. I was working with some permissions in samba, when the destop froze. After a reboot the remote desktop never worked again despite a month or so of fiddling. I get the same result when attempting access from outside the network, or inside. Other ssh functions continue to work fine, as does the samba file server, and our apache hosted website. At this point I am using a password login as root, with intentions to tighten things up once I get everything working well.
I assume that since it worked once, and since all other functions seem to be ok, that port forwarding is not an issue. BTW the server is behind a Tenda w300d router which has port forwarding and qos functionality.

---

