---
title: "graphcis drivers."
date: 2008-07-02
forum: Gaming &amp; Leisure
---

### Post by Lecotti on 2008-07-02
Hi, i am relativly new to linux and have a bit of a noob question to ask.
do i have to install the nvidia graphics card drivers (nvidia.com) as well as activiate proprietary drivers (system>admin>hardware drivers) beacuse at the moment i only have the proprietary ones enabled. Help would be appreciated

---

### Post by eragon100 on 2008-07-02
When you activate them in the restricted manager, they are automatically downloaded and installed for you. So they should already work right now :)

---

### Post by starcannon on 2008-07-02
@Lecotti short answer is: its a one or the other, not both.

Next answer:

To find out if they are working:

Open a terminal: Applications-->Accessories-->Terminal
Type or copy past in the following:

```
glxinfo | grep direct
```

if it spits out

> direct rendering: Yes

then you should be all set.

---

### Post by Lecotti on 2008-07-02
Thanks! :)

---

