---
title: "Multisync problem; Syncing Evolution-IrMC"
date: 2006-08-05
forum: Desktop Environments
---

### Post by drarmi on 2006-08-05
Hello fellow ubuntu users!

I have a problem! And need someones helping hand. I am hoping that someone else has found a solution or workaround for my problem.

I am new to Ubuntu. I have used Suse for a long time now and a couple of days ago I decided to move on to Ubuntu and see if this is something for me.

I am trying to sync between Evolution and my mobile phone using multisync and the multisync evolution and IrMC plugins.

First sync  everything goes well. The items from my phone are added in the empty evolution calendar. But after the first sync no sync will work after that.

In the log I see the message
"Failed to get first plugin changes: Unknown error "
and in that message "first plugin" referes to the evolution plugin.

I have have tried to find some other repository that has newer multisync packages that I can use but I cannot find any. maybe because I am new to Ubuntu.

Multisync is now being rewritten and will be released as a new project called opensync. I found a repository carrying packages to opensync but there was of course NO multisync-gui package. Only KDE gui.

I am hoping that someone can help me and probably others as well with this problem.

Grateful for all answers and help.

---

### Post by drarmi on 2006-08-08
Are there acctually no one in this forum that can help out in some way in regards to this problem ?

---

### Post by drarmi on 2006-08-08
One workaround I have figured out was to remove the files created by multisync in the evlution folder before a sync is initiated.

So when I want to sync my phone and evolution I do it doubleclicking a runnable script looking like this
-------------
#!/bin/sh

rm /home/patrik/.evolution/calendar/local/system/calendar.ics-msyncid3.db
multisync

-------------

This works for now but It would be alot better if anyone could come up with a real solution or possible a repository with later releases of multisync.

---

### Post by Jaxilian on 2006-08-12
> **drarmi said:**
> One workaround I have figured out was to remove the files created by multisync in the evlution folder before a sync is initiated.

So when I want to sync my phone and evolution I do it doubleclicking a runnable script looking like this
-------------
#!/bin/sh

rm /home/patrik/.evolution/calendar/local/system/calendar.ics-msyncid3.db
multisync

-------------

This works for now but It would be alot better if anyone could come up with a real solution or possible a repository with later releases of multisync.


Doesn't work for me. Don't even have that file. When I sync my cellphone, it tells that synch is complete. I am stuck at this point. doesn't Multisync create a link to Evolution by default at install? ](*,)

---

### Post by drarmi on 2006-08-12
> **flodis said:**
> Doesn't work for me. Don't even have that file. When I sync my cellphone, it tells that synch is complete. I am stuck at this point. doesn't Multisync create a link to Evolution by default at install? ](*,)


If you only can get the sync to work the first time this should be a solution for you. The file name "calendar.ics-msyncid3.db" could of cource be slightly  different for you. But you should get this file in your calendar directory.

When you set up Multisync pairs you get to choose what calendar and stuff you whant to sync. That must be the moment where the links are made to the correct calendar.

But you could also try out the rewritten Multisync called Opensync. Packages can be found here [http://www.in.fh-merseburg.de/~jahn/](http://www.in.fh-merseburg.de/~jahn/) .

---

### Post by Jaxilian on 2006-08-12
> **drarmi said:**
> If you only can get the sync to work the first time this should be a solution for you. The file name "calendar.ics-msyncid3.db" could of cource be slightly  different for you. But you should get this file in your calendar directory.

When you set up Multisync pairs you get to choose what calendar and stuff you whant to sync. That must be the moment where the links are made to the correct calendar.

But you could also try out the rewritten Multisync called Opensync. Packages can be found here [http://www.in.fh-merseburg.de/~jahn/](http://www.in.fh-merseburg.de/~jahn/) .

I get this errormessage in the log even though cellphone says synch goes ok:

"failed to connect local: connection error"

any ideas? I browsed google for it and nothing comes up. Wow! I thought....I must really be the only one in the world with that problem.

and if I put Multisync on auto, it doesnt detect ANYTHING I do in Evolution. Note: This is a fairly new install of Ubuntu

---

### Post by ryu kun on 2007-08-06
Well, I am in the same situation with drarmi with one difference, the "ugly way" didn't work here. Anyway, it looks like in 1 year after this thread posted there hasn't been any developments in any related software so we Ubuntu users still cannot sync our mobile phones easily and properly.

My addressbook, calendar and to do lists change very often. It is an everyday task to syncing them, so doing it in Windows isn't practical for me. I feel desperate.

---

