---
title: "Pidgin not working but gtalk in windows does"
date: 2008-07-03
forum: Desktop Environments
---

### Post by phazer on 2008-07-03
Sitting behind a proxy server at work. Not a problem, my google talk client in windows works like a charm. Installed Hardy, but Pidgin, just does not want to connect. I get a "
Could not establish a connection with the server.
Access Denied: HTTP proxy forbids port 433 tunneling. "

Now I have tried to use 5222 as well as the port to connect to talk.google.com same problem.

Anyone have any ideas. This is the only thing not working for me in Hardy, everything on my notebook(IBM Z61m) is working like a charm.

---

### Post by doorman on 2008-07-05
Same problem here...

I'm behind a http proxy without authentication...

To specify the problem, i get the error:
"HTTP Proxy server forbids port 5222 tunneling"

[This post]("http://ubuntuforums.org/showpost.php?p=3654324&postcount=109") said to upgrade to the proposed packages, but it didn't do the trick for me... And yeah, I'm running Hardy, not Gutsy...

---

### Post by eldanialonso on 2008-09-24
I got my pidgin working in windows (still not tested in linux but I think it will not be a problem)

Taken from [http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/]("http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/")

Force old (port 5223) SSL: Checked
Allow plaintext auth over unencrypted streams: Un-Checked
Connect Port: 443
Connect Server: talk.google.com
Proxy type: Use Global Proxy Settings

Hope this helps

---

### Post by z0mbie on 2008-11-04
> **eldanialonso said:**
> I got my pidgin working in windows (still not tested in linux but I think it will not be a problem)

Taken from [http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/]("http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/")

Force old (port 5223) SSL: Checked
Allow plaintext auth over unencrypted streams: Un-Checked
Connect Port: 443
Connect Server: talk.google.com
Proxy type: Use Global Proxy Settings

Hope this helps

This works well in Linux, Ubuntu Intrepid.

---

### Post by bhadotia on 2008-11-20
Can someone tell me how can I get this done with yahoo also (or do I have to start a new thread).
[This]("http://roshansingh.wordpress.com/2008/08/28/using-svn-and-proxy-behind-proxy/#comment-78") method has worked for gtalk, but still can't get my pidgin to work with yahoo.

I'm behind a proxy and am getting this error:
> Could not establish a connection with the server:
Access denied: HTTP proxy server forbids port 5050 tunneling.

---

### Post by brmc on 2009-08-14
> **eldanialonso said:**
> I got my pidgin working in windows (still not tested in linux but I think it will not be a problem)

Taken from [http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/](http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/)

Force old (port 5223) SSL: Checked
Allow plaintext auth over unencrypted streams: Un-Checked
Connect Port: 443
Connect Server: talk.google.com
Proxy type: Use Global Proxy Settings

Hope this helps


thanx buddy=D>
great help

---

### Post by IsraeliHawk on 2010-07-09
> **eldanialonso said:**
> I got my pidgin working in windows (still not tested in linux but I think it will not be a problem)

Taken from [http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/]("http://www.manast.com/2007/05/11/how-to-configure-pidgin-to-work-with-google-talk/")

Force old (port 5223) SSL: Checked
Allow plaintext auth over unencrypted streams: Un-Checked
Connect Port: 443
Connect Server: talk.google.com
Proxy type: Use Global Proxy Settings

Hope this helps

:D
thank you!
solved it

---

