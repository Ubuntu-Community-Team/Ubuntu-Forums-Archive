---
title: "gnome locales"
date: 2010-04-25
forum: Desktop Environments
---

### Post by docjones2 on 2010-04-25
I installed 10.04 in english, used the gui later to install spanish...

but the spanish is broken as hell.  The gui is half english and half spanish, even within the same app.

For example, the top panel calender will say "domingo 25 abril" and right underneath will say "locations"

How can I repair this?  Any point in uninstall/reinstalling spanish?

---

### Post by docjones2 on 2010-04-25
The issue resolved itself, logged out then back in and the whole was in spanish.

I guess it was a bug, should be fairly easy to reproduce for anybody out there who's into that sort of thing, I don't have the time to reinstall 10.04 for this.

---

### Post by docjones2 on 2010-04-25
nevermind, the problem's definitely a bug of some sort

Switching back to english I found that the system went back the half spanish half english configuration, logging out and back in did not fix it.  I restarted the computer the first time the half spanish half english configuration occurred and on startup, the system went full spanish.  I'm going to see if I can't do this same trick to get the system full english, I'll edit this post with the results.

---

### Post by docjones2 on 2010-04-25
Would have editted above post but now the problem is significant enough that I'd like this to get seen and helped...

Restarting did not fix the half eng half span problem, the computer will not go full english, it will however go full spanish.  Anytime I switch to english though, it goes half english half spanish.  I've tried this with both us and gb english with the same results...

Any ideas?  I'd lose my mind on a half and half config so I'm going full spanish, which I don't want to have to do for too long...

---

### Post by asalapi on 2010-05-04
I confirm this bug. I installed Ubuntu 10.4 upgrading from 9.10 from update manager on a 64bit version (English, Spanish and Catalan locales were installed on 9.10). Gave lots of errors such as:
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

during upgrade.
Afterwards, everything fell to English and gnome-language-selector refused running 
(window dissapeared in a couple of seconds).
By playing with export LC_ALL=C and export LANGUAGE or export LANG (I don't clearly remember)
I managed to get gnome-language-selector running but, anyway, whatever language pack I install and
the result is always English. This is my "locale":
LANG=es_ES.UTF-8
LANGUAGE=es_ES:ca:es:en_GB:en
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
LC_ALL=C

Note that es_ES is not actually installed on the system (it is es_ES.utf8)

I ran sudo dpkg-reconfigure locale (even deleting /usr/lib/locale) with no luck.
I understand English, but I'm afraid to upgrade a couple other computers (my mom and dad's) because they
do NOT understand English.

Doing it on a 32-bit Ubuntu (netbook) gave no problems.

---

