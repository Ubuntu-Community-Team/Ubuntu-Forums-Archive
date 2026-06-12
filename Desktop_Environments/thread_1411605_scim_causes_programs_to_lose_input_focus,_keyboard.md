---
title: "scim causes programs to lose input focus, keyboard stops responding"
date: 2010-02-20
forum: Desktop Environments
---

### Post by svamppi on 2010-02-20
Ok this is the worst problem I'm having with ubuntu right now and I'm not sure exactly what causes it. I'm using anthy with scim to input japanese text sometimes. But even when I'm just typing western characters scim seems to cause all kinds of problems with applications not registering my keypresses. Usually I have to alt-tab to another application and alt-tab back to the previous application for the application to register keypresses again. Chrome also seems to be affected by this. Every time I enter something in a field that did not match any of the stored earlier values the application stops registering keypresses and i have to alt-tab alt-tab. This is getting really annoying and I was wondering if anyone else is also experiencing this and if anyone has figured out a way to get rid of this problem.

---

### Post by drinian on 2010-05-11
I have been having the same problem. It's unfortunately a bug that seems to have been around for quite a long time.

This fix seemed to help, though I just applied it a few minutes ago:
[http://samiux.wordpress.com/2007/11/06/scim-bug-fix-for-ubuntu-710/](http://samiux.wordpress.com/2007/11/06/scim-bug-fix-for-ubuntu-710/)

Edit ```
/etc/X11/xinit/xinput.d/scim
``` and change these two variables:
```
GTK_IM_MODULE="SCIM"
QT_IM_MODULE="SCIM"
```

There are probably better, user-specific files to add those environment variables to, but this is the quick, all-users fix.

---

### Post by Zorael on 2010-05-11
You may also want to set those variables to **scim-bridge** if setting them to **scim** doesn't help. This requires the scim-bridge packages, obviously. I think they get installed by default but I'm not sure.

```
$ sudo aptitude intsall scim-bridge scim-bridge-client-gtk scim-bridge-client-qt4
```

SCIM is being transitioned out in favor of **ibus**, so bugfixes to the former may not be coming any time soon. I use **UIM** which also works very nicely.

---

