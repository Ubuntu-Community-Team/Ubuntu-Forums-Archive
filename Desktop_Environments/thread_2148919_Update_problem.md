---
title: "Update problem"
date: 2013-05-27
forum: Desktop Environments
---

### Post by Pally1 on 2013-05-27
Greetings, after last nights update, update manager seems to have a problem, i get this when i try to check for updates:
> 
 Failed to download [http://www.bchemnet.com/suldr/dists/debian/Release.gpg](http://www.bchemnet.com/suldr/dists/debian/Release.gpg) Could not connect to [www.bchemnet.com:80](www.bchemnet.com:80) (173.236.28.2). - connect (110: Connection timed out) Failed to download [http://www.bchemnet.com/suldr/dists/debian/extra/binary-amd64/Packages](http://www.bchemnet.com/suldr/dists/debian/extra/binary-amd64/Packages) Unable to connect to [www.bchemnet.com:http:](www.bchemnet.com:http:) Failed to download [http://www.bchemnet.com/suldr/dists/debian/extra/binary-i386/Packages](http://www.bchemnet.com/suldr/dists/debian/extra/binary-i386/Packages) Unable to connect to [www.bchemnet.com:http:](www.bchemnet.com:http:) Failed to download [http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en_US](http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en_US) Unable to connect to [www.bchemnet.com:http:](www.bchemnet.com:http:) Failed to download [http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en](http://www.bchemnet.com/suldr/dists/debian/extra/i18n/Translation-en) Unable to connect to [www.bchemnet.com:http:](www.bchemnet.com:http:) 



Any idea what this is?

---

### Post by ajgreeny on 2013-05-27
Is this a Samsung machine?

The address that you can not connect to appears to be a samsung drivers web-site which was perhaps temporarily unavailable.

I can get to [http://www.bchemnet.com/suldr/dists/debian/extra/binary-i386/Packages](http://www.bchemnet.com/suldr/dists/debian/extra/binary-i386/Packages) with no problem, but I have no idea why your machine has those update repos enabled unless you did so yourself, or it is a machine pre-installed with ubuntu.

---

### Post by Pally1 on 2013-05-27
> **ajgreeny said:**
> Is this a Samsung machine?

The address that you can not connect to appears to be a samsung drivers web-site which was perhaps temporarily unavailable.

I can get to [http://www.bchemnet.com/suldr/dists/debian/extra/binary-i386/Packages](http://www.bchemnet.com/suldr/dists/debian/extra/binary-i386/Packages) with no problem, but I have no idea why your machine has those update repos enabled unless you did so yourself, or it is a machine pre-installed with ubuntu.

I have lenovo laptop. I guess these links are for my samsung printe's universal driver. Problem is that due to these unavailable links, other updates cant be aquired aswell.

---

### Post by ajgreeny on 2013-05-27
You can disable those repos normally from the software-sources application simply by de-selecting them and then updating the repos again.  That should allow updating of everything, except those drivers, of course.

---

### Post by ReetP on 2013-06-04
I would suggest that this is definitely the problem :

Oooops 173.236.28.2 is currently listed in APEWS :-(
Entry matching your Query: E-505191
173.236.0.0/18CASE: C-17
Spambots, zombies, contaminated CIDR, bad reputation providerHistory:
Entry created 2012-01-09

It would therefore appear that my UK provider (but not my Spanish one) uses this list and blocks the IP.

Unfortunately I very much doubt that my provider is going to remove the IP from their list.

I hate to say it, but it really is up to the web site owner to get it resolved, just the same as if you have a mail server that is blocked.

Proxy chains is OK, IF you have another server :-)

---

