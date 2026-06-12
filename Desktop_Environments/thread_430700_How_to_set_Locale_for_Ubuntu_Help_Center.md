---
title: "How to set Locale for Ubuntu Help Center"
date: 2007-05-02
forum: Desktop Environments
---

### Post by Chris Kerr on 2007-05-02
After adding and removing locales on my Japanese localized ubuntu 7.04 machine, man pages in Ubuntu Help Center with Japanese characters don't display correctly. (They still display correctly in a terminal window).

I would like to restore the correct display of Japanese characters in Ubuntu Help Center but I do not know how. 

Locale information is as follows:

chris@vaio:~$ more /var/lib/locales/supported.d/ja
ja_JP.UTF-8 UTF-8

chris@vaio:~$ locale -a
C
POSIX
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
ja_JP.utf8

chris@vaio:~$ more /etc/environment 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:
/usr/games"
LANGUAGE="ja_JP:ja:en_GB:en"
LANG="ja_JP.UTF-8"
LANG="ja_JP.UTF-8"

chris@vaio:~$ env |grep LANG
LANG=ja_JP.UTF-8
LANGUAGE=ja_JP:ja:en_GB:en

chris@vaio:~$ locale
LANG=ja_JP.UTF-8
LANGUAGE=ja_JP:ja:en_GB:en
LC_CTYPE="ja_JP.UTF-8"
LC_NUMERIC="ja_JP.UTF-8"
LC_TIME="ja_JP.UTF-8"
LC_COLLATE="ja_JP.UTF-8"
LC_MONETARY="ja_JP.UTF-8"
LC_MESSAGES="ja_JP.UTF-8"
LC_PAPER="ja_JP.UTF-8"
LC_NAME="ja_JP.UTF-8"
LC_ADDRESS="ja_JP.UTF-8"
LC_TELEPHONE="ja_JP.UTF-8"
LC_MEASUREMENT="ja_JP.UTF-8"
LC_IDENTIFICATION="ja_JP.UTF-8"
LC_ALL=

Everything seems fine from the above (to me)

Is there some way to set the Locale information for Ubuntu Help Center to get man pages in Japanese to display correctly in Ubuntu Help Center?

---

