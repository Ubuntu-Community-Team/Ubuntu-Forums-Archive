---
title: "Printing...."
date: 2005-04-19
forum: Desktop Environments
---

### Post by cooperaaaron on 2005-04-19
I ran thru the printing setup options by selecting System at the bottom of the page.  I followed the directions and I got 1/2 a test page to print, now I can't get anything to print at all, under the Generic Unix LPD Print System.  I can't get anything to print under the CUPS system, every time something is sent to the printer, the job is queued and nothing prints, the printer stops accecpting jobs as soon as a job is sent. If I have to, I will reinstall, but that's only if I have to... Otherwise Kubuntu is a nice distro for everyday use.

Thanks to all in advance !

---

### Post by shamanic on 2005-04-21
After last update of Breezy i have that same problem.

from dmesg:
usb 1-2: new full speed USB device using uhci_hcd and address 9
drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 9 if 0 alt 0 proto 2 vid 0x03F0 pid 0x6204

looks fine, but (from /var/log/cups/error_log):

I [21/Apr/2005:18:37:17 +0200] Job 3 queued on 'hp5150' by 'shamanic'.
I [21/Apr/2005:18:37:17 +0200] Started filter /usr/lib/cups/filter/pstops (PID 20186) for job 3.
I [21/Apr/2005:18:37:17 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 20187) for job 3.
I [21/Apr/2005:18:37:17 +0200] Started backend /usr/lib/cups/backend/usb (PID 20188) for job 3.
E [21/Apr/2005:18:37:17 +0200] PID 20188 stopped with status 1!
I [21/Apr/2005:18:37:17 +0200] Hint: Try setting the LogLevel to "debug" to find out more.
E [21/Apr/2005:18:37:17 +0200] [Job 3] Unable to open USB device "usb://5150?serial=MY3AL3J4V87A": No such device
E [21/Apr/2005:18:37:20 +0200] PID 20187 stopped with status 9!


he can't handle device.. 

Any ideas ?  ](*,)

---

### Post by jkndrkn on 2005-04-24
[QUOTE=shamanic]
E [21/Apr/2005:18:37:17 +0200] PID 20188 stopped with status 1!
I [21/Apr/2005:18:37:17 +0200] Hint: Try setting the LogLevel to "debug" to find out more.
E [21/Apr/2005:18:37:17 +0200] [Job 3] Unable to open USB device "usb://5150?serial=MY3AL3J4V87A": No such device
E [21/Apr/2005:18:37:20 +0200] PID 20187 stopped with status 9![/QUOTE]

I'm having the same problem with my Lexmark X73 printer.
I checked to make sure i have the right driver and ppd installed.
Ubuntu recognized and set everything up automatically.
However, the error log shows a problem with the usb connection.

Anybody have a solution?

---

### Post by paulle on 2005-04-25
i've the same problem with a hp640c connected via usb.

---

### Post by jkndrkn on 2005-04-27
after searching through linuxquestions.com and googling around, things don't look very optimistic for my lexmark usb printer

i'll let you guys know if i ever figure out how to get it running

---

### Post by petertc on 2005-04-29
try this out just found out about it works fine with my set up


sudo chmod o=rw /dev/usb/lp0

so i read this changes the permissions on the usb port and enable it to work 

see how you get on

the only thing is you have to do it every time you boot  the machine up!!

---

### Post by jkndrkn on 2005-04-29
[QUOTE=petertc]sudo chmod o=rw /dev/usb/lp0[/QUOTE]

you mean o+rw ;)

yeah, i've tried it
doesn't work
don't know if it's related, but cups seems to think my printer is located at usb://Lexmark/X73
which doesn't seem to be a real location

---

