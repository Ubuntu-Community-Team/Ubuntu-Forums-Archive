---
title: "locale problem"
date: 2007-06-18
forum: Desktop Environments
---

### Post by speedygeo on 2007-06-18
This is the output of locale command on my kubuntu

```

locale

locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.utf-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.utf-8"
LC_NUMERIC="en_US.utf-8"
LC_TIME="en_US.utf-8"
LC_COLLATE="en_US.utf-8"
LC_MONETARY="en_US.utf-8"
LC_MESSAGES="en_US.utf-8"
LC_PAPER="en_US.utf-8"
LC_NAME="en_US.utf-8"
LC_ADDRESS="en_US.utf-8"
LC_TELEPHONE="en_US.utf-8"
LC_MEASUREMENT="en_US.utf-8"
LC_IDENTIFICATION="en_US.utf-8"
LC_ALL=

```

Can anyone explain me how to fix it?

---

### Post by avik on 2007-06-18
Other than the first three lines, it's pretty much the same as on my computer.  It doesn't look like the error is doing anything.  The output is unaffected, it seems.

---

### Post by speedygeo on 2007-06-18
Exact that three lines are my problem. Thanks. Have anyone any suggestion?

---

### Post by speedygeo on 2007-06-18
That appear when I install a package in synaptic.

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = (unset),
        LANG = "en_US.utf-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

---

### Post by zorog on 2007-08-21
Here's what worked for me from [http://www.howtoforge.com/forums/archive/index.php/t-1893.html](http://www.howtoforge.com/forums/archive/index.php/t-1893.html) posted by **Colin Dean**

> It's also useful to check you have language-pack-?? installed, as that provides the actual locales. English speakers will most likely want language-pack-en.

This was the problem in my case. language-pack-en-base was not installed.
apt-get install language-pack-en-base fixed it.

This worked for me good luck,
Have Fun
Simon.

---

