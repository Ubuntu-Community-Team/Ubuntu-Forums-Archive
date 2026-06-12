---
title: "Changing the default language from UTF-8 to LATIN1"
date: 2006-10-04
forum: Desktop Environments
---

### Post by tivo_box on 2006-10-04
I would like to change the default language or locale on my Ubuntu Dapper from UTF8 to POSIX. 
How can I do that please? 
Thanks.

PS. Here is the output from the locale command:

LANG=en_US.UTF-8
LANGUAGE=en
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

### Post by tivo_box on 2006-10-04
I think I found the answer, which is editing the /etc/environment file.

---

