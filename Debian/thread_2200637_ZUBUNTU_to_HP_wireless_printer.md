---
title: "ZUBUNTU to HP wireless printer"
date: 2014-01-20
forum: Debian
---

### Post by barry-thornton on 2014-01-20
Hello out there!
I just started using ZUBUNTU yesterday.  All is going well with the exception of getting my wireless HP 3512 all-in-one printer going. I've downloaded the driver from HP along with the certificate.  It shows the driver as being installed and connected to the host router however, it will not print.  I have my wife's latop dialled into this router/printer and the printer is working.
Thanks in advance
Barry

---

### Post by ajgreeny on 2014-01-20
What exactly did you do to download and install the driver?

Normally you only need to install the hplip package, along with hplip-gui for a configuration application that sits in the panel, and if you then go to System ->Printing you can add the machine from there.

---

### Post by rioguia2 on 2014-03-03
I've just struggled with setting up an Officejet_4500_G510n-z_2.

I used the instructions from [HPLIP]("http://hplipopensource.com/hplip-web/install_wizard/index.html") and tried the auto install.  

Regardless, the install wizard claimed that the printer did not have a good network connection.  Specifically, it indicated that the wizard couldn't find the IP address of the printer (even though the wizard detected it and displayed it.

What did work for me was configuring the wireless connection with a fixed IP address on the tool built into the HP printer and then simply s[upply the same IP when invoking the HP setup wizard]("http://hplipopensource.com/node/365").

```
/usr/bin/hp-setup <ip.address.assigned.printer>
```.  This resulted in a second set of printer drivers being loaded.  The first set is for USB printing and scanning and the second is for Wireless printing and scanning (see attached png). Both seem to work fine.

I hope this suggestion helps you.

---

### Post by Bucky Ball on 2014-03-03
*Thread moved to **Other OS/Distro Support**.*

Welcome. Why exactly are you using Zubuntu? It is a rather obscure Ubuntu spin for IBM zSeries mainframes. Is that what you're using? If not, install something we know about as Zubuntu is not officially supported in these forums. Thanks. :-k

Please give the exact details of your machine. Also provide a link to where you downloaded Zubutu, please.

---

### Post by buzzingrobot on 2014-03-04
> **rioguia2 said:**
> 
What did work for me was configuring the wireless connection with a fixed IP address on the tool built into the HP printer and then simply s[upply the same IP when invoking the HP setup wizard]("http://hplipopensource.com/node/365").



This is how my HP wireless printer has been set up for a long time. Getting it working on a new install requires the right proprietary driver from HP.  That can be manually grabbedfrom the HP site, but I find it's easier to run hplip-gui, point it at the printer's IP, and let it download and install the driver.

Quirks:  The "Print test page" function in hplip-gui often fails; the same function in system settings always works subsequently. If my printer has suspended itself, i.e., is asleep, the hplip-gui will not wake it up but will simply report it can't find a printer. 

(If the printer is close enough to use a USB cable connection, life is often likely to be simpler.)

---

