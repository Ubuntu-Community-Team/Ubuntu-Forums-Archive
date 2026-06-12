---
title: "CUPS not working today... any ideas?"
date: 2009-01-25
forum: General Help
---

### Post by daverich on 2009-01-25
CUPS all of a sudden seems to now not work. Jobs get sent and then theres an error.

I've tried in Kubuntu and Ubuntu and I'm running Ibex.

the diagnosis gives:-


--------------------------------


 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'EconoMode': u'off',
                                            u'InputSlot': u'auto',
                                            u'Margins': u'Corrected',
                                            u'MediaType': u'Plain',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'600x600dpi'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Brother;CMD:PJL,HBP;MDL:HL-2030 series;CLS:PRINTER;',
                      'device-info': u'Brother HL-2030 series USB #1',
                      'device-make-and-model': u'Brother HL-2030 series'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 169448L}
Page 9 (Print test page):
{'test_page_job_status': [(False,
                           304,
                           'brother',
                           'Test Page',
                           'Stopped',
                           None),
                          (False,
                           305,
                           'brother',
                           'KDE Print Test',
                           'Stopped',
                           None),
                          (True,
                           303,
                           'brother',
                           'Motor Certificate AXA',
                           'Stopped',
                           {'EconoMode': u'off',
                            'InputSlot': u'auto',
                            'Margins': u'Corrected',
                            'MediaType': u'Plain',
                            'PageSize': u'Letter',
                            'Resolution': u'600x600dpi',
                            'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-gb',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 303,
                            'job-k-octets': 261,
                            'job-media-sheets-completed': 3,
                            'job-more-info': u'ipp://localhost:631/jobs/303',
                            'job-name': u'Motor Certificate AXA',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'dave',
                            'job-preserved': True,
                            'job-printer-state-message': u'/usr/lib/cups/filter/foomatic-rip failed',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1232883761,
                            'job-printer-uri': u'ipp://dave-desktop:631/printers/brother',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 6,
                            'job-state-reasons': u'job-stopped',
                            'job-uri': u'ipp://localhost:631/jobs/303',
                            'job-uuid': u'urn:uuid:b42cc91c-c3ed-3bee-4d8f-2ca572d6ab5e',
                            'number-up': 1,
                            'printer-uri': u'ipp://localhost:631/printers/brother',
                            'time-at-completed': None,
                            'time-at-creation': 1232882750,
                            'time-at-processing': 1232883413})],
 'test_page_successful': True}
Page 10 (Error log fetch):
{'error_log': ['D [25/Jan/2009:11:42:32 +0000] cupsdCloseClient: 12',
               'D [25/Jan/2009:11:42:32 +0000] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [25/Jan/2009:11:42:32 +0000] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [25/Jan/2009:11:42:32 +0000] cupsdAuthorize: No authentication data provided.',
               'D [25/Jan/2009:11:42:32 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [25/Jan/2009:11:42:32 +0000] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [25/Jan/2009:11:42:32 +0000] cupsdCloseClient: 12',
               'D [25/Jan/2009:11:42:32 +0000] cupsdCloseClient: 7',
               'D [25/Jan/2009:11:42:32 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [25/Jan/2009:11:42:32 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jan/2009:11:42:32 +0000] cupsdAuthorize: No authentication data provided.',
               'D [25/Jan/2009:11:42:32 +0000] Create-Printer-Subscription /',
               'D [25/Jan/2009:11:42:32 +0000] cupsdCreateSubscription(con=0xb9e9e990(7), uri="/")',
               'D [25/Jan/2009:11:42:32 +0000] pullmethod="ippget"',
               'D [25/Jan/2009:11:42:32 +0000] notify-lease-duration=86400',
               'D [25/Jan/2009:11:42:32 +0000] notify-time-interval=0',
               'D [25/Jan/2009:11:42:32 +0000] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [25/Jan/2009:11:42:32 +0000] Added subscription 31 for server',
               'I [25/Jan/2009:11:42:32 +0000] Saving subscriptions.conf...',
               'D [25/Jan/2009:11:42:32 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jan/2009:11:42:32 +0000] cupsdCloseClient: 7',
               'D [25/Jan/2009:11:42:33 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [25/Jan/2009:11:42:33 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jan/2009:11:42:33 +0000] cupsdAuthorize: No authentication data provided.',
               'D [25/Jan/2009:11:42:33 +0000] Get-Notifications /',
               'D [25/Jan/2009:11:42:33 +0000] cupsdIsAuthorized: requesting-user-name="dave"',
               'D [25/Jan/2009:11:42:33 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jan/2009:11:42:33 +0000] cupsdCloseClient: 7',
               'D [25/Jan/2009:11:42:41 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [25/Jan/2009:11:42:41 +0000] Report: clients=2',
               'D [25/Jan/2009:11:42:41 +0000] Report: jobs=42',
               'D [25/Jan/2009:11:42:41 +0000] Report: jobs-active=3',
               'D [25/Jan/2009:11:42:41 +0000] Report: printers=2',
               'D [25/Jan/2009:11:42:41 +0000] Report: printers-implicit=0',
               'D [25/Jan/2009:11:42:41 +0000] Report: stringpool-string-count=1389',
               'D [25/Jan/2009:11:42:41 +0000] Report: stringpool-alloc-bytes=10064',
               'D [25/Jan/2009:11:42:41 +0000] Report: stringpool-total-bytes=27640',
               'D [25/Jan/2009:11:42:41 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jan/2009:11:42:41 +0000] cupsdAuthorize: No authentication data provided.',
               'D [25/Jan/2009:11:42:41 +0000] Get-Job-Attributes ipp://localhost/jobs/303',
               'D [25/Jan/2009:11:42:41 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jan/2009:11:42:41 +0000] cupsdCloseClient: 7',
               'D [25/Jan/2009:11:42:41 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [25/Jan/2009:11:42:41 +0000] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [25/Jan/2009:11:42:41 +0000] cupsdAuthorize: No authentication data provided.',
               'D [25/Jan/2009:11:42:41 +0000] Cancel-Subscription /',
               'D [25/Jan/2009:11:42:41 +0000] cupsdIsAuthorized: requesting-user-name="dave"',
               'I [25/Jan/2009:11:42:41 +0000] Saving subscriptions.conf...',
               'D [25/Jan/2009:11:42:41 +0000] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [25/Jan/2009:11:42:41 +0000] cupsdCloseClient: 7',
               'D [25/Jan/2009:11:42:41 +0000] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [25/Jan/2009:11:42:41 +0000] cupsdCloseClient: 11',
               'D [25/Jan/2009:11:42:41 +0000] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1',
               'D [25/Jan/2009:11:42:41 +0000] cupsdAuthorize: No authentication data provided.']}

-----------------------

I did notice a cups update recently,- anyway to rollback? it was work perfectly.

Kind regards

Dave Rich

---

### Post by daverich on 2009-01-25
hmm ok.

It's seems cups had added a driver which *it* recommended which actually didn't work.

I've changed driver and now cups can make the printer fan whizz up and at least do something,- so I'll go through all the other drivers for my printer and hopefully the one that worked before is still there.

Kind regards

Dave Rich

---

### Post by daverich on 2009-01-25
ok.

went into cups,- deleted both my printer and the CUPS-PDF printer thing, reinstalled my printer with the driver that wasn't working before and now it works.

Something goofy in there but I'm glad I'm back on track now :)

So if anyone else gets this problem go to the CUPS server using your browser by going to [http://localhost:631](http://localhost:631)

and manage your printers there.

:)

Kind regards

Dave Rich

---

