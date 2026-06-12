---
title: "FTP connection failed."
date: 2009-04-19
forum: General Help
---

### Post by runnner on 2009-04-19
I can remote access to ubuntu server using cygwin with root privilege. but when I want to upload some files to ubuntu with free FTP client Filezilla using root role, the connection always failed. "ECONNREFUSED - Connection refused by server"

Where is wrong, how should I do? Thanks for help!

---

### Post by paradigm2 on 2009-04-19
> **runnner said:**
> I can remote access to ubuntu server using cygwin with root privilege. but when I want to upload some files to ubuntu with free FTP client Filezilla using root role, the connection always failed. "ECONNREFUSED - Connection refused by server"

Where is wrong, how should I do? Thanks for help!

You are trying to login as root on the Ubuntu box?

I believe by default the root account is disabled globally in ubuntu.

Also I think it is usually disabled by the ftpserver as well.

do

```

cat /etc/ftpusers

```

and see what you have.

I would advise not trying the root account but instead whatever user account you installed first in ubuntu.  But if you want to use root, despite all the security issues, it is possible and we can do it...

---

### Post by paradigm2 on 2009-04-19
See this for info on ftpusers:

[http://manpages.ubuntu.com/manpages/intrepid/en/man5/ftpusers.5.html](http://manpages.ubuntu.com/manpages/intrepid/en/man5/ftpusers.5.html)

---

### Post by runnner on 2009-04-20
Why there is no ftpusers in /etc?

I ran the command 
root@ubuntu:/etc# find / -name ftpusers
and ubuntu can't find ftpusers.

I ran uname to get ubuntu version info, the version is 
Linux ubuntu 2.6.24-16-server

---

### Post by paradigm2 on 2009-04-20
> **runnner said:**
> Why there is no ftpusers in /etc?

I ran the command 
root@ubuntu:/etc# find / -name ftpusers
and ubuntu can't find ftpusers.

I ran uname to get ubuntu version info, the version is 
Linux ubuntu 2.6.24-16-server

There does not have to be an ftpusers file.

If you want to ftp as root, which is a security risk, you will need to first enable the root account in ubuntu:

[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

It is highly inadvisable though.  Even if you later disable root, people have reported certain issues.  Its your call but if you do this your ftp as root will probably work.

---

### Post by runnner on 2009-04-20
> **paradigm2 said:**
> There does not have to be an ftpusers file.

If you want to ftp as root, which is a security risk, you will need to first enable the root account in ubuntu:

[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)



I can already remote login as root using putty, so the root account is already activated.

---

