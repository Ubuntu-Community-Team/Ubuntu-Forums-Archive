---
title: "[SOLVED] Can't find the PDF Printer"
date: 2008-11-14
forum: Desktop Environments
---

### Post by fballem on 2008-11-14
I seem to remember under Hardy that there was a 'printer' that would produce a PDF file.

I am now running 8.10-AMD64 and I don't have that type of a printer. Could someone please tell me how to install it?

Many thanks,

---

### Post by binbash on 2008-11-14
i was using cups-pdf (sudo apt-get install cups-pdf)

---

### Post by fballem on 2008-11-14
> **binbash said:**
> i was using cups-pdf (sudo apt-get install cups-pdf)

Thanks for this - I was able to install and use it. Just one question - where does it put the resulting PDF file?

Thanks,

---

### Post by stinger30au on 2008-11-14
create a directory in your home directory called "PDF"


when installing the pdf printer it *should* default to this location

---

### Post by binbash on 2008-11-14
you can define the location at cups-pdf.conf

and pre-defined location is : ### Default: /var/spool/cups-pdf/${USER}  according to the config

---

### Post by fballem on 2008-11-14
> **stinger30au said:**
> create a directory in your home directory called "PDF"


when installing the pdf printer it *should* default to this location

Worked perfectly - many thanks

---

### Post by lyni on 2008-11-15
in Ubuntu 8.4 there is already a PDF folder in the home directory. have they taken it out in the 8.10?

---

