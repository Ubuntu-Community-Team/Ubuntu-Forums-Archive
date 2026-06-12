---
title: "Problem installing Samsung ML-1610 printer"
date: 2006-03-08
forum: Desktop Environments
---

### Post by Pangui on 2006-03-08
I'm trying to install a Samsung ML-1610 (USB printer), my dist. is Kubuntu 5.10.
The printer isn't listed into default printer list... i download the driver from samsung.com but the installation crashes with this message:
```

root@kubuntu:/home/pangui/image# ./setup.sh
./setup.sh: line 143: 11120 Violación de segmento  "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

Please contact your Customer Support

```
i've updated all mentioned libraries (libgtk) without success :-k 
any idea?:confused:

---

### Post by avantgardaclue on 2006-03-08
I was looking at buying one of these printers too, and am now not sure i should,.

An answer to this query would be most welcome

---

### Post by Pangui on 2006-03-08
i've found the solution:

run as root the final installation script, not the 'automatic' way...

```

/image/setup.data/bin/Linux/x86/glibc-2.1/setup.gtk

```

nevertheless, a new problem was the user/password required by /usr/local/linuxprinter/bin/linux-config

other 'solution' was copy the *.ppd files included in installation sub folders, to  /usr/share/cups/model, and install the printer using the automatic method provided by kde. Doing this, i can see my printer icon in System settings->printers, but i can't print the test page (a red symbol [x] appears in my printer icon when i try to print)

is this a typical problem of [Cups|Samsung|Kde|newbie:) ]??
where can i found information about cups configuration??

thx,thx,thx!

---

### Post by spandon on 2006-03-09
Hi,
I have a Samsung ML1610 Printer which works perfectly.
The solution is:
connect the printer to Computer, and switch the printer on.
restart ubuntu.
System>Admin>Print Manager>add printer
you should now see that ubuntu recognises your printer, choose the Samsung ML1510 driver, you will now find the printer works perfectly as mine does.
Cheers
Don

---

### Post by Legend_of_Excalibur on 2008-02-04
> **spandon said:**
> Hi,
I have a Samsung ML1610 Printer which works perfectly.
The solution is:
connect the printer to Computer, and switch the printer on.
restart ubuntu.
System>Admin>Print Manager>add printer
you should now see that ubuntu recognises your printer, choose the Samsung ML1510 driver, you will now find the printer works perfectly as mine does.
Cheers
Don

Use the 1510 driver? My 1610 installs but doesn't print well , unless it's the test page or preview page print. I will try the 1510 driver if I can find it, since I already downloaded and installed the new printer from samsung.

---

