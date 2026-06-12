---
title: "[WINE] PowerPoint 2007 and OneNote 2007 crash"
date: 2010-11-28
forum: Desktop Environments
---

### Post by The Wish Within on 2010-11-28
Hi.

I have installed Microsoft Office Home and Student 2007 on Linux Ubuntu 10.04
Word and Excel work fine with WINE, but PowerPoint and OneNote crash.
I don't really need OneNote but I'd like PowerPoint to be working.

When I start PowerPoint it asks me if I want to start it in Safe Mode and then for maybe a second or less the yellow splash screen of PowerPoint appears and disappears and nothing happens. What's the problem?
Has anyone got a solution?

Greetings
The Wish Within

---

### Post by Spyderkid on 2010-11-28
Go to Applications > Wine > Configure Wine
and see if you can change settings to do with Applications Graphics and Drivers

But I don't think Wine works great with Office products.

[Check here for some more information on how well Microsoft Office works on Wine]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992")

---

### Post by ronnielsen1 on 2010-11-28
Powerpoint 2007 works fine but . . .
> In order to run Powerpoint 2007, you must set riched20.dll to (native) in winecfg. Note that you do **not **have to copy the dll from a Windows partition or use winetricks to install it. Office 2007 installs its own version of richedit in a private directory, but Wine will not use it unless you set the override.  Do not set the override globally unless you have Office installed in a separate wineprefix.

One Note should work. Make sure of the following

> This program crashes when run in Vista or 7 mode but works ok in XP mode.


---

### Post by The Wish Within on 2010-11-28
I've set riched20.dll to (native) and now PowerPoint works and also OneNote seems to work more or less (there's still an error after closing it but nevermind).

Thanks!

---

### Post by TeeRoy32 on 2011-02-18
hi I've got 10.04 64bit and i used playonlinux with wine 1.2.2 to install ms office 2007 enterprise and everything  installed fine but powerpoint wouldn't open. I found this thread an I did the riched20.dll thing and it still won't load. the ms corefonts are installed so is there any thing i missed

---

### Post by icutler on 2011-03-15
I had the same problem and your fix worked - thank you so much! Just one quick thing - do you have any tips to get Microsoft Office Onenote going?

---

### Post by icutler on 2011-03-15
Actually, after reading another persons reply, I have discovered that Onenote does work - but not only do I get the error message after I close it, but everytime it close it, it just starts up again - without me doing anything! Can you please help with that?

---

