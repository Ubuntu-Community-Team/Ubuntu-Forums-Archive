---
title: "Ubuntu Server 8.04: OpenLDAP + SAMBA Domain Controller TUTORIAL Need"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by karthi on 2008-05-22
Hi

Good Morning, This is Karthikeyan,:) 


I new comer for Ubuntu. Please help me too. :)

I am using Ubuntu 8.04 LTS Server (64bit)

I am working as a System Administrator in Crewind Communication. 

We have 60 notes and 2 server. now we ll change the server windows to Ubuntu. So, I want domain controller, file server, Mail server and backup Server. 

This is organization in small business area. So, i dont get any help from organization. so need user help. 

"please help to, how do i configure this Ubuntu server 8.04 act as a File Serve, Mail Server, Domain Controller and Backup Server". 

"Now I configure File Server (Samba, Printer Server (CUPS), Backup Server. But i cont configure Domain Controller and Mail Server".

Pl. Teach to me how to do this configuration. 

thanks for your valuable time and reply.


Regards 

Your Friend
Karthikeyan .P
From India

---

### Post by archgriffin on 2008-05-31
I believe you can do it following this tutorial:

[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)

I know it is for 7.10 not 8.04. But I am doing a similiar setup, on a much smaller scale 1 server, 5 workstations, no mail server. I was practicing in a VMware environment, and it took a little tweaking but I had it working. I already wiped it because I am going to drop LDAP and just use SAMBA if I can. 

I also setup backuppc on the same VM during testing using the following tutorial:

[http://www.howtoforge.com/linux_backuppc](http://www.howtoforge.com/linux_backuppc)

However I have not setup a mail server before, so I haven't looked in to that much, but I would imagine you could find a exim tutorial for that in howtoforge as well, or elsewhere in these forums. 

Hopefully that is of some help. Of course you didn't mention your client machines, I would just be guessing they are MS Windows XP?

---

### Post by linkx on 2008-06-02
I am looking to do this exact thing. I am the single IT admin for a small business and I am planning to rebuild our outdated MS network using three new Ubuntu 8.04 servers to achieve the following:

[LIST]
[*]"Domain Controller" (DNS and LDAP and SAMBA server)
[*]VPN Server
[*]Apache/PHP/MySQL webserver
[*]FTP server
[*]File Share
[*]Backup Process
[*]NO email server (we use Google Apps)
[*]Virtual Machine server that will run several virtualized instances of Windows Server 2003
[/LIST]

If anyone has tips/guides/resources for projects like this--preferably specific to 8.04--please respond! Thanks to all!

---

### Post by adamos on 2008-06-02
Same situation as you.

I am the only sys admin here in a non profit organization. Just to give you a hint. installing ldap will give a headache because all the documentation out there mostly is rubbish(except ubuntu documentation and openldap.org). I read 3 books on ldap etc and I finally got it running from reading the docs. I installed phpldapadmin and so far so good! I wrote the documentation carefully but I wanted to finish with StartTLS first and then publish it(next week maybe). There are some differences from previous versions but I will figure it out.. I always do :). The rest of your requests are piece of cake. webserver is really easy.. Just pick apache cookbook from oreily and it will get you going in no time. Install phpmyadmin for sql administration and proftpd for ftp client.

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)  <- Theres no substitute for this documentation.. You better read it before proceeding deploying your servers.

---

### Post by scorp123 on 2008-06-02
You guys should definitely follow this thread then --- the stuff here works 100%, just follow the commands and make sure that you don't mistype anything:

**"Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller"**
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

The instructions should work tip top for Ubuntu 8.04 too, I am not aware of any changes in the relevant packages or commands.

---

### Post by Simontek on 2009-05-07
For backups you could always use Bacula

---

### Post by pogztimz on 2009-05-10
> **scorp123 said:**
> You guys should definitely follow this thread then --- the stuff here works 100%, just follow the commands and make sure that you don't mistype anything:

**"Ubuntu Server 7.10: OpenLDAP + SAMBA Domain Controller"**
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

The instructions should work tip top for Ubuntu 8.04 too, I am not aware of any changes in the relevant packages or commands.

i agree. i have followed this how-to 1 year ago and installed it on 8.04 server edition and it worked like a charm. OPENLDAP + SAMBA DOMAIN CONTROLLER.. << its great.. and easy to follow... :popcorn:

---

### Post by jviens on 2009-06-03
I went to restart the LDAP Service at the end of Step 8 and, while it stopped OK, the restart failed. It states that the operation failed but no output was produced. I'm using the tutorial with Ubuntu 8.04 (I had seen where some people had used this tutorial on 8.04 with no problems). Kernel version is 2.6.24-19-server. Fairly new to Linux so please bear with me.

---

### Post by jviens on 2009-06-03
Nevermind. I hadn't uncompressed my samba.schema.gz file. It restarts now.

---

### Post by jviens on 2009-06-04
OK...got that last problem figured out, now on to a new one.
When adding a user (Step 12) I try to enter the sample info:

*smbldap-useradd -a -m -M jdoe -c "John D" jdoe* 

and get the following:

[I]Error looking for next uid in sambaDomainName=$HYBORIA,dc=hyboria,dc=local:No such object at /usr/share/perl5/smbldap_tools.pm line 1071.

[/I]Eagerly awaiting any help that may come....

---

