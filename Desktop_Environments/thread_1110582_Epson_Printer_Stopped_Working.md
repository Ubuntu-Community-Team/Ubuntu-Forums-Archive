---
title: "Epson Printer Stopped Working"
date: 2009-03-29
forum: Desktop Environments
---

### Post by sweeny_here on 2009-03-29
Recently a Epson Stylus RX425 stopped working with Ubuntu 8.10.

System > Administration > Printing brings up a printer control panel. From here I can see the installed printer which was previously working.

If this default printer is right clicked,then select properties.A new window offers the option to "print self-test page".When selected an error is returned -  "cups server error - there was an error during the CUPS operation: client-error-document-format-not-supported".

If I attempt to print a page directly form any text editor,nothing happens!

Any tips or pointers would be much appreciated!

---

### Post by sweeny_here on 2009-03-30
The debug output from the Epson RX 425 printer is - 

```

Page 10 (Error log fetch):
{'error_log': ['D [30/Mar/2009:21:26:05 +0100] cupsdCloseClient: 8',
               'D [30/Mar/2009:21:26:05 +0100] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [30/Mar/2009:21:26:05 +0100] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [30/Mar/2009:21:26:05 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2009:21:26:05 +0100] Get-Jobs ipp://localhost/jobs/',
               'D [30/Mar/2009:21:26:05 +0100] [Job 38] Loading attributes...',
               'D [30/Mar/2009:21:26:05 +0100] [Job 39] Loading attributes...',
               'D [30/Mar/2009:21:26:05 +0100] [Job 40] Loading attributes...',
               'D [30/Mar/2009:21:26:05 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [30/Mar/2009:21:26:05 +0100] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [30/Mar/2009:21:26:05 +0100] cupsdCloseClient: 8',
               'D [30/Mar/2009:21:26:05 +0100] cupsdReadClient: 9 POST / HTTP/1.1',
               'D [30/Mar/2009:21:26:05 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2009:21:26:05 +0100] Create-Printer-Subscription /',
               'D [30/Mar/2009:21:26:05 +0100] cupsdCreateSubscription(con=0xb9ea9190(9), uri="/")',
               'D [30/Mar/2009:21:26:05 +0100] pullmethod="ippget"',
               'D [30/Mar/2009:21:26:05 +0100] notify-lease-duration=86400',
               'D [30/Mar/2009:21:26:05 +0100] notify-time-interval=0',
               'D [30/Mar/2009:21:26:05 +0100] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [30/Mar/2009:21:26:05 +0100] Added subscription 37 for server',
               'I [30/Mar/2009:21:26:05 +0100] Saving subscriptions.conf...',
               'D [30/Mar/2009:21:26:05 +0100] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [30/Mar/2009:21:26:05 +0100] cupsdCloseClient: 9',
               'D [30/Mar/2009:21:26:06 +0100] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [30/Mar/2009:21:26:06 +0100] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [30/Mar/2009:21:26:06 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2009:21:26:06 +0100] Get-Notifications /',
               'D [30/Mar/2009:21:26:06 +0100] cupsdIsAuthorized: requesting-user-name="user123"',
               'D [30/Mar/2009:21:26:06 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [30/Mar/2009:21:26:06 +0100] cupsdCloseClient: 8',
               'D [30/Mar/2009:21:26:19 +0100] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [30/Mar/2009:21:26:19 +0100] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [30/Mar/2009:21:26:19 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2009:21:26:19 +0100] Get-Job-Attributes ipp://localhost/jobs/40',
               'D [30/Mar/2009:21:26:19 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [30/Mar/2009:21:26:19 +0100] cupsdCloseClient: 8',
               'D [30/Mar/2009:21:26:19 +0100] cupsdAcceptClient: 8 from localhost (Domain)',
               'D [30/Mar/2009:21:26:19 +0100] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [30/Mar/2009:21:26:19 +0100] cupsdAuthorize: No authentication data provided.',
               'D [30/Mar/2009:21:26:19 +0100] Cancel-Subscription /',
               'D [30/Mar/2009:21:26:19 +0100] cupsdIsAuthorized: requesting-user-name="user123"',
               'I [30/Mar/2009:21:26:19 +0100] Saving subscriptions.conf...',
               'D [30/Mar/2009:21:26:19 +0100] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [30/Mar/2009:21:26:19 +0100] cupsdCloseClient: 8',
               'D [30/Mar/2009:21:26:19 +0100] cupsdAcceptClient: 8 from localhost:631 (IPv4)',
               'D [30/Mar/2009:21:26:19 +0100] cupsdReadClient: 8 GET /admin/log/error_log HTTP/1.1',
               'D [30/Mar/2009:21:26:19 +0100] cupsdAuthorize: No authentication data provided.']}

```

Does port 631 need to be enabled in the Firewall?

---

### Post by sweeny_here on 2009-03-30
I found a remedy by trial and error and here are the last set of steps which can be attributed to the fix -

1.Launched Synaptic Package Manger and removed packages 
> foomatic-db-engine
> foomatic-db
> foomatic-filters

2.Quit Synaptic and restarted printer.

3.Relaunched Synaptic and installed the following packages
> foomatic-db-engine
> foomatic-db
> foomatic-filters
> cups-driver-gutenprint
> escputil
> mtink
> libinklevel4

4.System > Administration > Printing and deleted the Epson printer.

5.Unplugged USB cable from computer.

6.Restarted printer.

7.Plugged USE cable back in.

8.Open a text editor and hit print,and this magically fixed the issue.

Just to note, the actual printer model, is the Epson Stylus RX425 but the system automatically detected the printer as a RX420.

PS. Port number 631 was also opened in the firewall and not sure if this was necessary.

---

