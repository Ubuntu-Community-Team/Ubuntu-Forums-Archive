---
title: "New to Ubuntu--firmware missing"
date: 2011-02-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by deedsr on 2011-02-16
I am new to ubuntu, don't really know much about linux at all. I installed ubuntu alongside my windows 7 os, and ubuntu says my firmware is missing. I am running a dell wireless 1397 wlan mini card. Can anyone help me?

---

### Post by mikewhatever on 2011-02-16
Just hook up a cable and you'll get a notification about the available firmware. It comes from System->Administration->Additional-Drivers, just need to be online to work.

---

### Post by deedsr on 2011-02-16
i have done that. it keeps coming up with a jockey error.

---

### Post by mikewhatever on 2011-02-16
Since Jockey doesn't work for you, do it the geeky way:

open Applications->Accessories->Terminal

run **sudo apt-get install bcmwl-kernel-source**

reboot
.

---

### Post by deedsr on 2011-02-16
i got it working. thanks. and the geeky way is why i want to learn linux. lol. i like a challenge, and almost nothing challenges me. i thought linux might.

---

