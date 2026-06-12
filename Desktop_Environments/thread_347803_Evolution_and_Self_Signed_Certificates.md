---
title: "Evolution and Self Signed Certificates"
date: 2007-01-27
forum: Desktop Environments
---

### Post by TerryHowe on 2007-01-27
Evolution drives me nuts because it won't permanently accept a self signed certificate.  My ISP uses a self signed certificate, so every time I send a mail Evolution complains the certificate is bad.  Anyone else have this problem?  How to work around.  Searches have been futile.

---

### Post by taurus on 2007-01-27
Have you tried thunderbird?  It's another option.

---

### Post by ThomasNovin on 2008-04-02
Go to Edit->Preferences->Certificates->Authorities

There you will probably find your mail server. In my case, since it's an Courier Mail server that I'm connecting to I could find it under Courier Mail Server and then three certificates all with the name of the mail host.

I then clicked Edit for all three of those and checked all boxes (trust this CA for...).

I then exited Evolution and also did 'evolution --force-shutdown' from a terminal.

I then started Evolution and the problem was gone!

---

