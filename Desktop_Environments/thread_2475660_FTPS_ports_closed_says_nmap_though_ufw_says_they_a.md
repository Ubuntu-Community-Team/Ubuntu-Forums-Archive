---
title: "FTPS ports closed says nmap though ufw says they are open"
date: 2022-06-03
forum: Desktop Environments
---

### Post by johnaaronrose on 2022-06-03
I'm getting 'bounces' on ports 21 & 22 when I try to connect to vsftpd with FTPS on my Xubuntu server (named RoseServer) from my Ubuntu desktop (named Desktop).
On RoseServer, 'ufw status' displays:
21/tcp                     ALLOW IN    Anywhere                  
20/tcp                     ALLOW IN    Anywhere 
On RoseServer, 'nmap localhost' doesn't show ports 21 & 20.

RoseServer, has e.g. ports 22 & 80 (I use RoseServer as my web server running nginx) open according to nmap:
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
with confirmation by ufw:
22/tcp                     LIMIT IN    Anywhere                  
80,443/tcp (Nginx Full)    ALLOW IN    Anywhere                  

I'm baffled! Help please!

---

### Post by #&amp;thj^% on 2022-06-03
You may have other rules in place or no firewall rules at all. Since only SSH traffic is permitted in this case, we&#8217;ll need to add rules for FTP traffic.

Let&#8217;s open ports 20 and 21 for FTP, port 990 for when we enable TLS, and ports 40000-50000 for the range of passive ports we plan to set in the configuration file:

Go through this read, might help you: [https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-18-04)

---

### Post by deadflowr on 2022-06-03
ssh into it and check that the services are actually running.
ufw only deals with the rules you have set, but cares nothing about whether or not any services are running on those ports.
nmap shows the outputs for any services actually listening on those ports.

I don't know about ftps but vsftpd should be
```
systemctl status vsftpd
```

---

### Post by johnaaronrose on 2022-06-03
> **1fallen said:**
> You may have other rules in place or no firewall rules at all. Since only SSH traffic is permitted in this case, we’ll need to add rules for FTP traffic.

Let’s open ports 20 and 21 for FTP, port 990 for when we enable TLS, and ports 40000-50000 for the range of passive ports we plan to set in the configuration file:

Go through this read, might help you: [https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-set-up-vsftpd-for-a-user-s-directory-on-ubuntu-18-04)

I have iptable rules allowing in ports 21 & 20. 

Apologies, I forgot to attach logs from 'ufw status' and 'nmap localhost': for some strange reason, I was able to upload the nmap file but not the ufw file. I'll upload the ufw file in another post.

[ATTACH]290564[/ATTACH]

I've already seen above digitalocean link on setting up vsftpd. I've also looked at [https://linuxize.com/post/how-to-setup-ftp-server-with-vsftpd-on-ubuntu-20-04/](https://linuxize.com/post/how-to-setup-ftp-server-with-vsftpd-on-ubuntu-20-04/) and others.

---

### Post by johnaaronrose on 2022-06-03
Still can't attach ufw status results. So here it is:

Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), deny (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     LIMIT IN    Anywhere                  
51820/udp                  ALLOW IN    Anywhere                  
137,138/udp                ALLOW IN    Anywhere                  
139,445/tcp                ALLOW IN    Anywhere                  
21/tcp                     ALLOW IN    Anywhere                  
20/tcp                     ALLOW IN    Anywhere                  
990/tcp                    ALLOW IN    Anywhere                  
10001:10009/tcp            ALLOW IN    Anywhere                  
80,443/tcp (Nginx Full)    ALLOW IN    Anywhere                  
22/tcp (v6)                LIMIT IN    Anywhere (v6)             
51820/udp (v6)             ALLOW IN    Anywhere (v6)             
137,138/udp (v6)           ALLOW IN    Anywhere (v6)             
139,445/tcp (v6)           ALLOW IN    Anywhere (v6)             
21/tcp (v6)                ALLOW IN    Anywhere (v6)             
20/tcp (v6)                ALLOW IN    Anywhere (v6)             
990/tcp (v6)               ALLOW IN    Anywhere (v6)             
10001:10009/tcp (v6)       ALLOW IN    Anywhere (v6)             
80,443/tcp (Nginx Full (v6)) ALLOW IN    Anywhere (v6)             

20/tcp                     ALLOW OUT   Anywhere                  
21/tcp                     ALLOW OUT   Anywhere                  
990/tcp                    ALLOW OUT   Anywhere                  
10001:10009/tcp            ALLOW OUT   Anywhere                  
20/tcp (v6)                ALLOW OUT   Anywhere (v6)             
21/tcp (v6)                ALLOW OUT   Anywhere (v6)             
990/tcp (v6)               ALLOW OUT   Anywhere (v6)             
10001:10009/tcp (v6)       ALLOW OUT   Anywhere (v6)

---

### Post by johnaaronrose on 2022-06-03
It is running.

---

### Post by TheFu on 2022-06-03
FTPS has an issue in that the data port can be randomly assigned. This is why most people use sftp instead, which uses port 22/tcp by default, but you can change that to another port or use port translation in your router, if you prefer.

I see little reason for FTPS when there are other, firewall-friendly, protocols available like scp, sftp, and sshfs for our use.  And if you need to provide anonymous access, but want the privacy that an encrypted tunnel provides, then use https with TLS v1.3+.

---

### Post by #&amp;thj^% on 2022-06-03
> **TheFu said:**
> 
I see little reason for FTPS when there are other, firewall-friendly, protocols available like scp, sftp, and sshfs for our use.  And if you need to provide anonymous access, but want the privacy that an encrypted tunnel provides, then use https with TLS v1.3+.

+100

---

### Post by johnaaronrose on 2022-06-03
BTW the digital ocean has vsftpd.conf parameters of:
user_sub_token=$USER
local_root=/home/$USER/ftp

neither of which is listed in the Manpages for vsftpd at [http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

---

### Post by johnaaronrose on 2022-06-03
I want to use FTPS as that is the method that the B4X RAD tool uses to develop Android apps.

---

### Post by TheFu on 2022-06-03
Their forums have this:
```
SFTP.UploadFile(...)
Wait For SFTP_UploadCompleted (...)
```

[https://www.b4x.com/b4j/help/jsch.html#sftp_uploadfile](https://www.b4x.com/b4j/help/jsch.html#sftp_uploadfile)

But I understand the hesitancy to change.

---

