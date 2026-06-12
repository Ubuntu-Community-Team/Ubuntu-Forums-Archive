---
title: "SMB printer"
date: 2005-08-19
forum: Desktop Environments
---

### Post by desertViking on 2005-08-19
Hi,

I have a quick question that's probably an easy one to solve.

Using 5.04, I can browse to my XP system and it will show all of my shared drives, but not my shared printer.  I am confident that the printer is shared correctly on the XP side, having recently migrated towards ubuntu. 

Using the "add printer" wizard, it will allow me to add an SMB printer, but I am not certain of the right format of the host name, and there's no browse resource to give me a clue.  So far my guess haven't proved correct as I am unable to successfully print anything.

Does anyone know the right format for the host or printer name to include?

Regards,

desertViking

---

### Post by chrisod on 2005-08-19
I think you need to install a print driver for the printer on the linux side. If one isn't available, you might try enabling Unix printing in Windows. Hopefully somebdy can offer details - I wouldn't trust them coming from me. I took the easy way out, I traded printers with my wife. She got the new one with no linux drivers available, I took her older one with a linux driver available.

---

### Post by Dogmeat on 2005-08-19
Hello, maybe [this thread](http://www.ubuntuforums.org/showthread.php?t=26166) will be helpful!

---

### Post by desertViking on 2005-08-19
Thx, I'll try that when I get home.

BTW, I'm curious about adding the XP's IP address instead of the workstation name.  That really works?  Never would have thought of that.

Thx again!

---

### Post by stevea1210 on 2005-08-19
I had issues with a smb shared printer on an XP box.  I could get print jobs to the queue, but nothing would ever come out of the printer.  The jb also would never leave the queue.   I disabled biderectional support on the queue in XP (printer properties, ports, uncheck enable bi-directional support), and I have been happily printing ever since.  This was for a HP PSC 1210.  

To be clear, this is a change on the XP machines print queue.

As far as using the IP instead of the unc name.  It will work.  The  only catch is if you use dhcp, and that machines IP changes.  Printing won't work then.  I would try it as another test.  If it works with the IP, but not the name, you have some internal DNS issues. But that's another thread altogether :)

---

### Post by desertViking on 2005-09-19
Hi All,

I fixed this awhile ago, but forgot to post a solution here.  I've been using the 5.10 pre-release.

1) Administration->Printing->New Printer icon
2) Select Network Printer->of sort Windows SMB
3) for Host, enter WORKGROUP name (substitute your name for WORKGROUP)
4) for Printer, enter WORSTATION/PRINTER name (substitute exactly as they appear)

From there, selecting the printer type and driver should be pretty obvious.

I never did get the SMB network to scan and identify the printer for me.

Hope this helps someone.

Regards.

---

