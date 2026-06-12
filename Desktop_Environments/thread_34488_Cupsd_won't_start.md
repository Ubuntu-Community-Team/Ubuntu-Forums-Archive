---
title: "Cupsd won't start"
date: 2005-05-15
forum: Desktop Environments
---

### Post by MZett on 2005-05-15
Hi everybody,

I don't know why, but my cupds does not want to start (anymore). I tried deinstall / reinstall, looked at cupds.conf etc. But now luck.

This is what I do (as root): /etc/initd./cupsys start
The only messega I get is then
 * Starting Common Unix Printing System: cupsd                                                                  [ ok ]

Which does not look to bad.

However, doing something like

ps -ef | grep cups

shows me that no cupds is running.

All the logs are empty (/var/log/syslog, /var/log/messages, /var/log/lpr.log)

All /var/log/cups/error_log says is
I [15/May/2005:11:27:29 +0200] Listening to 0:631
I [15/May/2005:11:27:29 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [15/May/2005:11:27:29 +0200] Configured for up to 100 clients.
I [15/May/2005:11:27:29 +0200] Allowing up to 100 client connections per host.
I [15/May/2005:11:27:29 +0200] Full reload is required.
W [15/May/2005:11:27:29 +0200] AddBanner: Banner "confidential" is of an unknown file type - skipping!
W [15/May/2005:11:27:29 +0200] AddBanner: Banner "classified" is of an unknown file type - skipping!
W [15/May/2005:11:27:29 +0200] AddBanner: Banner "standard" is of an unknown file type - skipping!
W [15/May/2005:11:27:29 +0200] AddBanner: Banner "secret" is of an unknown file type - skipping!
W [15/May/2005:11:27:29 +0200] AddBanner: Banner "unclassified" is of an unknown file type - skipping!
W [15/May/2005:11:27:29 +0200] AddBanner: Banner "topsecret" is of an unknown file type - skipping!
I [15/May/2005:11:27:30 +0200] LoadPPDs: Read "/etc/cups/ppds.dat", 2114 PPDs...
I [15/May/2005:11:27:30 +0200] LoadPPDs: No new or changed PPDs...
I [15/May/2005:11:27:30 +0200] Full reload complete.

Any idea anybody?

Thanks in advance


Michael

---

