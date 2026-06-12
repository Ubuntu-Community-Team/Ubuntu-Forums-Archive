---
title: "Problem Connecting to Personal Server (SSH)"
date: 2009-03-22
forum: General Help
---

### Post by cfree220 on 2009-03-22
Hi all,
I run a personal file server in my dorm room and store my music and video collection on it. Sometimes I am able to connect without any problems. I can log in and everything seems to be fine. Then I lose my connection. I can't say how long it takes, as it varies. When I try to reconnect, I get the following message:
> Could not display "sftp://binary-muse@muse.dyndns.ws/".
Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.

If I logout and sign in again, or reboot the computer, I am usually able to start the connection again. The error lists possible causes, but I'm still pretty new to Linux, and so they don't really point me to any likely problems based on my configuration. I'm pretty sure that the problem is not on the server end...

---

### Post by cfree220 on 2009-03-22
ok...
So, I tried opening the connection using a different client (filezilla). Worked fine. I then went back and tried with the connect to server feature, and this time it worked...

I'm not sure if this means that the problem is not a configuration thing and means that there is a problem at the network level, or what...

---

