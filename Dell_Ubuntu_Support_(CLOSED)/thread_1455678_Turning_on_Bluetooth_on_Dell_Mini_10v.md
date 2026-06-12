---
title: "Turning on Bluetooth on Dell Mini 10v"
date: 2010-04-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Birion on 2010-04-16
Hi,

I'm having a bit of a trouble with my new netbook. So far, I've managed to get everything working except the bluetooth. The tray icon is greyed out, clicking it shows (something like, I'm retranslating from Czech):

Bluetooth: On  <== this one is greyed out as well
Turn off: Bluetooth
-------------------
Preferences

Clicking preferences brings a window that says that Bluetooth is forbidden and has one HUGE button with "Turn on Bluetooth". Clicking this button does nothing. I tried to look around and apparently, there is a way to get it working... from Windows. Which I don't have (and c'mon, shouldn't Dell just work? What's the point of OEMing Ubuntu if you put Linux-unfriendly hardware in it first?!).

The exact same problem has been annoying me in 8.04, 9.10 and 10.04 Beta 2, and I'd really like to have it work.

EDIT: And, apparently, "Bluetooth: On" is another way of saying "You actually might not have Bluetooth".

---

### Post by Kai Summers on 2010-04-17
Check in your BIOS as in the new Dell BIOS screen you might have to enable your wireless activation button/switch to control the Bluetooth as well as the WiFi. If its the modern BIOS screen then its a Graphical Interface that is pretty easy to use, and should just be a checkbox within the wireless menu selectable somewhere on the left.

Let us know hoe you get on. Hope that helps.

---

### Post by Birion on 2010-04-23
Alright, I'm in the BIOS, looking at the Advanced tab (Main tab only has time&date setup, Security tab has a bunch of passwords, Boot tab is about boot order, and Exit tab is, predictably, saving and exiting).

Boot-time Diagnostic Screen:        [Disabled]
QuickBoot Mode:                     [Enabled]

Intel(R)SpeedStep(TM) Technology:   [Enabled]
On Board Lan Control:               [Enabled]
WLAN Control:                       [Enabled]
BlueTooth:                          [Enabled]
USB BIOS Legacy Support:            [Enabled]
USB Wake Support:                   [Disabled]
Function Key Behavior:              [Function]

I don't think either the diagnostic screen or the USB wake support has anything to do with Bluetooth, though. Otherwise, everything else is enabled.

---

### Post by blur xc on 2010-04-24
I have the same problem...  also looking for answers.

Thanks,
BM

---

### Post by winjeel on 2010-04-25
I hate to ask, but does your Mini 10v have the bluetooth hardware? Are you using the Dell Ubuntu 8.10LTS?

---

### Post by Birion on 2010-04-25
I'm currently on 10.04 UNR RC, but the exact same problem was already on the Dell 8.04.1 preinstalled.

And as for having Bluetooth, that's a bit of a problem. The manual claims that it has something like (again, translated from Czech):

Wireless network adapter   internal WLAN (half size of Mini-Card) with WiFi bgn, wireless category Bluetooth(r)

The page of the e-shop I bought it from is silent about Bluetooth.

And the paper I got with it (with warranty and such) claims that it has Bluetooth on one side (the actual warranty) and that it doesn't on the other side (which seems to be just for internal expedition or something).

So, in conclusion, I have absolutely no idea whether or not it has Bluetooth.

---

### Post by blur xc on 2010-04-26
> **Birion said:**
> I'm currently on 10.04 UNR RC, but the exact same problem was already on the Dell 8.04.1 preinstalled.

And as for having Bluetooth, that's a bit of a problem. The manual claims that it has something like (again, translated from Czech):

Wireless network adapter   internal WLAN (half size of Mini-Card) with WiFi bgn, wireless category Bluetooth(r)

The page of the e-shop I bought it from is silent about Bluetooth.

And the paper I got with it (with warranty and such) claims that it has Bluetooth on one side (the actual warranty) and that it doesn't on the other side (which seems to be just for internal expedition or something).

So, in conclusion, I have absolutely no idea whether or not it has Bluetooth.

Me neither, and I don't know how to check if it does...maybe I can dig up the owner's manual...

If I have to buy a bluetooth dongle, I'll buy one.  They aren't that much ($15 usd on newegg when on sale).

Thanks,
BM

---

### Post by gfe on 2010-04-28
I never could get Bluetooth working on the same model, so for under $5 including postage I bought a generic USB mini-dongle via eBay. It works like a charm, and I got one that's tiny enough that if I want I can just leave it attached to the side of the computer. It's about as good of a solution as I could have hoped for.

---

