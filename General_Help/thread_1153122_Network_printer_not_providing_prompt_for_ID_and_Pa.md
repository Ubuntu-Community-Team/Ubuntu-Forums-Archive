---
title: "Network printer not providing prompt for ID and Password"
date: 2009-05-08
forum: General Help
---

### Post by frabjous on 2009-05-08
Complete newbie ignoramus here. Installed Ubuntu 9.04 yesterday and so far I love it, but haven't decided on it for sure (still dual-booting).

One big problem so far, which will be a deal-breaker if I can't get it solved is the following. I'm trying to set it up to print to my department's Network printer. (I work at a large research University... I could ask the IT people, but I'd guess they'd be clueless with anything Ubuntu related.)

The printer is a Canon IR 4750. I connect to it through a standard TCP/IP port.

In Ubuntu, I can apparently add the printer by going to: 

System > Administration > Printing > New 

It searches for printers.

I can see the Network printer under Select Devices, and it lists the right Host IP, so it must be the right one.... I go through the rest, choosing the driver, etc., and everything seems to be OK in setting it up. The printer now shows up, and I can apparently send it print jobs, and it reports having completed them. 

However, nothing prints.

I suspect this is because the printer requires an ID and password to print to it. E.g., when I print to the same printer from Windows, whenever I send it a print job, a box appears requesting my ID and password, and nothing similar happens here. I can't find anywhere to tell it to prompt me for that. and the option to "Authenticate" any job is never present. 

Is this an Ubuntu issue, or do I need to do something special to my network settings so the printer can "talk back" to me, etc.?

Any help at all would be appreciated.

---

### Post by frabjous on 2009-05-08
Well, after spending over half the day today working on this, and staying an hour late to work, I finally got it to work. I actually (literally) jumped in joy when it worked. Anyway, I thought I'd share just in case anyone else has a similar problem.

First, the advice here helped a lot:
[wiki entry on Canon printers]("https://wiki.ubuntu.com/HardwareSupportComponentsPrintersCanon") -- turns out in order to supporting "accounting credentials" (e.g., user IDs and passwords), you need to use Canon's  proprietary driver rather than the foomatic-db package open package which I had been trying to use. 

You also have to follow the advice here for loosening some restrictions:
[How to #SQue]("http://dalbrizio.googlepages.com/how-to_#sque")

But even then it's not as easy as it would seem. With the proprietary driver, the printer properties has a space for entering the ID and password, but rather than providing a blank you can fill in, it provides a static list of possibilities from a drop down menu. In order to make my ID one of the choices, I had to manually edit the text of the PPD to include it and reinstall the driver.

---

