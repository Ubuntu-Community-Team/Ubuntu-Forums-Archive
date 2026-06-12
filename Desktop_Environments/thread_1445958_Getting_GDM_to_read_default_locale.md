---
title: "Getting GDM to read default locale?"
date: 2010-04-03
forum: Desktop Environments
---

### Post by nylle on 2010-04-03
Hi,

I'm having extremely annoying language problems, I want to be able to have English language in menus and messages, but have the gnome panel calendar applet start the week on a Monday, and have Swedish measurements. On debian I've solved this with a locale something like this (in /etd/default/locale):

```

LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
LC_TIME=sv_SE.UTF8
LC_NUMERIC=sv_SE.UTF8
LC_MONETARY=sv_SE.UTF8
LC_PAPER=sv_SE.UTF8
LC_NAME=sv_SE.UTF8
LC_TELEPHONE=sv_SE.UTF8
LC_ADDRESS=sv_SE.UTF8
LC_CTYPE=sv_SE.UTF8
LC_COLLATE=sv_SE.UTF8
LC_MEASUREMENT=sv_SE.UTF8

```

However, GDM seems to totally ignore this. I can choose "Unspecified" (in which case I get "C" locale) or English (in which case I get the American locale) on login but how do I get it to respect locale I want?

This problem is really driving me mad...

//Andreas

---

