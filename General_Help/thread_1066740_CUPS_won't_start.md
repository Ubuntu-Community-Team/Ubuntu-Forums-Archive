---
title: "CUPS won't start"
date: 2009-02-11
forum: General Help
---

### Post by theozzlives on 2009-02-11
* Starting Common Unix Printing System: cupsd                                  cupsd: Child exited on signal 15!
                                                                         [fail]
That's the error I get when starting CUPS after running a remastersys restore. The printer dialog says not connected! help please!!

---

### Post by theozzlives on 2009-02-11
Bump

---

### Post by lykwydchykyn on 2009-02-11
Can you post this file: /var/log/cups/error_log
Also, restart cups and immediately do : tail /var/log/syslog

---

### Post by theozzlives on 2009-02-11
From the error_log, there was a problem with the link to a file at /etc/cups/ssl. I went there and deleted those two files, and cups starts fine, but now my printer isn't in the drivers list. I provided the *.ppd file from my test Jaunty box and it said I had to install gutenprint-cups before I can print.

---

### Post by theozzlives on 2009-02-12
bump

---

### Post by lykwydchykyn on 2009-02-12
So did you install gutenprint?  Did it fix anything?

---

### Post by linux6994 on 2009-02-12
Have you tried to remove any printers and then performing a redetect?

On the initial grub message hit esc and it will open the boot choices, select the current kernel recovery. This will allow it to redetect everything and hopefully correct the cups trouble.

---

### Post by theozzlives on 2009-02-12
No gutenprint didn't do anything, and it's a network printer. There is nothing to detect.

---

### Post by lykwydchykyn on 2009-02-12
What make and model is the printer? Did it work previously?  Give us some history on this system and printer.

---

### Post by theozzlives on 2009-02-13
> **lykwydchykyn said:**
> What make and model is the printer? Did it work previously?  Give us some history on this system and printer.

the problem is not the system or printer, it's CUPS. To humor you, the system is a Dell Inspiron 1525, 1.73 GHz, 2 GB RAM, the printer is attached to a 500 MHz, 256 MB RAM which prints fine. The printer is an Epson Stylus CX8400 which Ubuntu 8.10 handles quite well. I'm sharing the printer over a SAMBA network.

I think I just need to re-do the whole CUPS package but don't know how. All four of my systems print fine except the one I restored.

---

### Post by lykwydchykyn on 2009-02-13
If you just want to "re-do" CUPS, then:
```

sudo aptitude purge cups
sudo aptitude install cups

```

That's for intrepid; if you're on hardy I believe the package is cupsys.

---

### Post by theozzlives on 2009-02-14
now my printer isn't in the driver list, how do I fix that?

---

### Post by theozzlives on 2009-02-14
I just re-installed my root partition and that took care of ot

---

