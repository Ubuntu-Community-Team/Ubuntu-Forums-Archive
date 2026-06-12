---
title: "Such a newb question - where do 'Startup Applications' get stored?"
date: 2010-11-21
forum: Desktop Environments
---

### Post by dillinga on 2010-11-21
Hi Guys,

I've just moved to Ubuntu and using Linux on the desktop in general. I use RHEL on a daily basis for work so don't really have much experience with window managers etc but like to understand how I'm doing what I'm doing.

In that regard, I've configured a couple of scripts to be run when I login using 'System -> Preferences -> Startup Applications' but what I want to know is where do these settings actually get stored within the file system?

Thanks!

Tony

---

### Post by Grumpey on 2010-11-21
Believe it's
 ~/.config/autostart

---

### Post by dillinga on 2010-11-21
Thanks. Don't know how that didn't turn up in the find command I did earlier(!)

---

### Post by sisco311 on 2010-11-21
Yep, the user's autostart directory is ~/.config/autostart/ and the system wide one is /etc/xdg/autostart/.

For more info check out:
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)
and
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

---

