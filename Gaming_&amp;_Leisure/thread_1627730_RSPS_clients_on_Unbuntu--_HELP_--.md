---
title: "RSPS clients on Unbuntu-- HELP --"
date: 2010-11-21
forum: Gaming &amp; Leisure
---

### Post by rayra3 on 2010-11-21
I am trying to get this RSPS client to work for my laptop.  I really dont know what i am doing but here is the code in the run file.  The file is run.bat atm, what do i do to make it work?

```
@echo off
title Client
start http://ultra-scape.tk/
start javaw -Xmx500m -cp .;./bin; EGUI
```

---

### Post by rayra3 on 2010-11-24
bumpity bump bump

---

### Post by doorknob60 on 2010-11-24
Try opening a terminal into the folder where the .bat file is and running this:
```
javaw -Xmx500m -cp .:./bin: EGUI
```

---

