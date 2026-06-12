---
title: "Gtk-WARNING (locale) error"
date: 2006-03-15
forum: Desktop Environments
---

### Post by stepore on 2006-03-15
hello (ubuntu) world,

the last few days i've been getting an error message in the terminal when ever i launch an application. it sometimes happens doing other things in terminal. is it a localization error, not sure what i could have done to cause this or how to fix it. 

i've tried googling but nothing good so far. any tips?
here's the error, when i launch gnome-calculator for instance:

(gnome-calculator:9591): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

cheers,
johnny

---

### Post by stepore on 2006-03-16
hey folks -- i do hope someone has some idea, please, as to what's going on. there are tons of errors exactly like this on google, but haven't found an answer. aside from the previous error in terminal i also get this when i type locale:

$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en
LC_CTYPE="en"
LC_NUMERIC="en"
LC_TIME="en"
LC_COLLATE="en"
LC_MONETARY="en"
LC_MESSAGES="en"
LC_PAPER="en"
LC_NAME="en"
LC_ADDRESS="en"
LC_TELEPHONE="en"
LC_MEASUREMENT="en"
LC_IDENTIFICATION="en"
LC_ALL=

---

