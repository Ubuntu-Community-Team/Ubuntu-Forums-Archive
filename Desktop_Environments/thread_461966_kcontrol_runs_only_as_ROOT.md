---
title: "kcontrol runs only as ROOT"
date: 2007-06-02
forum: Desktop Environments
---

### Post by janarene on 2007-06-02
Feisty 7.04 - KDE
Since the Administrator Mode button is missing In the KDM Theme Manager portion of System Settings, I'm trying to use kcontrol to change my themes.  Typing 'kcontrol' from the BASH prompt runs kcontrol as ROOT and not as me!  Needless to say, kcontrol changes ROOT's settings quite nicely...

but what about meeee?  Is there a way to run kcontrol as myself?  

-Peace

---

### Post by janarene on 2007-06-03
I dunno what bump means but I keep seeing it and nobody's replied.  Maybe this bump thingy gives more exposure?

---

### Post by Erunno on 2007-06-03
I never encountered the problem before but let's try the following and hope for the best:

1. Press Alt-F2.
2. Enter "kcontrol" without the quotation marks. 
3. Press Enter.
4. Report back and tell me if it worked. ;-)

EDIT:

Are you sure that you aren't running kcontrol from a root shell or with sudo?

---

### Post by janarene on 2007-06-03
Wonderful workaround - I hadn't thought of that.  My KDE desktop doesn't allow Alt-F2 but has a Run Command... in the sys menu that worked quite well.  Typing kcontrol from there ran the app with my username perfectly - so we'll do business that way.  Now the weird part of this still lies in the konsole session when I'm logged in as myself and typing kcontrol : I end up editing the roots settings!  I'm *triple* checking that I'm not su, and no.. I'm definitely not.

Weird - but since I know how to work with it, I'm happy.  Thank You! :)

---

