---
title: "system-config-printer-kde broken?"
date: 2009-01-07
forum: General Help
---

### Post by Wolf-Ekkehard on 2009-01-07
I have some serious problems with printing with kubuntu Intrepid.

I tried to re-install my printers after I failed to configure them with the Applications->System->Printing utility - bad mistake!!

The "Printing" utility deleted my printers just fine, but when I tried to re-install them it would just hang.  So I figured out what the name of that utility really was (system-config-printer-kde) and sudo-ed it in a terminal window (just to make sure there are no permission issues). As soon as I tried to add a "New Printer" it would give me the following errors:
> 
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 2580, in on_tvNPDevices_cursor_changed
    (self.cmbNPTSerialBaud, "baud", None),
AttributeError: cmbNPTSerialBaud
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 1181, in on_new_printer_activate
    self.newPrinterGUI.init("printer")
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 1596, in init
    self.fillDeviceTab()
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 2447, in fillDeviceTab
    self.on_tvNPDevices_cursor_changed()
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 2580, in on_tvNPDevices_cursor_changed
    (self.cmbNPTSerialBaud, "baud", None),
AttributeError: cmbNPTSerialBaud


I have a Brother HL-5250DN and a Canon BJC-3000 that used to work just fine on that machine for ages (Gusty, Hardy, and Intrepid until now).

In previous Kubuntu versions I never had a problem, so I came to rely on the configuration where my main machine is driving all the printers for the entire household, using Samba also for the Windows laptops.  That now being broken, I am facing some serious questions as to whether or not it was a smart idea to ditch XP for a "mission critical" computer...  

Pleas help!!

---

### Post by Wolf-Ekkehard on 2009-01-11
The problem with system-config-printer-kde giving error messages on a routine operation didn't go away, so as far as I can tell that's still broken (or not handling an error condition gracefully - i.e. broken just the same).

I now used CUPS's WEB interface [http://localhost:631](http://localhost:631) to add the printers.  I used ipp and [parallel:/dev/lp0](parallel:/dev/lp0) and [usb:/dev/usb/lp0](usb:/dev/usb/lp0) for the uri-s, as my Canon hangs off the USB prt and the Brother off the parallel port. So while THE problem with system-config-printer-kde still persists, MY problem with system-config-printer-kde went away - I am just not using it anymore, which may not be what the author(s) intended.

---

### Post by Blackmomba on 2009-01-21
I have the same problem here.

> Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 2580, in on_tvNPDevices_cursor_changed
    (self.cmbNPTSerialBaud, "baud", None),
AttributeError: cmbNPTSerialBaud
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 1181, in on_new_printer_activate
    self.newPrinterGUI.init("printer")
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 1596, in init
    self.fillDeviceTab()
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 2447, in fillDeviceTab
    self.on_tvNPDevices_cursor_changed()
  File "/usr/share/system-config-printer/system-config-printer-kde.py", line 2580, in on_tvNPDevices_cursor_changed
    (self.cmbNPTSerialBaud, "baud", None),
AttributeError: cmbNPTSerialBaud


---

### Post by Wolf-Ekkehard on 2009-01-25
Chances are your /etc/cupsd.conf has been corrupted by system-config-printer-kde.  You have to get a good version of this file (or clean it up manually) before you can use [http://localhost:631](http://localhost:631) to do your work.  Let me know if you need any help locating a good copy of this file.

---

### Post by yeats on 2009-03-11
You're right - same here with the KDE printer configuration program.  CUPS works flawlessly :-)

---

### Post by nonolemono on 2009-03-27
Still valid as of 27/03

---

