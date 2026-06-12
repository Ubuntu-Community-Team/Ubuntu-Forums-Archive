---
title: "OpenOffice crashes while copying and pasting in Evolution"
date: 2006-10-26
forum: Desktop Environments
---

### Post by jongkind on 2006-10-26
Openoffice crashes while copying from OO Writer followed by pasting in Evolution. Can anyone reproduce this problem?




PS: The same happens when I copy from OO Writer and paste in Firefox e.g. while composing a Gmail in Firefox)

---

### Post by Leonivek on 2006-10-26
I get the same issue from a fresh Ubuntu 6.10 installation.  I was copying from OOo Writer to my blog in Firefox today and everytime I tried to paste, it would crash. ](*,)

---

### Post by waldorf on 2006-10-26
yep exact same thing happens to me copying from OOo to thunderbird. Add this to the horrible font situation in OOo and I'm really starting to wonder what is going on.

---

### Post by jongkind on 2006-10-27
I filled in a bug report. It may help if you confirm that you have the same problems:

[https://launchpad.net/distros/ubuntu/+bug/68595]("https://launchpad.net/distros/ubuntu/+bug/68595")

---

### Post by robert114 on 2006-11-02
Same for me with firefox2

---

### Post by robert114 on 2006-11-02
Maybe this helps solving the prob. When I start openoffice in kubuntu from a terminal I get these errors:

```
robert@robert-desktop:~$ openoffice

(process:9086): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:9086): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed
robert@robert-desktop:~$
(process:9086): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:9086): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:9086): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:9086): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

(process:9086): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:9086): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

```

---

### Post by robert114 on 2006-11-04
"Kai Kasurinen  at 2006-10-27 16:34:32 UTC

Thanks for the bug report. This particular bug has already been
reported into our bug tracking system, but please feel free to report
any further bugs which you find."

Were can I find more information about this allready reported bug?

---

### Post by jongkind on 2006-11-04
[https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62432]("https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62432")

---

### Post by robert114 on 2006-11-05
Thanx with those updates I fixed OO

---

### Post by zek725 on 2006-11-05
> **Leonivek said:**
> I get the same issue from a fresh Ubuntu 6.10 installation.  I was copying from OOo Writer to my blog in Firefox today and everytime I tried to paste, it would crash. ](*,)

me too! but Abiword works fine. ](*,)

---

### Post by Leonivek on 2006-11-16
Just wanted to update people still having this problem that there is a fix on the [Launchpad's bug report]("https://launchpad.net/distros/ubuntu/+source/openoffice.org/+bug/62432") and I [posted it on my blog]("http://linuxfud.wordpress.com/2006/11/16/how-to-fix-the-openoffice-copy-and-paste-crash-bug/") to make it easier to find.

---

