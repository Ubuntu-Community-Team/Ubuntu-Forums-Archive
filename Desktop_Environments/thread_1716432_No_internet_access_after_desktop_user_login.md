---
title: "No internet access after desktop user login"
date: 2011-03-28
forum: Desktop Environments
---

### Post by kkelly77 on 2011-03-28
My laptop is running Ubuntu 10.04. I have my own account (custom) and 1 desktop user account. 

When I log in under my account and switch to the desktop user account, I can connect to the internet. However, if I start the laptop and log into the desktop user account first I get no internet connection and the same when I switch to my own (custom) account. What gives? :confused:

K

---

### Post by Krytarik on 2011-03-28
Although that wouldn't explain the last mentioned scenario, check if the option "Available to all user" is ticked in the settings of your connection in "System > Administration -> Network".

Also check if all related "User Privileges" for the user are ticked in "System -> Administration -> Users and Groups -> Advanced Settings".

Also, are you using a keyring for a possibly existing connection password?

---

### Post by wyliecoyoteuk on 2011-03-28
Log in as the main user, right click on the network icon, click "edit connections" select the network connection, and click "edit". Then tick "available to all users"

---

### Post by kkelly77 on 2011-03-28
> **wyliecoyoteuk said:**
> Log in as the main user, right click on the network icon, click "edit connections" select the network connection, and click "edit". Then tick "available to all users"

And we have a winner!!! :D

Thanks wyliecoyoteuk =D>

---

