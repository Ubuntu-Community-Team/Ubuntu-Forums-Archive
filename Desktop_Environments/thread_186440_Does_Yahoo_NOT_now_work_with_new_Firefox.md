---
title: "Does Yahoo NOT now work with new Firefox?"
date: 2006-06-01
forum: Desktop Environments
---

### Post by Neobuntu on 2006-06-01
What's the deal with this certificate warning? It says some odd site may be spoofing the login on [http://my.yahoo.com](http://my.yahoo.com) . 

How do I fix this (Dapper Firefox 1.5.0.3)?

---

### Post by nismoskys on 2006-06-02
i dont see anything..out of the ordinary..when i go there.
using the same version as you.

---

### Post by Neobuntu on 2006-06-02
I removed and reinstalled Firefox so I must be missing some certificate database telling Firefox what good or not. 

Anyone know what to do? It prob is a configuration thing but I can't be sure the sites not being spoofed.

---

### Post by MattCarp on 2006-06-02
[QUOTE=Neobuntu]I removed and reinstalled Firefox so I must be missing some certificate database telling Firefox what good or not. 

Anyone know what to do? It prob is a configuration thing but I can't be sure the sites not being spoofed.[/QUOTE]

I've got the same problem.  I was dorking with Firefox and I think something is mis-configured.  (I still have the ubuntu packaged 1.5.0.3)  I am on Dapper Drake, 6.06

In Firefox, when I go to the preferences>advanced>security>view certificates>authorities, it's blank.  i.e., I don't have any certificate authorities installed  (CAN SOMEONE CONFIRM THAT THIS IS INCORRECT?)

However, all of my root certificates are in /usr/share/ca-certificates/mozilla, but firefox is just not pointing to them.

I couldn't find a configuration variable in "about:config" that would fix it.

I've tried reinstalling the firefox and mozilla-firefox packages.  No luck

---

### Post by aysiu on 2006-06-02
I'm using Firefox 1.5.0.4 and have not experienced this problem.

Maybe upgrade?

---

### Post by MattCarp on 2006-06-02
[QUOTE=MattCarp]I've got the same problem.  I was dorking with Firefox and I think something is mis-configured.  (I still have the ubuntu packaged 1.5.0.3)  I am on Dapper Drake, 6.06

In Firefox, when I go to the preferences>advanced>security>view certificates>authorities, it's blank.  i.e., I don't have any certificate authorities installed  

I've tried reinstalling the firefox and mozilla-firefox packages.  No luck[/QUOTE]

Ok-  I was able to fix it by removing (purging) and reinstalling, just one more time!!

Although I preserved my bookmarks, it turns out that the purge didn't actually delete them.  (hmm...)  But, after the reinstall, I was able to go into the certificate authorities window and see all of the usual root CA's  (VeriSign, Thawte, RSA, etc.).

First I closed all Firefox sessions and then here are the packages I purged (from Synaptic):

firefox
firefox-gnome-support
gnome-app-install
mozilla-firefox
yelp

I probably didn't need to do all of these, but they were dependent on firefox, so I just thought it best to reinstall the whole group.

I then went into Synaptic and selected all of those packages for installation.  I also selected that libnss3 be reinstalled.  libnss3 may have done the trick, as I think that's a common package for ssl support for mozilla.

Anyway, it now works!!!!

---

### Post by stenka on 2006-12-10
I just got the same very weired problem, with the firefox package of Edgy.

Of course it didn't impact just Yahoo but all HTTPS sites as there were no master certificate.

I can confirm that reinstalling the libnss3 package - and only this one - solved the problem.

Thanks a lot for this tip ! (I spent a lot of time before finding this).

---

### Post by pearlie on 2007-01-23
This solution  - reinstalling libnss3 - also worked for me, using Firefox 2.0 under 6.06 AMD64.  Didn't work the first time; might have been the funny song and little dance I did the second time.  :D

---

