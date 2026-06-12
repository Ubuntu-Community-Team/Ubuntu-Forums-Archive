---
title: "No printer"
date: 2005-11-30
forum: Desktop Environments
---

### Post by rafeg on 2005-11-30
HI,  Can anyone help a total newbie please.  Iv'e just installed 
       Breezy and it has failed to detect my printer.  Have tried print 
       manager setup but the printer is not listed, (it's a Brother HL-2040
       laser).  Tried to install a driver for the 2060 model but nothing 
       happens.  I had Hoary installed previously and the printer was 
       detected but did not work.  I decided  to wait for Breezy, expecting
      to get better results, but no luck.  Any ideas would be most welcome.

---

### Post by discord on 2005-12-02
okay is the printer usb? if it is or isnt first goto a terminal and type dmesg. look for a field labeled printer and look for a device name. for example mine is listed as /dev/usb001 or something like that. then in the system->administration->printing choose the appropriate device which you got from the dmesg output. choose your driver and print a test page. If it doesnt work google for your printer name and linux and see if you find any information about it being supported in linux.. good luck

-C

---

### Post by rafeg on 2005-12-16
Thanks for your reply. Sorry not to have said so sooner but I couldn't 
find my thread!  As I said, I'm a complete newbie to this lark and even 
using the forums is foxing me a bit.  I'll try what you say and see what happens.

---

### Post by rafeg on 2005-12-17
Have tried your suggestion but no luck.  dmesg does not show any printers at all!  My printer
(Brother HL-2040) is a parallel type and is listed on the  Brother web site as supported under
Linux with drivers available for download.  Here I get stuck as I tried downloading them but am not
sure how to proceed with installing.  incidentally, when I installed Ubuntu from the CD my printer
was switched off.  does this make any difference?  May be a dumb question.  If so please  forrgive
me for being too used to windows where dumbness doesn't matter!!

---

### Post by rafeg on 2005-12-18
Following up on my last post, I have just done a complete re-install on a second
hard drive with my printer turned on.  Success!  Ubuntu detected it and has printed
the usual test page.  Top margin is too small but I guess I can find an answer to that.
I'm still not sure whether this was the right way to install but it may help someone else.

---

