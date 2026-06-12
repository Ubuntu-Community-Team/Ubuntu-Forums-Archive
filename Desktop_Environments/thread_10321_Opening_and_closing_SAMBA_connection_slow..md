---
title: "Opening and closing SAMBA connection slow."
date: 2005-01-06
forum: Desktop Environments
---

### Post by arx-lupus on 2005-01-06
Hi,

I am having a bit of an issue with using mounted samba shares in ubuntu. (Don't know if this is Ubuntu amd64 specific as that is the only install of Ubuntu I have)

Background info :
I have an establised samba server (redhat 9) which WinXP and linux clients can connect to fine. 

I have Ubuntu amd64 installed and working fine, I have a machine account setup on the samba server for the ubuntu machine.

The samba shares are mounted on boot. (fstab has same options as listed on a slackware PC that has no problems)

I can connect to the shares and do everything that I want to but there is a BIG but.

When opening a connection for a file i.e. dragging a file in nautilis from one window to another (both folders in the same samba share) it will take ages to start the transfer, transfer the file fine and then take ages to end the transfer.

I have tried this on command line and it is the same. To eliminate a network issue I have downloaded and uploaded the same 350Mb file through samba and ftp - ftp is fine but samba has the delay at the start of the transfer and also at the end.

If trying to extract tar files on the samba share it will delay at eachfile rather than at the start and end. 

I have check the samba logs on the server doing the 350Mb file transfer and the tar exraction and there is no unusual entries (same if done in WinXP, Slackware or Ubuntu)

smb.conf on the ubuntu machine isn;t and issue i don't think as I have tried it with the default one (edited for workgroup name) without a smb.conf and with a bare smb.conf.

Any ideas?

---

### Post by hardcandy on 2005-01-06
Some tips (the WinXP webclient slowed me down trying to connect directly to the XP machine):
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2531259](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2531259)

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html#id2599226](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html#id2599226)

---

### Post by arx-lupus on 2005-01-07
Thanks for the reply, I have had a look at those pages and I can't find anything that would make the Ubuntu client have such a delay (the WinXP, and Slackware clients don't suffer from this delay.)

I have just installed 32bit Ubuntu on a laptop and that doesn't seem to have the problem either. Possibly a amd64 samba issue. Will plough on and do some more googling.

Arx

---

### Post by mark_lagace on 2005-01-07
I found a huge speed increase when I added my samba server and client addresses to my /etc/hosts file.

---

