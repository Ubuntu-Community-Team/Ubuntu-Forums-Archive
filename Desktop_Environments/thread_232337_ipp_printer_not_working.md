---
title: "ipp printer not working"
date: 2006-08-08
forum: Desktop Environments
---

### Post by yoyoned on 2006-08-08
I have a small home network of Ubuntu (6.04) and windows desktops and a Centos server.  The server shares a printer via ipp and SMB.  I am able to print from the windows boxes using ipp and SMB.  SMB also works from the Ubuntu box. IPP worked until a few days ago.  I belive it stopped working after a cups upgrade.  When I send a jop to the printer via ipp the following prints:```

-12345X@PJL
@PJL JOB NAME="Ghost"
@PJL SET ECONOMODE=OFF
@PJL SET MEDIATYPE=REGULAR
@PJL SET SOURCETRAY=AUT0
@PJL SET RESOLUTION=300
@PJL SET RAS1200MEDE=OFF
@PJL ENTER LANGUAGE=PCL

```Then a line ao what apears to be random numbers and lettes.

Anyone have any ideas?

---

### Post by mssever on 2006-08-08
I have the same problem. I've tried re-intalling the printer on the machine that prints via IPP (my laptop), but it didn't make any difference. I can print fine from my dasktop, where the printer is connected. My printer is an HP Deskjet 5150. Here's the result of my prinouts:
```
-12345X@PJL ENTER LANGUAGE=PCL3GUI
17H10M12Ao-2M1-2Hg20W,, ,,
u300Dr2475Sr1Ap225Yb0Vb0Wb0Yp239Yb9V a
```(the final /a/ should be in superscript)

My workaround is this: Save whatever I want to print from my laptop as a PDF, copy it to my desktop, login to my desktop via XDMCP, and print the PDF. It works, but I'd rather print directly from my laptop.

---

### Post by mssever on 2006-08-10
*bump*

Does anyone have a solution?

---

### Post by thomasloo on 2006-08-14
I have the same problem :-(

---

### Post by mssever on 2006-09-05
Another bump an case anyone has any ideas now. It just doesn't seem right to print from one Linux computer to a printer on another using Samba, which is what I'm doing now!

---

### Post by mailcameel on 2006-09-05
I have the same problem, connecting to a HP 4050 TN

---

### Post by funkydan2 on 2006-09-05
This problem seems to be linked to HP printers only.  I have two printers shared via Samba and I can print to my Canon easily, but no luck with my HP LaserJet 5L.  The problem is something that is recent in Dapper (i.e. I didn't have the problem with I first dist-upgraded.)

---

### Post by mailcameel on 2006-09-05
> **mailcameel said:**
> I have the same problem, connecting to a HP 4050 TN

Found solution!

cd /usr/lib/cups/backend-available
sudo ln -s  ../backend-available/snmp /usr/lib/cups/backend/snmp
/etc/init.d/cupsys restart (just in case !)

See [http://www.kdedevelopers.org/node/2138](http://www.kdedevelopers.org/node/2138)

[http://localhost:631/](http://localhost:631/)
goto administration and 'Add This Printer' just by 2 cliks !

---

### Post by mssever on 2006-09-05
> **mailcameel said:**
> Found solution!

cd /usr/lib/cups/backend-available
sudo ln -s  ../backend-available/snmp /usr/lib/cups/backend/snmp
/etc/init.d/cupsys restart (just in case !)

See [http://www.kdedevelopers.org/node/2138](http://www.kdedevelopers.org/node/2138)

[http://localhost:631/](http://localhost:631/)
goto administration and 'Add This Printer' just by 2 cliks !
This is an entirely different issue, dealing with finding connected printers. My issue is getting garbage when I print to an already-installed IPP printer.

BTW, the commands given are confusing. This is a much better way: 
```
cd /usr/lib/cups/backend
sudo ln -s ../backend-available/snmp .
sudo /etc/init.d/cupsys restart
```

---

