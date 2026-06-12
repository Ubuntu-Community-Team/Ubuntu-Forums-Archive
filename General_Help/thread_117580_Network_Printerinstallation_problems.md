---
title: "Network Printerinstallation problems"
date: 2006-01-15
forum: General Help
---

### Post by Snamremmit on 2006-01-15
I'm a new user of Ubuntu.
I've a Canon S630 printer
My OS is Ubuntu 5.1
The printer is connected by the printerport of my router a IP515H
with the IP adress 192.168.0.150
I've tried to install the printer bij the menu Administration/Printers and I've chosen
under the tab<Connection> for a networkprinter <Cups printer ipp>
I think my hostname is <http:127.0.0.1:631/printers/>
At URI I've tried many strings like this <ipp://127.0.0.1/etc/cups/ppd/S630>
In the map </etc/cups/ppd/S630> is the file <S630.ppd>
Who can give me advice.

---

### Post by MJSOnline on 2006-01-15
Ok. Easy one.

In the Admin > Printing>  Add printer > Network Printer > CUPS >

in the URL box type your ip address of the printer e.g. 192.168.1.50

Click Forward > Select Manufacturer > Model > Apply. 

Print a test page.

Hope this helps.

Matthew

---

### Post by Snamremmit on 2006-01-15
Mathew

I've type in the Ip adress of the printer <192.168.0.150>
After I print a Test page.

The system comes with the message <destination printer doesnot exist>.

---

