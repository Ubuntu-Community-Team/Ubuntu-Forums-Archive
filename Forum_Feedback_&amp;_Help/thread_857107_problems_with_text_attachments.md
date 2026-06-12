---
title: "problems with text attachments"
date: 2008-07-12
forum: Forum Feedback &amp; Help
---

### Post by forger on 2008-07-12
I'm trying to figure out what causes this bug:
[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239952](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239952)

It happens on ubuntuforums.org and linuxforums.org so far.
Please don't remove this post, as I need to attach several attachments to see the bug's problems.

In the case it creates problems, move it to a "junk" folder or something, thanks :)

---

### Post by forger on 2008-07-12
testing 2

---

### Post by bapoumba on 2008-07-12
Confirmed. Epiphany 2.22.2 - Hardy.

---

### Post by popch on 2008-07-12
The problem exists on my PC as well, running Ubuntu 8.04, Intel, 32-bits. You may want to adjust the problem description which seems to restrict the problem to 64-bit installations.

---

### Post by forger on 2008-07-12
thanks for your input :)

---

### Post by david.rahrer on 2008-08-05
I get the error with all but PDF.  Hardy and FF current as of today.

---

### Post by IntuitiveNipple on 2008-09-09
gzip attachments too?

See [LP bug #239952](https://bugs.launchpad.net/ubuntu/+bug/239952) for progress on this.

---

### Post by IntuitiveNipple on 2008-09-09
The primary cause of this problem is the web-server hosting ubuntuforums.org is misconfigured, and reports the wrong Content-Type for all but PDF files.

The Canonical sysadmins have been made aware of it.

There is a secondary issue with xulrunner (the processing back-end for firefox, piphany, etc.,) where it correctly figures out the mime-type from the file extension but then forgets/loses the helper application that gnome-vfs gave it, resulting in the error.

---

### Post by IntuitiveNipple on 2008-09-17
xulrunner-1.9 packages to test this patch are now [available in my PPA for Hardy and Intrepid](https://launchpad.net/~intuitivenipple/+archive?field.name_filter=xulrunner-1.9&field.status_filter=published).

Please report successes and any regressions.

---

### Post by IntuitiveNipple on 2008-09-17
If making a report please give the following information.

What happened to the same file beforehand?

Also, if you have Live HTTP Headers installed ([http://livehttpheaders.mozdev.org/](http://livehttpheaders.mozdev.org/)) capture the HTTP *response* from the server that contains:
```

content-disposition:
Content-Type:

```
For example, for the page [http://ubuntuforums.org/showpost.php?p=5755405&postcount=7](http://ubuntuforums.org/showpost.php?p=5755405&postcount=7) that will look like this:
```

HTTP/1.x 200 OK
Date: Wed, 17 Sep 2008 18:03:37 GMT
Server: Apache/2.0.55 (Ubuntu) PHP/5.1.2
X-Powered-By: PHP/5.1.2
Cache-Control: max-age=31536000, private
Vary: User-Agent
X-UA-Compatible: IE=7
Expires: Thu, 17 Sep 2009 18:03:37 GMT
Last-Modified: Tue, 09 Sep 2008 12:59:04 GMT
Etag: "84692"
Accept-Ranges: bytes
content-disposition: attachment; filename*=ISO-8859-1''test4%20with%20space.txt.gz
Content-Length: 53
Content-Type: unknown/unknown
X-Cache: MISS from feijoa.canonical.com
X-Cache-Lookup: MISS from feijoa.canonical.com:8800
Via: 1.0 feijoa.canonical.com:8800 (squid/2.6.STABLE18), 1.1 ubuntuforums.org
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive

```
Also, because everyone collects a set of personal handling preferences in the ~/.mozilla/firefox/${PROFILE}/mimeTypes.rdf which will affect how the attachment is dealt with, please test the same file in a new clean profile (start Firefox from a command-line with "firefox -ProfileManager").

---

### Post by smLitvak on 2008-09-22
I am just getting started with Linux so please point me in the right direction if I am missing something.

I am having this problem on PPC running Hardy with both firefox-3.0 and epiphany. I checked TJ's PPA but did not see any xulrunner-1.9 build for PPC. Do I need to check elsewhere for this package? Is there a way for me to create a PPC version on my own?

Thanks!

---

### Post by cyberdork33 on 2008-09-22
> **smLitvak said:**
> I am just getting started with Linux so please point me in the right direction if I am missing something.

I am having this problem on PPC running Hardy with both firefox-3.0 and epiphany. I checked TJ's PPA but did not see any xulrunner-1.9 build for PPC. Do I need to check elsewhere for this package? Is there a way for me to create a PPC version on my own?

Thanks!
You are definitely in the wrong area. Please make a new post in the Apple Users' forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

Also, please be a bit more descriptive about what you are doing. What are you trying to accomplish? What issues are you facing? Why are you trying to use "TJ's PPA?"

---

### Post by Joeb454 on 2008-09-23
There is already a thread about this in the Apple area I believe

---

### Post by cyberdork33 on 2008-09-23
> **Joeb454 said:**
> There is already a thread about this in the Apple area I believe
I thought it looked familiar, but I didn't find it.

---

### Post by smLitvak on 2008-09-25
I will get my facts gathered together and post this in the Apple area.

---

