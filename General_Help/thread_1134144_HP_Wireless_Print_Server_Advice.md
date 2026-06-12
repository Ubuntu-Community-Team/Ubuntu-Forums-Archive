---
title: "HP Wireless Print Server Advice"
date: 2009-04-23
forum: General Help
---

### Post by lib99 on 2009-04-23
I have an HP Photosmart D5460 and HP 2101nw Wireless G Print Server from my Windows XP days. After searching around the forums and elsewhere I haven't found much about any implementations with Ubuntu [8.10 Intrepid Ibex].

Have tried assigning a JetDirect port, but no dice. My experience with CUPS and Linux printing is weak, since I don't print hard copy that often.

Any suggestions to try? ...or anyone have success connecting to such a device?

*IF* I were to set all this up via Windows XP VM (VirtualBox), would it be possible to share the printer with the Ubuntu host?

Thanks.

---

### Post by olafrv on 2009-06-17
I can't make it works natively on linux.

But I installed the printer in the Virtualbox VM (guest), share it on Windows XP and print from linux (host) :p.

Consider this:

1. Get the printer drivers (HP Photosmart c3180).

2. Configure the HP Wireless G Print Server from a Windows Machine (Vista or XP) to connect to the Wireless Router (TP Link 641), with this settings: SSID: REITMAIER, Encryption: AES (or TKIP), Password: ************, IP address asigned via DHCP.

3. Verify you can print from the Windows machine.

4. Install the printer driver into your Virtualbox VM.

5. Install the driver and software for the Print Server NOT FROM THE BOX CD, I DOWNLOAD THE LASTEST SOFTWARE FROM HP (Because the original CD software force you to connect via USB the print server to let you configure each workstation that will use it). 

Here is the: [DOWNLOAD DRIVER URL]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=AB-60529-1&lc=en&dlc=en&cc=us&product=3662206&os=228&lang=en").

6. Connect, Disconnect, Reconnect the printer server (It Really gets hot on the surface, don't know why) UNTIL you can ping it, from Windows Machine, Linux Machine and Virtual Machine (You must enable "HOST NETWORKING" in virtualbox so you can have direct connection and take a real IP from your Wireless LAN, with NAT you can't use the print server, some response packets are dropped.

7. Share the printer (published by the printer server) in the virtualbox WM (I renamed it as hpc3180, by default it is Printer).

8. Finally, configure the printer with cups ([http://localhost:631](http://localhost:631)) with the following URI smb://<ip of your virtualbox VM>/hpc3180

Good luck!!! :D

---

### Post by lib99 on 2009-06-19
Thanks olafrv! It would be great if HP would offer direct Linux support. Until then the VM solution will have to do. I appreciate the detailed steps you've provided.

---

