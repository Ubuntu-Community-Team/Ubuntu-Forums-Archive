---
title: "Help with CUPS and D-Link DPR-1260 Print Server"
date: 2006-07-01
forum: Desktop Environments
---

### Post by pbmax on 2006-07-01
I just got a DPR-1260 print server for my printers. The XP setup was no problem, but I can't figure out CUPS with the server.

The device is a wireless print server that connects up to 4 printers. I can communicate through it's web interface wirelessly, so I know its working. When I plug my HP3200 into a USB port on my PC, CUPS id's it and it works fine. I just can't get the two to work at the same time.

When I'm settin up the printer, what kinds of settings should I use: ipp ://fixedip/port#
ipp ://fixedip/printername
http ://sameasabove
or what?

I'm running Dapper Drake Xubuntu desktop.

Thanks.
pb

---

### Post by McTek on 2006-07-23
See what Packetcat has to say, what he did helped me finaly get my D-Link 301U print server up and running. I used the LPD mode and enter just the fix ip of the server (nothing but the number ie. 192.168.0.10 ) and the queue I left blank. Restart cups using his instructions.
Hope my experience will help.

---

### Post by pbmax on 2007-01-10
using Dapper, this is all fixed now.
I held the reset button on the print server until the lights reset (about 10 seconds) then connected using the browser to the default 192.168.0.10
Setup the networking/wireless and updated firmware from Dlink
Installed printer using the System Settings > Printers menu at 192.168.0.10:port# where the port was listed on the web control page for the server.
works fine now.
pb

---

### Post by cabbiepete on 2007-03-31
I am using **Ubutu Edgy** and I found that all I had to do was make sure that LPD was running on the DPR-1260 (by checking the Advanced Tab the LPR/LPD had the Enabled radio selected.

Then go to the status page and note down the value next to Server Name and the value next to LPR Queue Name for the printer you want to setup

Then I added the printer in the desktop by:

1. going the System menu -> Administration -> Printing

2. In the printing dialog double click New Printer

3. In the add a Printer dialog step 1 choose network printer, then in the drop down next to that choose Unix Printer (LPD), in host put the Server Name of the print server  that you noted down and in the queue put the LPR Queue Name that you noted down. Click Forward

3. Choose the Manufacturer and then the correct model, in my case HP and then PSC 1210. Then I went with the suggested driver hpijs. Click Forward

4. I left all fields as the default but you could put whatever makes sense here. click Apply

5. Now do a test print page and it worked.

---

### Post by kntgtaid on 2007-07-23
> Then go to the status page and note down the value next to Server Name and the value next to LPR Queue Name for the printer you want to setup

Then I added the printer in the desktop by:

1. going the System menu -> Administration -> Printing

2. In the printing dialog double click New Printer

3. In the add a Printer dialog step 1 choose network printer, then in the drop down next to that choose Unix Printer (LPD), in host put the Server Name of the print server  that you noted down and in the queue put the LPR Queue Name that you noted down. Click Forward

3. Choose the Manufacturer and then the correct model, in my case HP and then PSC 1210. Then I went with the suggested driver hpijs. Click Forward

4. I left all fields as the default but you could put whatever makes sense here. click Apply

5. Now do a test print page and it worked.

Can you see what was the final URI was set to?  I am using straight cups, and cannot figure out how to get the dpr-1260 working.

I am using an HP OfficeJet 5600, drp-1260 shows queue name of:  Officejet5600.  I am using the dpr-1260 as a wired print server with the static ip of 192.168.0.10.  The URI I am trying to use is:

lpd://192.168.0.10/Officejet5600

the error I am getting is:

"Remote host did not respond with data status byte after 300 seconds!"

Any help would be greatly appreciated.

Thanks 

Bryan

---

### Post by bwd1 on 2007-09-09
Here's how mine works.  
Background:  My DPR-1260 goes through a wireless router out to my workstations - some wireless, some hardwired.  

I used the IP address the router (DHCP) gave the DPR-1260.  So from the DRP-1260 "Status - Device Info" screen, I took the following information for input to the CUPS printer wizard: 

From DPR-1260's "IP Address:" 	 **192.168.0.136** (my address) into the wizard's Host field
From DRP-1260's "LPR Queue Name:"	 **OfficeJet6100Se** (my queue name) into the wizard's Queue field.  Follow the above recommendations (UNIX Printer LPR, etc.)

I input information using the 'New Printer' dialog.  Trying to change my existing 6100 configuration did not work.  I had to delete the old configuration and start over.

---

### Post by Totenglocke on 2008-04-26
I deleted XP off my laptop and installed Ubuntu last night (first time using linux) and the last thing I needed to get working was the print server.  Followed your tips and everything works fine.  

Thanks a lot!

---

### Post by TankCommander on 2008-05-01
Thanks for the help.  I just installed an old HP DeskJet932c to my NetGear FWG114Pv2 router's print server.  I used lpd://192.168.0.1/fwg114p.

I guess your queue name is set by the print server hardware, as per the router's instructions.

---

