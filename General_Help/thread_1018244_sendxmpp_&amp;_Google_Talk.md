---
title: "sendxmpp &amp; Google Talk"
date: 2008-12-21
forum: General Help
---

### Post by dgath on 2008-12-21
Does anyone know how to get sendxmpp working with their Google Talk account?  I've scoured the web looking for answers and haven't come up with any.

Here's my output
```

derek@linbox:~$ echo "Test" | sendxmpp -t -j talk.google.com:5222 -u someuser -p somepass anotheruser@gmail.com
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1787.
Use of uninitialized value $sid in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 2548.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 2550.
Use of uninitialized value $sid in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 1636.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1637.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 1637.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1639.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1641.
Use of uninitialized value in numeric eq (==) at /usr/share/perl5/XML/Stream.pm line 1641.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1643.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1646.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 2433.
Use of uninitialized value $sid in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 2548.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 2550.
Use of uninitialized value in hash element at /usr/share/perl5/Net/XMPP/Connection.pm line 383.
Use of uninitialized value in string eq at /usr/bin/sendxmpp line 450.
Error 'AuthSend': [?]
Use of uninitialized value $sid in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 1636.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1637.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1639.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1641.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1274.
Use of uninitialized value in string eq at /usr/share/perl5/XML/Stream.pm line 1274.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1274.
Use of uninitialized value in string eq at /usr/share/perl5/XML/Stream.pm line 1274.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1277.
Use of uninitialized value in delete at /usr/share/perl5/XML/Stream.pm line 1277.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1278.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in delete at /usr/share/perl5/XML/Stream.pm line 1282.

```

And I get nothing in my IM client.  :confused:

Thanks

---

### Post by dc2447 on 2009-10-17
> **dgath said:**
> Does anyone know how to get sendxmpp working with their Google Talk account?  I've scoured the web looking for answers and haven't come up with any.

Here's my output
```

derek@linbox:~$ echo "Test" | sendxmpp -t -j talk.google.com:5222 -u someuser -p somepass anotheruser@gmail.com
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1787.
Use of uninitialized value $sid in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 2548.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 2550.
Use of uninitialized value $sid in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 1636.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1637.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 1637.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1639.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1641.
Use of uninitialized value in numeric eq (==) at /usr/share/perl5/XML/Stream.pm line 1641.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1643.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1646.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 2433.
Use of uninitialized value $sid in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 2548.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 2550.
Use of uninitialized value in hash element at /usr/share/perl5/Net/XMPP/Connection.pm line 383.
Use of uninitialized value in string eq at /usr/bin/sendxmpp line 450.
Error 'AuthSend': [?]
Use of uninitialized value $sid in concatenation (.) or string at /usr/share/perl5/XML/Stream.pm line 1636.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1637.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1639.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1641.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1274.
Use of uninitialized value in string eq at /usr/share/perl5/XML/Stream.pm line 1274.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1274.
Use of uninitialized value in string eq at /usr/share/perl5/XML/Stream.pm line 1274.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1277.
Use of uninitialized value in delete at /usr/share/perl5/XML/Stream.pm line 1277.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1278.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in hash element at /usr/share/perl5/XML/Stream.pm line 1280.
Use of uninitialized value $sid in delete at /usr/share/perl5/XML/Stream.pm line 1282.

```

And I get nothing in my IM client.  :confused:

Thanks

No matter what I tried I couldn't send as a user @ gmail - ended up using an @jabber.org account to sent to my google talk account and it worked first time

---

### Post by gamid on 2010-02-24
1. make sure that you are using latest sendxmpp (I have sendxmpp 1.20)

2. add your Google Talk account info to the .sendxmpprc file:
[email]your_name@gmail.com;talk.google.com[/email] your_password

3. use the following command to send message to Google Talk user [EMAIL="someone@gmail.com"]someone@gmail.com[/EMAIL]:
$ echo "GTalk test" | sendxmpp -t -u your_name -o gmail.com someone

Example:
.sendxmpprc: [email]john@gmail.com;talk.google.com[/email] password

$ echo "GTalk test" | sendxmpp -t -u john -o gmail.com someone

---

### Post by dc2447 on 2010-02-26
anybody know if it's possible to make sendxmpp use a proxy?

---

