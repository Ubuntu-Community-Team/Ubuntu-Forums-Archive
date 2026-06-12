---
title: "Windows tool bar disappear"
date: 2008-12-13
forum: Desktop Environments
---

### Post by oc666 on 2008-12-13
Hello
I just install ubuntu-mobile package & window toolbar (with the close, minimise etc) disappear from all windows. I tried to uninsall compiz, reconfigure X & gnome but nothing help to solve this.
I see the next thread but it didn't help me:
[http://img143.imageshack.us/img143/8196/errorhz8.png](http://img143.imageshack.us/img143/8196/errorhz8.png)
Example for the situation:
[http://img143.imageshack.us/img143/8196/errorhz8.png](http://img143.imageshack.us/img143/8196/errorhz8.png)

Thanks.

---

### Post by Wartender on 2008-12-13
perhaps ```
metacity --replace
``` will work?

---

### Post by andahunter on 2008-12-13
> **oc666 said:**
> Hello
I just install ubuntu-mobile package & window toolbar (with the close, minimise etc) disappear from all windows. I tried to uninsall compiz, reconfigure X & gnome but nothing help to solve this.
I see the next thread but it didn't help me:
[http://img143.imageshack.us/img143/8196/errorhz8.png](http://img143.imageshack.us/img143/8196/errorhz8.png)
Example for the situation:
[http://img143.imageshack.us/img143/8196/errorhz8.png](http://img143.imageshack.us/img143/8196/errorhz8.png)

Thanks.

Well Try in apperance in visual effect to put it on none... that might be the problem... i had it myself for a while ago

---

### Post by oc666 on 2008-12-13
> **Wartender said:**
> perhaps ```
metacity --replace
``` will work?

It doesn't help:
> metacity --replace
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200003 (&#1500;&#1493;&#1495; &#1511;&#65533;)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1200026 (&#1500;&#1493;&#1495; &#1511;&#65533;)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x320000a (oc@oc-lapt)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x360008a (&#1502;&#1493;&#1499;&#1491;&#1490;)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x160001d (x-nautilus)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0xe000ce (Mozilla Fi)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4400016 (&#1492;&#1506;&#1491;&#1508;&#1493;)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

> **andahunter said:**
> Well Try in apperance in visual effect to put it on none... that might be the problem... i had it myself for a while ago

I removed compiz and it's disable.
Also, I tried to install xfce and the problem occur there also.

---

### Post by oc666 on 2008-12-13
I just removed the next packages (apt-get log):
> Log started: 2008-12-14  00:22:54
(Reading database ... 125891 files and directories currently installed.)
Removing gnokii ...
Removing gnokii-cli ...
gnokii:x:125:
Purging configuration files for gnokii-cli ...
Removing xgnokii ...
Purging configuration files for xgnokii ...
Removing gnome-phone-manager ...
Purging configuration files for gnome-phone-manager ...
Removing libgnokii3 ...
Purging configuration files for libgnokii3 ...
Removing gnokii-common ...
Purging configuration files for gnokii-common ...
Removing ubuntu-mobile-default-settings ...
Purging configuration files for ubuntu-mobile-default-settings ...
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2008-12-14  00:23:23

& it's just work! (after new loging)

Thanks

---

### Post by oc666 on 2008-12-23
Hello, again 
I don't know what happened but this problem come back.

How could I know what have been happened?

THANKS!

---

