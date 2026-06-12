---
title: "setting locale"
date: 2006-09-18
forum: Desktop Environments
---

### Post by kulashaker on 2006-09-18
Hi,

I'm on Dapper Drake and these are my current locale settings:

```

root@drake:/home/kula# locale
LANG=en_DK.UTF-8
LANGUAGE=en_DK:en
LC_CTYPE="en_DK.UTF-8"
LC_NUMERIC="en_DK.UTF-8"
LC_TIME="en_DK.UTF-8"
LC_COLLATE="en_DK.UTF-8"
LC_MONETARY="en_DK.UTF-8"
LC_MESSAGES="en_DK.UTF-8"
LC_PAPER="en_DK.UTF-8"
LC_NAME="en_DK.UTF-8"
LC_ADDRESS="en_DK.UTF-8"
LC_TELEPHONE="en_DK.UTF-8"
LC_MEASUREMENT="en_DK.UTF-8"
LC_IDENTIFICATION="en_DK.UTF-8"
LC_ALL=

```

The thing is that I need to take out the .UTF-8 encoding from the locale, wich would leave the setting at en_DK. 

How can I do this? Just changing the string in /etc/environment results in an error. Do I have to install anything?

Regards,
Christian

---

