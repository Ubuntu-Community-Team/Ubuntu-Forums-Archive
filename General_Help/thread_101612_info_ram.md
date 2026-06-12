---
title: "info ram"
date: 2005-12-10
forum: General Help
---

### Post by nene on 2005-12-10
how can I rezieve information of my ram??
th

---

### Post by doitashimashite on 2005-12-10
cat /proc/meminfo

---

### Post by nene on 2005-12-10
how to rezieve information like: ram type, frequency.... etc

---

### Post by SickTwist on 2005-12-10
Run this command in a terminal:

sudo lshw | less

It will print information about all of the hardware, including specifics about the RAM if that information is available. Use the arrow keys to scroll up and down. Press "q" (without quotes) when you are done viewing it.

---

