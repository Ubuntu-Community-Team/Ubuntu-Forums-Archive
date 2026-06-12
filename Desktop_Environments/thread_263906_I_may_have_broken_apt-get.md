---
title: "I may have broken apt-get"
date: 2006-09-23
forum: Desktop Environments
---

### Post by intimidat0r on 2006-09-23
I tried to install a package called 'amap'. This didn't seem to work, so I decided I didn't need it and went about my business.

A few hours later I wanted to install Wine:

```
intimidat0r@gibson:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 8785kB of archives.
After unpacking 41.4MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com dapper/universe wine 0.9.9-0ubuntu2 [8785kB]
Fetched 8785kB in 26s (335kB/s)
Selecting previously deselected package wine.
(Reading database ... 79178 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.9-0ubuntu2_i386.deb) ...
Setting up amap (4.8-1.1) ...
Upgrading trigger, response and rpc files ...
Running Online Update for fingerprints, connecting to www.thc.org/thc-amap
Error: file could not be found by web server: HTTP/1.1 302 Found
Date: Sun, 24 Sep 2006 01:29:29 GMT
Server: IIS 6.4                      mod_ssl/2.0.49 OpenSSL/0.9.7d PHP/4.3.10
Location: http://thc.segfault.net/appdefs.resp
Content-Length: 342
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>302 Found</title>
</head><body>
<h1>Found</h1>
<p>The document has moved <a href="http://thc.segfault.net/appdefs.resp">here</a>.</p>
<hr />
<address>IIS 6.4                      mod_ssl/2.0.49 OpenSSL/0.9.7d PHP/4.3.10 Server at thc.org Port 80</address>
</body></html>

dpkg: error processing amap (--configure):
 subprocess post-installation script returned error exit status 255
Setting up wine (0.9.9-0ubuntu2) ...

Errors were encountered while processing:
 amap
E: Sub-process /usr/bin/dpkg returned an error code (1)
intimidat0r@gibson:~$
```

As you can see it didn't quite work. Also, it seems to be trying to install amap still? Any idea what's going on and how I can fix this?

Thanks for your help. :)

---

### Post by croak77 on 2006-09-23
Do you need amap?

---

### Post by intimidat0r on 2006-09-23
Nah, I decided I don't really need it. However, I do need Wine and whatever else I may try to get via apt-get in the future.

---

### Post by Brownedwg89 on 2006-09-23
hmm... i was getting this problem earlier today.
I forget how i fixed it, does
```
sudo dpkg --configure -a
```
or
```
sudo apt-get -f install
```
work?

---

### Post by intimidat0r on 2006-09-24
Nope. The first one looks like this:

```
intimidat0r@gibson:~$ sudo dpkg --configure -a
Setting up amap (4.8-1.1) ...
Upgrading trigger, response and rpc files ...
Running Online Update for fingerprints, connecting to www.thc.org/thc-amap
Error: file could not be found by web server: HTTP/1.1 302 Found
Date: Sun, 24 Sep 2006 04:41:08 GMT
Server: IIS 6.4                      mod_ssl/2.0.49 OpenSSL/0.9.7d PHP/4.3.10
Location: http://thc.segfault.net/appdefs.resp
Content-Length: 342
Connection: close
Content-Type: text/html; charset=iso-8859-1

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>302 Found</title>
</head><body>
<h1>Found</h1>
<p>The document has moved <a href="http://thc.segfault.net/appdefs.resp">here</a>.</p>
<hr />
<address>IIS 6.4                      mod_ssl/2.0.49 OpenSSL/0.9.7d PHP/4.3.10 Server at thc.org Port 80</address>
</body></html>

dpkg: error processing amap (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 amap
intimidat0r@gibson:~$
```

And the second one is exactly the same output as my first post.

---

### Post by spydon on 2008-04-04
Hmm, weird. Did any installation get interupted when you were installing before you tried installing wine?

---

### Post by bonzodog on 2008-04-04
Looking at that output, what seems to have happened is the location of the file needed to update has moved, and there is a broken referrer link to it. The error is caused by it simply not being able to find the fingerprint file. It's not you, and you have not broken apt.  
```

Running Online Update for fingerprints, connecting to www.thc.org/thc-amap
Error: file could not be found by web server: HTTP/1.1 302 Found
Date: Sun, 24 Sep 2006 04:41:08 GMT
Server: IIS 6.4                      mod_ssl/2.0.49 OpenSSL/0.9.7d PHP/4.3.10
Location: http://thc.segfault.net/appdefs.resp

```
 Whats rather worrying about that is that it's running IIS!
You won't be able to fix this until thc.org fix their links.

---

