---
title: "Dapper No Print Problem"
date: 2006-06-09
forum: Desktop Environments
---

### Post by not_yet on 2006-06-09
In breezy my brother hl-1250 worked perfectly

In dapper it does not work at all

Is there a solution to this problem?

There is a driver available for my printer, a ppd file

How / where do I install a ppd ?](*,) 

thanks

---

### Post by not_yet on 2006-06-09
anyone:)

---

### Post by jimbob on 2006-06-09
If you have a *.ppd file for your printer just copy it to /usr/share/cups/model/(your ppd file here)

Then restart cups:
  >killall cupsd
  >/etc/init.d/cupsys start

This is how I got my Apollo P-2500 to work.  It was left out of the printer list on Dapper but worked fine on Breezy.  (Still not there by the way even after filing a bug report some time ago).
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

___________________________________
AMD 64 Sempron 3400+ 512MB 60GB IDE 80 GB SATA
Gigabyte GA-K8NS socket 754 nForce3 250 chipset
nVidia GeForce2 MX/MX400 64 MB

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

