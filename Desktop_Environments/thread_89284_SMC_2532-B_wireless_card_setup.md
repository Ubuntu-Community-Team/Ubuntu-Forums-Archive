---
title: "SMC 2532-B wireless card setup"
date: 2005-11-12
forum: Desktop Environments
---

### Post by Zipeh on 2005-11-12
I need some help getting this card to work. I am a Newbie to Linux and don't want to use the NDIS wrapper. I have a Acer Ferrari AMD 64 laptop. It's a Prism 2 based chipset. It will auto configure the card with Auditor Live CD on a P4 laptop but not the Acer.
So I want to get the card setup in my AMD 64 Ubuntu install on my Acer laptop.

I have installedfrom the synaptic package manager:
HoatAP driver & Wlan-ng driver

I know the system can see it because if I use:

cardctl ident
Socket 0:
   product info: "SMC" and the cards full name
   manfid: "what looks to be the manfacture ID in HEX format"
   function: 6 (network)

cardinfo
I get a GUI based popup that read unsupported card

cardctl status
   Socket 0:
   5V 16-bit PC Card
   function: 0 [ready]

I don't seem to have a /var/state/pcmcia/stab or /var/lib/pcmcia/stab directory if this even matters.

Cat /var/run/stab
Socket 0: unsupported card

Any help will be greatly appreciated

Thank You

---

### Post by rgolly on 2006-01-25
Yes, same card, same issues.  Anyone have a link or a previous thread I can be pointed to?  Primarily need to use the card for wireless assessments using kismet, airodump, and aircrack.  This is the first post that I found referencing the card, so may find something else in my searches...

---

### Post by Zipeh on 2006-01-26
I believe I read somewhere that the next version of Ubuntu "DrapperDrake" was going to have alot more hardware support of PCMCIA devices. It is coming in April this year. I don't know if  is with my system being a AMD baesed system or a chipset issue.

---

