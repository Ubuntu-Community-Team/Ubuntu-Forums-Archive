---
title: "Automatic Logout Ubuntu 22.04"
date: 2023-01-18
forum: Desktop Environments
---

### Post by touhid2 on 2023-01-18
Hello,
I am using ubuntu 22.04, freshly installed last month. After that its logout automatically closing all the running programs. It has no fixed time but I observe that when its idle, it doesnot logout. During office hours, when I am working, it logged our suddenly.
Any help on this is highly appreciated.

---

### Post by ActionParsnip on 2023-01-18
Which desktop environment are you being logged out of?

---

### Post by touhid2 on 2023-01-18
GNOME-Flashback:GNOME

---

### Post by Claus7 on 2023-02-05
Hello,

does it show a white screen with a depressed icon? If affirmative I was facing the same issue, without any luck.

Regards!

---

### Post by ian-weisser on 2023-02-05
A surprise logout may be a *desktop crash*.

Check your /var/crash for crash files.

---

### Post by Claus7 on 2023-02-07
Hello,

> **ian-weisser said:**
> A surprise logout may be a *desktop crash*.

Check your /var/crash for crash files.

I can see that I have some crashes (crash files), yet they are relatively new. The earliest at the time of writing is four days ago. Didn't know this one existed. Thank you for posting. 
Searching a little bit more I was able to find how to report bugs from these files:
[https://ubuntu.com/server/docs/reporting-bugs](https://ubuntu.com/server/docs/reporting-bugs)

Regards!

---

