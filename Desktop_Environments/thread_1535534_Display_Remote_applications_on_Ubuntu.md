---
title: "Display Remote applications on Ubuntu"
date: 2010-07-21
forum: Desktop Environments
---

### Post by cs_raja on 2010-07-21
Hello,

  I have applications running on some other machines. I want to display  the UI in UBUNTU.

  I dont know how to do that.

  Can somebody help out !

Advance Thanks

---

### Post by anglican on 2010-07-21
> **cs_raja said:**
> Hello,

  I have applications running on some other machines. I want to display  the UI in UBUNTU.

  I dont know how to do that.

  Can somebody help out !

Advance Thanks
Assuming you're talking about other linux machines:

```
ssh -X username@remotehost name_of_program
```If it's Windows then you'll need some sort of remote desktop to do this (e.g. VNC).

H

---

