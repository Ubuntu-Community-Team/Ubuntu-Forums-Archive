---
title: "no email with att.yahoo"
date: 2009-03-19
forum: General Help
---

### Post by jmore9 on 2009-03-19
Hello !  I have set up my pop and smtp accounts the same as on the windows outlook express ports.  But thunderbird and evolution mail keep failing on the sending password error.

Any one have any ideas on how to fix this ?

I looked on ATTs web page and they have several pages about using thunderbird but i could not get it to work.  So i called the support number and they said att does not support thunderbird even though they have several pages on how to set it up.  Go figure !

Thanks in advance for any help

---

### Post by silverwolf636 on 2009-09-10
I see this is an old thread but I am having the same problem.  I keep going and if I get it working I will let you know.

---

### Post by yabbadabbadont on 2009-09-10
Works fine for me with thunderbird.  ATT sent out an e-mail in May of 2007 with instructions on how to enable secure connections.  From the e-mail:
> Alternatively, you may take the following steps to change the settings on 
your desktop or mobile email client program:

1.	Open your email client program.
2.	Locate the email account settings for your particular client.
3.	Change the POP server to pop.att.yahoo.com.
4.	Change the SMTP server to smtp.att.yahoo.com.
5.	Check the option labeled Use an encrypted connection (SSL) and change the SMTP port to 465.
6.	Check the option labeled Use an encrypted connection (SSL) and change the POP3 port to 995.
7.	Confirm the above settings then click OK.


---

### Post by bkratz on 2009-09-10
> **silverwolf636 said:**
> I see this is an old thread but I am having the same problem.  I keep going and if I get it working I will let you know.



I use evolution all the time:  the secret is to do the following

set up receiving for pop
server=== pop.att.yahoo.com:995
use ssl

setup for outgoing
server   smtp
smtp.att.yahoo.com:465
use ssl

make sure you use :995 and :465

---

### Post by yabbadabbadont on 2009-09-10
Wow.  I wish I had posted that information... oh, wait.  :D

---

### Post by bkratz on 2009-09-10
> **yabbadabbadont said:**
> Wow.  I wish I had posted that information... oh, wait.  :D



It always seems to me awhile to do just about anything ( I looked at my settings ) while answering!

---

