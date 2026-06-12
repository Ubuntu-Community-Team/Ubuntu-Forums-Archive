---
title: "Dell M1330 wireless issues"
date: 2009-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tim bit on 2009-05-02
Hi everyone,

I recently purchased a Dell M1330 and installed Ubuntu for the first time.  It's working fairly well, but (surprise) the wireless isn't working.  The relevant specs are:

- Core 2 Duo
- Dell Wireless 1505 Mini-Card (which uses the Broadcom 4328 rev. 03)
- Ubuntu 9.04

Here is what I've tried so far:

1.  The following [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") that uses ndiswrapper.
Following the steps, I never managed to get "module=ndiswrapper".  Further, wireless does not appear in my network connections.
I have tried both the driver files provided and the latest from the Dell website for my laptop.

2.  I have used synaptic package manager to get a gtk application for adding drivers using ndiswrapper.  When I add them using this application, I get an error saying that the hardware could not be found, even though within the application it says that it is.

3. Activating the driver using System->Administration->Hardware Drivers
When I first entered this page, the driver had a grey circle next to it.  Even after activating the driver, the grey circle remained.
Despite the above, wireless appears to be working, and I can see other networks, but I can't connect to my network that uses WPA.  Further, when I reboot my machine, I need to activate the driver again.

Any help and pointers would be greatly appreciated!

Thank you,

Tim

---

### Post by csowm5je on 2009-05-03
System -> Administration -> Hareware driver
Deactivate and Activate the Broadcom driver and restart

Sorry, after posting this, I notice that you have already tried this
but mine worked just doing this.
Right click on the network manager, edit connection and add a wirless

---

### Post by tim bit on 2009-05-03
Oddly, it has started working.  I'm not sure exactly what I did.  I didn't setup anything through ndiswrapper.  However, now when I enter Hardware Drivers, the network card is active....

---

### Post by roachman5000 on 2009-05-06
Hi.  I have had a similar problem with my wireless drivers.  It has not been working for the past 24 hours after performing a partial upgrade.  The first thing I noticed (besides not having any wireless connection) is that the wifi indicator light above the keyboard was not on, so I checked *System > Administration > Hardware Drivers*.  It was then that I noticed that the Broadcom driver was no longer there.  In fact, there aren't any drivers displayed at all.  Does anyone know how to fix this?  Thanks in advance!!!

---

