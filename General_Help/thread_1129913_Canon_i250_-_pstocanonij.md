---
title: "Canon i250 - pstocanonij"
date: 2009-04-19
forum: General Help
---

### Post by belda on 2009-04-19
Hi there,
I finally got the printer working by following this article 
[http://gkn.interbrainz.com/i250ubuntu/](http://gkn.interbrainz.com/i250ubuntu/)

now it prints the test page, from gedit and oo im also able to print, but printing from evince, firefox results in halted print job and from that point onward, the printer shows status message 
> /usr/lib/cups/filter/pstocanonbj failed

But im still able to print test page/gedit/oo etc.

I was further diagnosing the problem with the diagnostic tool and this is the output ```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest i250 (default)>,
 'cups_instance': None,
 'cups_queue': 'i250',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Canon/i250',
                       'printer-info': u'',
                       'printer-is-shared': True,
                       'printer-location': u'martin-desktop',
                       'printer-make-and-model': u'Canon i250 ver.2.3',
                       'printer-state': 3,
                       'printer-state-message': u'/usr/lib/cups/filter/pstocanonbj failed',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 167948,
                       'printer-uri-supported': u'ipp://localhost:631/printers/i250'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'ColorModel': u'rgb',
                                            u'InputSlot': u'asf',
                                            u'MediaType': u'plain',
                                            u'PageRegion': u'a4',
                                            u'PageSize': u'a4',
                                            u'Resolution': u'600'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Canon;CMD:BJL,HAPS,BSCCe;MDL:i250;CLS:PRINTER;DES:Canon i250;VER:1.40;STA:10;TII:K,****,UK,/,C,****,UK,/,M,****,UK,/,Y,****,UK;',
                      'device-info': u'Canon i250 USB #1',
                      'device-make-and-model': u'Canon i250'}}
Page 7 (Printer state reasons):
{'printer-state-message': u'/usr/lib/cups/filter/pstocanonbj failed',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '2000000',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '1',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 103231L,
 'error_log_debug_logging_set': True}
Page 9 (Print test page):
{'test_page_job_status': [(False,
                           42,
                           'i250',
                           'pstocanonij failed from firefox - Vyhledat Googlem',
                           'Zastaveno',
                           None),
                          (False,
                           43,
                           'i250',
                           'mozilla.pdf',
                           'Zastaveno',
                           None),
                          (False,
                           45,
                           'i250',
                           'www.pojisteni.com',
                           'Zastaveno',
                           None)],
 'test_page_jobs_cancelled': True,
 'test_page_successful': True}
Page 10 (Error log fetch):
{'error_log': ['D [19/Apr/2009:13:19:48 +0200] cupsdCloseClient: 7',
               'D [19/Apr/2009:13:19:48 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [19/Apr/2009:13:19:48 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [19/Apr/2009:13:19:48 +0200] cupsdAuthorize: No authentication data provided.',
               'D [19/Apr/2009:13:19:48 +0200] Get-Jobs ipp://localhost/jobs/',
               'D [19/Apr/2009:13:19:48 +0200] [Job 42] Loading attributes...',
               'D [19/Apr/2009:13:19:48 +0200] [Job 43] Loading attributes...',
               'D [19/Apr/2009:13:19:48 +0200] [Job 45] Loading attributes...',
               'D [19/Apr/2009:13:19:48 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [19/Apr/2009:13:19:48 +0200] cupsdCloseClient: 7',
               'D [19/Apr/2009:13:19:48 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [19/Apr/2009:13:19:48 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [19/Apr/2009:13:19:48 +0200] cupsdAuthorize: No authentication data provided.',
               'D [19/Apr/2009:13:19:48 +0200] Create-Printer-Subscription /',
               'D [19/Apr/2009:13:19:48 +0200] cupsdCreateSubscription(con=0xb8cf55e8(7), uri="/")',
               'D [19/Apr/2009:13:19:48 +0200] pullmethod="ippget"',
               'D [19/Apr/2009:13:19:48 +0200] notify-lease-duration=86400',
               'D [19/Apr/2009:13:19:48 +0200] notify-time-interval=0',
               'D [19/Apr/2009:13:19:48 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [19/Apr/2009:13:19:48 +0200] Added subscription 196 for server',
               'I [19/Apr/2009:13:19:48 +0200] Saving subscriptions.conf...',
               'D [19/Apr/2009:13:19:48 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [19/Apr/2009:13:19:48 +0200] cupsdCloseClient: 7',
               'D [19/Apr/2009:13:19:48 +0200] process_browse_data: PSC_2100@192.168.88.101 not found...',
               'D [19/Apr/2009:13:19:49 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [19/Apr/2009:13:19:49 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [19/Apr/2009:13:19:49 +0200] cupsdAuthorize: No authentication data provided.',
               'D [19/Apr/2009:13:19:49 +0200] Get-Notifications /',
               'D [19/Apr/2009:13:19:49 +0200] cupsdIsAuthorized: requesting-user-name="martin"',
               'D [19/Apr/2009:13:19:49 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [19/Apr/2009:13:19:49 +0200] cupsdCloseClient: 7',
               'D [19/Apr/2009:13:19:54 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [19/Apr/2009:13:19:54 +0200] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [19/Apr/2009:13:19:54 +0200] cupsdAuthorize: No authentication data provided.',
               'D [19/Apr/2009:13:19:54 +0200] Cancel-Job ipp://localhost/jobs/42',
               'D [19/Apr/2009:13:19:54 +0200] cupsdIsAuthorized: requesting-user-name="martin"',
               'I [19/Apr/2009:13:19:54 +0200] Saving subscriptions.conf...',
               'I [19/Apr/2009:13:19:54 +0200] [Job 42] Canceled by "martin".',
               'D [19/Apr/2009:13:19:54 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [19/Apr/2009:13:19:54 +0200] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [19/Apr/2009:13:19:54 +0200] cupsdAuthorize: No authentication data provided.',
               'D [19/Apr/2009:13:19:54 +0200] Cancel-Job ipp://localhost/jobs/43',
               'D [19/Apr/2009:13:19:54 +0200] cupsdIsAuthorized: requesting-user-name="martin"',
               'I [19/Apr/2009:13:19:54 +0200] Saving subscriptions.conf...',
               'I [19/Apr/2009:13:19:54 +0200] [Job 43] Canceled by "martin".',
               'D [19/Apr/2009:13:19:54 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [19/Apr/2009:13:19:54 +0200] cupsdReadClient: 7 POST /jobs/ HTTP/1.1',
               'D [19/Apr/2009:13:19:54 +0200] cupsdAuthorize: No authentication data provided.',
               'D [19/Apr/2009:13:19:54 +0200] Cancel-Job ipp://localhost/jobs/45',
               'D [19/Apr/2009:13:19:54 +0200] cupsdIsAuthorized: requesting-user-name="martin"',
               'I [19/Apr/2009:13:19:54 +0200] Saving subscriptions.conf...',
               'I [19/Apr/2009:13:19:54 +0200] [Job 45] Canceled by "martin".',
               'D [19/Apr/2009:13:19:54 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [19/Apr/2009:13:19:54 +0200] cupsdCloseClient: 7',
               'D [19/Apr/2009:13:19:58 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [19/Apr/2009:13:19:58 +0200] cupsdCloseClient: 7',
               'D [19/Apr/2009:13:19:58 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [19/Apr/2009:13:19:58 +0200] cupsdReadClient: 7 POST / HTTP/1.1',
               'D [19/Apr/2009:13:19:58 +0200] cupsdAuthorize: No authentication data provided.',
               'D [19/Apr/2009:13:19:58 +0200] Cancel-Subscription /',
               'D [19/Apr/2009:13:19:58 +0200] cupsdIsAuthorized: requesting-user-name="martin"',
               'I [19/Apr/2009:13:19:58 +0200] Saving subscriptions.conf...',
               'D [19/Apr/2009:13:19:58 +0200] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)',
               'D [19/Apr/2009:13:19:58 +0200] cupsdCloseClient: 7',
               'D [19/Apr/2009:13:19:58 +0200] cupsdAcceptClient: 7 from localhost (Domain)',
               'D [19/Apr/2009:13:19:58 +0200] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1',
               'D [19/Apr/2009:13:19:58 +0200] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}

```

The mentioned file should be ok

```
martin@martin-desktop:~$ ls /usr/lib/cups/filter/pstocanonbj -la
-rwxr-xr-x 1 root root 13516 2003-12-16 05:27 /usr/lib/cups/filter/pstocanonbj

```

Anyone encountered similar problem?

---

### Post by Jail on 2009-05-09
Hi,
I have similar problem with Ubuntu 9.04. With 8.04 it worked fine. After installing the drivers I can print from firefox or evince but sometimes printer refuses to print with the same error message.
> /usr/lib/cups/filter/pstocanonbj failed 
I couldn't find any pattern so I don't know where is the problem.

---

### Post by dannyman on 2009-09-03
God, me too.

Might I note the blog post at the top of this thread references my own blog post which references someone else . . .

So, yeah, this used to work in 8.04 but not in the 2009 flavor of Ubuntu.  Test pages, sure.  Everything else kills pstocanonbj. :(

-d

---

### Post by petsku on 2009-09-25
Anyone found solution to this? I upgraded also from 8.04 to 9.04 and the Canon i250 does not work any more.

---

### Post by L_V on 2009-09-26
You should investigate around these libs: libpng3 and libtiff

sudo ln -s /usr/lib/libpng.so.3 /usr/lib/libpng.so.2
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

sudo killall cupsd
sudo cupsd

Canon i250 is working fine in Ubuntu (even Karmic) and Debian (all).
But needs some work and investigation .....

---

### Post by petsku on 2009-09-26
Thanks L_V for the suggestion. But I had already the links and printer is not working. I have tried to google for solution with no success. Current links in the named files:

libpng.so.2 -> libpng.so.3 -> libpng12.so.0 -> libpng12.so.0.27.0

libtiff.so.3 -> libtiff.so.4 -> libtiff.so.4.2.1

---

### Post by L_V on 2009-09-26
libcups2 libcupsys2 cupsys-client cupsys-common installed ?

+ which cups version ??? (there are some known problems with 1.4)

+ [_usblp Kernel module needs to be removed and /dev/bus/usb/*/* made accessible for USB printers to work with CUPS 1.4.x_](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015)

---

### Post by petsku on 2009-09-26
All the named packages are installed.

Cups version is 1.3.9

I tried the tricks mentioned in the link you provided (blacklisting, rmmod usblp, chmod). But no help. The CUPS finds my printer properly and the test page prints correctly. But when I try to print something else I get the error "/usr/lib/cups/filter/pstocanonbj failed".

---

### Post by L_V on 2009-09-26
This bug is not specific to Canon i250.

It has been introduced with recent cups updates.

---

### Post by L_V on 2009-10-09
This is my turn.

I now have the same problem after recent cups updates.
"/usr/lib/cups/filter/pstocanonbj failed ".

Also have "*There was an error during the CUPS operation: 'client-error-not-found*'" when trying to print a test page.

I have removed and reinstalled my Canon I250 => same problem.

Something has been definitively broken in cups 1.4.

---

### Post by L_V on 2009-10-10
@petsku

Can you check if **foomatic-filters foomatic-db ghostscript-cups** are installed ?

The solution should be very close.

When using cups 1.4, **usblp** should be _blacklisted_ .

/etc/modprobe.d/blacklist.conf
```
blacklist usblp
```

The good news: *Canon_i250 printer is still compatible with Karmic*.
But needs some work and attention....

---

### Post by oldfred on 2009-10-10
When I first update to fiesty my Canon mp160 worked. Then after a download of new cups I got the same error. I had noticed a question about keep my version or maintainers version of a config file. I kept mine and got the error. I went back renamed my config and reinstalled and it worked.

I then wanted to install a second version of the same printer with different defaults (for photos). It still does not work and gives me the** **pstocanonbj error even though my other config still works.

---

### Post by L_V on 2009-10-10
With cups 1.4, URI of the printer has changed

sudo cat /etc/cups/printers.conf | grep DeviceURI

should give something like

DeviceURI usb://Canon/i250?serial=30ABAA

---

