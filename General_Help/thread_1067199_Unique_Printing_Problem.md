---
title: "Unique Printing Problem"
date: 2009-02-11
forum: General Help
---

### Post by JustinAlf on 2009-02-11
Very few problems on these boards are unique, but I have searched and found nothing on the boards.  Here is my problem.

At my work, we have a HP officejet 6110.  When I plug is in via USB, Ubuntu finds the printer and prints fine.  When I plug that same printer into our Dell Windows XP computer, it prints fine.  When I have it plugged into via usb our windows computer, set printer to share, and find it on Ubuntu, it doesn't print.

Can anyone figure out why this doesn't work?  It shows up on my ubuntu machine, but it does not print.  Is it a windows firewall problem perhaps?  How would I disable the firewall on windows to print?  Any help would be great.

---

### Post by LowSky on 2009-02-11
It isn't a Firewall problem its a Windows share problem. Not windows fault but actually Ubuntu's

You need an applicaiton called samba, what it does is allow Linux users to use Windows Shares, including printing
check ou these links
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/8.10/serverguide/C/samba-printserver.html](https://help.ubuntu.com/8.10/serverguide/C/samba-printserver.html)

---

### Post by plucky on 2009-02-11
Also checkout this [link](https://help.ubuntu.com/community/WindowsXPPrinter)


Good Luck

---

### Post by JustinAlf on 2009-02-12
I have Samnba and Smbfs installed.  Here is my diagnostics report.  Hopefully this helps




Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest OtherP (default)>,
 'cups_instance': None,
 'cups_queue': 'OtherP',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://MSHOME/D6Y20L91/hpofficejet%206110',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'HP OfficeJet 6100 Foomatic/hpijs (recommended)',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167964,
                       'printer-uri-supported': u'ipp://localhost:631/printers/OtherP'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'nmblookup_output': ('querying D6Y20L91 on 192.168.1.255\n192.168.1.105 D6Y20L91<00>\n',
                      ''),
 'remote_server_name': '192.168.1.105'}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Duplex': u'None',
                                            u'InputSlot': u'Default',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PrintoutMode': u'Normal'},
                               u'PrintoutMode': {u'Quality': u'FromPrintoutMode'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Check network server sanity):
{'remote_server_name_resolves': ['192.168.1.105',
                                 '192.168.1.105',
                                 '192.168.1.105'],
 'remote_server_try_connect': '192.168.1.105'}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'LogLevel': 'warning',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '1',
                          '_share_printers': '0',
                          '_user_cancel_any': '1'},
 'error_log_checkpoint': 1701L,
 'error_log_debug_logging_set': True}
Page 8 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [31],
 'test_page_job_status': [(True,
                           31,
                           'OtherP',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 31,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/31',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'justin',
                            'job-printer-up-time': 1234449924,
                            'job-printer-uri': u'ipp://justin-laptop:631/printers/OtherP',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/31',
                            'job-uuid': u'urn:uuid:43c4cc68-dcee-3a36-6050-4fa3099a240d',
                            'printer-uri': u'ipp://localhost/printers/OtherP',
                            'time-at-completed': None,
                            'time-at-creation': 1234449908,
                            'time-at-processing': 1234449908})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [12/Feb/2009:08:45:03 -0600] cupsdCloseClient: 8',
               'D [12/Feb/2009:08:45:03 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [12/Feb/2009:08:45:03 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:03 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:03 -0600] Get-Jobs ipp://localhost/jobs/',
               'D [12/Feb/2009:08:45:03 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:03 -0600] cupsdCloseClient: 8',
               'D [12/Feb/2009:08:45:03 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [12/Feb/2009:08:45:03 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:03 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:03 -0600] Create-Printer-Subscription /',
               'D [12/Feb/2009:08:45:03 -0600] cupsdCreateSubscription(con=0xb9552c48(8), uri="/")',
               'D [12/Feb/2009:08:45:03 -0600] pullmethod="ippget"',
               'D [12/Feb/2009:08:45:03 -0600] notify-lease-duration=86400',
               'D [12/Feb/2009:08:45:03 -0600] notify-time-interval=0',
               'D [12/Feb/2009:08:45:03 -0600] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [12/Feb/2009:08:45:03 -0600] Added subscription 34 for server',
               'I [12/Feb/2009:08:45:03 -0600] Saving subscriptions.conf...',
               'D [12/Feb/2009:08:45:03 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:03 -0600] cupsdCloseClient: 8',
               'D [12/Feb/2009:08:45:04 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [12/Feb/2009:08:45:04 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:04 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:04 -0600] Get-Notifications /',
               'D [12/Feb/2009:08:45:04 -0600] cupsdIsAuthorized: requesting-user-name="justin"',
               'D [12/Feb/2009:08:45:04 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:04 -0600] cupsdCloseClient: 8',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 8 POST /printers/OtherP HTTP/1.1',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:08 -0600] Print-Job ipp://localhost/printers/OtherP',
               'D [12/Feb/2009:08:45:08 -0600] add_job: requesting-user-name="justin"',
               'D [12/Feb/2009:08:45:08 -0600] Adding default job-sheets values "none,none"...',
               'I [12/Feb/2009:08:45:08 -0600] [Job 31] Adding start banner page "none".',
               'I [12/Feb/2009:08:45:08 -0600] Saving subscriptions.conf...',
               'I [12/Feb/2009:08:45:08 -0600] [Job 31] Adding end banner page "none".',
               'I [12/Feb/2009:08:45:08 -0600] [Job 31] File of type application/postscript queued by "justin".',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] hold_until=0',
               'I [12/Feb/2009:08:45:08 -0600] [Job 31] Queued on "OtherP" by "justin".',
               'I [12/Feb/2009:08:45:08 -0600] Saving subscriptions.conf...',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] job-sheets=none,none',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] banner_page = 0',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] argv[0]="OtherP"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] argv[1]="31"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] argv[2]="justin"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] argv[3]="Test Page"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] argv[4]="1"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] argv[5]="job-uuid=urn:uuid:43c4cc68-dcee-3a36-6050-4fa3099a240d"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] argv[6]="/var/spool/cups/d00031-001"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[9]="SERVER_ADMIN=root@justin-laptop"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[12]="TZ=America/Chicago"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[13]="USER=root"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[16]="IPP_PORT=631"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[17]="CHARSET=utf-8"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[18]="LANG=en_US.UTF8"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[19]="PPD=/etc/cups/ppd/OtherP.ppd"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[20]="RIP_MAX_CACHE=8m"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[22]="DEVICE_URI=smb://MSHOME/D6Y20L91/hpofficejet%206110"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[23]="PRINTER=OtherP"',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] envp[24]="FINAL_CONTENT_TYPE=printer/OtherP"',
               'I [12/Feb/2009:08:45:08 -0600] [Job 31] Started filter /usr/lib/cups/filter/pstopdf (PID 8789)',
               'I [12/Feb/2009:08:45:08 -0600] [Job 31] Started filter /usr/lib/cups/filter/pdftopdf (PID 8790)',
               'I [12/Feb/2009:08:45:08 -0600] [Job 31] Started filter /usr/lib/cups/filter/foomatic-rip (PID 8792)',
               'I [12/Feb/2009:08:45:08 -0600] [Job 31] Started backend /usr/lib/cups/backend/smb (PID 8794)',
               'I [12/Feb/2009:08:45:08 -0600] Saving subscriptions.conf...',
               'D [12/Feb/2009:08:45:08 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] pstopdf argv[6] = 31 justin Test Page 1 job-uuid=urn:uuid:43c4cc68-dcee-3a36-6050-4fa3099a240d /var/spool/cups/d00031-001',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] PPD: /etc/cups/ppd/OtherP.ppd',
               'D [12/Feb/2009:08:45:08 -0600] cupsdCloseClient: 8',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Resolution: 1200',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Page size: Letter',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Width: 612, height: 792, absolute margins: , , ,',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Relative margins: 18, 36, 18, 9',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] PPD options: -r1200 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] PostScript to be injected:',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dPDFSETTINGS=/printer -r1200 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 - -',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:08 -0600] Get-Notifications /',
               'D [12/Feb/2009:08:45:08 -0600] cupsdIsAuthorized: requesting-user-name="justin"',
               'D [12/Feb/2009:08:45:08 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:08 -0600] Get-Job-Attributes ipp://localhost/jobs/31',
               'D [12/Feb/2009:08:45:08 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:08 -0600] Get-Notifications /',
               'D [12/Feb/2009:08:45:08 -0600] cupsdIsAuthorized: requesting-user-name="justin"',
               'D [12/Feb/2009:08:45:08 -0600] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'E [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: Local authentication certificate not found!',
               'D [12/Feb/2009:08:45:08 -0600] CUPS-Get-Printers',
               'D [12/Feb/2009:08:45:08 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'E [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: Local authentication certificate not found!',
               'D [12/Feb/2009:08:45:08 -0600] CUPS-Get-Classes',
               'D [12/Feb/2009:08:45:08 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 11 GET /admin/conf/printers.conf HTTP/1.1',
               'E [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: Local authentication certificate not found!',
               'D [12/Feb/2009:08:45:08 -0600] cupsdIsAuthorized: username=""',
               'D [12/Feb/2009:08:45:08 -0600] cupsdSendError: 11 code=401 (Unauthorized)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"',
               'D [12/Feb/2009:08:45:08 -0600] cupsdCloseClient: 11',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAcceptClient: 11 from localhost (Domain)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 11 GET /admin/conf/printers.conf HTTP/1.1',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: Authorized as root using Local',
               'D [12/Feb/2009:08:45:08 -0600] cupsdIsAuthorized: username="root"',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 11 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: Authorized as root using Local',
               'D [12/Feb/2009:08:45:08 -0600] CUPS-Get-Default',
               'D [12/Feb/2009:08:45:08 -0600] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdCloseClient: 9',
               'D [12/Feb/2009:08:45:08 -0600] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:08 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:08 -0600] Get-Notifications /',
               'D [12/Feb/2009:08:45:08 -0600] cupsdIsAuthorized: requesting-user-name="justin"',
               'D [12/Feb/2009:08:45:08 -0600] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:08 -0600] cupsdCloseClient: 12',
               'D [12/Feb/2009:08:45:08 -0600] cupsdCloseClient: 8',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Getting input from file',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] foomatic-rip version 4.0.0.195 running...',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Parsing PPD file ...',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option Resolution',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option PageSize',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option Model',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option PrintoutMode',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option InputSlot',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option ImageableArea',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option PaperDimension',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option Duplex',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option Quality',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Added option Font',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31]',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Parameter Summary',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] -----------------',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31]',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Spooler: cups',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Printer: OtherP',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Shell: /bin/bash',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] PPD file: /etc/cups/ppd/OtherP.ppd',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] ATTR file:',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Printer model: HP OfficeJet 6100 Foomatic/hpijs (recommended)',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Job title: Test Page',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] File(s) to be printed:',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] <STDIN>',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31]',
               "D [12/Feb/2009:08:45:08 -0600] [Job 31] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts",
               "D [12/Feb/2009:08:45:08 -0600] [Job 31] Pondering option 'job-uuid=urn:uuid:43c4cc68-dcee-3a36-6050-4fa3099a240d'",
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] Unknown option job-uuid=urn:uuid:43c4cc68-dcee-3a36-6050-4fa3099a240d.',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31]',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] ================================================',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31]',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] File: <STDIN>',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31]',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31] ================================================',
               'D [12/Feb/2009:08:45:08 -0600] [Job 31]',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] GPL Ghostscript 8.63: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] Filetype: PDF',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] Storing temporary files in /var/spool/cups/tmp',
               'D [12/Feb/2009:08:45:09 -0600] PID 8789 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [12/Feb/2009:08:45:09 -0600] PID 8790 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] File contains 1 pages',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5550" -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-vXUMCW',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] Starting process "kid3" (generation 1)',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] Starting process "kid4" (generation 2)',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] JCL: \x1b%-12345X@PJL',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] <job data>',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31]',
               'D [12/Feb/2009:08:45:09 -0600] [Job 31] Starting process "renderer" (generation 2)',
               'D [12/Feb/2009:08:45:24 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [12/Feb/2009:08:45:24 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:24 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:24 -0600] Get-Job-Attributes ipp://localhost/jobs/31',
               'D [12/Feb/2009:08:45:24 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:24 -0600] cupsdCloseClient: 8',
               'D [12/Feb/2009:08:45:24 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [12/Feb/2009:08:45:24 -0600] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [12/Feb/2009:08:45:24 -0600] cupsdAuthorize: No authentication data provided.',
               'D [12/Feb/2009:08:45:24 -0600] Cancel-Subscription /',
               'D [12/Feb/2009:08:45:24 -0600] cupsdIsAuthorized: requesting-user-name="justin"',
               'I [12/Feb/2009:08:45:24 -0600] Saving subscriptions.conf...',
               'D [12/Feb/2009:08:45:24 -0600] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [12/Feb/2009:08:45:24 -0600] cupsdCloseClient: 8',
               'D [12/Feb/2009:08:45:24 -0600] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [12/Feb/2009:08:45:24 -0600] cupsdReadClient: 8 GET /admin/log/error_log HTTP/1.1',
               'D [12/Feb/2009:08:45:24 -0600] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 10 (Printer state reasons):
{'printer-state-message': u'Connection failed: NT_STATUS_ACCESS_DENIED',
 'printer-state-reasons': [u'none']}

---

### Post by JustinAlf on 2009-02-12
bump, I need to figure this out fast.  Is it a router problem perhaps?

---

### Post by Indubitableness on 2009-02-15
I'm having the same problem with an Officejet 5610 All-in-One. On this same install it used to work when we had a windows XP system hooked up in the other room (that would be the system with the printer attached) one day it just broke.

 Since then i tried a couple times, one of the things that helped A LITTLE bit was using the ip address in place of the network name. We've just installed a new Vista system out there, which i love vista (don't kill me!!!) so i figured i'd try it out again.

 No go, when i use the IP address and click verify in the printing setup it finds the printer right away, says "Verified Connected" but nothing will print. 

  I hope someone can help you with this too, 'cause it's definitely not unique, just rare apparently.

 I tried a couple things in the smb.conf, and actually ended up setting up a couple network shares in the process that i had been meaning to, but that wasn't what i set out to do when i started editing smb.conf, i just want my printer to work.

---

### Post by JustinAlf on 2009-03-02
bump

---

### Post by crunchfighter on 2009-03-04
I just set up a Canon PIXMA IP3000 on a Windows XP machine. 
I shared it from Windows.
On Ubuntu, I added Samba.  (It was probably there already)
System->Administration->Printing
Click "New"
Click "Windows Printer via SAMBA"
Navigate your network to the host computer
Select the printer name and model to find the driver.
Print a test page.

It worked that smoothly for me.  No terminal commands or symbolic links required.

---

### Post by JustinAlf on 2009-03-05
I have tried many in many differnt ways.  I did not have this problem ever in Hardy.  I think I'm just going to downgrade.  To me, Ibex has been nothing more than Vista, a very pretty OS, but functionally doesn't work better than the previous version.

---

### Post by CMJ Tech on 2009-04-28
> **JustinAlf said:**
>  When I plug that same printer into our Dell Windows XP computer, it prints fine.  When I have it plugged into via usb our windows computer, set printer to share, and find it on Ubuntu, it doesn't print.



I had the same problem with my setup as well.  I was able to correct this problem by disabling 'Enable bidirectional support' on the ports tab of the printer properties in Windows XP.
This allowed me to print from my ubuntu machine, but I do not know the side effects of making this change.

---

