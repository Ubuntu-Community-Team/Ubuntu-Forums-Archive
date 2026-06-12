---
title: "bibus and locale"
date: 2007-02-20
forum: Education &amp; Science
---

### Post by tristan@Ubuntu on 2007-02-20
Hello,

I tried to install bibus on edgy by adding that to my source list:
```
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb-src http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
```

and then:

```
sudo apt-get install python-pysqlite2 bibus bibus-doc-en
```

No problem until that point, but then:

```
[tristan@babylon ~] bibus
Traceback (most recent call last):
  File "/usr/bin/bibus", line 67, in ?
    locale.setlocale(locale.LC_ALL,'en_US')                             # use english if any problem
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
``` 

I found some more or less relevant threads, and so I tried to modify the /usr/share/bibus/bibus.cfg file, by adding things like:

```
[LANG]
language =en
```

it doesn't work... Thank you...

-Tristan

here is my locale:
```
[tristan@babylon ~] locale
LANG=C
LANGUAGE=en
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=
```

---

### Post by slaanco on 2007-02-20
> **tristan@Ubuntu said:**
> Hello,

I tried to install bibus on edgy by adding that to my source list:
```
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb-src http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
```and then:

```
sudo apt-get install python-pysqlite2 bibus bibus-doc-en
```No problem until that point, but then:

```
[tristan@babylon ~] bibus
Traceback (most recent call last):
  File "/usr/bin/bibus", line 67, in ?
    locale.setlocale(locale.LC_ALL,'en_US')                             # use english if any problem
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
```I found some more or less relevant threads, and so I tried to modify the /usr/share/bibus/bibus.cfg file, by adding things like:

```
[LANG]
language =en
```it doesn't work... Thank you...

-Tristan

here is my locale:
```
[tristan@babylon ~] locale
LANG=C
LANGUAGE=en
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=
```

i would try to set LANGUAGE=en_US

---

### Post by tristan@Ubuntu on 2007-02-21
Well, I tried to play with locale-gen, dpkg-reconfigure locales, /etc/environment , ...
I even tried:
```
set LANGUAGE=en_US
export $LANGUAGE
```

so now my locales are like that:

```
[tristan@babylon ~] locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US
LC_CTYPE="en_US"
LC_NUMERIC="en_US"
LC_TIME="en_US"
LC_COLLATE="en_US"
LC_MONETARY="en_US"
LC_MESSAGES="en_US"
LC_PAPER="en_US"
LC_NAME="en_US"
LC_ADDRESS="en_US"
LC_TELEPHONE="en_US"
LC_MEASUREMENT="en_US"
LC_IDENTIFICATION="en_US"
LC_ALL=
```

but still: 
```
[tristan@babylon ~] bibus
Traceback (most recent call last):
  File "/usr/bin/bibus", line 67, in ?
    locale.setlocale(locale.LC_ALL,'en_US')                             # use english if any problem
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
  
```

I'm quite lost...

-Tristan

---

