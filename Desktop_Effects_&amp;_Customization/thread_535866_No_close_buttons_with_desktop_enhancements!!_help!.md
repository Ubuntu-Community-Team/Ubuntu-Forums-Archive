---
title: "No close buttons with desktop enhancements?!?!? help!"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by floydjunkie8 on 2007-08-27
ok so i am pretty new to ubuntu especially to 7.04. anyway my computer is plenty capable to run desktop effects.  so i enabled it and it worked but now the maximize, resize, and close buttons are gone!  

i dont know what has caused it and i cant seem to find any answers to it in the other posts.

plz help!!!:confused:

thanx in advance

---

### Post by be4truth on 2007-08-27
Do you run Beryl or you just enabled the Desktop effects in the System/Administration menu?

---

### Post by floydjunkie8 on 2007-08-27
i just enabled it and i dont know exactly how to run beryl

---

### Post by be4truth on 2007-08-27
I don't know what your problem is with the data provided. I have disabled the Ubuntu Desktop effects and installed Beryl which works 99% fine. It needs some configuration but it looks really fancy. Be aware that Beryl and Compiz are quite experimental. They are not stable and don't blame them if things don't work out of the box.

---

### Post by DarkN00b on 2007-08-27
Desktop effects are based on Compiz. Disable desktop effects and run this command in a terminal window:

```
compiz --replace
```

If that works, you should add that command to your startup session. The problem is that desktop effects is running with no window decorator.

---

