---
title: "Only root can run open office"
date: 2006-07-15
forum: Desktop Environments
---

### Post by kevin1 on 2006-07-15
This is what happens when trying to run as an ordinary user:

[INDENT]kevin@MainPC:/usr/lib/openoffice/program$ ./soffice.bin
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
Aborted[/INDENT]

If I try to start OO from the 'Applications' menu, or by double clicking in Nautilus on a .odt file (for which I have full permissions), the splash screen displays briefly, the bottom panel shows 'Starting OpenOffice.org Word Processor' for a few seconds, then they both disappear.

/usr/lib/openoffice/program/soffice.bin has the following permissions:

[INDENT][/INDENT]-rwxr-xr-x

so I should be able to execute it, shouldn't I?

Thanks for any advice,

Kevin

---

### Post by jordilin on 2006-07-15
You should not run openoffice like this > kevin@MainPC:/usr/lib/openoffice/program$ ./soffice.bin Type directly from the comand line oowriter and see what it says. If I'm not wrong soffice.bin is the program that loads openoffice in the memory and it resides in the notification area, so you can open an OpenOffice document in less than a second.

---

### Post by kevin1 on 2006-07-15
Thanks for the reply jordilin.

I was only trying to run via soffice.bin as an experiment because the 'Applications' menu & double clicking a .odt file failed to work.

Your suggested command line method results in:

[INDENT]kevin@MainPC:~$ oowriter
[Java framework] Error in function createUserSettingsDocument (elements.cxx).jav aldx failed!
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeExce ption'
/usr/lib/openoffice/program/soffice: line 233:  5211 Aborted                 "$s d_prog/$sd_binary" "$@"

** (process:5196): WARNING **: Unknown error forking main binary / abnormal earl y exit ...[/INDENT]

This message does not mean a lot to me. Any ideas?

Thanks,

Kevin

---

### Post by carontis on 2006-07-15
Alternate you can do this I use when something so, happens to me: 
System ==> Administration ==> System Monitor and in View choose "ALL PROCESSES , so you can see all; now choose Stop Process to all concerning Open Office and if it doesn't let you do so, choose Kill process. Sometime it's possible it get long to close, but usually it works (use it only if desperate...)

bye

---

### Post by jordilin on 2006-07-15
Give more details. Do you have a fresh Dapper Drake install? OpenOffice, as far as I know, runs smoothly in Dapper. Did you install some version of OpenOffice from OpenOffice website?

---

### Post by kevin1 on 2006-07-15
I checked with System / Admin / System Monitor as you suggested, and could not find any OO processes running.

I am running a fresh install of Dapper. I allowed the Update Manager to update all packages after the install. I have not installed OO from elsewhere, it is just as installed with Dapper.

Thanks,

Kevin

---

### Post by jordilin on 2006-07-15
Look into the file /var/log/messages and see if there's something related to openoffice when you are trying to run it.

---

### Post by kevin1 on 2006-07-15
There was nothing related to OO in /var/log/messages. I closed the file then tried starting OO from the 'Applications' menu again. I then opened /var/log/messages again: nothing had been added.

Thanks,

Kevin

---

### Post by jordilin on 2006-07-16
OpenOffice should run smoothly in a fresh Dapper install. If you really need it (as I suppose) why not try to reinstall Dapper as it only takes less than half an hour. You lose nothing but a little time. You can wait as well for another answer, but at this time I can't figure out what's going on.

---

### Post by andrewc6l on 2006-07-31
I ran into this problem as well with a fresh install of Dapper. In my case, when I tried to run oowriter from the command line, I saw:

[Java framework] Error in function createUserSettingsDocument (elements.cxx).javaldx failed!
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
/usr/lib/openoffice/program/soffice: line 233:  6437 Aborted                 "$sd_prog/$sd_binary" "$@"

** (process:6424): WARNING **: Unknown error forking main binary / abnormal early exit ...


It turned out that my OpenOffice 2.0 preferences directory somehow had magically changed ownership to root. (I still don't know how that happened. Maybe because the first app I opened was OpenOffice.org Database?) At any rate, I blew that config away:
   sudo rm -rf ~/.openoffice.org2/
and then reopened OpenOffice.org Word Processor. The directory was recreated and this time it was owned by me.

Presumably, I could have saved my config info with:
   sudo chown -R andrew.andrew ~/.openoffice.org2/
but in my case I didn't need to, since it was a fresh install.

    Andrew

---

### Post by kevin1 on 2006-08-04
Many thanks Andrew,

Problem sorted! :D 

Kevin

---

### Post by jmimick on 2006-08-23
Thanks - that was the fix. I had used sudo to access my Windows partition last night and opened up some Excel files. This changed the owner of the ~/.openoffice.org2/ folder to root - the chown worked like a charm.

Seems like a definite OpenOffice bug.

---

