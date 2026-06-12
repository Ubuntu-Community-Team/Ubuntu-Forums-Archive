---
title: "Locales problem en_US.utf8"
date: 2006-02-20
forum: Desktop Environments
---

### Post by burnboy on 2006-02-20
I am pulling my hair out because of this problem. I've done everything I could imagine doing.

dpkg-reconfigure localeconf
dpkg-reconfigure locales

Made sure there were no manual entries in /etc/environment or /etc/locale.gen that were causing problems. I'm running Badger (if you hadn't guessed). Here's all the pertinent information I can come up with:

The error itself:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = "ISO-8895-1",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

The config files

```
burnboy@spike ~ $ cat /etc/environment
### BEGIN DEBCONF SECTION FOR localeconf
# Do not edit within this region if you want your changes to be preserved
# by debconf.  Instead, make changes before the "### BEGIN DEBCONF SECTION
# FOR localeconf" line, and/or after the "### END DEBCONF SECTION FOR
# localeconf" line.
### END DEBCONF SECTION FOR localeconf

LANG=en_US.UTF-8
burnboy@spike ~ $ cat /etc/locale.gen
# This file lists locales that you wish to have built. You can find a list
# of valid supported locales at /usr/share/i18n/SUPPORTED. Other
# combinations are possible, but may not be well tested. If you change
# this file, you need to rerun locale-gen.
#
### BEGIN DEBCONF SECTION FOR localeconf
# Do not edit within this region if you want your changes to be preserved
# by debconf.  Instead, make changes before the "### BEGIN DEBCONF SECTION
# FOR localeconf" line, and/or after the "### END DEBCONF SECTION FOR
# localeconf" line.
en_US.UTF-8 UTF-8
### END DEBCONF SECTION FOR localeconf

burnboy@spike ~ $ locale
locale       localedef    locale-gen   localepurge
burnboy@spike ~ $ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="ISO-8895-1"
LC_NUMERIC="ISO-8895-1"
LC_TIME="ISO-8895-1"
LC_COLLATE="ISO-8895-1"
LC_MONETARY="ISO-8895-1"
LC_MESSAGES="ISO-8895-1"
LC_PAPER="ISO-8895-1"
LC_NAME="ISO-8895-1"
LC_ADDRESS="ISO-8895-1"
LC_TELEPHONE="ISO-8895-1"
LC_MEASUREMENT="ISO-8895-1"
LC_IDENTIFICATION="ISO-8895-1"
LC_ALL=ISO-8895-1
```

I seem to have cleared it up in the past but after rebooting or some unseen action, it starts coming up with the error again.

Any help is greatly appreciated. Some insight into why this happens.

Thanks

---

### Post by burnboy on 2006-02-22
Does anyone have any suggestions??

---

### Post by jrblevin on 2006-02-28
Installing language-pack-en-base should do the trick.

---

### Post by burnboy on 2006-03-12
That's already installed. 

I ended up setting this in .bashrc to temporarily fix the problem, but I don't see how that would be a proper solution.

```
export LC_ALL=en_US.UTF-8
```

---

### Post by adamkane on 2006-03-13
If possible, please describe what you were trying to do, and what you've done up to this point.

---

