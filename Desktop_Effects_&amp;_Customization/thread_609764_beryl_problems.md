---
title: "beryl problems"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by ricky_cullen on 2007-11-11
i have just installed beryl and i try to make the desktop effects work,
anyone know why this is happening? :confused:

---

### Post by Nano Geek on 2007-11-11
You could try [Compiz-Fusion.]("http://compiz-fusion.org/")
Here are the [installation instructions]("http://wiki.compiz-fusion.org/Installation").

---

### Post by Nano Geek on 2007-11-11
Or, if you want to keep Beryl, type **beryl --replace** into the command-line and tell us what it says.

---

### Post by ricky_cullen on 2007-11-12
it says
```

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```

---

### Post by chytraeus on 2007-11-12
I am using debian testing and i am getting the exact same error. would also like to know how to fix this.

---

### Post by ricky_cullen on 2007-11-12
umm i feel like a noob now for posting i have found a problem  just like ours and it has the solution here is the link [http://ubuntuforums.org/showthread.php?t=436110&page=3]("http://ubuntuforums.org/showthread.php?t=436110&page=3")

---

### Post by ricky_cullen on 2007-11-12
> **ricky_cullen said:**
> umm i feel like a noob now for posting i have found a problem  just like ours and it has the solution here is the link [http://ubuntuforums.org/showthread.php?t=436110&page=3]("http://ubuntuforums.org/showthread.php?t=436110&page=3")

open mouth insert foot, it didn't work for me,:(

---

### Post by ricky_cullen on 2007-11-12
ok ive tried compiz fusion, and well not i know longer see my GDM but it is like a termenal login sayin that xorg cant be found,](*,) what do i do, im a noob at this stuff:frown:
plz help ASAP, rite now the only way im gettin to do this is from the Live CD.

---

### Post by Nano Geek on 2007-11-13
> **ricky_cullen said:**
> ok ive tried compiz fusion, and well not i know longer see my GDM but it is like a termenal login sayin that xorg cant be found,](*,) what do i do, im a noob at this stuff:frown:
plz help ASAP, rite now the only way im gettin to do this is from the Live CD.So sorry I took so long responding. Try this:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by ricky_cullen on 2007-11-14
it no big deal i found my way by using my empty second harddrive and just copyed everything i need over, but i will remeber that for next time thanks.
One more thing why would compiz-fusion to cause X server to crash, just so i dont fall into the same probelm again lol

---

### Post by ricky_cullen on 2007-11-14
ok so i have compiz fusion install but nothing works, still, and my computer should hold it ATI 9600 pro 2 gighertz 512 ram, am i doing somthing wrong?

EDIT: Ive also swiched to 7.10 and i like what i see however im still getting the same error, i have the drivers installed, i looked the post i linked to before, and i seen  "xserver XGL" and that made my system run well less than normal any other ideas?

---

