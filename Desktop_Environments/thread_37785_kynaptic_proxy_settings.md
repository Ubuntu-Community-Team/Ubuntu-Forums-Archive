---
title: "kynaptic proxy settings?"
date: 2005-05-28
forum: Desktop Environments
---

### Post by recover82 on 2005-05-28
I'm sure it has been covered before, and I did some searching these past two weekends at work and I've yet to find a solution that works.  

I recently installed kubuntu on my laptop and I want to do some package updates with kynaptic while i'm on the connection here at work.  But to access the internet we go through a proxy.  

Kynaptic basically times out because i don't know where to configure it to use the proxy.  Is there a file I can edit to fix this problem?  

thanks for any info.

---

### Post by Mez on 2005-05-28
You want to add a file to /etc/apt/apt.conf.d:

```
sudo kwrite /etc/apt/apt.conf.f/01proxy
```

In this file, put the following line

```
Acquire::http::Proxy "http://user:pass@proxy.example.net:3128";
```

This should fix it! remember to substitute the user/pass/host/port to match your proxzy settings!

---

### Post by recover82 on 2005-05-28
i'm going to give that a try but i found a "workaround" for the time being.  
i edited my sources.list file and replaced the "http"'s with "ftp"'s  and the packages started SCREAMING in.  that's good.  is there any problem using the FTP route?

---

### Post by recover82 on 2005-05-28
I tried your suggestion and I get:

Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not resolve '(my proxy info here)'

that repeats for all the repositories listed.  then again, the FTP replacing solution works for now.

---

