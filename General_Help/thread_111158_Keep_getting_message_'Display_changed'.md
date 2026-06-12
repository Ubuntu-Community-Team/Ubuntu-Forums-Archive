---
title: "Keep getting message 'Display changed'"
date: 2006-01-01
forum: General Help
---

### Post by taseal on 2006-01-01
I keep getting the message 'Display changed: LCD on/off' message on my laptop's screen... comes up randomly about every min... kinda realll annoying...

any cure out there?

thx!

---

### Post by andrewpay on 2006-03-14
I periodically get an annoying flashing screen "Display Changed LCD on/off".

Yes I have had this problem before and after upgrading KDE I have it again

I found your message while trying to fix it again

I am led to believe that this is a bug in the Asus ACPI driver.

This is what I am going to do.  I cannot confirm that it works as I have not restarted KDE yet.

Disable kmilo, which is a daemon run by kded to support the special keys on the keyboard (browser launch, etc).
While these keys work under Gnome, they do not work under KDE.

sudo nano /usr/share/services/kded/kmilod.desktop
Changing the following lines to false:

X-KDE-Kded-autoload=false
X-KDE-Kded-load-on-demand=false

You need to restart KDE after making this change.

---

### Post by Jasman on 2006-05-16
Is any work being done to get those hotkeys working under KDE, and can applying a patch to asus_acpi solve the problem? Thanks.

---

