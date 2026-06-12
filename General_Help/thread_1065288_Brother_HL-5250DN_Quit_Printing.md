---
title: "Brother HL-5250DN Quit Printing"
date: 2009-02-09
forum: General Help
---

### Post by kslinux on 2009-02-09
I am using kubuntu 8.10 on a Dell Dimension 4500 desktop computer.  I have been printing to a Brother HL-5250DN.  I print wirelessly --- the printer is connected to my wireless router.

I was able to print on it yesterday.  I have been trying to get a second wireless printer on the network.  I also have a Brother MFC-490CW.  Both of these printers work on computers running a Windows XP OS.  However, neither of them are working with the kubuntu 8.10.  At least the HL-5250DN has a linux print driver.  I've reinstalled linux HL-5250DN print driver and the printer is still not working.

When I send a job to be printed, I get the printer icon on the bottom.  When I open that window, the print job is status'd as either "progressing" or "pending".  It seems to just sit there.  I have cycled both the wireless router and the HL-5250DN.  That doesn't help either.

I am still on a very steep learning curve with Linux.  Assume I know nothing and treat me as a newbie.

Thanks!

---

### Post by HermanAB on 2009-02-09
Try to open a browser and type: [http://localhost:631](http://localhost:631)

Then restart the printer and kill all pending jobs.

When all else fails, restart the cups service.

Cheers,

Herman

---

### Post by kslinux on 2009-02-09
Thanks.

I deleted all jobs.  I then used CUPS to reload the HL-5250DN print driver.  It's now working!

This does answer my question.


I also tried finding a print driver for my new printer - Brother MFC-490 CW.  CUPS did not have one.  Is there any print driver that can make this wireless printer work?  Note, the MFC-490 also has a scanner, copier and FAX.  All I wish is to make the printer function work.

Thanks to everyone for your help!

---

### Post by compman25 on 2009-02-09
> **kslinux said:**
> Thanks.

I deleted all jobs.  I then used CUPS to reload the HL-5250DN print driver.  It's now working!

This does answer my question.


I also tried finding a print driver for my new printer - Brother MFC-490 CW.  CUPS did not have one.  Is there any print driver that can make this wireless printer work?  Note, the MFC-490 also has a scanner, copier and FAX.  All I wish is to make the printer function work.

Thanks to everyone for your help!

[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW]("http://solutions.brother.com/linux/en_us/download_prn.html#MFC-490CW")

---

