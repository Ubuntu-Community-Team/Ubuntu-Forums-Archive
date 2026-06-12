---
title: "Where does cups-pdf output to?"
date: 2015-02-08
forum: Fedora/RedHat and derivatives
---

### Post by monkeybrain20122 on 2015-02-08
As the title says I don't find any directory that cups-pdf outputs to when print with evince. I went to settings and configured the printer (there is only one which is cups-pdf) to output to /home/mysusername/PDF (I created the directory) but still don't see any output. There was no error message, it just went through the motion with notifications such as "printing blah blah" and "printing blah blah completeted". 

Fedora 21 64 bit.

---

### Post by ajgreeny on 2015-02-08
I have never used cups.pdf but I presume it asks you to give a name to the output, so you should be able to find that named file with command ```
find -name filename.pdf
```and thus know to where it outputs.

---

### Post by sandyd on 2015-02-08
> **monkeybrain20122 said:**
> As the title says I don't find any directory that cups-pdf outputs to when print with evince. I went to settings and configured the printer (there is only one which is cups-pdf) to output to /home/mysusername/PDF (I created the directory) but still don't see any output. There was no error message, it just went through the motion with notifications such as "printing blah blah" and "printing blah blah completeted". 

Fedora 21 64 bit.

Have you checked the ANONYMOUS printing folder, if memory serves, its in /var/spool/cups-pdf/ANONYMOUS

---

### Post by monkeybrain20122 on 2015-02-09
> **ajgreeny said:**
> I have never used cups.pdf but I presume it asks you to give a name to the output, so you should be able to find that named file with command ```
find -name filename.pdf
```and thus know to where it outputs.

It doesn't find anything

---

### Post by monkeybrain20122 on 2015-02-09
> **sandyd said:**
> Have you checked the ANONYMOUS printing folder, if memory serves, its in /var/spool/cups-pdf/ANONYMOUS

There is a directory called  /var/spool/cups-pdf/SPOOL but it is empty.

---

### Post by Elfy on 2015-02-09
/etc/cups/cups-pdf.conf - where does that say it's saving?

---

