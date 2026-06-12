---
title: "Printing GUI Not Working"
date: 2011-08-11
forum: Desktop Environments
---

### Post by TimmyD on 2011-08-11
I am hopping to get some help with a printing application problem.

When I go to System>Administration>Printing, I get nothing.

I have found several possible solutions, but these did not work for me.

First, from Ubuntu Bugs, following the URL: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/210738](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/210738)

But Bug 210738, file 04/02/2008, doesn't fix my issue.

I did getting the following results by running 'system-config-printer' in a terminal:

tim@dell-desktop:~$ system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 104, in <module>
    from GroupsPane import *
  File "/usr/share/system-config-printer/GroupsPane.py", line 21, in <module>
    from GroupsPaneModel import *
  File "/usr/share/system-config-printer/GroupsPaneModel.py", line 19, in <module>
    import libxml2
  File "/usr/lib/pymodules/python2.6/libxml2.py", line 1, in <module>
    import libxml2mod
ImportError: /usr/lib/pymodules/python2.6/libxml2mod.so: symbol xmlFirstElementChild, version LIBXML2_2.7.3 not defined in file libxml2.so.2 with link time reference
tim@dell-desktop:~$ 

Next, Googling "not defined in file libxml2.so.2 with link time reference" yielded a link to Ubuntu Forums, 
[http://ubuntuforums.org/showthread.php?t=1383483&page=1](http://ubuntuforums.org/showthread.php?t=1383483&page=1),
but this did not fix it either

At this point I ought to mention that I can print to my existing printers, but I wanted to add a new printer.

I have no idea when this problem occurred, maybe when I upgraded from Ubuntu 8.4 LTS (Hardy Heron) to Ubuntu 10.4 LTS, but I can't be sure.

To add the printer I followed this link [http://localhost:631/printers/](http://localhost:631/printers/) and was able to add the new printer.

But, after all is said and done, I think the GUI should just work, especially if we want Ubuntu to be more ubiquitous on the desktop.

Could I get some help with this?

Thanks!

---

### Post by wazupwiop on 2011-08-11
You might want to try reinstalling or upgrading CUPS.....  You might try searching the software center for another printer gui.

---

### Post by trongbang on 2011-10-14
The same here bro!
Can't do anything else. Maybe that is the only solution!

---

### Post by mango.muncher on 2011-12-18
Info:
I came across this thread when searching for a solution because my print GUI also wasn't working. Tried running the program 'system-config-printer' in terminal and got output:
The program 'system-config-printer' is currently not installed.  You can install it by typing:sudo apt-get install system-config-printer-gnome
So I did and all OK. Somehow GUI had been removed.

---

