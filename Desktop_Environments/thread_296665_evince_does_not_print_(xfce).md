---
title: "evince does not print (xfce)"
date: 2006-11-09
forum: Desktop Environments
---

### Post by lduperval on 2006-11-09
Hi,

I am using xfce under edgy. For some reason, evince refuses to print on my default printer. I can send documents to the printer  from Firefox, Thunderbird, and OpenOffice. However, when I try to print to my default printer with evince, the print button is greyed out.

I tried with acrobat reader and it prints fine also.

Does anyone have an idea what could be the problem?

Thanks,

L

---

### Post by Bavo on 2006-11-24
I have the same problem but in gnome, most apps work just fine including gtk/gnome apps like gedit, evolution, ..

So far i have only noticed that evince and yelp don't seem to find any printers.

I'm using a cups server for the printers.

Does anyone have any idea how to fix this problem?

---

### Post by therblack on 2007-01-23
I'm having this problem too...the print button in evince is greyed out for all my printers (they are network printers).  I too use cups.

Any ideas?

thanks

---

### Post by richrosa on 2007-03-31
has anyone every solved this problem? I have it too.

---

### Post by robc02 on 2007-03-31
I have the problem as well (Ubuntu - Gnome). I can click on "Print" but nothing happens. When I check on the printer menu the job is shown as stopped.

---

### Post by lduperval on 2007-04-02
I may be wrong, but it seems to happen only with network printers.

L

---

### Post by robc02 on 2007-04-02
My printer is not networked.

---

### Post by smolakian on 2007-04-20
Yep, I'm having the same problem. I am using a network printer. I can print from everything else except eclipse. But, I'm not sure if thats part of the same problem.

---

### Post by John the train on 2007-04-22
This seems to be a general Linux problem, I had the same problem on my desktop, running Fedora Core 6, The only way i could print PDF's was to open thm in Gimp, until I installed the Adobe reader for Linux. I had wondered if it was a conflict between Evince and the Avasys driver for my usb Epson printer, but it sems not.

---

### Post by NickUhlig on 2008-03-11
I had this same problem for a while.  I could print using OpenOffice and AbiWord, but I couldn't print using any type of PDF viewing software.  

I fixed it by re-installing my printer.  Just go to Printer Settings and re-installation is relatively quick and painless.

Hope that helps.

---

### Post by ilborg on 2008-04-14
Same thing seems to be now problem in gentoo/windowlab and evince. Only option is "print to file". I have cups server in other machine, and i see printer in other softwares like opera etc. I'll try xpdf first before I try crappy adobe software.

---

### Post by ilborg on 2008-04-16
Problem solved. When I launched application from console, it gave couple of errors about missing file called  "libgnutls.so.13". However similiar file exists in library directory so I just symlinked the other file to "libgnutls.so.13".

Here is my command lines. Your file names could differ a bit.

```

sudo ln -s /usr/lib/libgnutls.so /usr/lib/libgnutls.so.13

```

If can't find libgnutls.so file, use "locate libgnutls.so" to find something like libgnutls.so.2.6.3 and use it instead.

---

### Post by pmorton on 2008-04-21
> **ilborg said:**
> Problem solved. When I launched application from console, it gave couple of errors about missing file called  "libgnutls.so.13". However similiar file exists in library directory so I just symlinked the other file to "libgnutls.so.13".

Here is my command lines. Your file names could differ a bit.

```

sudo ln -s /usr/lib/libgnutls.so /usr/lib/libgnutls.so.13

```

If can't find libgnutls.so file, use "locate libgnutls.so" to find something like libgnutls.so.2.6.3 and use it instead.

Have same problem with Hardy/Gnome. Print button shaded  out for network printer _and_ PDF printer. /usr/bin already contains symlink libgnutls.so.13 pointing to  libgnutls.so.13.x.x. Makes no difference.

---

### Post by Elegorod on 2008-04-29
Same problem after updating to Hardy. Printing from OpenOffice, Opera works normally. But from Gnome programs doesn't work. Still no solution?

---

### Post by Elegorod on 2008-05-12
I found a workaround to my problem. My computer has 2 Ethernet adapters, with IP 10.6.x.x and 192.168.0.1 . I hadn't enter CUPS ( [http://localhost:631/](http://localhost:631/) ) because of 403 forbidden error. CUPS saw ethernet IP's and not 127.0.0.1 (why?). And gnome programs hadn't access too and couldn't add printer job.
So I edited /etc/cups/cupsd.conf
Added strings which start with Allow 
```

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow 10.6.6.121
  Allow 192.168.0.1
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
  Allow 10.6.6.121
  Allow 192.168.0.1
</Location>

```

---

