---
title: "[SOLVED] Website &amp;quot;highjack&amp;quot; Firefox 3.0.4 ubuntu 8.10"
date: 2008-12-12
forum: General Help
---

### Post by kduivenv on 2008-12-12
Hello,

I am rather new in using Ubuntu 8.10 and Firefox 3.0.4

I try to visit the site: [http://webmail.ohv.net/](http://webmail.ohv.net/)
(This should give me a login screen for roundcube webmail.)

Instead I get a publicity site,about "off-highway vehicles"

I don't understand. It works perfectly well on my windows computer, but not on my ubuntu computer.

I try to do this from Belgium.

Can anyone help me?

Thanks a lot

---

### Post by ajcham on 2008-12-12
I get the same publicity site.  I've tried visiting through a few proxies (US, Germany, New Zealand) also, but no change.

I don't have a Windows machine, so I can't try that.  If someone else can confirm how this URL responds in Windows that probably would help.

---

### Post by Dr Small on 2008-12-12
wget is giving me the same page as Firefox, and netcat is receiving no output. Someone needs to verify that this site works on Windows.

---

### Post by ajcham on 2008-12-12
kduivenv, I've sussed it: there is a typo in the URL.

[http://webmail.**ovh**.net]("http://webmail.ovh.net") does indeed find a roundcube login.

---

### Post by kduivenv on 2008-12-13
@ajcham
You're right. Now it works. Thanks a lot!

---

