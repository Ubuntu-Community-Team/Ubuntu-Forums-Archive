---
title: "OpenOffice page size is not changed"
date: 2008-10-14
forum: Desktop Environments
---

### Post by gobi on 2008-10-14
I am using OpenOffice 3.0 and the printer is Fujixerox ApeosPort-II C4300 which works with no problem on Linux.

But only on OpenOffice I can not change its page size to A4. Page size is in default Letter and when I set it to A4 it will stay not changed.

I tried to change page size from File->Printer Settings->Properties.

Also I tried to change it in OO's spadmin program. And it will stay not changed.

I don't know that is it OpenOffice bug or is printer driver bug? I was little bit googling and found some discussions and it says it is not OpenOffice bug. But other programs work fine on this printer. Only OpenOffice page is not changed. 

Please tell me what should I do?

PS: 
Perhaps the following information is useful to figure out problems.
Attachmet:
my printer PPD file: /etc/cups/ppd/fx.ppd
my paper settings file: paper.config

And the result of locale command.
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

---

### Post by mssever on 2008-10-15
For some reason, I can't open your attached file. Also, I had problems a couple of years ago with OOo using A4 when I wanted letter. For me, the solution was in /etc/papersize.

---

