---
title: "Likewise-Open domain join problem"
date: 2009-05-28
forum: General Help
---

### Post by human118 on 2009-05-28
I have a fresh install of Server 8.04 and I am attempting to join the server to my AD. 

To install I did:
sudo apt-get update
sudo apt-get install likewise-open

to join I did:
sudo domainjoin-cli join <mydomain>.com administrator

I am then prompted for the admin password, which I provide and I get the following:

```

Error: Module not configured [code 0x00080042]

Even though the configuration of 'hostname' was executed, the configuration is not complete. Please contact Likewise support.

```I Googled the problem and I found [http://ubuntuforums.org/archive/index.php/t-810405.html](http://ubuntuforums.org/archive/index.php/t-810405.html)

So I tried adding an OU to the command:
sudo domainjoin-cli join --ou Computers <mydomain>.com administrator

and received the same result. 

I have traversed the documentation and performed all of the troubleshooting steps. The server has a static IP and DNS is set and the domain can be resolved. I thought it was curious that the error said 'hostname' when the hosts file and all other configurations seem to check out.

This is the second server install in two days. I ran into this with a clean install yesterday and finally scrapped it because I couldn't get it on the domain. 

Any ideas ](*,)??? Thanks in advance.

---

### Post by Ahlan on 2009-08-13
I had the same problem and same error message.
The reason turned out to be that i didn't type the domain name case sensitive when
i issued the domainjoin-cli join command.
If the domain name matches except for case then if fails with this strange error message
I went on the Windows AD domain controller and discovered exactly how the domain is named and used that.
In my case it was [email]Ultimate@White-Elephant.ch[/email]
Using capital U,W and E in the domain name solved the problem and I have been able to join the AD domain. :-)

---

### Post by mrbangus on 2010-01-22
I'm having the same problem.  I have typed the domain name correctly and it still gives me error.

---

### Post by amiine85 on 2010-12-23
I have many problems with likewise. You have another method to follow to achieve the same result : install krb5, winbind ...

thanks

---

