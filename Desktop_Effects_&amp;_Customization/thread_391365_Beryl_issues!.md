---
title: "Beryl issues!"
date: 2007-03-23
forum: Desktop Effects &amp; Customization
---

### Post by TURNER on 2007-03-23
Hi all,

I have just installed Beryl on my Ubuntu 6.10 system, and have thus far been able to log into an xgl session once....which was a pleasure! :)  However now when I attempt to start an xgl session the following occurs:

      Desktop items and all menu items disappear
      Unable to see any text within desktop
      desktop background graphic disappears.


See screen shots, before and after...

"Normal Gnome session"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=28065&stc=1&d=1174640666[/IMG]

"Beryl XGL session"

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=28066&stc=1&d=1174640435[/IMG]

My system details are as follows:

P4 2.4ghz
256mb RAM :oops: 
64mb ATI Radeon 7500

gixgears functions ok however. so I dont believe it's opengl related..

can anyone offer some advice?

---

### Post by swamytk on 2007-03-23
1. Ensure that you have enabled swap file system
2. Try changing the color depth in /etc/X11/xorg.conf file

---

### Post by TURNER on 2007-03-23
> 1. Ensure that you have enabled swap file system
2. Try changing the color depth in /etc/X11/xorg.conf file

I am uncertain how to perform both of these tasks, however I'll look it up, give it a whirl when iam back home (working at the moment, on the legacy os!).

I appreciate your feedback a lot! seems your one of a few people with any ideas about these issues....

I'll try this out and get back to you! :KS

---

### Post by orawax on 2007-04-06
> **TURNER said:**
> Desktop items and all menu items disappear
Unable to see any text within desktop
desktop background graphic disappears.

I found the solution for the exact same problem (in intel graphics driver) here:
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

There's also a collection of Beryl guides:
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

Hope these help, if you haven't found the solution already.

---

