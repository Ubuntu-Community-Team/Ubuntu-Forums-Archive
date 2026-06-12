---
title: "Open Office Problems"
date: 2009-01-22
forum: Education &amp; Science
---

### Post by some1udontknow on 2009-01-22
I have the default open office installation that comes with ubuntu 8.10 and I noticed that the spell check doesn't work. I have thought of trying to upgrade the open office but i am new to using the console / text commands. I have thought of trying to put microsoft office onto ubuntu (under wine) but I am too lazy to make a iso of the disk (i have ubuntu on a acer aspire one (mini laptop) it doesnt have a cd drive). Thanks for the help.

---

### Post by hzambran_cl on 2009-01-23
You should install 'language-support-en' to get full support for English language (spell checkers, OpenOffice locale packages, etc.). If you don't have it installed yet, you can try:

[HTML]sudo apt-get install language-support-en[/HTML]

If you also want your applications and the desktop to be translated,
you have to additionally install 'language-pack-en'.

[HTML]sudo apt-get install language-pack-en[/HTML]

---

