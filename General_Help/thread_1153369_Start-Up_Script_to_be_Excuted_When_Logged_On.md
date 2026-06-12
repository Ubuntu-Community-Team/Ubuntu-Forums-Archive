---
title: "Start-Up Script to be Excuted When Logged On"
date: 2009-05-08
forum: General Help
---

### Post by IamReck on 2009-05-08
Hey All - 

Here is my goal - 

I want to make it so that when I turn my system on and log in, the script will look at whether or not I have an internet connection (this really could just be ping google.com).

If that is successful, wait 30 seconds and start a list of services. (pidgin, gmail notify, firefox, dropbox are the ones I want for now).

I am also looking to see if I can get GMail Notify to start with out asking me enter the password for my keyrings...

Does anyone know where I need to place this script in order for it to execute at log in and what commands I would need to do to run it?

I had this:

#! /bin/bash

sleep 30
gm-notify.py
pidgin

exit 0

When I ran this in terminal all that started was GMail Notify...

Thanks!

---

### Post by cybergalvez on 2009-05-08
> **IamReck said:**
> Hey All - 

Here is my goal - 

I want to make it so that when I turn my system on and log in, the script will look at whether or not I have an internet connection (this really could just be ping google.com).

If that is successful, wait 30 seconds and start a list of services. (pidgin, gmail notify, firefox, dropbox are the ones I want for now).

I am also looking to see if I can get GMail Notify to start with out asking me enter the password for my keyrings...

Does anyone know where I need to place this script in order for it to execute at log in and what commands I would need to do to run it?

I had this:

#! /bin/bash

sleep 30
gm-notify.py
pidgin

exit 0

When I ran this in terminal all that started was GMail Notify...

Thanks!

Try adding & after you commands

---

### Post by IamReck on 2009-05-08
It is working now, thanks!

For anyone else that comes across this thread, the & (ampersand) sends the job to the background.

---

