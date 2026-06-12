---
title: "freenx client problems (yes, i searched the forums, and google)"
date: 2006-07-04
forum: Desktop Environments
---

### Post by xela321 on 2006-07-04
I am having problems connecting to my dapper box from my server2k3 machine.  I dont get any error messages, the client connects, but there is no window displayed.  the tasks for nx client are still running, and the matching tasks on the server are also running.  however, there is nothing on the display.

any suggestions?

---

### Post by harisund on 2006-07-05
I am having the exact same problems. I posted on the forums with no reply too :)(

---

### Post by atoponce on 2006-07-05
[quote=xela321]I am having problems connecting to my dapper box from my server2k3 machine.  I dont get any error messages, the client connects, but there is no window displayed.  the tasks for nx client are still running, and the matching tasks on the server are also running.  however, there is nothing on the display.

any suggestions?[/quote]
So are you trying to view files in the window manager, remote desktop, SSH, FTP, what?  How _exactly_ are you trying to connect?  What services are running?

---

### Post by atoponce on 2006-07-05
My apologies.  You are running Freenx.  (Maybe I should pay more attention to the title :) )

Here is a howto that I found.  Maybe it will help: [http://www.snakeoillabs.com/2005/10/27/freenx-on-ubuntu-breezy-howto/]("http://www.snakeoillabs.com/2005/10/27/freenx-on-ubuntu-breezy-howto/")

---

### Post by matcram on 2006-07-13
Hi all,

i had the same problem as described above. Very frustrating since the server seems to be running fine just like the client on my windows machine... Anyway

I checked the log of my connection and it looks like i have been installing the server V1.5 and the client V2.0 so nothing worked

Solution ?
Install V2 on your server.
OR
Download V1.5 of the client from their server (WARNING : it looks like there is no direct link to the 1.5. Only 2.0. I advise you to upgrade to V2.0)

[http://64.34.161.181/download/1.5.0/client/nxclient-1.5.0-138.exe](http://64.34.161.181/download/1.5.0/client/nxclient-1.5.0-138.exe)

---

### Post by rootberg on 2006-07-20
Yes!! You saved my day, litteraly :D
I can now connect using the old client. If any one would like to give me a quick guide how to upgrade the server to 2.0 I would love it... But I'm happy running 1.5 aswell.
Thanks alot!!

---

