---
title: "Print driver uses incorrect margin"
date: 2006-07-23
forum: Desktop Environments
---

### Post by mssever on 2006-07-23
I have an HP DeskJet 5150 printer, connected to my desktop. I usually print from my laptop over the network. Both machines are running Dapper. I'm using the hpijs driver (HPLIP 0.9.7).

Here's my problem: I regularly print documents in landscape orientation with 0.25in margins all around. This works perfectly in Windows. But in Linux, the left margin (corresponding to the bottom margin in portrait orientation) is wider--probably about 0.5in. Any text that is up against the margin gets cut off.

What can I do to fix this?

---

### Post by mssever on 2006-07-24
bump

---

### Post by mssever on 2006-07-25
another bump...

Is this problem unique to me?

---

### Post by easy_target on 2006-07-27
No it's not. I have a HP Laserjet 4P and I have exactly the same problem. If you (or maybe someone else in the forum) has an answer, please be kind enough to post it. 

:p

---

### Post by Lord Illidan on 2006-07-27
Me too..

I kinda remember I had temporarily solved it somehow, but I cannot remember how. It was worse in firefox, the url and page number and time which appear on the top and bottom of the page were all cut off!

---

### Post by CronoDekar on 2006-07-27
Climbing aboard the bandwagon, I have margin problems with my Deskjet 940c.  Namely, the very bottom cuts off.  It's a little annoying printing out puzzles in gnome-sudoku only to have the last row cut off.  Anybody have any ideas?

---

### Post by CronoDekar on 2006-07-27
Aaand just think I found the answer, at least to my problem.  The default letter size seems to be set to A4, when it should be set to Letter.  So in the Advanced printer properties, set that to Letter, and when printing something out, switch to the Paper tab and make sure the size is Paper instead of A4.  Supposing you're printing to a typical 8.5x11", anyway.

EDIT: I found that to get Letter as the default, I had to go through the web administration of CUPS -- the GNOME printer manager didn't seem to change anything.  There instructions on how to get into it here: [https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html](https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html)

---

### Post by mssever on 2006-07-28
> **CronoDekar said:**
> Aaand just think I found the answer, at least to my problem.  The default letter size seems to be set to A4, when it should be set to Letter.  So in the Advanced printer properties, set that to Letter, and when printing something out, switch to the Paper tab and make sure the size is Paper instead of A4.  Supposing you're printing to a typical 8.5x11", anyway.

EDIT: I found that to get Letter as the default, I had to go through the web administration of CUPS -- the GNOME printer manager didn't seem to change anything.  There instructions on how to get into it here: [https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html](https://help.ubuntu.com/xubuntu/desktopguide/C/printer-configuration.html)

Thanks for the tip. My default was also set to A4. Unfortunately, I can't seem to change it. I set the page size properly in the Gnome printer tool, but when I looked in CUPS as the link above directed, I found that the page size was still set to A4. When I tried to change it, CUPS flatly refused. It popped up a password dialog, and upon entering my password, it did nothing. However, here's a snippet from the error log:
```
E [28/Jul/2006:14:10:46 -0500] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [28/Jul/2006:14:10:49 -0500] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [28/Jul/2006:14:10:51 -0500] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [28/Jul/2006:14:11:04 -0500] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [28/Jul/2006:14:11:04 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [28/Jul/2006:14:11:15 -0500] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [28/Jul/2006:14:12:31 -0500] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [28/Jul/2006:14:12:34 -0500] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
E [28/Jul/2006:14:12:36 -0500] cupsdAuthorize: pam_authenticate() returned 7 (Authentication failure)!
```
Grrr..... Why not set the default page size from the locale? Other programs realize that I'm in the USA, and as far as I know, you can't buy A4 paper here even if you want it. So the default paper size for the US should be US Letter.

All that aside, I changed the page size in OpenOffice's printer settings, and it didn't make any difference.

---

### Post by easy_target on 2006-08-09
I found something that can probably work for you - well, it worked for me.

Edit the file /etc/papersize to your specifications. Mine is "letter". 

Now I wonder... if the solution is that easy, why isn't it implemented in the graphical tool?


Hope this helps.

---

### Post by mssever on 2006-08-10
Thanks. I made the change you suggested. I don't know yet if it will solve my problem, as currently I can't print at all (see [this thread]("http://www.ubuntuforums.org/showthread.php?t=232337")).

---

### Post by Charles Hand on 2006-09-05
I struggled with that margin problem for weeks until I realized that printers are installed with default paper size of A4. Hopefully this thread will turn up in searches for printer margin problems.

Shifted print? Maybe you want letter size instead of A4.

Regarding the cups authentication thing, I couldn't get cups to authenticate me, either, neither as myself nor as root. I'm in group lpadmin.

So I changed all AuthType Basic to AuthType Digest in /etc/cups/cupsd.conf and then did
```
sudo lppasswd -a <my user name>
```
and of course
```
sudo /etc/init.d/cupsys restart
```

After that, cups authentication works.

---

### Post by mssever on 2006-09-05
Unfortunately, that still doesn't work for me. I've set the default paper to letter in three different places (none of which seem to affect the other, BTW): the Gnome printer properties, /etc/papersize, and through the CUPS web interface, thanks to Charles Hand. Yet the bottom margin is *still*
clipped when I set it to 0.25in. What gives?

Also, I don't know why basic authentication doesn't work. It's crazy to have a CUPS password that isn't tied to the login password--especially when lppasswd refused to accept the password I use for login because it doesn't have a number in it, despite the fact that I was running it as root (which should allow me to do anything a la passwd) and the fact that my password is plenty secure (a pseudo-random string).

---

### Post by JetSirus on 2007-05-20
I am jumping on this bandwagon as well.  I have an hp LaserJet 2200d and the top, right and bottom sides get cut off by varying degrees.  I am using the postscript driver.  None of the fixes listed have helped.

---

### Post by TheSimkin on 2008-06-04
> **JetSirus said:**
> I am jumping on this bandwagon as well.  I have an hp LaserJet 2200d and the top, right and bottom sides get cut off by varying degrees.  I am using the postscript driver.  None of the fixes listed have helped.

I found the easy fix was to change the printer driver to a postscript one.  (In my case HP Laserjet 8150 Postscript).

I found my printer here: [http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_8150dn](http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_8150dn) and it recommended this driver.  I tried it.  It worked!

---

