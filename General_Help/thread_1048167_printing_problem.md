---
title: "printing problem"
date: 2009-01-23
forum: General Help
---

### Post by florus on 2009-01-23
After over a year of working perfectly, my system has suddenly developed a printing problem. I am printing over a network to a USB attached printer on a Windows XP computer. I can print a test page and emails without a problem, but I cannot print pdf files or print from the internet. The error output seems to hinge on: CupsdAuthorize:No authentication data provided
Full output:
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest HL-5240_BR-Script3 (default)>,
 'cups_instance': None,
 'cups_queue': 'HL-5240_BR-Script3',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://OWL/MESH/BrotherH',
                       'printer-info': u'brother HL 5240',
                       'printer-is-shared': True,
                       'printer-location': u'mark-desktop',
                       'printer-make-and-model': u'Brother HL-5240 BR-Script3',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 4370500,
                       'printer-uri-supported': u'ipp://localhost:631/printers/HL-5240_BR-Script3'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'nmblookup_output': ('querying MESH on 192.168.2.255\n192.168.2.101 MESH<00>\n',
                      ''),
 'remote_server_name': '192.168.2.101'}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'BRLanguageLevel': u'L3',
                                            u'BRMediaType': u'Plain',
                                            u'CAPT': u'Middle',
                                            u'InputSlot': u'AutoSelect',
                                            u'ManualFeed': u'False',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'ScreenLock': u'True',
                                            u'Sleep': u'PrinterDefault',
                                            u'TonerSaveMode': u'Off'},
                               u'InstallableOptions': {u'OptionTrays': u'1Trays'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Check network server sanity):
{'remote_server_name_resolves': ['192.168.2.101',
                                 '192.168.2.101',
                                 '192.168.2.101'],
 'remote_server_try_connect': '192.168.2.101'}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 63190L}
Page 8 (Print test page):
{'test_page_job_status': [], 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [23/Jan/2009:11:21:46 +0000] cupsdCloseClient: 12',
               'D [23/Jan/2009:11:21:46 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:21:46 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:21:46 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:21:46 +0000] Get-Jobs ipp://localhost/jobs/',
               'D [23/Jan/2009:11:21:46 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:21:46 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:21:46 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:21:46 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:21:46 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:21:46 +0000] Create-Printer-Subscription /',
               'D [23/Jan/2009:11:21:46 +0000] cupsdCreateSubscription(con=0xb86bbf80(11), uri="/")',
               'D [23/Jan/2009:11:21:46 +0000] pullmethod="ippget"',
               'D [23/Jan/2009:11:21:46 +0000] notify-lease-duration=86400',
               'D [23/Jan/2009:11:21:46 +0000] notify-time-interval=0',
               'D [23/Jan/2009:11:21:46 +0000] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [23/Jan/2009:11:21:46 +0000] Added subscription 47 for server',
               'I [23/Jan/2009:11:21:46 +0000] Saving subscriptions.conf...',
               'D [23/Jan/2009:11:21:46 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:21:46 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:21:47 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:21:47 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:21:47 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:21:47 +0000] Get-Notifications /',
               'D [23/Jan/2009:11:21:47 +0000] cupsdIsAuthorized: requesting-user-name="mark"',
               'D [23/Jan/2009:11:21:47 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:21:47 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:07 +0000] CUPS-Get-Printers',
               'D [23/Jan/2009:11:22:07 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:07 +0000] CUPS-Get-Classes',
               'D [23/Jan/2009:11:22:07 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:07 +0000] CUPS-Get-Default',
               'D [23/Jan/2009:11:22:07 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:07 +0000] CUPS-Get-Printers',
               'D [23/Jan/2009:11:22:07 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:07 +0000] CUPS-Get-Classes',
               'D [23/Jan/2009:11:22:07 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:07 +0000] CUPS-Get-Default',
               'D [23/Jan/2009:11:22:07 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:07 +0000] CUPS-Get-Printers',
               'D [23/Jan/2009:11:22:07 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [23/Jan/2009:11:22:07 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:07 +0000] cupsdReadClient: 12 GET /printers/HL-5240_BR-Script3.ppd HTTP/1.1',
               'D [23/Jan/2009:11:22:07 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:07 +0000] cupsdCloseClient: 12',
               'D [23/Jan/2009:11:22:10 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:10 +0000] Report: clients=3',
               'D [23/Jan/2009:11:22:10 +0000] Report: jobs=419',
               'D [23/Jan/2009:11:22:10 +0000] Report: jobs-active=0',
               'D [23/Jan/2009:11:22:10 +0000] Report: printers=1',
               'D [23/Jan/2009:11:22:10 +0000] Report: printers-implicit=0',
               'D [23/Jan/2009:11:22:10 +0000] Report: stringpool-string-count=1147',
               'D [23/Jan/2009:11:22:10 +0000] Report: stringpool-alloc-bytes=7104',
               'D [23/Jan/2009:11:22:10 +0000] Report: stringpool-total-bytes=19888',
               'D [23/Jan/2009:11:22:10 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:10 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:10 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:10 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:10 +0000] CUPS-Get-Printers',
               'D [23/Jan/2009:11:22:10 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:10 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:14 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:14 +0000] cupsdReadClient: 11 POST /printers/HL-5240_BR-Script3 HTTP/1.1',
               'D [23/Jan/2009:11:22:14 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:14 +0000] Print-Job ipp://localhost:631/printers/HL-5240_BR-Script3',
               'D [23/Jan/2009:11:22:14 +0000] [Job ???] Auto-typing file...',
               'I [23/Jan/2009:11:22:14 +0000] [Job ???] Request file type is application/postscript.',
               'E [23/Jan/2009:11:22:14 +0000] Print-Job: Unauthorized',
               'D [23/Jan/2009:11:22:14 +0000] cupsdSendError: 11 code=401 (Unauthorized)',
               'D [23/Jan/2009:11:22:14 +0000] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"',
               'D [23/Jan/2009:11:22:14 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:17 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:17 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:17 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:17 +0000] Get-Notifications /',
               'D [23/Jan/2009:11:22:17 +0000] cupsdIsAuthorized: requesting-user-name="mark"',
               'D [23/Jan/2009:11:22:17 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:17 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:29 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:29 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:29 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:29 +0000] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [23/Jan/2009:11:22:29 +0000] cupsdAuthorize: No authentication data provided.',
               'D [23/Jan/2009:11:22:29 +0000] Cancel-Subscription /',
               'D [23/Jan/2009:11:22:29 +0000] cupsdIsAuthorized: requesting-user-name="mark"',
               'I [23/Jan/2009:11:22:29 +0000] Saving subscriptions.conf...',
               'D [23/Jan/2009:11:22:29 +0000] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [23/Jan/2009:11:22:29 +0000] cupsdCloseClient: 11',
               'D [23/Jan/2009:11:22:29 +0000] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [23/Jan/2009:11:22:29 +0000] cupsdCloseClient: 10',
               'D [23/Jan/2009:11:22:29 +0000] cupsdReadClient: 11 GET /admin/log/error_log HTTP/1.1',
               'D [23/Jan/2009:11:22:29 +0000] cupsdAuthorize: No authentication data provided.']}

Any advice would be appreciated.

---

### Post by florus on 2009-01-23
Bump

---

### Post by florus on 2009-01-25
Bump

---

