---
title: "HP J6480 Problems"
date: 2009-01-18
forum: General Help
---

### Post by ergjoop3 on 2009-01-18
Hi

I have tried setting up an HP OfficeJet J6480 with Ubuntu 8.10 using USB and then networking.

The printer inexplicably stops printing after 9 pages. The 9th page gets stuck in the duplexer and does not print. The only way to get the printer back up again is to remove its power supply.

I have HPLip 2.8.7 installed. I tried to update it but I get the error message
error: Configure failed with error: pthread-devel not found
when running the auto-installer for HPLip 2.8.12.

I tried to go through the manual setup, but I get the error
configure: error: cannot find libpthread support

I looked in synaptic and I have all libpthread apps installed.

How do I resolve these issues?

Thanks.

---

### Post by steveneddy on 2009-02-04
I have this same printer in my SOHO and I am not experiencing this issue.

Mine is set up to run from the network and sets up in less than 1 minute.

Print, scan, copy and fax - what more could an office geek ask for in one device?

I do wish it had a phone cradle, though.

EDIT:

I'm downloading the latest version of HPLIP. I addresses this printer specifically.

This really is a very nice printer.

---

### Post by chimiasanchi on 2009-07-13
upgrading HPLIP also remedied my problem. My HP J6480 was not printing the bottom cm or so of documents. Update your with the nice script that hp provides here:

[http://hplipopensource.com/hplip-web/install/install/index.html]("http://hplipopensource.com/hplip-web/install/install/index.html")

hp printers are still my favorite (thanks to the awesome Linux support).

---

### Post by renihanc on 2009-07-28
installed new lib for Hp j6480 but it still say j6400 series is this the same driver ???? I dl off the hp site and it installed ok. Just wanna make sure I have latest driver.

Thanks

---

### Post by Malvolio on 2010-03-04
Sigh, I'm having the same problem as the starting post and I did install the latest HPLIP, according to the instructions on the HP web site.  It stops at page 16, even in a two-page print of 15-16.  This is aggravating as all hell as I've followed every suggestion I can find.  Something about page 16 makes the printer freeze up. >,<

Append: Okay, correction, as soon as it goes to duplex it freezes. Strangely, it printed 7 duplex pages just fine beforehand so I don't get what's happened.  If left to it's own devices it eventually cancels the print job and then freezes at that, shutting it down afterwards takes several minutes if I don't intervene.

Extra Append: Looking at the printer list the printer shows "usr/lib/cups/backend/hp failed".  Wish I knew more about Linux.

Every Extra Append: Okay, with some back and forth with my much more knowledgeable friend we've done some things and now I can't select double-sided printing at all.  The options are selected in Printer Properties but in the actual printing dialogue it only gives me one-sided.  This is getting rather aggravating to say the least.  Or rather, only Firefox can print double-sided.

---

