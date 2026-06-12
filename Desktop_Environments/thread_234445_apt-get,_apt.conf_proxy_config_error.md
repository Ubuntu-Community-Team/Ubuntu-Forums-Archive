---
title: "apt-get, apt.conf proxy config error"
date: 2006-08-11
forum: Desktop Environments
---

### Post by monteros on 2006-08-11
Hey all, I am having some issues getting apt-get to work.  I have been reading the man for apt-get, apt.conf and help pages here, and it looks like I need to add the proxy lines into the apt.conf file and it should work, here is what I have:
/etc/apt/apt.conf file contents
```
Acquire::http::proxy "http://ID:password@domain.name.com:80";
Acquire::ftp::proxy "ftp://ID:password@domain.name.com:80
```
However, every time I true to sudo apt-get upate I get 
```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  407 Proxy Authentication Required
```
The id and password I am using are correct I know that, but something is wrong, anyone out there got a sec to assist a newer Ubuntu user?

Thank you
-Monteros

---

### Post by jordilin on 2006-08-11
take a look at the following thread:
[http://www.ubuntuforums.org/showthread.php?t=129843](http://www.ubuntuforums.org/showthread.php?t=129843)

---

### Post by monteros on 2006-08-11
Thanks but that is all stuff I have tried with no luck.  I appear to have the correct /etc/apt/apt.conf file configurations for the proxy and id and password; however it doesn't work.  I am sure it is someting simple, I jsut can't seem to see it or fix it.

I even tried exporting http_proxy in .bashrc and it didn't work either - I had a friend show me how to setup the apt.conf file before and it worked fine, which makes me wonder if it isn't something simple that I am obvisouly doing wrong.

The configs above are still correct. with the exception that I changed the apt.conf for testing to just this: 
```
ACQUIRE {
  http::proxy "http://myid:mypassword@proxyserver:8085"
}

```

---

### Post by jordilin on 2006-08-11
Have you tried setting the http_proxy variable and export it?

---

### Post by monteros on 2006-08-11
yes, however I got an error saying that it didn't work.  What would the syntax be for setting it with ID and password via the .bashrc?  I tried the same syntax as above [http://id:password@server:port/](http://id:password@server:port/) but that is what didn't work.

---

