---
title: "Inspiron 1525 microphone in Ubuntu 8.04"
date: 2008-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by luisjorge on 2008-04-28
Hi everyone! I installed Ubuntu 8.04 in my Inspiron 1525, and I can't get the internal analog microphone to work. I already tried recording with every input device I can find, but all I get is silence.
Does anyone know how to get this working?

Thanks in advance!

Luis Jorge.

---

### Post by jdelaros1 on 2008-05-21
Do you mean the built-in analog that you can speak into or the analog jack, where you would need to plug-in an external mic?

Either way, run gnome-volume-control

Select Edit -> Preferences and select all tracks. In the Options tab, set the Digital Input Source to "Analog inputs" and select the first "Input Source" field to "Mic" for the built-in mic and "Front-Mic" for the external microphone.

---

### Post by ostamb on 2008-08-27
Hey thanks! gnome-volume-control worked beautifully! However, why isn't it available through the Applications or System menus? Can you only access it through the terminal?

---

