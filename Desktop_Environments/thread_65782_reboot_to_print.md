---
title: "reboot to print"
date: 2005-09-15
forum: Desktop Environments
---

### Post by rplantz on 2005-09-15
I have a Samsung ML-1430 usb printer that works fine if it's on when I boot the system, but not if I turn the printer on after booting.

When I reboot, print jobs in the queue are printed.

After rebooting (and the job in the queue printing), I got:

bob:~$ lpstat -t
scheduler is running
system default destination: ML-1430
device for ML-1430: usb:/dev/usb/lp0
ML-1430 accepting requests since Jan 01 00:00
printer ML-1430 is idle.  enabled since Jan 01 00:00

Then I turned the printer off, then on and tried to print another page. It doesn't print, and I get:

bob:~$ lpstat -t
scheduler is running
system default destination: ML-1430
device for ML-1430: usb:/dev/usb/lp0
ML-1430 accepting requests since Jan 01 00:00
printer ML-1430 now printing ML-1430-48.  enabled since Jan 01 00:00
        Printer not connected; will retry in 30 seconds...
ML-1430-48              bob              67584   Wed 14 Sep 2005 10:41:52 PM PDT

(It does not retry.)
I've tried restarting cups and removing and reinstalling my printer, but no luck.

Bob

---

