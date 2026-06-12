---
title: "Shotwell publish photos to Facebook and Google plus/Picasa?"
date: 2012-11-09
forum: Desktop Environments
---

### Post by kolslorr on 2012-11-09
Hello, 

I was able to use Shotwell and easily publish photos to Facebook and Google plus using ubuntu unity or gnome shell... But after switching to a pure xubuntu 12.10 environment, the Facebook and Google plus options are missing and can't be added anymore... 

Anyone know why? And how to solve this?

---

### Post by eric-yorba on 2012-11-12
So the deal is that Canonical has patched Shotwell 0.13 to use Ubuntu Online Accounts.  If Xubuntu doesn't ship with the control panel for Ubuntu Online Accounts, then you won't be able to log in to Google, Facebook, etc in Shotwell or many other apps.

If this is indeed a missing feature in Xubuntu, you should ticket it with their bug tracker so it gets resolved.

The easiest interim solution is to remove the Shotwell package and build it from source yourself.  Info on doing this is here:
[http://yorba.org/shotwell/install.html](http://yorba.org/shotwell/install.html)

---

### Post by TiberiusT on 2013-01-07
Good grief! Tks Eric. 12.10 x64 Xubuntu here. Shotwell from repo.

I clicked publish in Shotwell to send another album to Picasa/G+ just now and got a kind of slimmed down XFCE settings page with only an Ubuntu One option. Clicking the Ubuntu One option just gave me my Ubuntu one program opening page....

They don't seemed to have patched it very well - the edit/preferences/plugins/publishing options still showed the usual Shotwell upload options - except they don't work. That makes Shotwell look buggy and crappo - which it isn't at all.

I call that 'Crapware' and very annoying since Shotwell's publishing was/is a great feature. Anyway, I followed your link and installed the PPA - it replaced 13.1 with...erm 13.1...but I have my publishing options back.

WTH???!!!!  Tks again - I didn't realise Canonical had started doing this sort of thing. I'll be on my guard from now on.

T

---

