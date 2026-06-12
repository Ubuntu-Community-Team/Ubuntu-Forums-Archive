---
title: "XFCE uses less CPU than LXDE. Is that normal?"
date: 2012-08-02
forum: Desktop Environments
---

### Post by yoreei on 2012-08-02
Hi. I have an old laptop running Xubuntu. I thought that LXDE would be better for it because it is lighter. When I switch to LXDE I can clearly see the CPU meter indicating higher CPU usage. The fan apparently agrees with it because it is much louder while running LXDE. I can't, however, notice any performance impact. Strange, isn't it? I thought that LXDE was made with speed in mind.

---

### Post by LewisTM on 2012-08-02
Out of curiosity, what process is using all that CPU?
Open a taskmanager (top, lxtask) and fin the top CPU% processes then report back.
If it's something related to LXDE then maybe the Lubuntu people might like to know.

Cheers!

---

### Post by yoreei on 2012-08-03
> **LewisTM said:**
> Out of curiosity, what process is using all that CPU?
Open a taskmanager (top, lxtask) and fin the top CPU% processes then report back.
If it's something related to LXDE then maybe the Lubuntu people might like to know.

Cheers!
Hi and sorry for the late reply. I followed your advice and found that it wasn't LXDE. It was BOINC! This is a program that lets you contribute some of your CPU to projects around the world that need it. I installed it on this old laptop just out of curiosity and then disabled it because I felt pity for the old machine handling computations about a cryptographic project. For some reason when I switch DEs, the program starts (it proceeds even when I switch back to XFCE. I read that this behaviour is normal for the program).

---

