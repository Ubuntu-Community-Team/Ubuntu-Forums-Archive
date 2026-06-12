---
title: "[Hardy] Have to login twice..."
date: 2008-05-22
forum: Desktop Environments
---

### Post by excogitation on 2008-05-22
So when I get to the login screen and
enter my username and password -> the console appears -> a few seconds go by ->
login screen again -> username and password -> successful login.

It's not that big of a deal - it's just annoying.

I'm only using Ubuntu for ~3 months so tell me whatever information you
need to help me and I'll gladly provide it.

[dmesg output]("http://de.pastebin.com/m49418feb")
If any other problems stick out - I'd be interested in fixing those as well :???:

---

### Post by excogitation on 2008-05-25
bump?

---

### Post by prshah on 2008-05-26
> **excogitation said:**
> So when I get to the login screen and
enter my username and password -> the console appears -> a few seconds go by ->
login screen again -> username and password -> successful login.


Your dmesg looks fine except for a small error with the ata2.00 device; but I don't believe that to be related.

A more suitable source of information will be your '/var/log/Xorg.0.log' file... can you attach that?

---

### Post by excogitation on 2008-05-26
Thanks for taking the time, prshah.


[Xorg.0.log]("http://pastebin.com/m257a065c")

---

