---
title: "SMTP setup"
date: 2009-03-07
forum: General Help
---

### Post by jonwcode on 2009-03-07
I'm just asking away on today.... Anyways.. lol So I'm a new user to ubuntu server, and I'm very excited to learn how to use it. And the only way I can seem to learn is to ask questions! :D So I have the SMTP server install on my server.... Just not to sure why it isn't working. I tested the SMTP Server when I installed phpBB3 forums on my server. I notice it isn't sending activation emails. And that has to be because the SMTP server isn't working. So how do I configure my SMTP server? Is there a good step by step guide out there that explains how to do this?


Thanks for the help. :)

Jon W

---

### Post by Dr Small on 2009-03-07
What SMTP server did you install?

---

### Post by jonwcode on 2009-03-07
I'm not totally sure. I think the name is Postfix. I didn't really know there was more then one. lol

---

### Post by dcstar on 2009-03-07
> **jonwcode said:**
> I'm not totally. I think the name is Postfix. I didn't really know there was more then one. lol

Look in your System Log for the mail messages.

---

### Post by jonwcode on 2009-03-07
How is that done? I'm a total noobie. lol

---

### Post by jonwcode on 2009-03-07
Anyone?

---

### Post by dcstar on 2009-03-07
> **jonwcode said:**
> How is that done? I'm a total noobie. lol

System-Administration-System Logs.

---

### Post by jonwcode on 2009-03-07
I'm using ubuntu server.

---

### Post by dcstar on 2009-03-07
> **jonwcode said:**
> I'm using ubuntu server.

```
cd /var/log
more syslog
more mail.log
more mail.warn
more mail.err
```

---

### Post by T.J. on 2009-03-07
If you look in /var/log/mail.log you should see some information.

Working with Postfix can be pretty elaborate. I use it on ISP mailservers. With all things, there are "catch 22's".  I'll try to help, if you can confirm that you are using Postfix.

A lot of basic information can be found here: [http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

---

### Post by jonwcode on 2009-03-07
Yes, I'm using postfix. I just install sendmail too. I'm really trying to get this to work, and nothing seems to be working.

---

### Post by T.J. on 2009-03-08
You shouldn't try to use Postfix and Sendmail at the same time, they are pretty much mutually exclusive of each other.  You have to perform some setup yourself.  

Can you post your main.cf file from /etc/postfix, and I'll have a look?

---

### Post by dcstar on 2009-03-09
> **T.J. said:**
> You shouldn't try to use Postfix and Sendmail at the same time, they are pretty much mutually exclusive of each other.  You have to perform some setup yourself.  

Can you post your main.cf file from /etc/postfix, and I'll have a look?

A lot of things could have been posted already to help "fix" this problem, that lack of any of them makes any sort of meaningful assistance pretty much impossible.

---

