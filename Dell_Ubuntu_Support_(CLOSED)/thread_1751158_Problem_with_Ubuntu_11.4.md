---
title: "Problem with Ubuntu 11.4"
date: 2011-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ndphysics on 2011-05-06
Recently I upgraded Ubuntu in my Desktop to 11.4. In the next day I tried to turn on computer and switch to Ubuntu. I could not see anything other than blinking. It shows up with distorted icons after many back and forth and again does the same. It never stops. I rebooted computer many times the problem is the same. Once I chose the  option of previous version. It looked good once but in the next time appeared nothing. 
May you tell me what could have caused it and what I have to do to fix it.

---

### Post by Grenage on 2011-05-06
> **ndphysics said:**
> Recently I upgraded Ubuntu in my Desktop to 11.4. In the next day I tried to turn on computer and switch to Ubuntu. I could not see anything other than blinking. It shows up with distorted icons after many back and forth and again does the same. It never stops. I rebooted computer many times the problem is the same. Once I chose the  option of previous version. It looked good once but in the next time appeared nothing. 
May you tell me what could have caused it and what I have to do to fix it.

This is probably a graphical driver issue, but I can't be sure.  Did you enable any restricted (additional) drivers, or are you using the defaults?  Do you know what graphics card you have?  If not, please post the output of the terminal command:

```
lspci | grep VGA
```

---

### Post by ndphysics on 2011-05-06
It is surprising that I could do for 1 day and it came up in the next. I can not see anything because the screen is not stable too so I can not write the output of the terminal. I am not sure with the graphic card in my computer; may you tell me how I can check it please?  For sure, it is with Bit 64.

---

### Post by Grenage on 2011-05-06
Of course you can't; what I should of added was that you should be able to get a terminal prompt by pressing Ctr-Alt-F1.  Ctr-Alt-F8 would normally take you back to the GUI.

---

