---
title: "Network settings for Dialout"
date: 2006-03-11
forum: Desktop Environments
---

### Post by Jumpy on 2006-03-11
Hi again
this is another problem that I have created whilst trying to connect to my ISP with an external D-Link modem.
This did used to load up but never worked. now I get the followng message when I try to access the activate.
administration/networking/network settings/modem connect.
Activate causes an error box to show up with the following message
"Could not enable the interface ppp0 check settings are correct for this network and that computer is correctly connected to it."

Well I know the computer is correct OK, but how and where do I check for correct settings.
Many thanks in advance for any suggestions.
Jumpy

---

### Post by eriefisher on 2006-03-11
Is this a usb or serial modem?
Usb modem are still softmodems and need special attention.
Have you entered the connection info under properties?
You must also tell it where your modem is connected(ttyS0 etc).
If it's a serial modem it should just work with the right info entered.

eriefisher

---

### Post by Jumpy on 2006-03-11
Thanks for reply
This is a serial Modem
Yes I have entered all connection info and yes the ttyS0 is correct.
I can reach the modem with wvdial but not the otherway.
It is something I have done with the program I think.
I just need to know how to reset it.
In some things with Linux if you remove a  .  file it will recreate the correct info and reset it next time you use it.
(not sure if it can be done with this application???)
Thanks again
Jumpy

---

