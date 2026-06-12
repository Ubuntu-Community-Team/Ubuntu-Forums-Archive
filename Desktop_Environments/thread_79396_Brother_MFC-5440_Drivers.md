---
title: "Brother MFC-5440 Drivers"
date: 2005-10-20
forum: Desktop Environments
---

### Post by Brian Clark on 2005-10-20
I've found the LPR drivers at the Brother site but Ubuntu doesn't use LPR? Does this mean that they are not useable or do I have to do something clever to make them work.

Drivers are at [http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html) if its any use to other users...

Any ideas would be great!

---

### Post by Trajan on 2005-10-20
I have the same model, but haven't been able to configure the printer correctly in ubuntu. Anyone that has dealt with this problem and found the solution, please share it with us.

---

### Post by paulegal on 2006-07-24
Well, I am a beginner you would not believe and I am not sure how much I can contribute, however, this is the questions that I send to Brother support group:

Network Printer at 192.168.XXX.9:
The installation under Administrative permissions went well. I changed the

file "/etc/printcap" and tried to restart " /etc/init.d/lpd restart". This command failed. I condulted your FAQ and executed the following commands:
"ln -s /etc/init.d/cupsys /etc/init.d/lpd"
"ln -s /etc/init.d/cupsys /etc/init.d/lprng"
and executed " /etc/init.d/lpd restart" again, this time with success. All looks good, but I can not see any printer? What went wrong? What can I do else.
Thanks for your help.


the support replied very friendly:


Dear Sir/Madam,

This is the Japanese Solutions Center.
Thank you for your inquiry.

The printing system you are using seems to be CUPS,
not LPR.
Please change the system to LPR or keep the current CUPS setting
and install the CUPS Wrapper driver additionally.
<CUPS Wrapper driver>
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)


We recommend you keep the current CUPS system
and install the CUPS Wrapper driver additionally.
(please do not uninstall the current installed LPD/LPRng printer driver)

After the installation, the default port setting is USB.
Please access to the CUPS web interface "http://localhost:631/printers"
and click on "Modify Printer".
You can change the port there from USB to Network.
For Device, select "LPD/LPR$B!!(BHost or Printer" and
for Device URL, please set "lpd://192.168.XXX.9/binary_p1".

With regard to the print settings, click on "Configure Printer"
at the page "http://localhost:631/printers".


Thank you for your try.

Best regards,
Brother Solutions Center
 
 
But I still can't get it to work. Maybe someone does and can me tell how.

Good luck!

---

### Post by CadetD on 2006-09-29
Has anyone had any luck getting the MFC-5440 working with a 64bit version (AMD64)?

---

### Post by StarLog on 2006-12-04
This information from paulegal, works, as I have my MFC-5440cn running on 6.10 using USB and CUPS.

The goal however is to use the network interface, and that is where I am stuck. The only USB system working is the wifes Sony with 6.10 Ubuntu. I want to access the same printer via the network, on my desktop now. 

Any help would be great, I have searched all over Brothers site, and that as not given much about the network version.

The current CUPS Version 1.2.4 does not show any examples of using Brother in the "Network printer" section. A lot of others are in there, so maybe I need to just keep trying all the combinations until one works.

On another note, I really do not need ALL the functionality of the MFC-5440cn, just the printer part, anyone know what provided CUPS Brother printers are similiar on the printer side to the MFC-5440cn.?

Thanks

---

### Post by StarLog on 2007-04-28
So now I am on 7.04 Feisty, and still this is not working over the network.
Are there no users trying to network their MFC-5440.?

Brother is not much help on this one either.

---

### Post by bingen on 2007-04-30
Hi,

I've installed MFC-5440CN over the network on two computers: a laptop with feisty anb a desktop 64-bit with edgy.
For the printer, I've installed the .deb packeges and followed the instructions from here:
[http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)
For the 64 bit machine you have to do a dpkg -i --force-all *.deb because it complains about the platform.

For the scanner more or less the same, but with the 64 bit machine I've installed the 64-bit rpm packeges with kpackage, without checking dependecies of course. You have to install rpm packege before with apt-get, adept or synaptic.

If you need more details please ask me.

   ßingen.

---

### Post by jimbean on 2007-04-30
looked for this guy that had a fix it guide on unbutu site use search function and look for bobsongs postings

he helped me figure out how to add cup`s and lpr driver from brother printer site
then i went into usr/share/cups/model directory
and added the driver at the new printer setup

---

