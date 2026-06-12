---
title: "Problem: HP Printer is not working correctly"
date: 2006-06-03
forum: Desktop Environments
---

### Post by zpro on 2006-06-03
Problem:
In breezy my HP 5simx printer was working just find on the the LAN network,
however, after doing a Full install of Dapper, I went to configure the HP,
select the driver, and print test page, as I have done before....AND

Printer error: the HP Printer tell me to install pre-punched paper in
tray 1 (manual feed) to print this test page out.. Huh?

Go back to setting(pref) and selected, tray 4 (2000 sheet feeder)
and yes all option a selected in the driver pane: and  select plain paper.

print test page... NOPE, it wants pre-punched paper in tray 1
after 30 mins of trying all setting, there no way around this error
that I keep getting with this printer driver.

So, is it a driver problem or a CUPS problem. ](*,) 

Thanks -

---

### Post by rmac on 2006-06-07
I am having a similiar issue. I install a HP laserjet 5100 (postscript drivers), and it will not print to anything other than the manual feed tray one. Configuration does have the ability to select which tray, but changing this has no effect. I am not sure what has been changed between dapper|breezy, but this configuration worked perfectly in the latter.

As an aside, I would recommend printing in Unix Printer (LPD) under connection for the 5100 as the margins seem to be the best fit. 

Any help on this would be greatly appreciated. ](*,)

---

### Post by PcPixel on 2006-08-07
I'm having the same problem. I have an HP 5100tn printer, with Ubuntu 6.06 LTS. I am using the CUPS-LPD daemon to print from Windows & Unix. Windows prints come out fine (as the system thinks the Windows printer is Raw). However when users print from Unix, the printer demands that A4 be loaded despite the configuration of the printer.

I'd rather not downgrade to 5.10. Does anyone know what the problem is, or if there is a work-around available?

---

### Post by dugh on 2007-08-08
I am seeing this problem too even in Ubuntu Feisty.

Apparently the hp drivers are way out of date in the Ubuntu repositories.

You have to manually compile the latest, even then I don't know if that will fix the problem, and of course next time you update Ubuntu it may all break again.

---

### Post by aravinda_sh on 2008-07-18
Hi All,
I installed latest Ubuntu 8.04.1. Where can I find printer driver for HP LAserJet 5100 PCL 6.

Thanks,
Aravinda

---

