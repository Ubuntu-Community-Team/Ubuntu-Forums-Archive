---
title: "Evolution/OWA/Exchange-How I got it to work"
date: 2006-06-28
forum: Desktop Environments
---

### Post by ledonnell on 2006-06-28
A friend in the office (Gentoo user) figured out what is wrong with the current Evolutions and Exchange Connector.  He has submitted some code for a change and we will see if it takes effect.  I have not been able to connect for a LONG time now and I am pleased to say he walked me through how to get it working:

1.  Don't use the menu options for Evolution.

2. Open Gnome-Terminal (or Konsole if you are a heathen) and type: ximian-connector-setup-2.6.  Walk through your setup and let it close.

3.  Open Evolution and ignore the errors.  Go to Edit>Preferences>Accounts.  Edit your accounts.  Where the retarded Evolution bug has re-written your https to http change it BACK to https
*****************IMPORTANT******************
DO NOT click authenticate.  If you click authenticate it will rewrite your https settings again.
Just click ok.
Restart evolution.
You may have to tweak a few settings to your liking.

This has worked like a charm for all of us in the office and from my home connecting in.

Cheers.

---

### Post by MattToner on 2006-06-28
i have tried this but it is asking me for a GC Server, i have contacted my Email service provider but they said the servers dont use this... what can i do?

---

### Post by ledonnell on 2006-06-28
[QUOTE=MattToner]i have tried this but it is asking me for a GC Server, i have contacted my Email service provider but they said the servers dont use this... what can i do?[/QUOTE]
_________________________________________

Well.
if your email provider is your ISP I would be really surprised if they used Exchange.  They probably wouldn't use GC (calendar for shared calendars) either.  You could probably go with POP setups in Evolution.

---

### Post by MattToner on 2006-07-01
hi,

no my email is provided by Fasthosts.co.uk.

it is a full exchange mailbox.

---

### Post by ledonnell on 2006-07-01
Well they could have multiple servers.  My job has one for the GC one for mail.
You may have to ask your Mail Admin what it is.

---

### Post by infrasup on 2008-03-29
is worked for me on Redhat 5 and evolution to a 
Windows 2003 SBS Exchange server

OWA URL:

[COLOR="Blue"]https://svr-01.mycompany.london/exchange[/COLOR]

---

