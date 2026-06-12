---
title: "System freeze using Intel 3945 wlan card in inspiron1525"
date: 2008-04-05
forum: Dell  Ubuntu Support
---

### Post by Basti83 on 2008-04-05
Hi,

I just got a Inspiron 1525 with Ubuntu preinstalled. Unfortunately the system freezes from time to time. By freeze I mean, that I can't do anything (no mouse cursor moving, no killing of the X-Server, no logging in from somewhere else via SSH). I assume that the built in wlan card is the cause, because the system only freezes under havy wlan network activity (memory is ok, checked it with memtest86).
Are there any known issues with the driver (ipw3945) or do you think that this is a hardware problem?
What would you suggest to do? Installing an alternative driver (iwl3945) or using the ndiswrapper and trying the windows driver?

thanks for your suggestions!
Sebastian

---

### Post by ridgeland on 2008-04-05
Try top.
When the system freezes try to open a terminal and run
$ top
If that is impossible use
[Ctrl]+[Alt]+[F1]
then run top there.  You may have to log in first.
Top will show how busy your processor is and what program is hogging the resources.
In Top try [Shift]+M to sort my Mem column.  Then [Shift]+[<] to sort by the next column to the left (CPU).
What do you find?

Edit: Oh yeah.  To get back to the GUI after going to F1 is [Ctrl]+[Alt]+[F7]

---

### Post by notwen on 2008-04-06
The ipw3945 module is very unstable in Gutsy.  Try using the iwl module and see if this resolves it.  More details can be found on this [page]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues") on Dell's Linux Wiki.  Post back and let us know if this resolves your issue.  =]

---

### Post by Basti83 on 2008-04-06
the iwl3945 module works great! And it was very easy to install too ;-)
Thanks a lot!

---

