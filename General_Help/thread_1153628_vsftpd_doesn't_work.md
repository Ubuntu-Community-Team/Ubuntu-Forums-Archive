---
title: "vsftpd doesn't work"
date: 2009-05-08
forum: General Help
---

### Post by AboutToFly on 2009-05-08
I'm using Kubuntu Jaunty and I'm trying to set up an FTP server using vsftpd. When I try "ftp 127.0.0.1" from my desktop I am able to connect, but when I try "ftp mydomain.com" it hangs and then gives a "Connection timed out" message. Trying to connect from Windows, I get "Connected to mydomain.com" and then "Connection closed by remote host." I think it may be a firewall problem. I have a firewall in my router (it's a 2Wire Home Gateway) which I set to allow an FTP server, and I also set KMyFirewall to accept outgoing FTP connections. I'm also running an SSH server which works fine, it's just the FTP that doesn't seem to work. Can anyone help me out? Thanks.

---

### Post by soro2005 on 2009-05-09
You may have to set up port forwarding in the router. One thing is to let it pass the firewall, another thing is to forward the port to the server.

---

### Post by AboutToFly on 2009-05-09
I have the router set up to forward port 21 to my computer.

---

### Post by paradigm2 on 2009-05-09
What happens when you try to connect using:

```

ftp 192.168.1.25

```

(Insert your local address for the machine instead of 192.168.1.25)

Ftp may not be set to bind to any interface but the local interface, thus not being reachable by anything not on your computer (or tunneled over ssh).

---

### Post by AboutToFly on 2009-05-09
It still times out when I use my local IP address.

---

### Post by LiQuidAiR on 2009-05-10
Try adding two lines to your config file.


pasv_min_port=31000
pasv_max_port=32000

Don't forget to forward this range through your firewall.

The basic definition of pasv_min and pasv_max is located at the vsftpd website. [http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html).  Use the find function and type pasv_min to get to the first definition.

The actual definition for the usage of a passive mode connect is at [http://searchnetworking.techtarget.com/sDefinition/0,,sid7_gci512897,00.html#](http://searchnetworking.techtarget.com/sDefinition/0,,sid7_gci512897,00.html#).  

Pretty kewl stuff.

---

