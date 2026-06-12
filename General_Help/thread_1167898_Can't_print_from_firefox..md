---
title: "Can't print from firefox."
date: 2009-05-23
forum: General Help
---

### Post by vaul on 2009-05-23
I am running Jaunty and experiencing following issue: when I am trying to print anything from firefox, first page is printed properly, then it stops with "wrong paper size: letter" error. Paper placed in the tray and surely  is A4.
Printing out of any other application is OK. I am using multifunctional Canon MF 4018, proprietary driver installed properly, page size is set to the A4 in the options of multifunctional, driver and firefox printing dialog.
What could be the problem, people?

---

### Post by vaul on 2009-06-02
Is there anyone here?

---

### Post by Magpie. on 2009-09-08
> **vaul said:**
> Is there anyone here?
I'm here, but I haven't even got as far as you've got.

I connected a Samsung 1610 printer and Ubuntu 9.04 recognised it. I can print from, say, the text editor, but there's no sign of a printer in the Firefox print-preview dialogue, so there's no way I know of to print the preview. 

Anyone know how to fix this?

---

### Post by Magpie. on 2009-09-09
Bump.

---

### Post by vaul on 2009-09-09
I solved this issue myself. It was problem related to some idiot in the Canon™.
When installed, proprietary driver makes values related to the printing in the Firefox'es about:config equal «LTR», which results in my MFD thinking it's letter size paper stacked in the tray.

Everything is right after I edited necessary values manually and set them to «A4».
I found them searching for «print.tmp», «print.printer» and «print.postscript» in the about:config.

Maybe it's worth looking into the «lets say text editor's» configuration file for some equivalent of idiotism described above?

---

### Post by vaul on 2009-09-09
Sorry, didn't read you post properly. Are proprietary drivers installed?

Your printer should work just fine, if believe [report]("http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-1610") at the OpenPrinting database.
There's also a link to driver that reported to be working there, check it.

---

### Post by Magpie. on 2009-09-09
> **vaul said:**
> Sorry, didn't read you post properly. Are proprietary drivers installed?

Your printer should work just fine, if believe [report]("http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-ML-1610") at the OpenPrinting database.
There's also a link to driver that reported to be working there, check it.
Thanks for your interest in my problem.

I haven't knowingly installed any drivers for the printer on Ubuntu. All I know is that Ubuntu sees it by the correct name, that it works fine from the text editor delivered with Ubuntu, and that it doesn't show up in the Firefox/ File/ Print Preview dialogue. 

In other words,  I can't use it in Firefox but it works fine elsewhere.

---

### Post by vaul on 2009-09-09
If you didn't, that probably means, some kind of free generic driver is used. Try that from the link above.

A am not very concerned about your problem, I just googled for a while. I did remember that it's quite unpleasant to be left alone with your problems.

And one more, did you set it as your default printer from the «system» menu? Try, if you didn't yet.

---

### Post by Magpie. on 2009-09-10
> **vaul said:**
> If you didn't, that probably means, some kind of free generic driver is used. Try that from the link above.

A am not very concerned about your problem, I just googled for a while. I did remember that it's quite unpleasant to be left alone with your problems.

And one more, did you set it as your default printer from the «system» menu? Try, if you didn't yet.
I must be missing something here -- I wouldn't know what to do with the driver link. It's working already. But I'll have a look. 

Yes, it's set to Default. I think I'll take this to the Firefox forums. Maybe there's a way to add a printer manually, though I can't see it. I'll report back with anything that seems useful.

---

