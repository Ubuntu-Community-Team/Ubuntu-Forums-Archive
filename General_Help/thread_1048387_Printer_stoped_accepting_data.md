---
title: "Printer stoped accepting data"
date: 2009-01-23
forum: General Help
---

### Post by wadesmart on 2009-01-23
I had posted this else where but Im not getting any help so I just posted it all back here.

A quick update. 

I have tried plugging the usb cable into each of my usb ports and immediately I get this error in my log:

Jan 23 11:23:49 wadesmart kernel: [ 3484.945180] usb 2-2: new full speed USB device using uhci_hcd and address 6
Jan 23 11:23:49 wadesmart kernel: [ 3485.352346] usb 2-2: device not accepting address 6, error -71

I have performed some research via google and it talks about removing the hi speed ability of the 2.0 port - but I dont think that is the problem as I have both port 1 and 2.0 ports and Im getting this message. 

Wade


Wade Smart wrote:
> 20090123 1010 GMT-5
>
> I got a kit to fix my printer but now I cant send data to it.
>
> I haven't changed the USB port.
> Nor the cable.
> In cups the address of the printer is:
> Device URI:
> hal:///org/freedesktop/Hal/devices/usb_device_4348_5584_noserial_if0_printer_noserial
>
> I printed a test page from the printer.
> I can NOT print a test page from the computer.
> Status in cups is: processing, accepting jobs
> Under device manger I can see the printer connected.
>
> using:
> sudo tail -f /var/log/messages
> I see:
> Jan 23 10:13:17 wadesmart kernel: [ 2501.138082] usb 1-1: new full speed
> USB device using uhci_hcd and address 88
>
> Nothing comes up when I do lsusb... and I have had that problem in the
> past too though it was printing.
>
> I dont know what to do next.
>
> This is my HP LaserJet 4050 running from parallel to usb, no network
> option available.
>
> Wade
>
>
> 20090123 1018 GMT-5
>
> I just found the error messages button in cups and it has only this:
> E [23/Jan/2009:09:25:39 -0600] [Job 18] No %%BoundingBox: comment in header!
> E [23/Jan/2009:09:32:21 -0600] [Job 18] No %%BoundingBox: comment in header!
> E [23/Jan/2009:09:32:21 -0600] [Job 18] Could initialize HAL daemon: (null)
> E [23/Jan/2009:09:50:41 -0600] [Job 19] No %%BoundingBox: comment in header!
> E [23/Jan/2009:09:51:32 -0600] Cancel-Job: Unauthorized
> E [23/Jan/2009:09:51:50 -0600] Pause-Printer: Unauthorized
> E [23/Jan/2009:09:51:50 -0600] Pause-Printer: Unauthorized
> E [23/Jan/2009:09:52:02 -0600] Resume-Printer: Unauthorized
>
> Wade


20090123 1024 GMT-5

Ah crap. In /var/log/syslog I have hundreds of lines with this:
Jan 23 10:23:17 wadesmart kernel: [ 3099.402989] usb 1-1: new full speed USB device using uhci_hcd and address 41
Jan 23 10:23:17 wadesmart kernel: [ 3099.814140] usb 1-1: device not accepting address 41, error -71
Jan 23 10:23:17 wadesmart kernel: [ 3099.925926] usb 1-1: new full speed USB device using uhci_hcd and address 42
Jan 23 10:23:18 wadesmart kernel: [ 3100.333105] usb 1-1: device not accepting address 42, error -71


20090123 1040 GMT-5

I think I have another problem.

I have hundreds of lines of:
Jan 23 10:40:00 wadesmart kernel: [  861.743026] usb 1-1: new full speed USB device using uhci_hcd and address 118

in my /var/log/messages and its just counting up and up and then restarting.

----------------

---

