---
title: "Any USB HID Plugins for REALBasic???"
date: 2009-02-02
forum: General Help
---

### Post by Maconvert on 2009-02-02
Hello,

I’m very interested in getting REALBasic for writing cross platform executables (XP, Vista, Mac, Ubuntu).
I design hardware that requires a PC for configuration and data retrieval and I want to be able to cover the greatest amount of customers.
The PC side does not need to be fast or terribly efficient (just stable) so REALBasic fits the bill nicely.
Plus, I have a fair amount of experience with VB so the transition should be pretty easy.
Currently, a company called Monkey Bread Software makes USB HID plugins for Windows and Mac, but not for Linux.
This is frustrating for me because I’m not a super strong PC programmer and it would take forever to write a Linux plugin myself.

My only other options are:

A)
Use an RS232-to-TTL communications chip in my design and then include a USB-to-Serial cable (with a driver CD) with every product.

B) 
Add a USB-to-RS232 chip to my design and then just have the user install the chip manufacturer’s driver on their machines.

With both of these solutions I could just use the COM object in REALBasic, much like I would with VB. However, both of these solutions are inefficient and wasteful because I plan to use microcontrollers that already have USB capability built in so that I don’t need a USB-to-Serial cable or separate communications chips. If I can solve this issue with software then I can save parts on my designs and increase profits.

Anyway, has anybody here written a Linux USB HID plugin for REALBasic that allows them to communicate directly with a USB device?
If so, I’d really appreciate some help here.

Cheers.

---

