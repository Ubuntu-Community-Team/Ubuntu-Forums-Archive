---
title: "can't print from mini 9 8.04 to hp3930 on win xp"
date: 2008-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mrearl on 2008-11-22
Hi all:
This is my first post to this forum.  I recently acquired a Dell mini 9 running Hardy but I'm really a newb on Linux.

I've been trying to print from my mini 9 through a wireless connection to a win xp machine with a USB attached hp3930 printer.  As far as the mini 9 is concerned, files I try to print end successfully but they never print.  On the win xp machine they show up in the print monitor but they never actually print.  I've waited up to an hour or more but they never print. The icon for the hp3930 goes from "Ready" to "No Toner" but I just put new toner in yesterday and I can print to this printer from 2 other win xp boxes in the workgroup.

I originally thought this was a win xp problem but I'm not completely sure.  I also have an hp2550 laser printer attached to the same win xp box.  I installed the driver for that printer and everything was smoothe sailing.  The test page printed and I can print any doc to it so at leat in the case of the 2550 connectivity and communication seems to be fine.

Here's a copy of the printing troubleshooter log but I'm afarid that I'm too new to Linux to even know where or how to interpret it:

```
Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0x86f3b60>,
 'cups_instance': None,
 'cups_queue': 'DeskJet_3900',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://HOMEGRP/GRAPE/HPDeskjet%203930',
                       'printer-info': u'HP Deskjet 3930',
                       'printer-is-shared': True,
                       'printer-location': u'GRAPE',
                       'printer-make-and-model': u'HP DeskJet 3920 Foomatic/hpijs, hpijs 2.8.2',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 135180,
                       'printer-uri-supported': u'ipp://localhost:631/printers/DeskJet_3900'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(11, u'Job completed.')],
 'test_page_job_id': [11],
 'test_page_job_status': [(11, 'DeskJet_3900', 'Test Page')],
 'test_page_jobs_cancelled': True,
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

```

I welcome any suggestions or help to solve this sticky little problem.  With this exception, I really like the little mini 9 and Ubuntu Hardy Heron and I plan to get a lot of good use out of them.

Thanks
mrearl

---

