---
title: "unable to login"
date: 2006-11-29
forum: Desktop Environments
---

### Post by viveknz76 on 2006-11-29
Hi,

I made my ubuntu machine a member of windows domain.  Once I restrarted the machine and tried to login the system does not allow me to login. I tried logging in through console.If I use the local username and pass it says "Module is unknown". If I use domain login details It says "User not known to underlying authentication module".  What's the issue and how can I overcome it

Thanks

---

### Post by dlehman on 2006-11-29
well I don't know the answer, I'm sure someone here is more of an expert them me but

try recovery mode and reset it back to normal

also why would you rely on windows to authenticate ubuntu???

---

### Post by defishguy on 2006-12-01
The message usually means that there is a problem with the user name or password.  If you have dot in your username such as joe.smith then that would be your problem... linux doesn't do dots in user names or any other "meta" characters.

---

