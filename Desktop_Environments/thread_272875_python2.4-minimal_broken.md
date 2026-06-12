---
title: "python2.4-minimal broken"
date: 2006-10-07
forum: Desktop Environments
---

### Post by NiceGuyUK on 2006-10-07
Updating from apt this morning reported a broken python2.4-minimal which stopped me continuing with subsequent updates.  There's a couple of typos in one of the python files (UserString.py) which breaks it. :( 

Edit lines 78 and 80 of /usr/lib/python2.4/UserString.py, replacing the word rdturn with the word return and save it out.  I'm not 100% sure, but you may need to do this as root (via sudo).

Then just re-run your update and all should work. :) 

See [https://launchpad.net/distros/ubuntu/+source/python2.4/+bug/64504](https://launchpad.net/distros/ubuntu/+source/python2.4/+bug/64504) for the bug report.

---

