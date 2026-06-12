---
title: "VNC over HTTPS using OpenSSL"
date: 2007-04-27
forum: Desktop Environments
---

### Post by shreeram13 on 2007-04-27
Hello Friends,

I am a Linux Newbie. I installed Ubuntu 7.04 Fiesty on my laptop and desktop. I do not want to install Ubuntu Server as of now. I am trying to configure VNC over HTTPS the reason for going in for such configuration is because I liked Ubuntu and would like to install it on my parents desktop which is in different country. I want to remotely manage the desktop over ssl using https so that there is no question of firewall and secondly its easy to manage.

I studied following 2 documentations and tried going step by step:

Post 1: [https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)
Post 2: [http://www-128.ibm.com/developerworks/linux/library/l-sslvnc.html?ca=dgr-lnxw16SSLVNC](http://www-128.ibm.com/developerworks/linux/library/l-sslvnc.html?ca=dgr-lnxw16SSLVNC)

From procedures given in Post 2 I was stuck at following location: 

**stunnel -d 5705 -r 5905 -p /etc/ssl/certs/stunnel.pem**

My error:
Apr 27 14:15:48 csi-laptop2 stunnel[17748]: Using '5905' as tcpwrapper service name
Apr 27 14:15:48 csi-laptop2 stunnel[17748]: /etc/ssl/certs/server.pem: No such file or directory (2)



But I was unable to start stunnel. I am stuck. Can someone tell me a any other way to do this or point to some or tutorial for VNC over SSL.

Please help me

With warm regards,

Harshal

---

### Post by jonj on 2007-12-11
Looks like either the SSL certificate is located in a different place to that in the example, or you still need to create the SSL certificate. There was some info here:

[http://www.ibm.com/developerworks/linux/library/l-sslvnc.html#sidebar](http://www.ibm.com/developerworks/linux/library/l-sslvnc.html#sidebar)

---

