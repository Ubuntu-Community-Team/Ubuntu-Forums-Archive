---
title: "Procmail Question"
date: 2005-08-01
forum: Desktop Environments
---

### Post by hzs202 on 2005-08-01
I have recently installed procmail... if I want to catch all freebsd-questions emails can I use:```
* ^TO_.*questions@freebsd.org
``` Will this work or do I have to user another header like [COLOR=Red]**Delivered-To:**[/COLOR] or [COLOR=Blue]**X-Delivered-To:**[/COLOR]... in addition if someone could point me to a place where I could find this information it would also be helpful.

---

### Post by nemin on 2005-08-02
[QUOTE=hzs202]I have recently installed procmail... if I want to catch all freebsd-questions emails can I use:```
* ^TO_.*questions@freebsd.org
``` Will this work or do I have to user another header like [COLOR=Red]**Delivered-To:**[/COLOR] or [COLOR=Blue]**X-Delivered-To:**[/COLOR]... in addition if someone could point me to a place where I could find this information it would also be helpful.[/QUOTE]
If that mailinglist uses the list-id header ([http://rfc2919.x42.com/](http://rfc2919.x42.com/)) you'd better filter on that.

---

