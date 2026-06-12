---
title: "Set start of week in gnome"
date: 2009-06-24
forum: Desktop Environments
---

### Post by rggjan on 2009-06-24
I'm trying to set the start of the week to monday instead of sunday, but keep the system's language English.

What I did now in Archlinux was the following:
I added the lines
```

export LANG=en_GB
export LC_CTYPE="de_CH.utf8"
export LC_NUMERIC="de_CH.utf8"
export LC_TIME="de_CH.utf8"
export LC_COLLATE="de_CH.utf8"
export LC_MONETARY="de_CH.utf8"
export LC_MESSAGES="en_GB.utf8"
export LC_PAPER="de_CH.utf8"
export LC_NAME="de_CH.utf8"
export LC_ADDRESS="de_CH.utf8"
export LC_TELEPHONE="de_CH.utf8"
export LC_MEASUREMENT="de_CH.utf8"
export LC_IDENTIFICATION="de_CH.utf8"
export LC_ALL=""

```
to my .bashrc, so "locale" gives me:
```

LANG=en_GB
LC_CTYPE=de_CH.utf8
LC_NUMERIC=de_CH.utf8
LC_TIME=de_CH.utf8
LC_COLLATE=de_CH.utf8
LC_MONETARY=de_CH.utf8
LC_MESSAGES=en_GB.utf8
LC_PAPER=de_CH.utf8
LC_NAME=de_CH.utf8
LC_ADDRESS=de_CH.utf8
LC_TELEPHONE=de_CH.utf8
LC_MEASUREMENT=de_CH.utf8
LC_IDENTIFICATION=de_CH.utf8
LC_ALL=

```
But still, the week (for example in the gnome calendar applet) starts on sunday! Even though in "/usr/share/i18n/locales/de_CH" there is a line "first_weekday 2".

Also, when I set the language of everything to german (de_CH), then it works, too...

Anyone knows what to do here? Thanks.

---

### Post by dajare on 2010-01-03
This seems to be a perennial issue! I have searched and googled, and tried tweaking my en_GB file, reloading, setting "first-weekday" to values of 0, 1, and 2 -- nothing seems to change the way that the Gnome Clock applet displays its calendar! I *always* get Monday first, and what I want to see is Sunday first!

I'm on Ubuntu 9.04; and some settings:

```
$ locale
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=
```

And currently, my en_GB file looks like this:

```
LC_TIME
 ...
first_weekday 1
```

Is there any hope here? It seems like such an obvious thing (given I've been reading forum posts on this dating back to 2005!) to add a "first-weekday" setting to the Clock applet to override the locale settings. Sigh!

Or am I missing something obvious? Thanks for any help with this!

---

### Post by I_can_see_the_light on 2010-01-03
The way I solved this issue was to manually edit ```
gksudo gedit /etc/default/locale
``` making it look like this: ```
LANG="sv_SE.UTF-8"
LANGUAGE="en_US.UTF8"
LC_MESSAGES="en_US.UTF-8"
```
Now I have all the locale specific settings of my country and the systen is still in english. However it seems that AbiWord and Google Chrome for some reason is in swedish, everything else is in english.

[Another way]("http://www.lathund.nu/2009/02/19/andra-forsta-veckodag-i-ubuntu/") that supposedly should work is to edit the file ```
/usr/share/i18n/locales/en_US
``` finding a section looking like this: ```
week 7;19971130;7
first_weekday	1
first_workday	2
``` and changing the value for first_weekday to 2. Save the file (but remember to make a backup of the original) and run the command ```
sudo locale-gen
``` now you can either restart X or run ```
killall gnome-panel
```

---

### Post by nilarimogard on 2010-01-03
Changing the locale to UK will make the week start on Monday, while keeping all the applications language in English. 

This sets the software messages in English (US), but time, paper size and units in British i.e. weeks starting with Mondays, A4, metric.

```
LANG="en_US.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
```

From here: [http://www.webupd8.org/2009/06/change-gnome-calendar-week-start-day-to.html](http://www.webupd8.org/2009/06/change-gnome-calendar-week-start-day-to.html)

---

### Post by dajare on 2010-01-03
Thanks for all the suggestions. The very strange thing is, that no matter WHAT I change regarding "locale" (en_GB for me), the Clock applet calendar stays the same. Always the same. Always first_weekday is Monday. Always.

Is the Clock applet really picking up its settings from "locale"? or is there another place where its settings are stored?

Thanks for continuing help with this!
David.

---

### Post by I_can_see_the_light on 2010-01-03
What if you made /etc/default/locale look like this: ```
LANG="en_GB.UTF-8"
LC_TIME="en_US.UTF-8"
``` and then rebooted

---

