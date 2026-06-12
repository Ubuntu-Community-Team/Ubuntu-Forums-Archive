---
title: "Bad JobSheets value"
date: 2010-11-23
forum: Desktop Environments
---

### Post by barna on 2010-11-23
A few years ago this problem has been reported. Will this ever be fixed? I don't know if this is related to kde or cups, the problem is the following: when configuring a printer from the kde system settings, /etc/cups/printers.conf will contain this line for the new printer:
```

JobSheets

```
whereas it should
```

JobSheets none none

```
Printing anything from a graphical program with gui, one just gets no output. Output is visible from command line printing, the error message is:
```

lpr: Bad job-sheets value ""!

```
one has to edit (as superuser) /etc/cups/printers.conf, and restart cups (/etc/init.d/cups restart)

---

### Post by Laloi on 2010-12-07
Thank you ! Merci !!

---

### Post by DatBugler on 2011-01-25
Thank you! This has been getting on my nerves for months and I had no clue how to fix it!

---

### Post by barna on 2011-01-25
Could somebody post a bug report? I already did quite a long time ago, and I am fed up posting another one for no benefit...

---

### Post by Racecar56 on 2011-02-24
I just had this in Debian Squeeze with KDE 4.4.5.

---

### Post by wolfgangpauli on 2011-04-20
Thanks, works for me too!

---

