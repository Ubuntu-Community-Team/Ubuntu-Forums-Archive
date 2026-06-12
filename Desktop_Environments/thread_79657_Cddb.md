---
title: "Cddb"
date: 2005-10-20
forum: Desktop Environments
---

### Post by H4rm0ny on 2005-10-20
Hi  - a simple question. How do I disable CDDB. Forever. All applications. 

I cannot find the settings. Google is pretty much implying that I am the only person in the world that despises it. 

Currently, I've just blocked connections to the feedb site in my firewall. I would like to do this properly.

---

### Post by H4rm0ny on 2005-11-12
*bump*

Sorry - but surely this is so simple that someone must know how to do it. I'm currently dropping every packet headed for the IP address of the CDDB servers, but there **has** to be a more elegant way of doing this. Am I the only one who doesn't want to broadcast live everything I'm listening to?

---

### Post by ace2005 on 2005-11-12
I have no Idea what CDDB is but when i googled it i found

> CDDB (which stands for Compact Disc Database) is a database for software applications to look up CD (compact disc) information over the Internet. This is performed by a client which calculates a (nearly) unique disc ID and then queries the database.

So i guess you should just get rid of "libkcddb1" and possibly "python-cddb" in adept

---

### Post by H4rm0ny on 2005-11-12
Whenever you put a CD in, the default Kubuntu set-up goes off and compares the track information (lengths and numbers, I think) with a central database and gets a reply back saying "You're listening to Andrew Lloyd Webber's Greatest Hits" (note - made up example! ) Most of the programs available do this (Amarok, Kscd, Kaffeine, et al.) but personally I find it both unnecessary and intrusive to my privacy. 

I was sure that there must be a setting somewhere that enabled or disabled it, or configured where the servers were, but I can't find it. 

I've taken out the packages you suggested as fewer things depended on them than I had thought. Fingers crossed... and thanks.

-H.

---

### Post by datube on 2006-01-06
Try this:

```
# cddb-slave2-properties
```

Then you can specify how to use cddb; On the Server-tab select "Other server" and change the port to 0 (or type a bogus server name). This should do the trick

Hope this helps

---

