---
title: "vsftp Help"
date: 2006-02-19
forum: Desktop Environments
---

### Post by rado_london on 2006-02-19
Hi Today I installed and set up a ftp server. Its address is [ftp://82.2.252.160](ftp://82.2.252.160)


I would like to get two things.
First is to get an opportunity to log in as owner or anonymous from a firefox for example when I am at college I can add folders etc.

Also I would like to change that name to [ftp://radopetsov.org](ftp://radopetsov.org)


Thanks in Advance

---

### Post by darth_vector on 2006-02-19
the following link will help you set up anonymous ftp: [http://www.die.net/doc/linux/man/man5/vsftpd.conf.5.html](http://www.die.net/doc/linux/man/man5/vsftpd.conf.5.html)

for the other thing; do you own the domain radopetsov.org? if so, do you host the DNS records for it? if you own the domain, you will have to create a new record that maps radopetsov.org to 82.2.252.160

---

### Post by rado_london on 2006-02-19
I dont have any domain. How can I get a free one? Also what is that DNS linking etc.

Thanks for the quick reply!

---

### Post by darth_vector on 2006-02-19
i dont think you can get free domains. you have to register a domain and that costs money. google turned up this: [http://www.ukreg.com/](http://www.ukreg.com/) as one possible place you could register your domain.

the internet's DNS system is what translates between domain names and IP addresses. when you put [www.google.com](www.google.com) in your web browser, it sends a DNS quiery to one of the DNS servers listed in you /etc/resolv.conf file. this file returns the IP address corresponding to the service you requested. you can read more about DNS at wikipedia: [http://en.wikipedia.org/wiki/Domain_name_service](http://en.wikipedia.org/wiki/Domain_name_service)

---

### Post by CarlosinFL on 2006-02-19
I use this as my free domain.

[www.dyndns.org](www.dyndns.org). It works great with my Apache and vsFTPd server!

---

### Post by rado_london on 2006-02-20
Thanks a lot for the info but I have a big problem. I just restarted my pc and found out that there is no ftp server. However I opened a terminal and wrote down vsftpd. Here is the output:
```
rado@linux:~$ vsftpd
500 OOPS: bad bool value in config file for: local_enable

```

What is wrong?

---

### Post by pjbgravely on 2006-05-06
Paste you vsftpd.conf file here, use the code tags.

Paul

---

### Post by tbresson on 2006-07-31
I just got the same error.

My FTP server has been working just fine, all of a sudden the server response like that and I havn't changed anything. Just installed updates.

There are no comments in my config file, I head that could be a problem.

---

### Post by cstudent on 2006-07-31
> **rado_london said:**
> Hi Today I installed and set up a ftp server. Its address is [ftp://82.2.252.160](ftp://82.2.252.160)


I would like to get two things.
First is to get an opportunity to log in as owner or anonymous from a firefox for example when I am at college I can add folders etc.

Also I would like to change that name to [ftp://radopetsov.org](ftp://radopetsov.org)


Thanks in Advance

You're not going to be able to get the domain name radopetsov.org for free. You would have to pay for a domain name like that. You can register one pretty cheap at [www.godaddy.com](www.godaddy.com). If you want something free you can use [www.no-ip.com](www.no-ip.com) and setup a free account that points to your ip address. If your ip address is not static, meaning it will change, then you can use the no-ip package found in synaptic to have your computer tell no-ip.com what your ip is periodically. With no-ip.com you can get a domain name something like radopetsov.myftp.org. I use the free service for my own personal ftp server. 

Another thing to take into consideration. If you open up port 21 your server is eventually going to be found and someone you don't want to may try to access it. If you allow annonymous access, you definitely are going to have someone in there messing around. I have my server setup to only allow access from the internal network and the ip of my workplace. All other ip addresses are off limits.

---

### Post by tbresson on 2006-08-16
I found the solution.

For some reason the error occurs when copying a new config file over to /etc/vsftpd.conf even though the permissions are set correctly.

But if I reinstall the VSFTPD and open the example config file and redo the whole config as I prefer it then the problem went away.

Invisible chars or something ? I have no idea...

---

