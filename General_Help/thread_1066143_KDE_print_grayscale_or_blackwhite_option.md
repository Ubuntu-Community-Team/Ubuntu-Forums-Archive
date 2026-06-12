---
title: "KDE print grayscale or black/white option"
date: 2009-02-10
forum: General Help
---

### Post by wankel on 2009-02-10
I want to print a PDF in grayscales or in black and white. I have not been able to find a way to tell it to the KDE print dialog.

I have checked the dialog, the printer properties and the system options in the dialog, the printer settings in the CUPS and printer management window in KDE settings, but it does not show up.

Googling points to a request for a handier available button, instead of editing a not closer specified XML-sheet. 

On the forums I have not been able to find any pointer.

This all on KDE 3.5.10.

Any idea?

---

### Post by wankel on 2009-02-11
If anyone got the same problem, I found a workaround that worked for me:

- go to the web interface of CUPS ([http://localhost:631](http://localhost:631))
- go to printers
- go to "set printer options"
- with some luck there is a drop down box for colour/grayscale

If you have to give an account name and a password, use your username and the password you use to login to your computer. There have been some problems with that, but that was before 2006 or 2007, so that should not apply. 

By the way, the page that set the printer options for me was at:
[https://192.168.1.64:631/admin/?op=set-printer-options&printer_name=DCP330C](https://192.168.1.64:631/admin/?op=set-printer-options&printer_name=DCP330C)
- The IP is the CUPS server address.
- DCP330C is the name of the printer.

---

### Post by wankel on 2009-02-11
nevermind... The option is there, but it does not affect actual printing: it still turns out to print in colour.

So, if anyone has another guess, I'd be happy to try it out.

---

### Post by LowSky on 2009-02-11
Could you tell us the Printer brand and model, that would help so much, thanks! If it is an HP, then use the program called HPLIP, its in the Repos.

---

### Post by wankel on 2009-02-11
Thanks for your reply.

It is a Brother DCP-330c.

---

