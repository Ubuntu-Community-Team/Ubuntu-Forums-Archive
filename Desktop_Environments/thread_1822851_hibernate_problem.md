---
title: "hibernate problem"
date: 2011-08-11
forum: Desktop Environments
---

### Post by Sameh Ataa on 2011-08-11
_**hibernate problem**_
i am using fujitsu s761 laptop with ubuntu 10.10 mavrick when i press hibernate nothing happen. when i am try to use pm-hibernate command message indicate that the running script exit with 128 code number

---

### Post by westie457 on 2011-08-11
> **Sameh Ataa said:**
> _**hibernate problem**_
i am using fujitsu s761 laptop with ubuntu 10.10 mavrick when i press hibernate nothing happen. when i am try to use pm-hibernate command message indicate that the running script exit with 128 code number

The only thing I can think of to cause this is the size of you Swap partition.

Open a terminal please (System > Applications > Terminal) and type in ```
sudo fdisk -l
```
# The l is a lower-case L not a 1.
# You will be asked for your password. Nothing will show on the screen not even a * your typing will be recognised.

Copy and Paste the output in a New Reply. Remembering to click the # at the top of the Message pane and paste between the [CODE] brackets.

Thank you.

---

