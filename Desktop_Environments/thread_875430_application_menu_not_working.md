---
title: "application menu not working"
date: 2008-07-30
forum: Desktop Environments
---

### Post by yon2501 on 2008-07-30
For some reason or another my applications menu decided to stop coming down when i click it, places and system still pop down but not applications, also the menu editor wont open when i right click and select it. also the launch menu applet in awn only shows the places and system menus as well. any suggestions?

---

### Post by Gibbs on 2008-10-26
I just had this problem and it was a quick fix so thought I should reply.

Just delete the **applications.menu** file under **/home/<username>/.config/menus**

---

### Post by azeezp on 2009-03-22
Thanks Gibbs, very good solution.
It worked for me too.. But any idea what was the cause of this beahviour?

Azeez

---

### Post by Lylex11 on 2009-06-07
Thanks for this fix. I had the same problem after upgrading to 9.04. I tried deleted .config .configd but did not work. deleting applications.menu worked

---

### Post by Adhok on 2009-09-17
Great fix, helped me a ton.  Happened to me after installing the MIPS32 simulator(SPIM) from synaptic package manager.  Any idea what caused the problem though, just for a brain tease :)

Thanks again!

Adhok

---

