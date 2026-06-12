---
title: "FireFox Printer Settings - Revisit"
date: 2009-03-05
forum: General Help
---

### Post by dr.wong on 2009-03-05
Hey everyone,

I found this post a long time ago : [http://ubuntuforums.org/showthread.php?t=869537](http://ubuntuforums.org/showthread.php?t=869537)

It has to do with FireFox 3 not being able to save printer settings.

There was never a conclusion or solution in that thread, but this is still a serious problem so I think we should revisit it.

Basically, the problem is that when you print a web page in FireFox on Ubuntu (8.10), the printer settings aren't ever saved, so if you set the page headers and footers to blank, the next time you print a page, the settings go back to default.

In previous versions of FireFox, this always used to save.

A bug report has been filed here : [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/250140](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/250140)

Many people, myself included cannot wait any longer as the problem has not been solved.

Does anyone know how to write a plugin perhaps? One that applies settings each time you print?

I am a PHP programmer and I know a bit of delphi, not sure if that will help but if you know of a good tutorial for writing plugins, I am willing to try.

Anyone think we can MAKE a work around for this problem?

---

### Post by gofishel on 2009-05-31
Just want to check in that I also have this problem. I renamed my firefox user profile and still have the issue so I know it's not a setting in firefox.

---

### Post by gofishel on 2009-05-31
OK I think I found the answer. 
try changing the settings with: "/usr/lib/openoffice/program/spadmin"
The settings stuck for me. Got it from [https://answers.launchpad.net/ubuntu/+question/24669](https://answers.launchpad.net/ubuntu/+question/24669)

---

### Post by dr.wong on 2009-07-04
Hey! Great to see some responses at last :)

I will try that when I get home in couple weeks. On vacation now so I can't report back.

Does anyone know if this problem has been resolved in FF3.5?

---

