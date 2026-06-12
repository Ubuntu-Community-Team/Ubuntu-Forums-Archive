---
title: "Cannot connect to ftp server using gnome-commander"
date: 2006-12-05
forum: Desktop Environments
---

### Post by yusufk on 2006-12-05
Hi,

I can't connect to any ftp servers using gnome-commander. It just shows "connecting to..." all the time. I used wireshark to trace the network activity and it seems like its not even attempting the connection. I also tried showing debug info ( -d=m ) which shows nothing.

Oh, I can connect using commandline ftp without a problem.

Any ideas?

p.s. I suspect that it may have something to do with vfs ftp, because the "Connect to Server" app also fails to connect to any FTP server I specify.

Y

---

### Post by paparucino on 2006-12-05
> **yusufk said:**
> Hi,

I can't connect to any ftp servers using gnome-commander. It just shows "connecting to..." all the time. I used wireshark to trace the network activity and it seems like its not even attempting the connection. I also tried showing debug info ( -d=m ) which shows nothing.
I used it a few minutes ago and it works without any problem.
I tried with the normal connection and with quick connection.
Try with quick connection. It is setted for ftp.gnome.org and it works :-)

> 
Oh, I can connect using commandline ftp without a problem.

Try with gftp.

---

### Post by yusufk on 2006-12-06
Hi,

I've tried both options (Quick and normal) and no luck, nor does Places-->Connect to Server work.

GFTP works fine, but I'd really like to get Gnome Commander working with FTP.

Any ideas?

Where are the config and/or log files for VFS ?

---

### Post by yusufk on 2006-12-06
Ok, finally some progress...

It's working now, the problem was proxy settings.

I use ntlmaps to get through the company proxy server.

Therefore my gnome ftp proxy settings were showing localhost 5865.

I just disabled the the proxy and voila, it works.

However, the ftp server I'm connecting to is on the LAN, connecting to outside servers will still need to go through ntlmap and there seems to be an issue there, but I'll cross that bridge when I get there...

Thanks

---

