---
title: "Unable to logon to main user in LightDM after changing graphics drivers"
date: 2011-10-26
forum: Desktop Environments
---

### Post by unobtruse on 2011-10-26
Hi All. I've found a few similar threads, but nothing quite like my own. I'll try to be as specific as possible:

After installing proprietary drivers from ATIs website to replace the proprietary drivers I had installed from the "Additional Drivers" menu, I was unable to login at all after rebooting. After searching a few forums I changed the xorg.conf "Driver" entry in the "Device" section from "fglrx" to "radeon". 

This solved my initial problem... I could now login. This is when the actual problem started: I decided to try to remove the proprietary drivers completely and get "full" support from the ATI open source drivers. After following some commands on forums and rebooting, I was able to reach lighDM, but not able to login! After entering my password it would briefly switch to a black screen and then return to lightDM, once again requesting a password. I was able to login from the terminal using Ctrl-Alt-F1. Tried to get help, but to no avail... I managed to create a new user account (using the Ctrl-Alt-F1 terminal) from which I am able to login, but I still can't login to my main account using lightDM!?

Please help. It would be much appreciated.

(Running Ubuntu 11.10 on a Toshiba Satellite notebook.)

---

### Post by W00ster on 2011-10-27
I have a similar issue with a non discrete graphics card, the 5770HD and opened a new thread earlier today.
[http://ubuntuforums.org/showthread.php?t=1870231](http://ubuntuforums.org/showthread.php?t=1870231)

When I boot normally, I get a blank screen and can't even switch to the text based consoles.
If I go into the grub menu at boot time, select recovery console, then wait for the menu to appear and select Resume normal boot, it works like a charm.

---

### Post by unobtruse on 2011-10-27
Thanks W00ster, I'll check it out.

---

### Post by unobtruse on 2011-10-27
I managed to fix my problem by removing the ```
/home/username/.Xauthorization
``` configuration file (where *username* is my account username). Clearly X got caught up in something in between all the changes I recklessly made.

---

