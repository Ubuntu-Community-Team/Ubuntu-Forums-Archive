---
title: "Suspend/Hiberante problems Dell Inspiron 1150 Hardy 8.04"
date: 2008-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 954kwh on 2008-07-28
I'm pretty new to Linux/Ubuntu and have searched numerous forums for a solution.  The problem I'm having is that neither Suspend nor Hibernate work properly.

Suspend:  when the computer comes out of Suspend, all is good except the network connection is no longer functioning.

Hibernate: it goes into Hibernation but freezes at the initial Ubuntu progress screen.

Any easy solutions to this.

Thanks.

Peter

---

### Post by 954kwh on 2008-07-28
A little update:

Changing /ect/defaults/acpi-support such that POST_VIDEO=false  allowed it to come out of Hibernation.  However, like when it came out of Suspend, it is no longer connected to the network.  I have to use Network Manager to reset the Network Location to (in my case) "Home".  Is there some way of getting the network location to reset automatically?

Thanks.

Peter

---

