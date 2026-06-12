---
title: "How to read internal temperatures on Inspiron 520n"
date: 2008-07-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RedRat on 2008-07-06
Ok, my memory has faded. What command do you use in terminal (command line) to read back the internal temps, such as CPU temps. I am running an Inspiron 520n and not the laptop. the command acpi seems designed for laptops and not desktops.

---

### Post by konungursvia on 2008-07-06
```
acpi -t
``` Worked on my desktop too... wonder why it's different in your case.

---

### Post by RedRat on 2008-07-06
> **konungursvia said:**
> ```
acpi -t
``` Worked on my desktop too... wonder why it's different in your case.

Yeah I found that too. But I get back 40.0 C every time I try it. When I see a number like 40.0 and it keeps coming up consistently I begin to worry that perhaps I am not measuring in the real world. Being a scientist by training, if I got results like that in the lab, I would be very suspicious--we scientists are a skeptical lot.

---

### Post by Denny Johnson on 2008-07-06
I just checked my 1420n. Same 40.0 C.

---

### Post by RedRat on 2008-07-06
> **Denny Johnson said:**
> I just checked my 1420n. Same 40.0 C.
Well this indeed makes me very suspicious that two very different computers get the same result, and probably different processors. I suspect that acpi is not measuring the actual cpu temp.

---

