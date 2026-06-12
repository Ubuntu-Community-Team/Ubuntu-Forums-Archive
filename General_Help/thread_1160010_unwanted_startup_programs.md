---
title: "unwanted startup programs"
date: 2009-05-15
forum: General Help
---

### Post by david sousa on 2009-05-15
There is an option at System/preferences/startup applications/options which says "remember blah blah". And because i wanted to try this I have selected this checkbox.

And then when I turned on my netbook i had the terminal and firefox starting with ubuntu.

But now i don't want them to start with ubuntu and i turned off that option but they still appear.

What can i do? they are not at the startup programs list...

thanks

---

### Post by dnairb on 2009-05-15
The "remember blah blah" will remember applications that are running at the time you make the selection.

Close applications that you don't want running at startup, then select the "remember blah blah" thingy and reboot.

---

### Post by david sousa on 2009-05-15
already  tried...

---

### Post by david sousa on 2009-05-16
it did not work so there must be another way to do this

---

### Post by scouser73 on 2009-05-16
Try **System** > **Administration** > **Services** and unchecking any of the services that are associated with the start-up.

---

### Post by AlNaimi on 2009-05-16
Hi david sousa
You may have to start ubuntu and close all applications start when you login, Then check (remember blah blah) and try to log out agin.
when you log in again you have to check the box again so it could not remember blah blah... that how it is work...
I hope it work

---

### Post by david sousa on 2009-05-16
There must be a config file or something because any of this things do what i want

---

### Post by dnairb on 2009-05-16
OK, this works on my system:

System --> Preferences --> Startup Applications.
Options tab.
Make sure that "Automatically remember..." ***is*** ticked.
Close.

**Close all applications not required at startup**.

Log off, then back on.

No applications should be running.

Go to Startup Applications, Options again, and this time ensure that "Automatically remember..." ***is not*** ticked and then close.

---

### Post by david sousa on 2009-05-17
that worked. thanks

---

### Post by dnairb on 2009-05-17
Cool :) Glad to help..

---

