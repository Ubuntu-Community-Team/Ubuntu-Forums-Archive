---
title: "Printing from OS X Client with CUPS"
date: 2006-03-08
forum: Desktop Environments
---

### Post by schnarff on 2006-03-08
So after much poking around this forum, I've got CUPS set up to use my HP LaserJet 1150 as a network printer under Breezy Badger (theoretically, anyway). If I hit [http://192.168.1.80:631/printers/LaserJet-1150](http://192.168.1.80:631/printers/LaserJet-1150) from my OS X client, the web interface pops right up, and I can print a test page from there no problem.

After getting this going, I decided to add the printer in OS X's System Preferences/Printers area. If I tell it that I'm adding an Internet Printer (IPP), give it the IP of my CUPS box, and go, it adds no problem. I can even print -- it's just that I get a page that reads:

```
%!PS-Adobe-3.0 %RBINumCopies:1 %%Pages: (atend)...
```

and then blank pages until I cancel the job via the printer.

Given that OS X does not have the LaserJet 1150 in its list of HP printers, my first thought is that this is a driver issue (though oddly enough, if I plug the printer in directly to the OS X system via USB, it sees the model and prints perfectly). However, I'm concerned that I may have CUPS set up incorrectly, or some other disaster on the Ubuntu end, since Linux is notoriously bad at printing.

That said, here is my cupsd.conf:

```
DefaultCharset notused
LogLevel debug
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

```

I don't see anything in there that would cause a problem, but then again, I don't know CUPS. Any ideas on how I can get this working?

Thanks,
Alex Kirk

---

### Post by WelterPelter on 2006-03-08
I have a powerbook for working, and I always need to print to my ubuntu box's HP. I tried to get this working through CUPS, and ran into exactly the kind of niggling weirdness you are experiencing. It always seemed just about to work, but I could never ring the bell. 

Eventually, however, I needed to *actually print something*, so I set it up in Samba and it worked after some fiddling (because you need 3.0.21 to play well with OSX). That is repugnant to me -- I don't know why I have to bring a Windows thing into the picture. I mean, these are two *nix machines, right? But that is how I did it.

---

