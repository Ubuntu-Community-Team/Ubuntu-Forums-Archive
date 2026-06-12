---
title: "Totem &amp; DVD"
date: 2005-02-07
forum: Desktop Environments
---

### Post by recmar on 2005-02-07
Does anybody know how to enable DVD's in totem?

---

### Post by lt_kije on 2005-02-07
If you're trying to play encrypted DVDs (and you most likely are...), you need libdvdcss. Unfortunately, due to various legal issues, libdvdcss is classed as a "circumvention device" which makes it illegal to distribute in certain contexts. You can find a quick reference on libdvdcss, et al on the wiki's RestrictedFormats page[1].

To get encrypted DVDs playing in Ubuntu, you need to add the Debian-marillat repository to your apt sources.list, then grap libdvdcss2. For more complete instructions, refer to the wiki (see link below).

HTH

lt_kije

[1]http://www.ubuntulinux.org/wiki/RestrictedFormats

---

### Post by recmar on 2005-02-08
Actually i've already installed libdvdcss but totem complains about plugins. Do I need to configure totem?

---

### Post by trivialpackets on 2005-02-08
I have found that these steps will work for some DVD's, but not all.  A bit frustrating, but at least I know that I'm close.  Is this working for any dvd's?

---

### Post by recmar on 2005-02-08
To be honest I've tried just one. But I'll check others as well and give you info about results.

---

