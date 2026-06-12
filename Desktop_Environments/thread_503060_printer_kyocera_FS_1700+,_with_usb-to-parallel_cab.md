---
title: "printer kyocera FS 1700+, with usb-to-parallel cable on ubuntu 704"
date: 2007-07-17
forum: Desktop Environments
---

### Post by eeos support on 2007-07-17
Dear friends

ubuntu 704 here (kubuntu flavour).

I have a problem with a laser printer kyocera FS-1700+. I connect it to the laptop with a usb - to - parallel cable (usb on laptop side, parallel on printer side of course!:)).

I configure it easily on cups, using the recommended drivers and settings.

Unfortunately, the printer does not work: when you send a document to the printer, even the test page, you can see it with lpstat or print manager, but then it disappears from the queue without being printed. No error is shown. The printer receives it on the port because the display flashes accordingly and shows all the appropriate text messages.

Printer works fine with same configuration when laptop is booted in MS Viruses XP.

I tried all the available drivers for the same printer, but no luck. could it be that the system has a problem in managing the usb-to-parallel cable?

Any clue? Help!

---

### Post by Lord.Quicksilver on 2007-07-25
Hi, I think Kyocera support for ubuntu 7.04 is all but perfect at the moment: I have tried to install a network FS-1700+ and it doesn't work.
I easily installed it, it took me no more than 2 minute, but nonetheless it's unable even to print the test page: it only prints some useless stuff that sounds like:
<</Duplex false>>setpagedevice %!PS-Adobe-3.0 %%Title: PPR Test Page %%D
Any other print job I've tried didn't print anything at all... I'm already surfing the Web in search for a good installation guide for Kyocera: should I find it I'll post it in this forum on a new thread.

---

### Post by Lord.Quicksilver on 2007-07-25
Well I guess a new thread will take me some time, so meanwhile I can tell you that I surfed kyocera's website and downloaded a new driver, and now it works fine. Dunno if you already tried it, anyway:

[http://www.kyoceramita.it/index/assistenza___supporto/download_center.html?initial=false&search=any&searchTerm=fs-1700+&category=](http://www.kyoceramita.it/index/assistenza___supporto/download_center.html?initial=false&search=any&searchTerm=fs-1700+&category=)

The page is in Italian, anyway you only have to find the Linux section and download the driver, which is in English too. Or you can try find it on kyocera's U.S. website, which is :

[http://usa.kyoceramita.com](http://usa.kyoceramita.com)

Unzip it in a directory.
Then you go to printer options, select the "Drivers" tab and select "Normal" driver instead of "Postcript (recommended)" one, then you click on "Install driver" and select the directory where you unzipped the driver. Now you should have two labels saying "Normal" in the driver select, try the second one (should it not work, try the first one :-D).
Now you should print fine.

This worked  for me, at least.

---

