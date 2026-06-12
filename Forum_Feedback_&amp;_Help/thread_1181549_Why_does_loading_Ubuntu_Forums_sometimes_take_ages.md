---
title: "Why does loading Ubuntu Forums sometimes take ages?"
date: 2009-06-08
forum: Forum Feedback &amp; Help
---

### Post by TideMan on 2009-06-08
Sometimes (frequently, even), I click a thread or new page on this forum and my system sits there waiting for Ubuntu Forums.........
If I click stop and try again, it will sometimes load straight away.
But if I leave it and it sits there for a minute or two, the system will come back asking if I want to save a .php file.
Is it me or is it that this forum is very slow sometimes?
I'm using Firefox and I have cable with nominal download of 4 Mbits/s.

---

### Post by kevdog on 2009-06-08
This happens to me too from time to time.  I'm not sure of the reason.

---

### Post by s.fox on 2009-06-08
> **TideMan said:**
>  asking if I want to save a .php file

I also get this too sometimes in firefox.  Not just on these forums either.  I can't seem to recreate the event deliberately though.  It just seems to happen.

-Ash R

---

### Post by _Purple_ on 2009-06-08
> **TideMan said:**
> asking if I want to save a .php file.

> **Ash R said:**
> I also get this too sometimes in firefox.  Not just on these forums either.  I can't seem to recreate the event deliberately though.  It just seems to happen.

-Ash R

I had similar problem that was caused by apache. I am not sure if that is the case here. Fixed it by adding the following line to the file /etc/apache2/apache2.conf:

```
AddType application/x-httpd-php .php .phtml
```

Then restart Apache.

---

