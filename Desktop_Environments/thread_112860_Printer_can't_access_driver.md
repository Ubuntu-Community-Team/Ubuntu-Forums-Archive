---
title: "Printer can't access driver"
date: 2006-01-05
forum: Desktop Environments
---

### Post by moontide on 2006-01-05
I have an Epson Stylus Photo 915 ink jet printer (usb) that I can't get to work. I have just installed Ubuntu 5.04 from disk and then upgraded to 5.10. I seem to have every thing else working great, Kino, Xine, Qdvdauthor, Amarok, gl-117 all work well. The problem seems to be getting the print driver associated with the printer. I notice that Gimp doesn't show the cups driver as an option although I have installed it. Usually I would just log on to the cups site and set up the printer but I can't do this with Ubuntu. The only message I get is "job Paused" or "Printer not ready".

With Thanks, Robert.

---

### Post by Sef on 2006-01-05
Take at look at this page in linuxprinting:

[http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_915]("http://linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_915")

If you still need some help afterwards, just post again.

---

### Post by moontide on 2006-01-06
have an Epson Stylus Photo 915 ink jet printer (usb) that I can't get to work. I have just installed Ubuntu 5.04 from disk and then upgraded to 5.10.  The problem seems to be getting the print driver associated with the printer. I notice that Gimp doesn't show the cups driver as an option although I have installed it. Usually I would just log on to the cups site and set up the printer but I can't do this with Ubuntu. The only message I get is "job Paused" or "Printer not ready".

Thanks Sef,
I tried the link, but just can't find the answer. The frustrating this is I suspect the usual 2 minutes logged into cups would fix the problem and I have spent many hours on this now. I have installed every thing I can find that may be of use but everything appears unable to direct my printer to the cups drivers.
"xpp" shows my correct printer as associated with cups+gimp drivers but gimp will only give the postscript driver option. System/Admin/Printers shows my printer as ready but will not reset from pause.

Tried "sudo /etc/init.d/cupsys restart"

Edited "/etc/udev/rules.d/020permissions.rules" under usb heading changed "lp" to "0666" (to overcome possible bug that prevents access to printer)  
Installed "libppd0", "cupsys-pt", "python-foomatic", "printconf". (still no-go)
Installed "xpp" print setup program. (still no-go)

---

### Post by moontide on 2006-01-06
I seem to have fixed the problem of my printer not working although I don't understand why.  I am a member of the lp group, but "sudo chmod 666 /dev/usb/lp0" got the printer going both for gedit text files and gimp colour photos. Prior to chmod 666, "ls -l /dev/usb/lp0" showed no read & write for "others" (xrw-rw---). So it seems to only work with read and write privelages enabled for root, group and others. Hope this is of help to others. 

Oh! also I had to select the location of the PPD files for gimp and gpr. Never had to do that before.

(Another late night, but I should sleep well now)

---

### Post by moontide on 2006-02-12
I thought I had fixed my printer but it only worked the once, then went back to the printer paused situation I had before.

Since then I have set up my Breazy to allow me administration rights to the cups web site. Funny thing is, once again, my printer worked perfectly once (gimp printing a photo) and then failed to print anything from then on.

My printer is an Epson Stylus Photo 915 and I usually use the cups+gimp-print drivers. I tried installing the latest gutenprint-5.0.0-rc2 but that didn't fix the problem.

I am now at a complete loss of what to do next. If any one has a suggestion as to how I can track down whats happening I will be most greatfull.

Everything else in my ubuntu works great, seems crazy to have such an fantastic  desktop but not be able to do something as basic as print.

---

