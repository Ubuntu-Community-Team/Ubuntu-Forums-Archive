---
title: "Inspiron Mini 9 won't print to HP Deskjet D2530"
date: 2009-04-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by epb223 on 2009-04-03
Here's the bug report I got when I tried to print a test page (for the nth time, by the way; does anyone know how to clear the print queue? It always shows no jobs under the printer, but the job number keeps going up):

Public bug reported:

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x860dd60>,
 'cups_instance': None,
 'cups_queue': 'Deskjet_D2500_series',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'hp',
 'cups_printer_dict': {'device-uri': u'hp:/usb/Deskjet_D2500_series?serial=TH89H133B1055M',
                      'printer-info': u'HP Deskjet D2500 series',
                      'printer-is-shared': True,
                      'printer-location': u'',
                      'printer-make-and-model': u'HP DeskJet D2400 Foomatic/hpijs, hpijs 2.8.2',
                      'printer-state': 3,
                      'printer-state-message': u'',
                      'printer-state-reasons': [u'none'],
                      'printer-type': 4108,
                      'printer-uri-supported': u'ipp://localhost:631/printers/Deskjet_D2500_series'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(48, u'Job completed.')],
 'test_page_job_id': [48],
 'test_page_job_status': [(48, 'Deskjet_D2500_series', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

** Affects: ubuntu
    Importance: Undecided
        Status: New

Any suggestions? It's starting to seem like this computer just doesn't want to print.

---

