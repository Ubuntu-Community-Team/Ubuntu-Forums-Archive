---
title: "xbox 360 pad installer ?"
date: 2007-06-27
forum: Gaming &amp; Leisure
---

### Post by bhuthogg on 2007-06-27
has anyone made an xbox 360 pad installer eg. .DEB ?

just wondering cos being the noob i am. i cant get it work with doing the tutorial :(

thanks

---

### Post by po0f on 2007-06-27
bhuthogg,

What about the directions is unclear?  If you specified what step you were stuck at, surely someone would help you.  :)

All the steps in a nutshell:

[list=1]
[*]Download xbox360.tar.gz
[*]Extract it to a location you have write access to with the command `tar xvzf /path/to/xpad360.tar.gz -C /wherever/you/want/it` (most likely ~/.xpad360)
[*]`cd` into the directory where you extracted the source
[*]Run `make` then `sudo make install` in the directory
[*]Reboot and enjoy
[/list]

When booting, remember to make sure that the controller is **un**plugged, and also to plug it in prior to use.  And if you need more help, post back.  ;)

---

### Post by Frem on 2007-06-27
You'll also need some development tools installed. If step 4 is giving you problems, run the command "sudo apt-get install build-essential", and try doing step 4 again.

---

### Post by po0f on 2007-06-27
Frem,

Thanks; it totally slipped my mind that you need build-essential as well as linux-headers appropriate for the current kernel installed.  The following command should take care of both of these:

```
$ sudo apt-get install build-essential linux-headers-$(uname -r)
```


bhuthogg,

Hope this helps.  :)

(Hint: the dollar sign is not part of the command, it represents your terminal prompt.)

---

### Post by lemmer on 2008-03-04
hello! i'm italian, so a first sorrry for my bad english....
excuse me, but where do I get the .deb package of the installer?
or.... where do I get the tar.gz?

---

