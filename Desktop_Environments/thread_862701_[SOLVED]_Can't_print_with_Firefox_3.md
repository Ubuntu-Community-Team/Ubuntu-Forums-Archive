---
title: "[SOLVED] Can't print with Firefox 3"
date: 2008-07-17
forum: Desktop Environments
---

### Post by neymac on 2008-07-17
When I try print preview or print to PDF in Firefox 3, it crashes.
To print internet staff I have to use Opera, that print to PDF without problems.
Running Firefox 3 from terminal with --debug option I got when try to print:

```
...ila:~$ firefox --debug
/usr/lib/firefox-3.0/firefox: symbol lookup error: /usr/lib/xulrunner-1.9/libxul.so: undefined symbol: cairo_ps_surface_restrict_to_level
```
I don't know how to fix it.
I saw some bugs lists but didn't help to fix.
Help welcome.

---

### Post by apswartz on 2008-07-17
Okay. How did you fix it?

---

### Post by cabrito on 2008-07-30
I had this problem too.

The problem was originated when i installed cairo-dock manually because it installs an old version of libcairo into /usr/local/lib.

Read the thread at [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/203019](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/203019)

I solved it by uninstalling cairo-dock.

I think it does not affect the packaged version, only if you compiled it. 

If you used the cairo-dock_svn.sh you can uninstall it like this:

./cairo-dock_svn.sh --uninstall # for Cairo-Dock
./cairo-dock_svn.sh --uninstall-glitz # for Glitz

I hop this is helpful.
Good luck!

---

