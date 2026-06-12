---
title: "Epson CX5000 No Longer Prints"
date: 2009-01-25
forum: General Help
---

### Post by wdp on 2009-01-25
I've been using this former Windoze printer, connected to a USB port of my Hardy machine for about a month. Recently the ink of one of the colors ran low and I installed mtink to find out what my ink levels were.  To get mtink working I set it to run as root.

Since then I have been unable to print from OO.org, but I CAN print nozzle tests from mtink!  I have reinstalled the printer several times, but all attempts to print from OO.org or scite or any other program, initially put the file in the print queue with a status "Processing", but soon it soon changes to "Held".  Attempts to Release the documents in the queue all change to Procesing with a second change back to Held a few seconds later.

I have a Windoze laptop with a shared HP Photosmart 5145 connected to it and I CAN print to that printer over the network.  I believe this proves that CUPS is working.

I have installed Intrepid in another partition (64 bit version) with MythTV and I can print from that install.  This proves the printer still functions from OO.org (and others), locally on this box.

I know I must have mangled some permissions in getting mtink working but I can't think of where to look to straighten this problem out.  mtink is currently set up like:
root@we-pete-black:/usr/bin# ls -AlF mtink
-rwsr-xr-x 1 root root 212284 2007-10-28 09:08 mtink*

Any suggestions?

Additional notes -- Under Hardy (which is where everything worked before), I can still use xsane to scan documents using this printer's scanner.  Also, the print jobs that keep going to "Held" eventually drop off the queue leaving job number gaps.

Today I reinstalled the printer AGAIN after a "Held" hang.  When attempting to send another print job while this one was held, I saw an error message in the printer selection window:
Unable to open parallel port device file:  Permission denied
in the status column.  The printer is on /dev/usb/lp0 and this device shows ownership as:
wes@we-pete-black:/$ cd /dev/usb/
wes@we-pete-black:/dev/usb$ ls -AlF
total 0
crw-rw---- 1 root lp 180, 0 2009-01-25 11:50 lp0
I changed the rights with:
wes@we-pete-black:/dev/usb$ sudo chmod -v 'o+rw' /dev/usb/lp0 
mode of `/dev/usb/lp0' changed to 0666 (rw-rw-rw-)
and the printer now works.

This is not a setting I changed earlier for mtink.  I don't know how it got to what it was (assuming it was set correctly earlier when the printer worked).

Should this device be locked down and something else changed to allow cups to print?

---

