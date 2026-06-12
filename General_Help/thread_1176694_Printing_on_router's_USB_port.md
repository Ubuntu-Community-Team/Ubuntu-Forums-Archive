---
title: "Printing on router's USB port"
date: 2009-06-02
forum: General Help
---

### Post by GrootBrak on 2009-06-02
I have the following hardware setup I want to make work.

An ADSL router (Siemens Giga 762 SX) and a Samsung CLP300 connected to the router's USB port.

In windows I was able to add my printer successfully to the machine via the routers USB port. (Thanks to the write-up for windows that comes with it... grrr...) In windows I had to add the printer as local, then at the port I added a new TCP/IP port. Entered my router's IP and used "lp0" under queue name. Then disabling bidirectional printing and finally added the printer to make use of the newly created port. 

Now how do I get to print on that usb port on my router from Ubuntu?

---

### Post by dcstar on 2009-06-03
> **GrootBrak said:**
> I have the following hardware setup I want to make work.

An ADSL router (Siemens Giga 762 SX) and a Samsung CLP300 connected to the router's USB port.

In windows I was able to add my printer successfully to the machine via the routers USB port. (Thanks to the write-up for windows that comes with it... grrr...) In windows I had to add the printer as local, then at the port I added a new TCP/IP port. Entered my router's IP and used "lp0" under queue name. Then disabling bidirectional printing and finally added the printer to make use of the newly created port. 

Now how do I get to print on that usb port on my router from Ubuntu?

I assume that you use the Printer tool in Administration to add a new printer in exactly the same way.

---

### Post by GrootBrak on 2009-06-03
That is what I am trying to do. But I am unsure how and where to add what.
Add New printer >>> Network printer (There is no "local printer" option available like in windows unless the printer is plugged into the computer's usb, but that defies the object.;))

Then >>>Internet  Printing Protocol (ipp)
Host: 10.0.0.2
queue: lp0 (i.e. lima papa zero)

After that I add my specific printer, in my case Samsung CLP300. Doing a test page, nothing happens. 

I've also added Printer >>> Other
URL: [http://10.0.0.2/lp0](http://10.0.0.2/lp0)
and
URL: ipp://10.0.0.2/lp0

Printing a test page  "Processing-recoverable:Network host 10.0.0.2 is busy will retry" 

Thanks for the reply, I hope I can get more help! :popcorn:

---

### Post by dcstar on 2009-06-03
> **GrootBrak said:**
> That is what I am trying to do. But I am unsure how and where to add what.
Add New printer >>> Network printer (There is no "local printer" option available like in windows unless the printer is plugged into the computer's usb, but that defies the object.;))

Then >>>Internet  Printing Protocol (ipp)
Host: 10.0.0.2
queue: lp0 (i.e. lima papa zero)

After that I add my specific printer, in my case Samsung CLP300. Doing a test page, nothing happens. 

I've also added Printer >>> Other
URL: [http://10.0.0.2/lp0](http://10.0.0.2/lp0)
and
URL: ipp://10.0.0.2/lp0

Printing a test page  "Processing-recoverable:Network host 10.0.0.2 is busy will retry" 

Thanks for the reply, I hope I can get more help! :popcorn:

What happens when you use the "Find Network Printer"?

Anyway, you should probably be using the AppSocket/HP method.

---

### Post by GrootBrak on 2009-06-03
Searching for network printer yield no result.

I added the printer under >>> LPD/LPR Host or printer
Host: 10.216.8.1
Queue: lp0

(BTW. I changed the routers IP, I did not like the default IP)

Under Printer poperties the device URL is displayed as
lpd://10.216.8.1/lp0

It start to spool the print job to 97% in a few seconds. Then it sits there for about 5 minutes and next thing, it prints. I'm including the printout from the troubleshooter.

> Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x94c0020>,
 'cups_instance': None,
 'cups_queue': 'LAN',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'lpd',
 'cups_printer_dict': {'device-uri': u'lpd://10.216.8.1/lp0',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'Ubuntu-desktop',
                       'printer-make-and-model': u'Samsung CLP-300 Foomatic/foo2qpdl (recommended)',
                       'printer-state': 4,
                       'printer-state-message': u'Spooling LPR job, 98% complete...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167964,
                       'printer-uri-supported': u'ipp://localhost:631/printers/LAN'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': 'Spooling LPR job, 98% complete...',
 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_job_status': [(20, 'LAN', 'Test Page')],
 'test_page_successful': True}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

I suspect the problem lies in the fact that I must disable bi-directional messages, as needs to be done for windows. I don't know where to disable it though. The router's instructions is very specific about disabling bi-directional messages. Any help?

---

### Post by GrootBrak on 2009-06-04
I did a port scan with "Network Tools"
It returns the following:
Port:  515
State: open
Service: printer

Will this be of any help installing a printer?
Regards

---

