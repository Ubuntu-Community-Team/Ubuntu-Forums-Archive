---
title: "Wget from FTP server"
date: 2008-12-16
forum: General Help
---

### Post by OOzypal on 2008-12-16
wget and ftp

how can I use wget to download a bunch of files from an ftp server.  I tried this but no help

username: [email]me@example.com[/email]
password  1234567
server:   192.192.192.192  (not real)

```
wget ftp://me@example.com:1234567@192.192.192.192/file.tar.gz
```

I get an error of  

> Bad port number.

---

### Post by Bachstelze on 2008-12-16
```
wget ftp://me@example.com:1234567@192.192.192.192/file.tar.gz
```

It's basically [ftp://user:password@host:port](ftp://user:password@host:port)

---

### Post by OOzypal on 2008-12-16
hmmm,  my user name is

[email]me@example.com[/email] and password is 1234567

you wrote :

me:1234567@example.com

is this correct?

---

### Post by Bachstelze on 2008-12-16
Fixed.

---

