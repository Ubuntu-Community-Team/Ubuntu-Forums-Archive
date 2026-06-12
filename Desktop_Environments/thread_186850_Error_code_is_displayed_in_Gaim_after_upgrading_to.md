---
title: "Error code is displayed in Gaim after upgrading to dapper drake"
date: 2006-06-02
forum: Desktop Environments
---

### Post by wcai on 2006-06-02
All,
I find Gaim on my laptop doesn't work well after upgrading to Ubuntu 6.06 today. The messages sent by friends using MSN are displayed as some numbers which might be the encoding. (See the attachement) And Gaim throws an error message as below.
(gaim:5442): Pango-WARNING **: shape engine failure, expect ugly output. the offending font is '&#23435;&#20307; 9.9990234375'

I have very limited knowledge/experience on I18N/L10N issues. Could anybody help figure it out?

Any response is appreciated!

---

### Post by wcai on 2006-06-02
To answer myself, this problem could be resolved by removing msttcorefonts package. Seems there are some conflicts in 6.06 environment.

---

