---
title: "umlauts are displayed wrong in konsole (z.B. &lt;FC&gt;)"
date: 2007-07-16
forum: Desktop Environments
---

### Post by Ulrich Scholz on 2007-07-16
Dear all,

now I managed to get my locales right - at least I do not get any error messages when starting programs

scholzuh@kiste:Forschung] >locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE="de_DE&#8364;euro"
LC_NUMERIC="de_DE&#8364;euro"
LC_TIME="de_DE&#8364;euro"
LC_COLLATE="de_DE&#8364;euro"
LC_MONETARY="de_DE&#8364;euro"
LC_MESSAGES="de_DE&#8364;euro"
LC_PAPER="de_DE&#8364;euro"
LC_NAME="de_DE&#8364;euro"
LC_ADDRESS="de_DE&#8364;euro"
LC_TELEPHONE="de_DE&#8364;euro"
LC_MEASUREMENT="de_DE&#8364;euro"
LC_IDENTIFICATION="de_DE&#8364;euro"
LC_ALL=de_DE&#8364;euro

Here my questions:

1) Where do these error messages come from?

2) My main questions:

The konsole shows German umlauts as <FC> and alike.  How can I get real umlauts?

Example:
Die Reihenfolge, in der die Aktionen in den Plan eingef<FC>gt werden.

Thank you,

Ulrich

---

### Post by lizzard on 2007-07-16
I think you have to replace the "de_DE€euro" entries with "de_DE@euro".

---

### Post by Ulrich Scholz on 2007-07-16
Actually, my .profile looked like this:

> export LANG=en_US.UTF-8
export LC_CTYPE="en_US.UTF-8"
export LC_NUMERIC="de_DE.UTF-8"
export LC_TIME="de_DE.UTF-8"
export LC_COLLATE="de_DE.UTF-8"
export LC_MONETARY="de_DE.UTF-8"
export LC_MESSAGES="en_US.UTF-8"
export LC_PAPER="de_DE.UTF-8"
export LC_NAME="de_DE.UTF-8"
export LC_ADDRESS="de_DE.UTF-8"
export LC_TELEPHONE="de_DE.UTF-8"
export LC_MEASUREMENT="de_DE.UTF-8"
export LC_IDENTIFICATION="de_DE.UTF-8"
export LC_ALL=

According to your suggestions, I changed it to 

> export LANG=en_US.UTF-8
export LC_CTYPE="en_US.UTF-8"
export LC_NUMERIC="de_DE@euro"
export LC_TIME="de_DE@euro"
export LC_COLLATE="de_DE@euro"
export LC_MONETARY="de_DE@euro"
export LC_MESSAGES="en_US.UTF-8"
export LC_PAPER="de_DE@euro"
export LC_NAME="de_DE@euro"
export LC_ADDRESS="de_DE@euro"
export LC_TELEPHONE="de_DE@euro"
export LC_MEASUREMENT="de_DE@euro"
export LC_IDENTIFICATION="de_DE@euro"
export LC_ALL=

Result:

```
[scholzuh@kiste:Verwaltung] >locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LC_CTYPE=en_US.UTF-8
LC_NUMERIC=de_DE@euro
LC_TIME=de_DE@euro
LC_COLLATE=de_DE@euro
LC_MONETARY=de_DE@euro
LC_MESSAGES=en_US.UTF-8
LC_PAPER=de_DE@euro
LC_NAME=de_DE@euro
LC_ADDRESS=de_DE@euro
LC_TELEPHONE=de_DE@euro
LC_MEASUREMENT=de_DE@euro
LC_IDENTIFICATION=de_DE@euro
LC_ALL=
```

But

> [scholzuh@kiste:Verwaltung] >more wichtiges.txt
"wichtiges.txt" may be a binary file.  See it anyway?
B<E4>rbel ist f<FC>r das Personal zust<E4>ndig

and

> [scholzuh@kiste:Verwaltung] >ooffice Telefonverzeichnis_76.doc
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = "",
        LC_PAPER = "de_DE@euro",
        LC_ADDRESS = "de_DE@euro",
        LC_MONETARY = "de_DE@euro",
        LC_NUMERIC = "de_DE@euro",
        LC_TELEPHONE = "de_DE@euro",
        LC_MESSAGES = "en_US.UTF-8",
        LC_COLLATE = "de_DE@euro",
        LC_IDENTIFICATION = "de_DE@euro",
        LC_MEASUREMENT = "de_DE@euro",
        LC_CTYPE = "en_US.UTF-8",
        LC_TIME = "de_DE@euro",
        LC_NAME = "de_DE@euro",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
I18N: Operating system doesn't support locale ""
I18N: Operating system doesn't support locale "en_US"


In short: your fix causes more errors and does not help the problem

Thanks,Ulrich

---

### Post by lizzard on 2007-07-16
Did you substitute the UTF-8 (e.g.: de_DE.UTF-8 UTF-8
 settings in your /var/lib/locales/supported.d/de with de_DE@euro ISO-8859-15? 
After that you have to generate your new locales with  "sudo dpkg-reconfigure locales"

---

### Post by Ulrich Scholz on 2007-07-17
I did as you told and changed /var/lib/locales/supported.d/de (including regeneration) and my locales in .profile.  They are now

```
export LANG=de_DE@euro
export LC_CTYPE="de_DE@euro"
export LC_NUMERIC="de_DE@euro"
export LC_TIME="de_DE@euro"
export LC_COLLATE="de_DE@euro"
export LC_MONETARY="de_DE@euro"
export LC_MESSAGES="de_DE@euro"
export LC_PAPER="de_DE@euro"
export LC_NAME="de_DE@euro"
export LC_ADDRESS="de_DE@euro"
export LC_TELEPHONE="de_DE@euro"
export LC_MEASUREMENT="de_DE@euro"
export LC_IDENTIFICATION="de_DE@euro"
export LC_ALL=

```

```
[scholzuh@kiste:~] >locale
LANG=de_DE@euro
LC_CTYPE=de_DE@euro
LC_NUMERIC=de_DE@euro
LC_TIME=de_DE@euro
LC_COLLATE=de_DE@euro
LC_MONETARY=de_DE@euro
LC_MESSAGES=de_DE@euro
LC_PAPER=de_DE@euro
LC_NAME=de_DE@euro
LC_ADDRESS=de_DE@euro
LC_TELEPHONE=de_DE@euro
LC_MEASUREMENT=de_DE@euro
LC_IDENTIFICATION=de_DE@euro
LC_ALL=

```

You see: locale works fine and starting programms (perl -e "") don't give an error.

Unfortunately, the initial problem is only changed but not solved. Now, umlauts are displayed as empty space.  Same example as before

```
[scholzuh@kiste:Verwaltung] >more wichtiges.txt
B&#65533;bel ist f&#65533;r das Personal zust&#65533;dig

```

OK, in the konsole I see the "&#65533;" as " ".  

Regards, Ulrich

---

### Post by swisscow on 2007-07-17
I'm using Kubuntu and I have perfect umlauts in Konsole. all I have done is in system settings added a keyboard layout for German (in regional and language settings). This has added a little flag on the task bar, I just click on it to switch between English layout and German layout.

This is probably to simple for your problem but it may help

---

