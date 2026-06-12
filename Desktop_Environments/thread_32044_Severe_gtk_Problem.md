---
title: "Severe gtk Problem"
date: 2005-05-05
forum: Desktop Environments
---

### Post by sp33dy on 2005-05-05
Hi people,

Forgive my noobishness, but  I am having a severe problem with all gtk apps. I keep getting two warning from Gtk and Gdk that the Locale not supported by C library. I have no idea how I got to this stage as I have only one language installed, the default english installation.

Any help is appreciated,
Thanks.

---

### Post by poofyhairguy on 2005-05-05
[QUOTE=sp33dy]Hi people,

Forgive my noobishness, but  I am having a severe problem with all gtk apps. I keep getting two warning from Gtk and Gdk that the Locale not supported by C library. I have no idea how I got to this stage as I have only one language installed, the default english installation.

Any help is appreciated,
Thanks.[/QUOTE]


Sounds like something happed bad during the install. Did you install from a mailed CD or and install ISO burned at low speeds?

---

### Post by sp33dy on 2005-05-05
No it installed fine, and everything has worked without problems for 2 months. The last think I instaled was the Jack sound daemon...but I do not think that did it.

Is there a way to change or set the locale? Other apps do not complain, only the gtk ones.

---

### Post by sp33dy on 2005-05-06
*bump*

---

### Post by sp33dy on 2005-05-06
*bump*

I really need help here please...

---

### Post by khc on 2005-05-07
What's the output of `locale'?

---

### Post by sp33dy on 2005-05-08
I get the following output...

> 
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_CA.UTF-8
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=


---

### Post by khc on 2005-05-08
Is en_CA.UTF8 installed? Try `sudo dpkg-reconfigure locales', and make sure that en_CA.UTF8 is selected.

---

### Post by sp33dy on 2005-05-08
I have a problem, locales is not installed and will not install because of a dependency 'glibc-2.3.2.ds1-20ubuntu13'. I can't find this package to install it.

Is it normal not to have the locales package missing? I do not remember removing it.

---

### Post by sp33dy on 2005-05-08
I think I found the problem. I had to upgrade libc6 to version 2.3.2.dsl-21. I did this so I could install the latest aMule and mplayerplug-in packages. I grabbed the latest locales package and now everything is fine....phew! :D

Thanks

---

