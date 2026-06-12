---
title: "Can't connect to wireless network with Network Manager"
date: 2007-06-08
forum: Dell  Ubuntu Support
---

### Post by thetictacaddict on 2007-06-08
On my new laptop, Network Manager manages the wired connection fine, but I can't reliably connect to my wireless network.  Once, for a few seconds, it worked perfectly, but I can't seem to recreate that situation.  In general, I can see my network and the signal strength, but if I try to connect, it fails after attempting for a while.  It doesn't seem to make a difference whether I turn on encryption.  My wireless card is an Intel Pro Wireless 3945.  I know that the wireless access point is working because another laptop (with Windows XP) was able to connect.  For the record, this is an Inspiron E1505 that came with Ubuntu pre-installed.

Is there something obvious I should try?  What kinds of things do you think might be going wrong here?

---

### Post by issueperson on 2007-06-08
I recommend uninstalling package manager and installing Wicd.  It works like a charm with my dell latitude D610, and if worst comes to worst, you can reinstall network manager from your Ubuntu install CD.  Download the package at this website: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
and just double click on it.  You have to uninstall Network Manager before it will let you install Wicd.

---

### Post by haftan on 2007-06-08
Wireless has worked well out of the box on my E1505n.  The only time I can't get throughput is when the ISP itself is having trouble, or some other machine is grabbing what little bandwidth there is.  Otherwise, the installed wireless manager is pretty reliable in quite a few settings so far.

---

### Post by issueperson on 2007-06-08
I just know that having used breezy, dapper, edgy, and now fiesty with my latitude, I've never just had it completely easy using Network Manager to do wireless.  There's always something that has to be fixed and it is usually rather obscure.

---

### Post by thetictacaddict on 2007-06-09
Thanks, issueperson, I tried wicd can connect to my nework okay (plus it seems to have better support for static IP's!).  However, I still can't connect if I turn on WEP encryption.  Wicd says "Generating PSK...", I can't cancel, and then I can't get the Wicd gui to run again unless I reboot the computer *and* reinstall it.

---

### Post by issueperson on 2007-06-09
> **thetictacaddict said:**
>  I can't cancel, and then I can't get the Wicd gui to run again unless I reboot the computer *and* reinstall it.

Hmmm... I don't know about the WEP generation part.  I use WPA (stronger than WEP) and it works fine.

So are you clicking the dropdown menu, selecting WEP, and typing in the password, and then it hangs on WEP?

---

### Post by thetictacaddict on 2007-06-09
> **issueperson said:**
> So are you clicking the dropdown menu, selecting WEP, and typing in the password, and then it hangs on WEP?
Right.  For now, I've left the network unsecured, but I'd prefer to have at least some security.  My access point doesn't support WPA.

---

### Post by camarojones on 2007-06-09
My WEP worked just fine.

When connecting, I used the drop down box from the Panel icon next to the clock, selected my wireless network form the list, and it asked what the key was. I entered the key after making sure that the correct type (HEX) was selected, and showed Open Authentication at the bottom of the window. Once it started to connect, it asked for a password to use for the key ring, and once that was put in it works like a champ.

When ever I log in, I have to enter that password, but it's not big deal to me. I've had no problems otherwise.

---

### Post by issueperson on 2007-06-09
Looking at the wicd webpage:
> Sometimes this can be fixed by putting quotation marks " " around the key, inside the text box.

try putting quotes around your key and let me know if that helps.

---

### Post by thetictacaddict on 2007-06-09
Okay, currently I can't seem to connect to the network even if it unsecured.  I'm going to play with my settings for a while, maybe even fiddle with /etc/network/interfaces...

Update: Just a few minutes ago, I connected no problem, though I don't think I changed anything.  I don't know why it worked.  I turned on WEP, and now I'm trying to connect (unsuccessfully).  It's not getting stuck like it was before, though!  Maybe the quotes helped.

---

### Post by thetictacaddict on 2007-06-13
Here's the latest.  My wireless worked for a while, then stopped again.  I waited a few days to see if it would start up again, but no such luck.  The problem always seemed to be with getting an IP, so today I set up Wicd to use a static IP for my wireless connection.  I can connect quite quickly, and I've been using my wireless connection all afternoon.  So, I'll try this for a few days and hope it works.

---

### Post by Diranda on 2007-06-21
Hello, 
I was having the same problem with Fiesty and my atheros wireless card.  After researching this issue and trying various things, I came across this posting.

For me, the wicd program is working really well.  I have set up the network monitor applet in my taskbar to keep an eye on it, but so far, it's doing exactly what I need it to.

Thanks for the information!

Diranda

---

### Post by mcdewey on 2007-06-22
I know this is totally bizarre, but I couldn't get my new Dell 1505n w/ Ubuntu to connect with WPA until I set the wireless router to broadcast the SSID. If it is set to not broadcast, I couldn't connect. Looking at Syslog, the Dell was trying to connect to an SSID of <unknown> (or something similar).

The moral: try configuring your router to enable SSID broadcast and see if that helps.

---

### Post by mcdewey on 2007-06-22
I know this is totally bizarre, but I couldn't get my new Dell 1505n w/ Ubuntu to connect with WPA until I set the wireless router to broadcast the SSID. If it is set to not broadcast, I couldn't connect. Looking at Syslog, the Dell was trying to connect to an SSID of <unknown> (or something similar).

The moral: try configuring your router to enable SSID broadcast and see if that helps.

---

