---
title: "How to Disable Login Screen"
date: 2007-02-18
forum: Desktop Environments
---

### Post by insyted on 2007-02-18
How do you disable login screen?

---

### Post by navneeth on 2007-02-18
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s01.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s01.html)

---

### Post by insyted on 2007-02-18
The "Login Window" option disappeared from my System/Administration menu.

---

### Post by insyted on 2007-02-18
I realized that the Login Window option disappeared from the Administration menu when I logged on as "root".
Does anybody know why this happened?
Now what do I have to do allow enable automatic login?

---

### Post by mcduck on 2007-02-19
> **insyted said:**
> I realized that the Login Window option disappeared from the Administration menu when I logged on as "root".
Does anybody know why this happened?
Now what do I have to do allow enable automatic login?

You should never ever log into desktop as root. That's really unsafe, and there's absolutely no reason to do that anyway.

Anyway, all administration tools are configured to be run b your own user using 'sudo'. And that's why they don't work if you are root.

---

### Post by insyted on 2007-02-19
Is it possible to log in automatically as root?

I don't understand about logging in as root.
Isn't that the administrator?
I don't want any users on my PC. Just a single administrator.

---

