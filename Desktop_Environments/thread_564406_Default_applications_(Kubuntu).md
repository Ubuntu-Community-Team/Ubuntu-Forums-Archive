---
title: "Default applications (Kubuntu)"
date: 2007-10-01
forum: Desktop Environments
---

### Post by VSpike on 2007-10-01
I get some strange behaviour around default applications.

In KControl, I've set thunderbird to be the default mail applicaiton, and yet everything (GNOME or KDE) opens KMail instead.

Also, I get different defaults for various file types for KDE apps and GNOME apps in KDE.  This is particularly irritation for Thunderbird and Firefox (two apps which I use pretty much all the time) which both choose to open everything with different handlers to KDE apps.  

To make matters worse, you then find that for example the GNOME zip file handler which Thunderbird opens starts Nautilus to view the unpacked files.

All in all, it's a right dog's breakfast.  Is this normal, expected behaviour that I have to live with, or is something misconfigured here?

Thanks in advance,

John

---

### Post by kellemes on 2007-10-01
I guess you're using KDE on Ubuntu? I can imagine that's where the defaults come from.

In Thunderbird and Firefox you need to change the filetype-association yourself I'm afraid..
Both apps. also have an option to check if they're the default application on the system, it's somewhere in the preferences-dialog..

You can do also use kcontrol to set the filetype-associastion systemwide..

---

### Post by VSpike on 2007-10-01
Hi Kellemes, thanks for the reply.

I am using KDE on Kubuntu as you rightly say, and for KDE apps they seems to pick up the defaults no problem, apart from the mail client.

I checked in Thunderbird, and Thunderbird thinks that it is the default mail client.  As I said, I've also configured Thunderbird as the default in the "Default Applications" section of KControl.  KDE apps honour this, but Openoffice and Firefox among others do not.

I checked the "Edit -> Preferences -> Content -> File Types -> Manage" section in Firefox, but it doesn't actually list more than a few items, mostly related to in-browser plugins, so it must be picking up the default file handlers from somewhere.  They seem to be the defaults for the GNOME desktop, but is there any way to change these other than to log into GNOME?

---

### Post by kellemes on 2007-10-01
Will this help?
[http://kb.mozillazine.org/Default_mail_client]("http://kb.mozillazine.org/Default_mail_client")

---

### Post by VSpike on 2007-10-01
Thanks, I've now fixed the default email client for Firefox and Open Office too, which is a big improvement.

I'd still like to figure out the other file associations though.

---

