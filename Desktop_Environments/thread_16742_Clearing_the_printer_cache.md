---
title: "Clearing the printer cache?"
date: 2005-02-23
forum: Desktop Environments
---

### Post by geofff on 2005-02-23
Can someone tell me what's happening and how to cure it? If I try to print without a printer connected, when it gets connected it prints gobbledegook - continuously - page after page. I go to Computer>Printers>StylusColour600 (my printer)>Jobs and remove all outstanding jobs. The rubbish continues.

I can turn both computer and printer off and turn them back on again, clearing the job queue before the printers back on or after etc and still it carries on. It will continue overnight and for days at a time!  8-[ 

My previous system had the ability to flush the printer cache. I've not been able to find anything similar in Ubuntu. I know I'm missing something but what??

 TIA

---

### Post by Leif on 2005-02-24
have you tried using lpq and lprm ? type lpq -Pprintername to get some info, and then lprm -Pprintername, followed by the job id or your username to clear everything.

---

### Post by geofff on 2005-02-27
[QUOTE=Leif]have you tried using lpq and lprm ? type lpq -Pprintername to get some info, and then lprm -Pprintername, followed by the job id or your username to clear everything.[/QUOTE]
 No I hadn't tried these. They are new to me. It all is! However when I did they didn't get a result!

~ $ lpq -PStylus-Color-600
Stylus-Color-600 is ready
no entries
~ $ lprm -PStylus-Color-600 gfff
lprm: Job or printer not found!

and the printer carried on printing! On turning it off and connecting to a Riscos computer it prints normally. When I reattach it to the Linux box it carries on printing rubbish. Any other ideas very welcome!

TIA

---

### Post by Leif on 2005-02-28
Is Stylus-Color-600 the right driver for your printer ? Either way, you might want to try uninstalling the printer driver, and re-installing it. Maybe also try a different driver that is similar to your printer.

---

### Post by rosslaird on 2005-02-28
I have an Epson Stylus Photo 750 and have had similar problems.
Two things have sort of worked:

Experimenting with the gimp-print and other drivers selectable from the print setup dialog.

restarting cups (sudo /etc/init.d/cupsys restart).

But I have had to reboot my whole system, turn off the printer, let it sit, and so on. Sometimes it works, sometimes not. On the other hand, I haven't had problems since I setup the cups interface using the web access: [http://localhost:631/admin/](http://localhost:631/admin/)

So a grab bag of stuff, I guess. I wish I could remember what I did exactly to stop the endless gibberish printing...

---

### Post by kevinlyfellow on 2005-02-28
The easiest way I found was to use cancel -u <username> and restart the power to the printer.

This will clear the queue of all jobs with the specified user name

---

### Post by akaihola on 2005-12-17
Kevinlyfellow, *thank you* for that tip!

I've struggled with this stupid problem when using Linux and my HP LaserJet 5L and never found a simple solution no matter how much documentation I read or what keywords I googled.

This is definitely something that has to be always mentioned along with the lprm instructions.

---

