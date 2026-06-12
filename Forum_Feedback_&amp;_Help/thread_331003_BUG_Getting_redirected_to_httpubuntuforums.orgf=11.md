---
title: "BUG: Getting redirected to http://ubuntuforums.org/?f=11 in konqueror"
date: 2007-01-03
forum: Forum Feedback &amp; Help
---

### Post by Steveire on 2007-01-03
Hi.

When I access a forum from outside of ubuntuforums.org, the forumdisplay.php gets dropped from the url, and the Currently active users box is shown. I'm using Konqueor and have no other browser to verify with. w3m displays the forum correctly.

How I recreate this:

Go to [www.google.com](www.google.com)
put ubuntuforums.com/forumdisplay.php?f=11 in the address box and hit go.
get redircted to ubuntuforums.com/?f=11

I suspect this is an issue with skins. I've been experiencing it for a day or two. Can someone confirm?

---

### Post by raul_ on 2007-01-04
Happens here too

---

### Post by Steveire on 2007-01-04
Any chance of a fix? Opera seems to handle it fine.

---

### Post by Steveire on 2007-01-05
Found the fix.

```

In [10]: urllib.urlopen("http://ubuntuforums.com/forumdisplay.php?f=11")
connect: (ubuntuforums.com, 80)
send: 'GET /forumdisplay.php?f=11 HTTP/1.0\r\nHost: ubuntuforums.com\r\nUser-agent: Python-urllib/1.16\r\n\r\n'
reply: 'HTTP/1.1 301 Moved Permanently\r\n'
header: Date: Sat, 06 Jan 2007 02:31:53 GMT
header: Server: Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1
header: Location: http://ubuntuforums.org/?f=11
header: Content-Length: 337
header: Connection: close
header: Content-Type: text/html; charset=iso-8859-1
connect: (ubuntuforums.org, 80)
send: 'GET /?f=11 HTTP/1.0\r\nHost: ubuntuforums.org\r\nUser-agent: Python-urllib/1.16\r\n\r\n'
reply: 'HTTP/1.1 200 OK\r\n'
header: Date: Sat, 06 Jan 2007 02:31:53 GMT
header: Server: Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1
header: X-Powered-By: PHP/4.4.2-1build1
header: Set-Cookie: bblastvisit=1168050713; expires=Sun, 06 Jan 2008 02:31:53 GMT; path=/; domain=.ubuntuforums.org
header: Set-Cookie: bblastactivity=0; expires=Sun, 06 Jan 2008 02:31:53 GMT; path=/; domain=.ubuntuforums.org
header: Expires: 0
header: Cache-Control: private, post-check=0, pre-check=0, max-age=0
header: Pragma: no-cache
header: Connection: close
header: Content-Type: text/html; charset=ISO-8859-1
Out[10]: <addinfourl at -1216171124 whose fp = <socket._fileobject object at 0xb782d1b4>>

```
The redirect drops the forumdisplay.php from the url. It seems I was also wrong in that the bug occurs when using ubuntuforums.com, not .org.

---

