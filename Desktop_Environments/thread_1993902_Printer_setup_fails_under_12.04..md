---
title: "Printer setup fails under 12.04."
date: 2012-06-02
forum: Desktop Environments
---

### Post by Randy Schilling on 2012-06-02
I have a Dell 1320c printer.
To begin the setup process, 
I select Unity Launcher > System Tools > Printing > Add Printer,
which finds this printer connected to my usb port. I select it and click forward.
Attached is a .png with the configration that results from my attempt to setup this printer.
This printer is not supported by any of the Dell drivers listed under "Select printer from database."
Therefore, in attempting to set up my printer, I  select "Provide PPD file,"
and I navigate to the file "FX_DocuPrint_C525_A_AP.ppd" located in my
"/usr/share/cups/model/FujiXerox/en" directory, click forward, select 
"Use the new PPD as is," then apply.  When I try to print a test page (or anything)
I get lights flashing and whirling sound but no printout.

The PPD file and the process described herein worked previously under 8.04 and 10.04.
The PPD file came to my attention long ago through this forum.
It is the result of a download from a FujiXerox website, 
followed by an RPG to DEB conversion using a program called "alien", 
followed by a "dpkg -i" command applied to the DEB file.

The setup process I've described here is identical to what worked previously  (I think).
But something is not working.  Any suggestion would be appreciated.
Regard - Randy

---

