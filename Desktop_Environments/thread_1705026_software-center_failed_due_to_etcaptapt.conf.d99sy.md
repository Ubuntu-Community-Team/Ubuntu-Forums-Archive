---
title: "software-center failed due to /etc/apt/apt.conf.d/99synaptic permission"
date: 2011-03-11
forum: Desktop Environments
---

### Post by btng on 2011-03-11
Ubuntu Software Center failed to launch.  There is an error message on the top panel giving a wrong lead.  It said something about a broken package.  The real error is a permission on the file /etc/apt/apt.conf.d/99synaptic.

Here's the output from running software-center from a shell:
Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 37, in <module>
    from softwarecenter.db.application import Application, DebFileApplication
  File "/usr/share/software-center/softwarecenter/db/application.py", line 19, in <module>
    from apt.debfile import DebPackage
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 35, in <module>
    apt_pkg.init()
SystemError: E:Opening configuration file /etc/apt/apt.conf.d/99synaptic - ifstream::ifstream (13: Permission denied)

The permission on the 99synaptic file is 640, whereas the permission on other files in this directory is 644.  Adding world the missing world read permission seems to fix the problem, but I'm not sure if that's the correct fix or not.  Perhaps there's a reason for not having world read permission on this file.

Someone smarter than I am has to decide whether my fix is good or not.

Maybe the real solution is to run software-center under sudo.  I don't know.

Thanks.

---

### Post by Krytarik on 2011-03-11
"644" is fine on "99synaptic", I also have it that way, and I didn't change anything there.

About Software Center with "gksudo": No need to do this, it is designed to ask for a password if it needs to.

Greetings.

---

### Post by btng on 2011-03-13
I don't know why my 99synaptic file had 640 permission.  But ok, the problem is fixed by adding the missing permission.

---

### Post by dlazerka on 2011-04-18
Just to note, that I also got 640 on 99synaptic somehow.

---

