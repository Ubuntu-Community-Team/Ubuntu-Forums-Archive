---
title: "dell 922 aio printer/juanty"
date: 2009-07-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ken78724 on 2009-07-23
any help appreciated. cups recognizes dell 922 aio printer but fails to print though indicator says job was printed. :popcorn: troubleshooter says: "Fails to find problem" here are results: 
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Photo_AIO_922 (default)>,
 'cups_instance': None,
 'cups_queue': 'Photo_AIO_922',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'hal',
 'cups_printer_dict': {'device-uri': u'hal:///org/freedesktop/Hal/devices/usb_device_413c_5109_CS51371_if1_printer_noserial',
                       'printer-info': u'Dell  Photo AIO 922',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Dell 1100, SpliX V. 2.0.0',
                       'printer-state': 4,
                       'printer-state-message': u'Printer is now on-line.',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143444,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Photo_AIO_922'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Altitude': u'LOW',
                                            u'ColorModel': u'Gray',
                                            u'Duplex': u'None',
                                            u'EconoMode': u'0',
                                            u'InputSlot': u'Auto',
                                            u'JamRecovery': u'False',
                                            u'MediaType': u'OFF',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PowerSave': u'5',
                                            u'Resolution': u'600dpi',
                                            u'TonerDensity': u'3'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Dell ;MDL:Photo AIO 922;CLS:PRINTER;',
                      'device-info': u'Dell  Photo AIO 922',
                      'device-make-and-model': u'Dell  Photo AIO 922'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'Printer is now on-line.',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '2000000',
                          'PreserveJobHistory': 'No',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 7785,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_job_status': [(False,
                           154,
                           'Photo_AIO_922',
                           'Test Page',
                           'Processing',
                           None),
                          (False,
                           155,
                           'Photo_AIO_922',
                           'Test Page',
                           'Pending',
                           None)],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['D [23/Jul/2009:11:10:11 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [23/Jul/2009:11:10:11 -0500] cupsdAuthorize: No authentication data provided.',
               'D [23/Jul/2009:11:10:11 -0500] Get-Jobs ipp://localhost/printers/',
               'D [23/Jul/2009:11:10:11 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [23/Jul/2009:11:10:11 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [23/Jul/2009:11:10:11 -0500] cupsdAuthorize: No authentication data provided.',
               'D [23/Jul/2009:11:10:11 -0500] Get-Jobs ipp://localhost/printers/',
               'D [23/Jul/2009:11:10:11 -0500] [Job 133] Loading attributes...',
               'D [23/Jul/2009:11:10:11 -0500] [Job 134] Loading attributes...',
               'D [23/Jul/2009:11:10:11 -0500] [Job 135] Loading attributes...',
               'D [23/Jul/2009:11:10:11 -0500] [Job 137] Loading attributes...',
               'D [23/Jul/2009:11:10:11 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [23/Jul/2009:11:10:11 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [23/Jul/2009:11:10:11 -0500] cupsdAuthorize: No authentication data provided.',
               'D [23/Jul/2009:11:10:11 -0500] Create-Printer-Subscription /',
               'D [23/Jul/2009:11:10:11 -0500] cupsdCreateSubscription(con=0x7f3a0b08e3f0(8), uri="/")',
               'D [23/Jul/2009:11:10:11 -0500] pullmethod="ippget"',
               'D [23/Jul/2009:11:10:11 -0500] notify-lease-duration=86400',
               'D [23/Jul/2009:11:10:11 -0500] notify-time-interval=0',
               'D [23/Jul/2009:11:10:11 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [23/Jul/2009:11:10:11 -0500] Added subscription 99 for server',
               'I [23/Jul/2009:11:10:11 -0500] Saving subscriptions.conf...',
               'D [23/Jul/2009:11:10:11 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [23/Jul/2009:11:10:12 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [23/Jul/2009:11:10:12 -0500] cupsdAuthorize: No authentication data provided.',
               'D [23/Jul/2009:11:10:12 -0500] Get-Notifications /',
               'D [23/Jul/2009:11:10:12 -0500] cupsdIsAuthorized: requesting-user-name="k78724"',
               'D [23/Jul/2009:11:10:12 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [23/Jul/2009:11:10:31 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [23/Jul/2009:11:10:31 -0500] cupsdAuthorize: No authentication data provided.',
               'D [23/Jul/2009:11:10:31 -0500] Cancel-Subscription /',
               'D [23/Jul/2009:11:10:31 -0500] cupsdIsAuthorized: requesting-user-name="k78724"',
               'I [23/Jul/2009:11:10:31 -0500] Saving subscriptions.conf...',
               'D [23/Jul/2009:11:10:31 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [23/Jul/2009:11:10:31 -0500] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [23/Jul/2009:11:10:31 -0500] cupsdReadClient: 9 GET /admin/log/error_log HTTP/1.1',
               'D [23/Jul/2009:11:10:31 -0500] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 11 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

### Post by ken78724 on 2009-07-26
Not solved but I relocated AIO printer drivers @ Linux Foundation OpenPrinting. They are worrisome and kinky; actually the same Lexmarkz600 drivers I came across 24 months back. has meant use a different printer which is very trying. 

I'd think Dell which now sells PCs and laptops with Ubuntu OSs that someone inside the company would post answers so Dell printers would/could be used on dell running off of ubuntu OSs. Have visited with many Dell sales people but none can tell you what printer they sell works with Ubuntu OSs installed.

---

