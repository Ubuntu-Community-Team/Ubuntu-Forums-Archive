---
title: "3 thermal readings, but only 2 processors.  What's the 3rd?"
date: 2009-06-23
forum: General Help
---

### Post by cknight on 2009-06-23
Well, post title pretty much says it all.  Here's my acpi output:

```
...
     Thermal 0: ok, 47.0 degrees C
     Thermal 1: ok, 42.0 degrees C
     Thermal 2: ok, 46.0 degrees C
     Cooling 0: Processor 0 of 10
     Cooling 1: Processor 0 of 10

```

I've got a dual core laptop with (duh!) 2 processors.  What's the 3rd thermal reading for?

---

### Post by RJ12 on 2009-06-23
Ok my answer was wrong but it still could in other cases be the cpu fan has a sensor
I guess the real answer is below my post

---

### Post by Thingymebob on 2009-06-23
[COLOR=Black]Core i7 and Core 2 processors have 2 different types of temperature sensors; a CPU case (not computer case) Thermal Diode centered under the Cores, and Digital Thermal Sensors located on each Core. The case Thermal Diode measures Tcase (Temperature case), which is CPU temperature, and the Digital Thermal Sensors measure Tjunction (Temperature junction), which is Core temperature. Since these sensors measure 2 distinct thermal levels, there is a 5c temperature difference between them, which is Tcase to Tjunction Gradient. Ci7s and C2Q's have 1 Tcase and 4 Tjunction sensors, while C2D's have 1 Tcase and 2 Tjunction sensors. Uncalibrated default temperatures are seldom accurate.

So briefly, you have 2 core temperatures and a processor case temperature and it looks like thermal 1 is probably Tcase, while 0 and 2 are your core temps
[/COLOR]

---

### Post by cknight on 2009-06-23
> **Thingymebob said:**
> [COLOR=Black]Core i7 and Core 2 processors have 2 different types of temperature sensors; a CPU case (not computer case) Thermal Diode centered under the Cores, and Digital Thermal Sensors located on each Core. The case Thermal Diode measures Tcase (Temperature case), which is CPU temperature, and the Digital Thermal Sensors measure Tjunction (Temperature junction), which is Core temperature. Since these sensors measure 2 distinct thermal levels, there is a 5c temperature difference between them, which is Tcase to Tjunction Gradient. Ci7s and C2Q's have 1 Tcase and 4 Tjunction sensors, while C2D's have 1 Tcase and 2 Tjunction sensors. Uncalibrated default temperatures are seldom accurate.

So briefly, you have 2 core temperatures and a processor case temperature and it looks like thermal 1 is probably Tcase, while 0 and 2 are your core temps
[/COLOR]
Brilliant. :)  Thanks for that

---

