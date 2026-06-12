---
title: "Nautilus Elementary breadcrumbs"
date: 2010-05-30
forum: Desktop Environments
---

### Post by aaronp on 2010-05-30
Hi guys,

I tried to install nautilus-elementary as per the instructions here:

[http://www.techdrivein.com/2010/05/what-is-nautilus-elementary-and-how-to.html](http://www.techdrivein.com/2010/05/what-is-nautilus-elementary-and-how-to.html)

Everything works ok but I can't see anything has changed in Nautilus and even though I enable the breadcrumbs in the Tweaks section, the breadcrumbs don't appear at all.

Any thoughts?

thanks
Aaron

---

### Post by bra|10n on 2010-05-30
Enter the following into a terminal.
```
wget http://gnaag.k2city.eu/nautilus-breadcrumbs-hack.tar.gz
``````
tar -xvf nautilus-breadcrumbs-hack.tar.gz
``````
nautilus -q
```I'm guessing you know the rest;)

---

### Post by hok00age on 2010-05-30
> **aaronp said:**
> Hi guys,

I tried to install nautilus-elementary as per the instructions here:

[http://www.techdrivein.com/2010/05/what-is-nautilus-elementary-and-how-to.html](http://www.techdrivein.com/2010/05/what-is-nautilus-elementary-and-how-to.html)

Everything works ok but I can't see anything has changed in Nautilus and even though I enable the breadcrumbs in the Tweaks section, the breadcrumbs don't appear at all.

Any thoughts?

thanks
Aaron

Read this article:
[http://www.webupd8.org/2010/04/nautilus-elementary-breadcrumbs-for-any.html]("http://www.webupd8.org/2010/04/nautilus-elementary-breadcrumbs-for-any.html")

Hope it helps you
Regards :)

---

### Post by aaronp on 2010-05-30
Thanks bra|10n, but that's part of the instructions I followed.

---

### Post by aaronp on 2010-05-30
> **hok00age said:**
> Read this article:
[http://www.webupd8.org/2010/04/nautilus-elementary-breadcrumbs-for-any.html]("http://www.webupd8.org/2010/04/nautilus-elementary-breadcrumbs-for-any.html")

Hope it helps you
Regards :)

Thanks, but no same behaviour. I tried manually downloading and copying all the files to my home folder but still no change to Nautilus.

---

### Post by nilarimogard on 2010-05-30
If it doesn't work, it means you're using a text-based location bar. Use this:


gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry false

---

### Post by aaronp on 2010-05-30
> **nilarimogard said:**
> If it doesn't work, it means you're using a text-based location bar. Use this:


gconftool-2 --type=Boolean --set /apps/nautilus/preferences/always_use_location_entry false

Correct! Thanks very much.

---

### Post by ameseisch on 2010-10-06
I was having a hard time with this problem, but found an easy fix. 

In nautilus I needed to select View>Location Bar. 

For some reason it was unchecked.

---

