---
title: "Hardware reporter"
date: 2009-01-30
forum: General Help
---

### Post by YigalB on 2009-01-30
Is there a utility that reports back the hardware installed on the PC?
I am looking to know:
- Motherboard vendor and model
- BIOS version (and update if available)
- Chipset vendor and model
- Network/sound cards vendors and drivers
- Graphic card: vendor, model, BIOS version, driver and updates

---

### Post by Neural oD on 2009-01-30
command line type in sud lshw

---

### Post by Neural oD on 2009-01-30
sorry typo  - it should be sudo lshw 
that should give u all the info u need :)

---

### Post by hyper_ch on 2009-01-30
```

sudo lshw -html > ~/Desktop/hardware.html

```

---

### Post by YigalB on 2009-01-30
> **Neural oD said:**
> sorry typo  - it should be sudo lshw 
that should give u all the info u need :)

Absolutely - exactly what I needed!

Thank you.

---

### Post by Neural oD on 2009-01-30
glad to help - remember to mark your thread as solved :)

---

### Post by YigalB on 2009-01-30
> **Neural oD said:**
> glad to help - remember to mark your thread as solved :)

How do I do that?

---

### Post by hyper_ch on 2009-01-30
you can't right now as this feature has been turned off.

---

### Post by Neural oD on 2009-01-30
> **hyper_ch said:**
> you can't right now as this feature has been turned off.

Jeez - sorry about that - wasn't aware of that - why has this been turned off may i ask?

---

### Post by hyper_ch on 2009-01-30
there ware some database and performance problems a little while back and to lessen the burden of the server several "unnecessary" tools were (temporarily) switched of... like the thread solved and thanks tools.

---

### Post by Neural oD on 2009-01-30
> **hyper_ch said:**
> there ware some database and performance problems a little while back and to lessen the burden of the server several "unnecessary" tools were (temporarily) switched of... like the thread solved and thanks tools.
Thanks for the explanation

---

