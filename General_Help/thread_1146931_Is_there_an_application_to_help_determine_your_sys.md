---
title: "Is there an application to help determine your system's configuration?"
date: 2009-05-03
forum: General Help
---

### Post by YMS_1975 on 2009-05-03
I'm running Ubuntu 9.04 Jaunty Jackalope, and was wondering if there's any sort of application or an internal utility tool (already included with Ubuntu 9.04) that will display information such as :

- Motherboard information (Make/Model)
- Amount & type of Ram installed on the system
- Video Card Information

Is there something out there that will display that information?

---

### Post by DeMus on 2009-05-03
> **YMS_1975 said:**
> I'm running Ubuntu 9.04 Jaunty Jackalope, and was wondering if there's any sort of application or an internal utility tool (already included with Ubuntu 9.04) that will display information such as :

- Motherboard information (Make/Model)
- Amount & type of Ram installed on the system
- Video Card Information

Is there something out there that will display that information?

Try hwinfo, it's in the repositories.

Edit: or use lshw >lshw.txt which will make a text file with the results it found.

---

### Post by fballem on 2009-05-03
> **DeMus said:**
> Try hwinfo, it's in the repositories.

Edit: or use lshw >lshw.txt which will make a text file with the results it found.

Once it is installed, where does it show up on the menus?

Thanks,

---

### Post by jmszr on 2009-05-03
YMS_1975,

This will show you all (or more than) you want to know: 

```
lshw -html > ~/Desktop/hardware.html

```
It will show up on your Desktop, just click on it for your information.

---

### Post by SLEEPER_V on 2009-05-03
and the hwinfo?  It showed in the terminal, but is there a desktop location?

---

### Post by DeMus on 2009-05-03
> **SLEEPER_V said:**
> and the hwinfo?  It showed in the terminal, but is there a desktop location?

No, it's controlled from the terminal as so many programs and instructions

---

### Post by SLEEPER_V on 2009-05-03
thats cool with me.  I dont really need it.  I like a silky smooth desktop

---

