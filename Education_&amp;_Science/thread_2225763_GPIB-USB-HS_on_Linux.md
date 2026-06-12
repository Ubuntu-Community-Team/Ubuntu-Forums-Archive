---
title: "GPIB-USB-HS on Linux"
date: 2014-05-23
forum: Education &amp; Science
---

### Post by Pierre_Guillem on 2014-05-23
Hello,

I've been pulling my hair out for one week trying to connect devices to my PC with a NI_GPIB_USB_HS adapter.
I'm completly new to this but I desperately need to retrieve data from a spectrum analyser and the only way to do this for the moment is to use a flopy disk and an old computer. :(

I think I've installed the needed packages and did my best to configure the gpib.conf file.
The instruction *udevadm monitor --environment* shows that my PC detects the adapter since the ID_MODEL, ID_VENDOR etc. are correct.
The *gpib_config* seems to work too.
Then I do *ibtest*, choose *d* (for device), type *0* (for 0 is the GPIB adress of my device), *w* to write data string, and *IDN?
The answer is :

gpib status is: 
ibsta = 0x8100  < ERR CMPL >
iberr= 2
ENOL 2: No listeners

ibcnt = 0

If I have understood correctly, the NI_GPIB_USB_HS has been detected but not the device that is plugged after.

Does anybody have an idea to help me?
Thanks in advance,

Pierre

---

### Post by chiques on 2014-08-19
We had the same problem. We scrapped Ubuntu from our factory floor and pulled out a Windows machine. It took some time but we were able to get the NI488.2 drivers installed, Visual Studio Express libraries and communicate with the GPIB bus within a 1week. I love Ubuntu but this was a huge disappointment.

---

