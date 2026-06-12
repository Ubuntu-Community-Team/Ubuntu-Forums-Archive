---
title: "how can I change the time format to 12 hr clock and login clock as well?"
date: 2008-12-27
forum: General Help
---

### Post by Lukasz Tarkowski on 2008-12-27
how can I change the time format to 12 hr clock and login clock as well?

---

### Post by Monotoko on 2008-12-27
Right click the time, go to preferences, click 12hr

Not sure if this changes it on the logon screen, it should though

---

### Post by Lukasz Tarkowski on 2008-12-27
Thank You Monotoko
It didn't work for the login window :(
If there is no solution to this then its fine :P

---

### Post by dcstar on 2009-01-10
> **Lukasz Tarkowski said:**
> Thank You Monotoko
It didn't work for the login window :(
If there is no solution to this then its fine :P

I found this didn't work on my 8.04 and 8.10 installs, and then found an old bug (that they said was fixed ages ago) which I have just added to:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/129528](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/129528)

---

### Post by jrusso2 on 2009-01-10
No matter what I check or try the clock is 24 hours time.

---

### Post by todak on 2009-01-10
Go to **System> Administration> Login Window**. On the **General** tab you will see an entry for **Use 24 Hour Clock**. Your choices are **auto yes no**. Choose **no** for 12 hr. clock in login screen! :)

---

### Post by Lukasz Tarkowski on 2009-02-13
This fixed it for me
[https://help.ubuntu.com/community/UbuntuDateBug]("https://help.ubuntu.com/community/UbuntuDateBug")Solved!

---

### Post by Lukasz Tarkowski on 2009-02-13
Ok I have the **datebug** This solution I posted earlier only works untill I reboot and then again I have to enter it :(
I hope you can fix this guys!

---

