---
title: "How Do I Play Midi Files?"
date: 2006-09-29
forum: Desktop Environments
---

### Post by hk_2999 on 2006-09-29
I've got a system with no sound card but has internal HDA(high definition audio) hardware. Whatever that means.

Anyway, I was wondering, is there any GUI that could let me play my MIDI files, or even manage them? I tried pykaraoke, but it does not play even just half of my midi files, and I'm tired of using timidity on the console too.

---

### Post by LKRaider on 2006-10-07
run: **timidity -ig**

if it doesn't work, install the **timidity-interfaces-extra** package. It will give you a GTK2 interface to timidity.

---

### Post by fragos on 2006-10-07
Thanks LKRaider.  I'd been using timidity on the command line.  It's nice to finally get a GUI interface.

---

### Post by hk_2999 on 2006-10-24
> **LKRaider said:**
> run: **timidity -ig**

if it doesn't work, install the **timidity-interfaces-extra** package. It will give you a GTK2 interface to timidity.

Whoa! I didnt know that. Thanks a lot LKRaider!

---

