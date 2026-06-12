---
title: "Firefox 3.0.5 - shows IFRAMEs as popup windows, then crashes"
date: 2009-01-25
forum: General Help
---

### Post by Cato2 on 2009-01-25
I've been having this problem for at least a few months on Firefox 3.0.4 and 3.0.5, and only on Ubuntu - same version on Windows doesn't have a problem.  I'm using Ubuntu 7.10 with the Hardy kernel.

I'm using the mozilla.org version of Firefox, not the Ubuntu package.

Problem is that sites that use IFRAMEs will intermittently show the IFRAMEs as pop-up windows in Ubuntu, with the X Windows logo (grey X) as the window icon. Sometimes the window has the right content for the IFRAME, sometimes it has what looks like noise or is blank.

Closing these pop-up windows makes Firefox crash every time.  Sometimes if I reload the web page, the IFRAMEs go away, but once they have started they tend to recur.

Restarting Firefox cures the problem for a while, but eventually they recur - sometimes within 20-30 minutes.

On one page, before I got this IFRAME problem, a simple drop-down list failed to work - this is a site I use every day so I'm sure it's not a site error.

I do have almost 300 tabs open in this session (Tab Mix Plus and Tree Style Tabs, plus Tab Hunter, make it easier to do this!) so maybe that's related - perhaps the stress of so many tabs is causing this...

Has anyone else seen this?

UPDATE: I have tried removing plugins and using safe mode, so it's not a plugin/extension issue.

WORKAROUND: I'm not using so many tabs...  I managed to export Tab Mix Plus's URLs from session.rdf into a web page, and am now using less than 50 tabs.  Hasn't recurred at all so far - hence I believe this is a Firefox bug that shows up when using hundreds of tabs.

UPDATE: I still get this with 80 to 100 tabs.

---

### Post by Cato2 on 2009-02-06
This is a Firefox bug which affects frames as well as IFRAMEs, and probably other Gecko based browsers as well - see [https://bugzilla.mozilla.org/show_bug.cgi?id=263160](https://bugzilla.mozilla.org/show_bug.cgi?id=263160) for the details - unfortunately it's hard to reproduce and fix.

---

### Post by Cato2 on 2009-07-05
This bug is unfortunately still present on Firefox 3.5 on Linux.  It doesn't affect Windows or other platforms, only Linux.

---

### Post by Cato2 on 2010-01-24
This was fixed by a recent 3.5.x update - not having any of these IFRAME pop-outs or crashes on 3.5.7 (version downloaded from [http://getfirefox.com](http://getfirefox.com), not the Ubuntu version).  I'm using Ubuntu 8.04 so there was no need for a major GTK2+ upgrade.

---

