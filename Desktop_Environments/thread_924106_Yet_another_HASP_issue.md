---
title: "Yet another HASP issue"
date: 2008-09-19
forum: Desktop Environments
---

### Post by igorashu on 2008-09-19
I've installed a Windoze app under Wine. There were no problems, but the app is protected with an Aladdin HASP HL key.
I have installed Aladdin's HSP SRM for Linux 3.50, everything went smooth - aksusbd, winehasp, hasplmd are all running by default.

However, the SRM Admin Control Center (web-based) doesn't list the key:
[ATTACH]100125[/ATTACH]

lshw -businfo shows:
 usb@3:1                       generic        HASP HL 2.16

lsusb shows:
Bus 003 Device 007: ID 0529:0001 Aladdin Knowledge Systems HASP v0.06

How can I get the key to be recognized by the SRM Admin Control Center so that it might be recognized under Wine?

Thanks

---

### Post by BigJules on 2009-01-03
If its any consolation, Igorashu, I also had a Windoze app needing HASP. As well, I downloaded and ran your Aladdin SRM with identical results - except that the SRM Admin Control centre did come up ok, saying that the dongle was alive and well in Linux (huge breakthrough!). 

The daemons all run, the USB dongle light came on and so forth so full of joy I installed the Windoze - to be met with the usual 'dongle not recognised' etc So at least we're to the point where a dongle can function in Linux. And the program installing, I guess its now only a Wine driver problem. 

Ah me. :(

---

### Post by igorashu on 2009-01-04
Well, I have finally succeeded in making the dongle work in Linux.
Turns out that the firmware of the dongle needs to be updated (only a Windows app can do that though - thanks Aladdin) and I had to do the following:
1. In /etc/fstab, enter none /proc/bus/usb usbfs defaults 0 0. 
2. Mount /proc/bus/usb. The file /proc/bus/usb/devices is displayed. 
3. Stop the daemon and the HASP License Manager using /etc/init.d/aksusbd stop. 
4. Restart the daemon and the HASP License Manager using /etc/init.d/aksusbd start. 

Now it is only a Wine driver problem as you said.

---

### Post by chronographer on 2009-01-16
I would like to do the same, using a hasp aladdin dongle, but I'm not going to try till I'm sure it will work... as an aside...anyone managed to emulate a dongle? (The whole dump usb key contents, create hardware emulator thingy???)

Oh another thing... you can pass t he HASP thing through to Virtualbox and run the XP app in the virtual machine... works fine, easy to do.

---

### Post by igorashu on 2009-01-17
> **chronographer said:**
> as an aside...anyone managed to emulate a dongle? (The whole dump usb key contents, create hardware emulator thingy???)
That would kinda defeat the purpose of an usb key, wouldn't it? :)
I mean everybody could use the same virtual key and that would leave the apps unprotected.

LE: apparently you can do that. See [here]("http://www.dongleservice.com/emulate-hasp.phtml"). Hmmm...

---

### Post by chronographer on 2009-01-17
I have checked out that link, but it requires payment. I would prefer an 'open' solution! I think it is arguably fair use, I am using a dongle from my university and really, really don't want to lose it! So if I can back it up it means I can legitimately use it right?

---

### Post by cplusguy on 2009-02-25
Did anyone ever use a driverless dongle UniKey from SecuTech, it seemed the driverless can reduce the problem of DONGLE CON NOT FOUND.

---

### Post by bartverm on 2010-07-05
I just managed to run the Alladin HASP daemon without errors but first I had to recompile my ubuntu kernel with usbfs enabled to get the thing working.

---

### Post by BigJules on 2010-10-18
Good for you! Does this mean you're now able to run your app under Ubuntu? Using Wine? If so, this counts as some sort of breakthrough and I wanna hear more!

---

### Post by FLORIBUNTU on 2010-11-08
> **igorashu said:**
> Well, I have finally succeeded in making the dongle work in Linux.
Turns out that the firmware of the dongle needs to be updated (only a Windows app can do that though - thanks Aladdin) and I had to do the following:
1. In /etc/fstab, enter none /proc/bus/usb usbfs defaults 0 0. 
2. Mount /proc/bus/usb. The file /proc/bus/usb/devices is displayed. 
3. Stop the daemon and the HASP License Manager using /etc/init.d/aksusbd stop. 
4. Restart the daemon and the HASP License Manager using /etc/init.d/aksusbd start. 

Now it is only a Wine driver problem as you said.

Hi igorashu, I m using a dongle with same ref. displayed. Just wondering is you are talking about windev (XI) I could Run this one under Virtualbox but not wine, if that's what you suceed, i'd be interested in running it with wine. ;)
Thanks for any info !
Terii

---

### Post by igorashu on 2010-11-08
Heya, I have successfuly set up the License Manager in Ubuntu, but I had no luck in getting the app (running under wine) to recognize the HASP key.
But I haven't tried it since and considering how fast OSS is moving nowadays, it might work.
Cheers!

---

### Post by FLORIBUNTU on 2010-11-09
Hmmm...still wondering if you used windev from pcsoft.fr for this test or not at all.... ;) Thanks

---

### Post by igorashu on 2010-11-09
No, I haven't:)

---

