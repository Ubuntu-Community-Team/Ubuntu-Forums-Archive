---
title: "Linksys Print Server"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Uta on 2006-06-11
My setup is a Epson Color Stylus 880(USB), trying to print to a Linksys WPS54G(print server). I'm running Dapper on a Dell laptop. I can print to the server with a Kubuntu (Dapper) install but not from an Ubuntu (Dapper) install. I have read many posts and the advice is to use a Unix (LPD) network setup, using for the Host the print server's IP (my PS IP is "192.168.0.100") and for Queue, use either L2 or IP_192.168.0.100
I have tried both configurations and I get the following error message:

"/usr/lib/cups/filter/pstoraster failed"
I am completely at a lost at this point. My print server and printer worked previous to Dapper. Where do I start troubleshooting this? Any help with problem solving this would be appreciated. Thanks!
Update:
I found another post that suggested I  should be using "L1" as the Queue so after doing that I get this error message: "Network host '192.168.0.1' is busy, down, or unreachable; will retry in 30 seconds..."
Well my printer server is not down, it's not busy but it certainly seems unreachable.
Could it be the new driver,(EPSON Stylus Color 880 - CUPS+Gutenprint v5.0.0-rc2) ?

---

### Post by Uta on 2006-06-12
How I solved my issue of printing to my Linksys Printer server was editng my "printers.conf" file.

# Printer configuration file for CUPS v1.2.0
# Written by cupsd on 2006-06-06 19:48
<Printer Epson880Basement>
Info Epson EPSON Stylus Color 880
Location Upstairs Office
DeviceURI socket://192.168.0.100:
State Idle
StateTime 1149641279
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
AllowUser your-username-goes-here
OpPolicy default
ErrorPolicy stop-printer
</Printer>


This "socket://192.168.0.100:" seems to be key. 
Looking in the System>Administration>Printing and checking the properties>Connection tab,
I see Host: 192.168.0.100 and Port: 9100
Printer Type is Network Printer  > HP JetDirect

I am using the "EPSON Stylus Color 880 - CUPS+Gutenprint v5.0.0-rc2"
Which I placed in my ppd directory since it wasn't installed for some reason? It was in Kubuntu but not in Ubuntu so I copied it and placed it in the correct folder. It's been a lot of work just to get a little inkjet printer working with Ubuntu.It works now and for that I am grateful!

---

