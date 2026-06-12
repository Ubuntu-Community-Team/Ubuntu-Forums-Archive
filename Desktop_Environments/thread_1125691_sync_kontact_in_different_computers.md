---
title: "sync kontact in different computers?"
date: 2009-04-14
forum: Desktop Environments
---

### Post by hutxubix on 2009-04-14
Hello,

I always use two computers, one at home and the other one at home. Could someone tell me if there is a simple way to sync kontact between the two computers, both running kubuntu 8.10?

Note: I have read in kontact's web page about the possibility of using OpenSync for this purpose, but I am not able to figure out how exactly

Thanks in advance

---

### Post by inobe on 2009-04-14
akonadi is what you probably need, it comes with kde4.2 upgrade packed with mysql.......

[http://pim.kde.org/](http://pim.kde.org/)

---

### Post by inobe on 2009-04-14
actually i take that back, just did some research and found it's not up to par yet.

i am sure others here may have an alternative method.

---

### Post by hutxubix on 2009-04-15
Thanks inobe,

I will take a look anyway.

Any other ideas please?

---

### Post by hutxubix on 2009-04-19
I have been looking around and have found that there is a possibility of doing this using an IMAP mail server (IMAP resource), as the one I use. However, I have not been able to get it to work. Any suggestions?

---

### Post by bertmanphx on 2010-04-09
hutxubix,
I've found that I can accomplish this by:

Add IMAP as a resource into akonadi
add Kolab as a resource into akonadi
goto Kontact, enable Groupware
goto addressbook and add it as an Imap resource on Kmail

Now, I have contacts and calendar saved on my email server.  Problem is though, I cannot see these items from the webmail portion, so I have to use Kontact to view or use them.

Does this help?  I know this is an old thread, but it's something I had been trying to do for a long time.

bertmanphx

---

### Post by hutxubix on 2010-04-09
Hey! Thank you, I will try!

As I had not been able to do it, I was syncronithing with dropbox (soft linking the proper conf folders)

Thanks again

---

