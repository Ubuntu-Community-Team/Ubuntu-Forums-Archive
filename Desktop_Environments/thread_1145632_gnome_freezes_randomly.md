---
title: "gnome freezes randomly"
date: 2009-05-01
forum: Desktop Environments
---

### Post by melefire on 2009-05-01
Recently I have started to have issues with Ubuntu 9.04. It seems to just randomly freeze during use. I GNOME and have a nvidia graphics chipset. I cannot however seem to pin the problem. The freezes occur at completely random times and I have to forcefully restart my computer. Any ideas for a fix?

---

### Post by Peasantoid on 2009-05-01
Do you have Compiz enabled?

---

### Post by melefire on 2009-05-01
not that im aware of

---

### Post by Peasantoid on 2009-05-01
Okay, do this. Go to System > Preferences > Appearance, click the Visual Effects tab, and tell me what it's set to.

---

### Post by melefire on 2009-05-01
its set to "Normal"

---

### Post by Peasantoid on 2009-05-01
...you have Compiz enabled.

Set it to None and tell me if that helps.

---

### Post by melefire on 2009-05-02
I have now concluded that it is not compiz or gnome, or even xorg. This is because i just experanced a freeup right when ubuntu was booting. Right when the little things moves accross the loading bar at bootup. Any other ideas?

thanks for your help sofar

---

### Post by Peasantoid on 2009-05-02
Sorry, I've never encountered that before... Try booting in recovery mode?

---

### Post by keithld on 2009-05-02
Have you checked you PC Fans to see if they are still running???... How old is your computer???

If the fan on your CPU stops intermittently it can lock up the system because it's overheating...

---

### Post by melefire on 2009-05-02
thats what i thought at first so i installed temp monitors and the temp never rises above 106F so i dont think its overheating.

---

### Post by juliosergio on 2009-08-10
I have what seems to me the very same problem. Apparently this has to do with the Java virtual machine or the Java run time environment, because the situation arises when some application launches Java. In my case, I discovered it when starting Mozilla Firefox. Firefox froze and sometimes all the desktop froze as well, then I killed it and then a small display announcing that "Java VM is loading" lasted for ages until I also killed it. Now, the situation also arose when I started Netbeans, (an IDE for Java and other languages) which again launches Java VM. I don't know how to solve the problem yet. Maybe installing a new version of Java will solve the problem.

---

### Post by ArmenianLeader4 on 2009-08-10
Turn off compiz, your effects, any excess apps, desklets or anything like that, and you should be fine.

---

