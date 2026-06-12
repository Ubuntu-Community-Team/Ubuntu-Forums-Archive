---
title: "Memory Leak?"
date: 2005-08-01
forum: Desktop Environments
---

### Post by jlacroix on 2005-08-01
Hey all, I got a quick question, I looked at my System Monitor and it says I have 758.2MB of RAM. I actually have 768MB. I tried rebooting but it still says the same thing.  Am I losing RAM?!

---

### Post by jasmuz on 2005-08-02
Did you check if your RAM is being used by integrated video? or maybe there is a faulty memory unit?

---

### Post by jlacroix on 2005-08-02
I don't think I have integrated video, I am using an NVidia AGP card.

---

### Post by varunus on 2005-08-02
Some of your RAM will get used by udev to mount a ramdisk over /dev, that's possibly where its going.

---

