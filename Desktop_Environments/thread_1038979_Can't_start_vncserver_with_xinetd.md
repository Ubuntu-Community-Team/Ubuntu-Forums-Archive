---
title: "Can't start vncserver with xinetd"
date: 2009-01-14
forum: Desktop Environments
---

### Post by mang_ucup on 2009-01-14
I hope this is the best Categories for this post.

I had a problem with xinetd config file. I need to run vncserver command with xinetd but lead to no avail.
I able to run this command from console:
> vncserver :0 -name kde -geometry 1024x768 -depth 16 -httpport 5800
And now i need to add this command to xinetd so it'll run on startup. Here is my config file for xinetd.
> service vncserver
{
        type = UNLISTED
        disable = no
        socket_type = stream
        protocol = tcp
        wait = no
        user = afd
        server = /usr/bin/vncserver
        server_args = :0 -name kde -geometry 1024x768 -depth 16 -httpport 5800
        port = 5900
}
What i saw from netstat -tap, xinetd successful open the service port which is tcp 5900 but when i tried to remote with vncviewer... error came out saying "Invalid protocol".
> 
root# netstat -tap
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
[B]tcp        0      0 *:5900                  *:*                     LISTEN      28249/xinetd
[/B]
Anyone can help me?

---

