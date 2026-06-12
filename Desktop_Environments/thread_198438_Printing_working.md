---
title: "Printing working"
date: 2006-06-17
forum: Desktop Environments
---

### Post by frogotronic on 2006-06-17
Hello,

  After installing (clean) DD, I had numerous printing problems.  Here's how I solved them:

1) I installed the latest update to [HPLIP]("http://hplip.sourceforge.net/").  There are some pretty clear instructions on the web, specifically for Ubuntu 6.06.  I also downloaded and applied the associated patch from the SourceForge.

2) I have set-up and used a network configured (not attached to another machine) HP LaserJet 4000 printers using the vanilla DD 'PRINTERS' utlity and choosing HP JETDIRECT.  

  *Tip:  Make sure you select "plain paper" - the default is "none" and your printer won't print anything!!  Also, make sure you choose "letter size" paper otherwise, the HP LJ4000 will always want you to load A4 paper via the manual Tray 1.*

3) When printing to SAMBA  (i.e. to a printer connected to a WindowsXP computer); many of the drivers that worked under BB **DO NOT** work under Dapper Drake.  The print function is working, but the print driver is causing problems.

   *For example:  I have a Canon i550 printer connected to my WindowsXP desktop and Ubuntu is on my laptop.  With Breezy Badger everything worked as per these [instructions]("http://www.willmer.com/kb/2005/05/printing-to-windows-xp-printer-from-ubuntu/") .  However in Dapper Drake this was a no go.  **HOWEVER**, choosing different Canon BJ drivers did "work" to varying degress, giving poor quality prints, likely because they were incorrect drivers.  This would indicate that the problem is probably with the [Canon PixusVer2.2 drivers]("ftp://download.canon.jp/pub/driver/bj/linux/") for the Canon i550 :( .  I think several people have posted similar problems.*

**_SOLUTION:_**
  I have cheated on this one.   My solution (as I need a functional laptop for work) is to download and install [TURBOPRINT]("http://www.turboprint.de/english.html").  Yes, it costs money (about $35.00 USD), but it was seemless install and works perfectly, with all the configuration of the Canon i550 windows driver.  Allows you to install network printers, windows/Samba printers, etc.

----------------------------------------

Overall:

Print setup was clunky in DD and the lack of Canon drivers for Linux is really dissappointing.  Not Ubuntu's fault, but rather Canon's.  I have always been a big fan of Canon and this was a letdown for me in the switch to Ubuntu/Linux.

Anyway, hope this helps.  Feel free to post if you have questions and I'll try to help out.

-CH

---

### Post by frogotronic on 2006-06-21
> **cement_head]Hello,

  After installing (clean) DD, I had numerous printing problems.  Here's how I solved them:

1) I installed the latest update to [HPLIP]("http://hplip.sourceforge.net/").  There are some pretty clear instructions on the web, specifically for Ubuntu 6.06.  I also downloaded and applied the associated patch from the SourceForge.

2) I have set-up and used a network configured (not attached to another machine) HP LaserJet 4000 printers using the vanilla DD 'PRINTERS' utlity and choosing HP JETDIRECT.  

  *Tip:  Make sure you select "plain paper" - the default is "none" and your printer won't print anything!!  Also, make sure you choose "letter size" paper otherwise, the HP LJ4000 will always want you to load A4 paper via the manual Tray 1.*

3) When printing to SAMBA  (i.e. to a printer connected to a WindowsXP computer) said:**
> instructions[/URL] .  However in Dapper Drake this was a no go.  **HOWEVER**, choosing different Canon BJ drivers did "work" to varying degress, giving poor quality prints, likely because they were incorrect drivers.  This would indicate that the problem is probably with the [Canon PixusVer2.2 drivers]("ftp://download.canon.jp/pub/driver/bj/linux/") for the Canon i550 :( .  I think several people have posted similar problems.*

**_SOLUTION:_**
  I have cheated on this one.   My solution (as I need a functional laptop for work) is to download and install [TURBOPRINT]("http://www.turboprint.de/english.html").  Yes, it costs money (about $35.00 USD), but it was seemless install and works perfectly, with all the configuration of the Canon i550 windows driver.  Allows you to install network printers, windows/Samba printers, etc.

----------------------------------------

Overall:

Print setup was clunky in DD and the lack of Canon drivers for Linux is really dissappointing.  Not Ubuntu's fault, but rather Canon's.  I have always been a big fan of Canon and this was a letdown for me in the switch to Ubuntu/Linux.

Anyway, hope this helps.  Feel free to post if you have questions and I'll try to help out.

-CH



DD update:

DON'T add "guest@"  for the hostname/printername in DD!.  Just insert <hostname>/<printername>

L8R

---

