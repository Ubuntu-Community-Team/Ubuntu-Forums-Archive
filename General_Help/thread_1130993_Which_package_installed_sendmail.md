---
title: "Which package installed sendmail"
date: 2009-04-20
forum: General Help
---

### Post by Tyconic on 2009-04-20
Hey all, I'd like to find out which package was responsible for installing sendmail (so I can rid my computer of it)

Is there a way to do this using apt? synaptic?

Thanks

---

### Post by unutbu on 2009-04-20
To find out which package provides a file installed on your machine, type into a terminal:
```

dpkg -S /path/to/file
```
Or, in your case,
```
dpkg -S $(which sendmail)
```

Alternatively you can search for which package provides "bin/sendmail" by going to [http://packages.ubuntu.com/](http://packages.ubuntu.com/).
Go to the "Search the contents of packages" area.
Click the "packages that contain files whose names end with the keyword" radio button. 
Search for "bin/sendmail".

The results are here:
[http://packages.ubuntu.com/search?searchon=contents&keywords=bin%2Fsendmail&mode=&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=bin%2Fsendmail&mode=&suite=intrepid&arch=any)

It shows that any of these packages could have installed sendmail:
```

citadel-mta, courier-mta, esmtp-run, exim4-daemon-heavy, exim4-daemon-light, masqmail, msmtp-mta, nbsmtp, nullmailer, postfix, ssmtp, xmail
```

---

### Post by Tyconic on 2009-04-20
Thanks unutbu, that's quite a useful tool. FYI

```

dpkg -S /usr/sbin/sendmail

```

didn't turn up anything but 

```

dpkg -S /usr/sbin/checksentmail

```

turned up sendmail-base

---

### Post by HermanAB on 2009-04-20
The program you perceive to be 'sendmail' is likely just a compatibility program provided by whichever MTA you installed eg. Postfix, Qmail, Citadel, Zimbra... they will all install a little program called 'sendmail', in order to ensure that common scripts still work.

---

