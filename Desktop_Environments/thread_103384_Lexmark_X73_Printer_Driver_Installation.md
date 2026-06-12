---
title: "Lexmark X73 Printer Driver Installation"
date: 2005-12-14
forum: Desktop Environments
---

### Post by imortlco on 2005-12-14
Hi!

I am a total newbie looking for info on how to install the driver for my
Lexmark X73 printer that is ALREADY in Ubuntu.

I go through the wizard, it finds my printer, it lists a driver for me, I click
on it, apply, and it tells me can't do something or other---PPD.  Sorry, I
can't recall exactly what it says.  It then makes my printer the default and
says it's ready.  I go to do a test page and nothing happens.

Learning about Linux as much as I am, I figure I have to "command line" it to
work, find the driver, use it or something.  Right or wrong?

Help!!!

THANKS!!!

BOB

---

### Post by amohanty on 2005-12-14
PPD files are postscript printer drivers. More info here:
[http://www.postscript.org/FAQs/language/node22.html](http://www.postscript.org/FAQs/language/node22.html)

Basically you need one of those in the right place in your box for the driver to work. The PPD files for the Lexmark are in:
> /usr/share/ppd/Lexmark 
called
> Lexmark-X73-drv_z42.ppd.gz

Since the files are present the problem is elsewhere. Can you post the exact error?

Edit: Given the number of times I have been beaten... this is a treat :)

---

### Post by RAOF on 2005-12-14
You really will need to be more precise.
> I click on it, apply, and it tells me can't do something or other---PPD. Sorry, I
can't recall exactly what it says. It then makes my printer the default and
says it's ready. I go to do a test page and nothing happens.
This is where your problem is (as you say, the driver is already there), and if we don't know what the problem actually is, we can't fix it ;)

Could you please try that again and get the actual error message?

Edit: Whoops, beaten to the punch ;)

---

### Post by imortlco on 2005-12-14
My apologies.  I am not at home right now, but I WILL get the exact error message and post it tomorrow.

THANKS!!!

BOB

---

### Post by imortlco on 2005-12-17
Hi!

OK, here is the error message I'm getting:

MISSING ASTERISK IN COLUMN 1 AT 1:'/USR/SHARE/PPD/LEXMARK/LEXMARK-X73-DRV_Z42.PPD.GZ'

This pops up after I have seemingly installed the printer.  Ubuntu finds it and identifies it as an X73.  I go through the properties of my printer, (which by the way, shows READY underneath the icon in the printers folder), and see the driver in the menu.  I click on install and then this error window pops up every time.  A test page does not print either too by the way.  Nothing happens:  No windows, errors etc.

THANKS for any help with this, as I have just fully installed Ubuntu on my system and have been playing with it and configuring it since ten this morning and I LOVE IT SO FAR!!!  Very nice, fast, smooth, efficient, and so on.  I have been a BIG Windows person for a long time, and am even a Microsoft Certified Systems Engineer, but I AM SWITCHING!!!

If I may, I have one other minor problem I can't seem to work through yet:  When I try and access my floppy drive with a floppy in it, I get this error every time:  

Unable to mount the selected volume.  AND  Error: given UDI is not a mountable volume


THANKS A BUNCH TO ALL OF YOU!!!

Sincerely,
BOB

---

### Post by amohanty on 2005-12-17
Try this:

> cupstestppd  /usr/share/ppd/Lexmark/Lexmark-X73-drv_z42.ppd.gz

This is a wizard that should help you fix any errors in the file.

HTH
AM

---

### Post by imortlco on 2005-12-18
Ok, here is the result of the wizard IMMEDIATELY after typing it into a terminal and hitting enter:

/usr/share/ppd/Lexmark/Lexmark-X73-drv_z42.ppd.gz: PASS

I then tried a test page and nothing happened still.

I then went into the printer properties and tried to install the driver and got the same message as previously posted:  'Missing asterisk in column 1...

BOB

---

### Post by amohanty on 2005-12-18
Take a look at this forum thread:
[http://ubuntuforums.org/showpost.php?p=136297&postcount=4](http://ubuntuforums.org/showpost.php?p=136297&postcount=4)

---

### Post by imortlco on 2005-12-19
Thanks for the link/thread, but it doesn't work for me either.  The thread is referring to drivers for Red Hat and a different Lexmark.

I did a search on the Lexmark site though, as a result of the thread, for my printer and Linux drivers for it, but they do not list any.

I guess what I'm not understanding is WHY I can't access the driver for my printer that is already WITHIN Ubuntu???  I mean, it comes up in the list, is there, and so on.  I'm just not following why I can't get it installed, extracted or whatever.

Does this mean I can't use my X73 with Ubuntu then?  For this release anyway?  Maybe the next one?

Thanks.

BOB

---

### Post by amohanty on 2005-12-19
That is something interesting, because theoretically, if the ppd file is valid and is in the right place your printer shoudl work properly. 
Maybe you coud repost with something like: Lexmark X73 detected, but non-functional and hopefully a printing guru can help you out.

---

### Post by imortlco on 2005-12-19
THANKS!!!  I will take your advice and repost and see what happens.  

I REALLY want to stick with Ubuntu if I can, because I am REALLY liking it, so if I can get my printer going, then it's done.

THANKS AGAIN!!!

BOB

---

