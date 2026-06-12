---
title: "set font style to default theme?"
date: 2013-09-15
forum: Desktop Environments
---

### Post by pickarooney on 2013-09-15
For some reason my fonts have gone all ugly* in Firefox and a few other applications. I've tried everything I can think of within FF to get them to look better but to no avail. I tested with the guest account login and the fonts in Firefox and in everything else look much nicer. So, I'm looking for a simple way to get my own account to use the default/guest font settings for everything.

*The thickness of the letters, particularly the M and W is not consistent and everything is kind of jaggedy.

---

### Post by ajgreeny on 2013-09-15
Have you got a file called .fonts.conf in your home and do you run kde applications which you've configured with kde-system-settings?

If so delete the .fonts.conf file and start a new session (logout and login again) and you may find all is well again.

See a previous thread of mine [http://ubuntuforums.org/showthread.php?t=2125379](http://ubuntuforums.org/showthread.php?t=2125379)

---

### Post by pickarooney on 2013-09-15
> **ajgreeny said:**
> Have you got a file called .fonts.conf in your home and do you run kde applications which you've configured with kde-system-settings?

If so delete the .fonts.conf file and start a new session (logout and login again) and you may find all is well again.

See a previous thread of mine [http://ubuntuforums.org/showthread.php?t=2125379](http://ubuntuforums.org/showthread.php?t=2125379)

That seems to have worked like a charm. Many thanks :)

---

### Post by pickarooney on 2013-09-15
The downside is now my KDE apps look like crap. Is there some way of keeping both happy?

---

### Post by ajgreeny on 2013-09-16
You can still use the kde system-settings app but just avoid making changes to the font configuration.

Perhaps you need to make changes to your fonts in xubuntu that will also look good in KDE/qt apps.  Here is my fonts configuration from settings-manager and how my qt/kde app look..
Default font - ubuntu 11
Anti-aliasing - enabled
Hinting - slight
Sub-pixel order - None
Default DPI settings (96dpi)

---

### Post by pickarooney on 2013-09-17
Thanks once again. That's another significant improvement :)

---

### Post by ajgreeny on 2013-09-17
Great!

Just fiddle around with your Xubuntu font config and you may find with your own hardware that the clarity improves even more than you have already, particularly with changes to the sub-pixel-order, which I find can suddenly change font rendering, but best settings does depend on the monitor, I think.

---

### Post by cmcanulty on 2013-09-17
try the firefox addon "theme font & size changer", really helps

---

### Post by pickarooney on 2013-09-18
This is probably a bit cheeky as it's a little off topic but I've been struggling with the appearance of what I think are GTK apps in Xubuntu. The buttons and colours are a bit 'old school' as you can see in post 3 of this thread:
[http://ubuntuforums.org/showthread.php?t=2172367](http://ubuntuforums.org/showthread.php?t=2172367)

Does anyone know what config tool I need to use to alter that theme?

---

