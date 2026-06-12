---
title: "How to build boot scripts?"
date: 2005-06-28
forum: Desktop Environments
---

### Post by sickdude on 2005-06-28
ok i want to make a botscript for my bluetooth device but i dont really have a clue how to do that

so i was wondering if someone can help me out with this :)

---

### Post by sickdude on 2005-06-29
[CENTER] ](*,)  bump ](*,)[/CENTER] 




:P

---

### Post by debian_n00b on 2005-06-29
try this...


create the file /etc/init.d/startup.sh          The first line should be:

#!/bin/sh

make the file executable:

chmod 755 /etc/init.d/startup.sh

schedule the script to run on boot-up:

update-rc.d startup.sh defaults


then edit /etc/init.d/startup.sh and add the commands you want to run...

i havnt actually done this on a ubuntu box yet, but it does enable me to execute specific commands on my straight debian machines
you will also be required to execute the above commands as root, or use sudo of course

---

### Post by sickdude on 2005-06-29
[QUOTE=debian_n00b]try this...

schedule the script to run on boot-up:

update-rc.d startup.sh defaults

[/QUOTE]

what should i edit in this file, there is a sh*tload of text in this file and i cant seem to find something that has to do with things he should do when it boots  :-?

---

### Post by alastair on 2005-06-29
There's a "skeleton" init script in /etc/init.d.

Copy this to /etc/init.d/bluetooth (say) - then edit.

Remember, that the basic question is just to "do something" when an argument to the script is "start", "stop" etc. You can experiment, and don't need to deal with everything.

Test by running :

/etc/init/d/bluetooth start
/etc/init/d/bluetooth stop
etc.

---

### Post by sickdude on 2005-06-30
ok this is really helpfull thx

but the files in de ini.d/ folder are not going to start on boot, right?

so in what file can i find the stuff that the system starts on boot?

---

### Post by alastair on 2005-06-30
I have a feeling you do not know the boot/init process. So it might be worth doing a little research on this aspect of unix/linux e.g.

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

The files in /etc/init.d are started at boot (and runlevel change e.g. shutdown) IF configured to do so.

---

### Post by sickdude on 2005-07-01
aaaa ok i didnt know that

well i got it running now

thnx for helping me out with this :D

---

