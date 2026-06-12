---
title: "Monitor"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-10
I have a monitor that requires 1024 x 768 and I need to edit the xorg file but I cant remember what I need to have in the file...  Can somebody post exactlly what I need in my xorg file, For my monitor to work?  

Note:  My monitor is Hatachi Superscan Surpreme 21

Thanks in advance

---

### Post by Ramses de Norre on 2006-09-10
Something like this in your screen section: ```
                Modes           "**1024x768**" "832x624" "800x600" "720x400" "640x480"

```

---

### Post by Magiczero on 2006-09-10
Should I erease all the the other ones and just have 1024 x 768?

---

### Post by Ramses de Norre on 2006-09-10
That makes no difference, X uses the first available resolution.

---

