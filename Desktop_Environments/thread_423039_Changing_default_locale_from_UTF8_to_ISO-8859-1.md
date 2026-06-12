---
title: "Changing default locale from UTF8 to ISO-8859-1"
date: 2007-04-25
forum: Desktop Environments
---

### Post by randomstuff on 2007-04-25
The following thread describes the same problem, but the *"dkpg-reconfigure locales"* solution is outdated and won't work in neither edgy nor feisty:

[http://ubuntuforums.org/showthread.php?t=30803&highlight=change+character+encoding]("http://ubuntuforums.org/showthread.php?t=30803&highlight=change+character+encoding")

I found a [danish guide]("http://wiki.sslug.dk/index.php/Ubuntu_FAQ"), with the following (translated) solution:

[LIST]
[*]Open /var/lib/locales/supported.d/local as root and add "da_DK ISO-8859-1" at the bottom of the file (without quotes)
[*]Open /etc/default/locale as root and change LANG="da_DK.UTF-8" to LANG="da_DK"
[*] sudo locale-gen --purge 
[/LIST]

however, this does not work either. running *"locale"* for confirmation still displays en_US.UTF8 as the default language (the first entry called LANG?), and I still have the same unicode issues.

Any help on this issue would be much appreciated.

---

### Post by treris on 2007-05-13
I think I may have the answer to your question, 

With a bit of fiddling and twiddling I've been able to set my system to ISO-8859-1.

    > * Open /var/lib/locales/supported.d/local as root and add "da_DK ISO-8859-1" at the bottom of the file (without quotes)
    * Open /etc/default/locale as root and change LANG="da_DK.UTF-8" to LANG="da_DK"
    * sudo locale-gen --purge 

this is what I've used but instead of changing (in my case) LANG="en_US.UTF-8" to LANG="en_US" I changed it to LANG="en_US.ISO-8859-1"

Furthermore I added "en_US.ISO-8859-1 ISO-8859-1" to both my /var/lib/locales/supported.d/local en /var/lib/locales/supported.d/en files

running sudo locale-gen --purge after that and restarting KDE did the trick, I now have no problems anymore with dodgy accents etc.

Hope this helps

---

