---
title: "Problems with addUser"
date: 2006-07-03
forum: Desktop Environments
---

### Post by tzenes on 2006-07-03
When I run adduser I get the following message:

adduser: Only one or two names allowed.

I currently only have one name and would like to add others.

Forgive my ignorance, but is there a reason for this? or a way to change this?

I found a thread which talked about this problem befor, but provided no solution:
[http://www.ubuntuforums.org/showthread.php?p=1155489](http://www.ubuntuforums.org/showthread.php?p=1155489)

---

### Post by mlind on 2006-07-03
It's probably bug with adduser, but it's not supposed to be used that way.
try adduser --help

---

### Post by tzenes on 2006-07-03
[QUOTE=mlind]It's probably bug with adduser, but it's not supposed to be used that way.
try adduser --help[/QUOTE]

Thanks, I noticed under help there was the option to supply the username on command line, which worked without the error message

However in previous builds of adduser I was able to supply the username interactively.

While this isn't a fix to the bug it is a quick work around.

---

### Post by mlind on 2006-07-03
[QUOTE=tzenes]Thanks, I noticed under help there was the option to supply the username on command line, which worked without the error message

However in previous builds of adduser I was able to supply the username interactively.

While this isn't a fix to the bug it is a quick work around.[/QUOTE]

I couldn't find non-argument usage from adduser manual page..
If you feel this behaviour is a bug, report it on [https://launchpad.net/distros/ubuntu/+source/adduser/+bugs](https://launchpad.net/distros/ubuntu/+source/adduser/+bugs)

---

