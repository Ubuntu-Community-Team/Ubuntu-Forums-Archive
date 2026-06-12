---
title: "gdesklets-daemon timeout"
date: 2006-04-13
forum: Desktop Environments
---

### Post by halfvolle melk on 2006-04-13
Hi,
Trying to run the freshly installed gDesklets results in this error:
> Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
The log file says this:
> Log messages of /home/jz/.gdesklets/logs/gdesklets%3A0.0.log

==========================================================[04/13/06-10:02:00]====== Unhandled error! Something bad and unexpected happened.

[EXC]/usr/lib/libcairo.so.2: undefined symbol: FT_GlyphSlot_Embolden
in /usr/lib/gdesklets/gdesklets-daemon: line 127 ?
in /usr/lib/gdesklets/gdesklets-daemon: line 108 _gdesklets_main
in /usr/lib/gdesklets/main/__init__.py: line 115 init
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 123 _new_imp
in /usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py: line 37 ?
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 123 _new_imp
[EXC]/usr/lib/gdesklets/utils/ErrorFormatter.py

[---]  118 # give us an absolute path.
[---]  119 #
[---]  120 _old_imp = __import__
[---]  121 def _new_imp(name, globs = {}, locls = {}, fromlist = []):
[---]  122
[ERR]> 123     module = _old_imp(name, globs, locls, fromlist)
[---]  124     # builtin modules have no "__file__" attribute, so we have to check for it
[---]  125     if (hasattr(module, "__file__")):
[---]  126         module.__file__ = os.path.abspath(module.__file__)
[---]  127     return module
[---]  128
[---]  129 import __builtin__
Any ideas on how this can be resolved?

Cheers,
HM

---

### Post by Ramses de Norre on 2006-04-13
Is it the version from the repo's? Maybe just try reinstalling it..
```
sudo apt-get remove --purge gdesklets gdesklets-data && sudo apt-get install gdesklets gdesklets-data
```

---

### Post by halfvolle melk on 2006-04-13
Thanks for your reply.

Yup, it's the version from the repo's.
> gdesklets:
  Installed: 0.35.2-1build1
  Candidate: 0.35.2-1build1
  Version table:
 *** 0.35.2-1build1 0
        500 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) breezy/universe Packages
        100 /var/lib/dpkg/status

Unfortunately a reinstall didn't help. The errors and log file are identical.

Edit: Fixed!
There was a similar issue with Bittorrent, this fixed both:

**sudo gedit /etc/apt/sources.list**
then add in the end this
**deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted**
Save (you can let the window open).
**sudo apt-get update**
**sudo apt-get install libfreetype6**
Comment out/remove the Dapper repository from /etc/apt/sources.list

[http://nowherenet.altervista.org/blog/static.php?page=linux-ubuntu-libcairo6](http://nowherenet.altervista.org/blog/static.php?page=linux-ubuntu-libcairo6)
[https://launchpad.net/distros/ubuntu/+source/libcairo/+bug/6100](https://launchpad.net/distros/ubuntu/+source/libcairo/+bug/6100)

---

### Post by josef.sabl on 2008-04-20
I have this problem in Hardy, suggested solution does not work however. Not even with changing **dapper** word to **hardy** :-)

Thanks for any help.

---

### Post by zaius55 on 2008-04-28
I have the exact same problem.  Haven't been able to use gdesklets in hardy yet (been playing with it for a couple months).

---

### Post by icedogchi on 2008-05-04
Same issue, except my log file is empty, located here (maybe I'm looking at the wrong log folder?):

~/.gdesklets/logs/gdesklets%3A0.0log


Edit: (Just upgraded to Hardy, never used gdesklets in the previous Ubuntu version)


Edit:  Here's a solution:

[http://ubuntuforums.org/showthread.php?t=582721](http://ubuntuforums.org/showthread.php?t=582721)

---

