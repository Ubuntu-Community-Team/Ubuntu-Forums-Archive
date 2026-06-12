---
title: "sendmail and postfix"
date: 2006-10-04
forum: Desktop Environments
---

### Post by mitjab on 2006-10-04
```
"For the Mail functions to be available, PHP must have access to the sendmail binary on your system during compile time. If you use another mail program, such as qmail or postfix, be sure to use the appropriate sendmail wrappers that come with them. PHP will first look for sendmail in your PATH, and then in the following: /usr/bin:/usr/sbin:/usr/etc:/etc:/usr/ucblib:/usr/lib. It's highly recommended to have sendmail available from your PATH. Also, the user that compiled PHP must have permission to access the sendmail binary."
```

so how can i have boath postfix and sendmail that mail() funxtion will work?

Thx

---

### Post by skymt on 2006-10-04
All mail() needs is a command called "sendmail", which Postfix provides.

---

### Post by mitjab on 2006-10-04
i read that i need postfix sendmail wrapper and i install postfix but what must i enter in php.ini that will strat using sendmail. I google, using serach in ubuntu forum but can not find my answer. Can you help me?

Thx

---

### Post by skymt on 2006-10-04
> **mitjab said:**
> i read that i need postfix sendmail wrapper and i install postfix but what must i enter in php.ini that will strat using sendmail. I google, using serach in ubuntu forum but can not find my answer. Can you help me?

Thx

It should just work. The bit of documentation you posted says it looks for the sendmail command in (among other places) /usr/sbin, and that's where the postfix package puts it.

---

### Post by mitjab on 2006-10-05
i try with path /usr/sbin/sendmail but doesn't work, still doesn't send mail.

if i try
/usr/sbin/sendmail -d0.1 -bv root

i get error about unrecognized -d paramether.

any idea why?

---

### Post by skymt on 2006-10-05
Is Postfix set up? If not, check out [the howto on the wiki](https://help.ubuntu.com/community/Postfix).

---

### Post by skymt on 2006-10-05
> **mitjab said:**
> if i try
/usr/sbin/sendmail -d0.1 -bv root

i get error about unrecognized -d paramether.

any idea why?

Maybe because Postfix sendmail doesn't have a -d option? ;) 

What are you trying to do with the -d0.1 bit? There's probably another option for that. You can look at the sendmail manual (run "man sendmail") if you want.

---

### Post by mitjab on 2006-10-05
yes i think that postfix isn't install properly, i will reinstall it again by your wiki.

I see this!

```
In this setup I assume that your domain is yourdomain.com and it has a valid MX record call mail.yourdomain.com. Remember to replace yourdomain.com with your actual domain in the example codes in this howto. Also I assume that you know what an MX record is. To find out MX your type in a terminal:
```

i do not have a valid  MX record call mail.mitjab.com.
What i must do that i will have it?
is this howto ok for dns with bind9
[http://www.ubuntuforums.org/showthread.php?t=236093](http://www.ubuntuforums.org/showthread.php?t=236093)
or better to use
[https://help.ubuntu.com/community/BIND9ServerHowto?highlight=%28bind%29](https://help.ubuntu.com/community/BIND9ServerHowto?highlight=%28bind%29)

thx

---

### Post by skymt on 2006-10-05
I am in no way an expert on DNS. However, you probably don't need your own DNS server. You should probably contact your domain name registrar for this sort of thing.

---

### Post by pod25 on 2006-10-05
> **skymt said:**
> I am in no way an expert on DNS. However, you probably don't need your own DNS server. You should probably contact your domain name registrar for this sort of thing.
He will need DNS working, my reason for saying that is, I recall seeing a previous post from this guy, he wants to set up a web server so he can host other peoples web sites.
I have already suggested installing ISPconfig but he refused.

---

### Post by envis on 2006-10-19
once your postfix is installed on your Ubuntu, open  terminal and write: postconf -d sendmail_path that will tell you whta is the sendmail path that you need to put in your php.ini dont forget to add -t and -i after, here's how it looks in my php.ini: sendmail_path = /usr/sbin/sendmail -t -i

iam no expert but i can tell you it works for me

---

