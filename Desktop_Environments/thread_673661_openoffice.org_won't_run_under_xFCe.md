---
title: "openoffice.org won't run under xFCe"
date: 2008-01-20
forum: Desktop Environments
---

### Post by lamarcheb on 2008-01-20
I installed Ubuntu 7.10 on an old Thinkpad T22. Since it is an old computer I also installed the xFCE desktop since it is more efficient on old hardware. When I log on using xFCe, OpenOffice.org does not start. There is no error message. :confused: It runs fine under GNOME.

Any clues? Thanks!

---

### Post by reckless2k2 on 2008-01-20
try running it from the direct path. i've had this problem with the wrong path and it won't start until i have the right path in there.

---

### Post by urukrama on 2008-01-21
What do you get when you type ooffice in a terminal? Do you get any error messages? If so, post them here and perhaps someone can help.

---

### Post by peertje on 2008-07-17
I have the same problem with Gentoo. Although...I installed Xfce4 also, and the bin package of OO and when I log in as root, I can start OO from within the menu, but logged-in as a normal user the program keeps alive for a second or two and then closes. When I start "ooffice" from terminal, no errormessages occur and OO just works. So wierd! So I went looking in my /usr/share/applications to find the exact commands like "ooffice -writer". This reproduced the problem with the following error message:
```
/usr/lib/openoffice/program/soffice: line 254:  8880 Segmentation fault      "$sd_prog/$sd_binary" "$@"
```
Magowiz (gentoo forums) found a workaround: set OOO_FORCE_DESKTOP=none as environment variable works well also in gnome.
He added this OOO_FORCE_DESKTOP="none" to /etc/env.d/99local
This is an option, but it looks ugly...it does tell us that there's a compatabilityproblem with gtk.
According to [http://forums.gentoo.org/viewtopic-p-5128367.html?sid=5c371bee9219c9978b51f2eb047570bd](http://forums.gentoo.org/viewtopic-p-5128367.html?sid=5c371bee9219c9978b51f2eb047570bd) this bug was fixed, maybe you should try upgrading or downgrading to another version.
Here is beiing refered to the reported bug with a couple of workarounds:
[http://bugs.gentoo.org/show_bug.cgi?id=228703](http://bugs.gentoo.org/show_bug.cgi?id=228703)
For me, a preceding GTK_PLUGINS="" worked, but now for Xfce4...

---

### Post by Hagar Delest on 2008-07-18
OOo 2.4.1 runs fine on my xubuntu box (with Hardy). Try to rename your Ooo user profile (~/.openoffice.org2).

In the past, there was an issue with the screen color depth, that had to be reduced to 16bits. but haven't seen that issue for a long while.

---

