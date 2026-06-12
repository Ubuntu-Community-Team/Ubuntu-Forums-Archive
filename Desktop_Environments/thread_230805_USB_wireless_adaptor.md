---
title: "USB wireless adaptor"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Forko on 2006-08-06
I have a Peak USB wireless adaptor, will i be able to get a driver for it for Linux? I need it for connecting to the net and i have not yet installed Ubuntu, and if i can't install my USB adaptor then i can't use Linux. Thanks

---

### Post by x64Jimbo on 2006-08-06
You'll need to find out what chipset the adapter has. Do a google search for the model number of the adapter along with the word "chipset."
Once you know, post back here and I can tell you if the chipset is supported natively with a Linux driver or if you'll have to use NDISWrapper to get the Windows driver working in Linux. 
You could just download the LiveCD and boot that, and if the interface works, you would have saved yourself the trouble of all the research and stuff. I know for a fact that a lot of wireless interfaces will work with Ubuntu right out of the box.

---

### Post by chocbar31 on 2006-08-06
Here is a good place to start.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

You can install NdisWrapper using Synaptic. Also, use the search feature to do some searches here for your wireless device and on NdisWrapper.

:D

---

### Post by Forko on 2006-08-06
I have run the liveCD and the adapter doesn't work. I will try searching for the chipset and see if i can get a driver, but i have already went on the official website of the USb adapter and they don't do a Linux driver. Cheers

---

### Post by Forko on 2006-08-06
I searched and i couldn't find it. It is a PEAK WUG2200 Wireless LAN USB Adapter. How would i be able to get a driver for Linux?

Edit: I found this on the link and the only Peak thing i found was 

Card: Peak Hardware 802.11g Wireless 54Mbps Cardbus Adapter

    * Chipset: Texas Instruments | Subsystem: Abocom Systems
    * pciid: 104c:9066
    * Driver: Peak Hardware Distributed Windows Driver: [http://www.peakhardware.com/support/downloads.aspx](http://www.peakhardware.com/support/downloads.aspx), works fine - up to 54Mbps.
    * Other: WEP works. Also works with iwlist and airsnort. No support with Kismet as yet (21/10/04) 

Should i install Linux and then install the normal Windows driver  ?

---

### Post by x64Jimbo on 2006-08-07
Definitely. Make sure to check out this wiki article about NDISWrapper too - It'll help you a lot:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Forko on 2006-08-07
I am going to install Ubuntu on my computer later, but i have a problem with my other computer. It is a HP a409.uk and it won't run the liveCD at all. I want to try Ubuntu on this computer off of the 
LiveCD, but it won't run. I tryed going into the boot options menu and setting it up so that it would only boot from the CD drive, and when the Ubuntu page comes up and it says press the enter key to boot i press it, and then it just restarts and goes back to that page after booting up again. Any ideas how i can get it to work?

---

### Post by x64Jimbo on 2006-08-07
Try booting with acpi and apic turned off. Have a look at the boot options that the LiveCD offers you when you boot.

---

### Post by Forko on 2006-08-09
Thanks mate, i turned acpi off an it worked. For anyone with the same problem type this on the boot screen:

live acpi=off

It worked for me, so trying it can't hurt.

---

### Post by Forko on 2006-08-09
I have taken the plunge and finally installed it on my computer. I just have to find a driver for my M-audio Jamlab. I can't seem to find one, but i will try and see if i can install the windows driver (don't know how to do it yet, but i will work it out eventually) and see if it works. Cheers for the help mate.

---

