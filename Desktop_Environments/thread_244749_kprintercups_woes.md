---
title: "kprinter/cups woes"
date: 2006-08-26
forum: Desktop Environments
---

### Post by mediocre on 2006-08-26
I know you've heard it before: "It was working just a few hours ago!"

"Suddenly" some applications (eg. firefox) can print, and others (openoffice.org) can't. 

If I run kprinter, it immediately replies with:

> An error occurred while retrieving the printer list:

Connection to CUPS server failed. Check that the CUPS server is correctly installed and running. Error: Connection to CUPS server failed. Check that the CUPS server is correctly installed and running..

The dialogue box that opens lists no printers.

On the other hand, gnome-cups-manager works perfectly--starts without error and shows my printer, correctly configured. 

As well, if I browse to 192.168.0.104/printers, that seems to work as well, showing my printer in place and ready to accept jobs. Printing test pages works.

It's weird because I swear: I successfully printed a page with OpenOffice.org Writer just a few minutes before I tried again and it failed. I actually rebooted the computer. Hmmmm.... I didn't think to reboot the printer as well, but I don't think... well, I'll give that a try but...

I've noticed some older posts with this problem, but they seems to suggest that it was corrected. This is a recent install of Ubuntu Dapper, all updates, plus kubuntu-desktop.


Any ideas?

Nick.

---

### Post by mediocre on 2006-08-27
An update:

Things got really weird for a while. The K/System Settings/Printers dialogue took forever to load, and when it did, I couldn't get into Administrator Mode. I removed the printer using kdesu gnome-cups-manager (!) and re-installed it. That got the printer working again, but something is still pretty strange. I can get into the Admin. mode in kde now, but it takes about 45 seconds for the screen to load and moving about the dialogue box is a slow process--takes about 10 seconds to move from the information tab to the jobs tab, for example. Also, if I'm flipping between apps (as I'm doing now) and the printer dialogue box is obscured, it takes it about 5 seconds to re-draw when it gets focus. 

What have I done?

N

---

### Post by mediocre on 2006-09-03
To finish off this "busy" thread:

It would appear that the problem had to do with my changes to one of
  * /etc/cups/cupsd.conf
  * /etc/cups/cups.d/*
in my attempt to make the printer sharable with a Windows machine on the network. 

A complete refresh of the /etc/cups folder was needed (from another Ubuntu machine). This time, I made a /etc/cupsbackup folder and copied the works into it before mucking about. 

Anyway, all appears to be well now.

FUNNY thing... I could never get my printer to go at all when using Slackware (current, recently). I would get error messages about ehci_hcd usb disconnects at boot time, and /dev/usb/lp0 would refuse to appear. The concensus among slackers was that the cable might be at fault--I tried four different ones. The only way I could get the printer to appear was to rmmod ehci_hcd or blacklist it. I notice that with Ubuntu, the ehci_hcd modules is loaded and apparently working fine--/dev/usb/lp0 was created without complaint. Yay, Ubuntu, of course, but what the heck?

Now that everything's working, my plan is to LEAVE IT ALONE! 

Nick.

---

