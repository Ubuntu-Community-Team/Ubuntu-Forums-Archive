---
title: "Need standard /etc/apache2/apache2.conf"
date: 2006-09-07
forum: Desktop Environments
---

### Post by MaleqAlhaq on 2006-09-07
Hi!
 I had some trouble with my Apache2, so removed all the Apache packages and also deleted the /etc/apache2/ directory ... This was a huge mistake, as I found out after reinstalling Apache2. The reinstall did not regenerate the config file. Everything else worked fine, but the /etc/apche2/apache2.conf was missing (and apache wont start, as it can't find the config). I tried using the default config from the documentation, but that didnt work too good either... Can somebody please post his / her /etc/apche2/apache2.conf? Preferably in the standard version without much added modules? That would be really great.

Thanks

Phil

---

### Post by DtJee on 2006-09-07
I had a similiar problem. But I´ve forgotten to remove apache2-common... after purging it ... I´ve reinstalled it .. an the config showed up again...

---

### Post by MaleqAlhaq on 2006-09-07
I even tried purging it, but still no effect, or better: the same effect... I have no config file...

Edit: I'm just installing the Apache2 again, and it wont even include the /etc/init.d/apache2 script... could somebody post that, too?
Thank you very much !

Edit2: OK, I must have done something wrong while purging the packet last time.... I purged it again and now it works again... Thank you!

---

### Post by TwoWordz on 2006-09-07
I am not sure (I am not on my linux box right now) but you should have a sample in /usr/share/doc/.

Most of the time there is an exemple configuration there.

TW

---

### Post by atia on 2007-10-11
Hi!
I had the some problem that you, but the httpd.conf and sites-available/default are also missing (this last one I'm not sure if it's important) and I'm still not having an apache2.conf file.
Did you fix the problem? how did you reinstalled apache2? I've tried with synaptic but I'm afraid there are missing files...
Thanks!!
Atia

---

### Post by kyogoiano on 2008-03-12
I had the same problem installing apache2, the reason was that, i'd removed Apache and Apache2, to start eith everything clean, normally we thought that is just necessary to install Apache2 and everything is done, but is also necessary to remove all packages of apache2 and install then again including apache-common too , in order to fix the problem! OK, i expect that solution could help someone with the same problem ... :)

---

### Post by netzstriker on 2008-03-13
I had the same issue. Just resolved it. every time i would try to purge apache-common and then re-install I did not get the default /etc/apache2 directory back. This time I used "aptitude" instead of just apt-get .Make sure to go to options and uncheck the part about resolving and install dependent packages automatically, it will be cache22 if you don't. Then find the apache2-common, purge, commit changes, then go back to options re-enable the automatic dependency, then re-install.

hope this helps.

-Adrian

---

### Post by beefiron on 2008-03-28
Just wanted to say thanks to the last poster - Adrian.

I had the same issue. I opened up the synaptic package manager and marked apache-commons for complete removal. Once that was done, reinstalling it using apt-get recreated my lost apache2.conf file.

Is there a reason why nobody has just posted their apache2.conf file, obviously with any sensitive information removed? I think it would be useful for there to be one here for fools like me who, in a moment of madness, delete their existing file and just want to restore it with a vanilla one.

M.

---

### Post by moxy1 on 2008-04-11
I'm having this problem on Ubuntu server and can't use the synaptic. Anyone have command line help?

---

