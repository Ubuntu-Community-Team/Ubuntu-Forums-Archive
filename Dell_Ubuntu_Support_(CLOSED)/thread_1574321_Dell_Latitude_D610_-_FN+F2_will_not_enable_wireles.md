---
title: "Dell Latitude D610 - FN+F2 will not enable wireless - help!"
date: 2010-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by travlemon on 2010-09-14
Hey everybody,

I was just recently given a Dell Latitude D610 from someone who didn't want it.  It came with Windows XP Pro on it, and I logged in real quick to check things out.  Wireless was working as it should and the FN + F2 key combination was enabling/disabling the wireless card as it is supposed to.

Installed a fresh copy of Ubuntu 10.04 and wiped the entire disk to use with Ubuntu.  Upon setting everything up, I installed ndiswrapper and installed the driver for this laptop's wireless card.  I am familiar with ndiswrapper and have used it many times, so I know my workflow with that was correct.

After installing the driver, I couldn't find the device anywhere in network manager.  I noticed the WiFi light is not turned on, and thus probably the root of my problem here.  I tried pressing FN + F2 (the wireless enable/disable key combo for this model laptop), and I get no response.  The light WiFi light does not come on.  I've seen on other forums that the light may not come on, but wireless may still be enabled.  

I've double checked so many things, but the system just doesn't seem to want to enable this device.  In the long run, it seems as though this is not a driver issue, but just a matter of getting the darn wireless card to enable, so the system can recognize it.

Does anyone know how to address this? I've googled my brains out and searched the forums, and the closest thing I've found was aircraft manager.  However, another forum suggested that aircraft-manager is only for 2 specific Dell mini models, which may explain why it won't open for me.

Anyway, thank you in advance! Any suggestions are more than appreciated!

---

### Post by niteshifter on 2010-09-14
Hi,

Have you checked in the BIOS settings to see if wireless is enabled?

---

### Post by travlemon on 2010-09-14
> **niteshifter said:**
> Hi,

Have you checked in the BIOS settings to see if wireless is enabled?

Hi, thanks for responding.  Yes, I have double checked many times in BIOS that wireless is enabled.  And several times, I will save the settings and then re-enter BIOS to make sure they saved correctly.

---

### Post by MartijnV on 2010-09-14
Why are you using ndiswrapper drivers? What kind of wifi card do you have? My intel 2200BG card works "out of the box" And it was very easy to get my pc card with broadcom chipset working. No need of windows drivers. Maybe ndiswrapper is the cause?

---

### Post by travlemon on 2010-09-14
> **MartijnV said:**
> Why are you using ndiswrapper drivers? What kind of wifi card do you have? My intel 2200BG card works "out of the box" And it was very easy to get my pc card with broadcom chipset working. No need of windows drivers. Maybe ndiswrapper is the cause?

I am using ndiswrapper because the card wasn't working at all, out of the box.  The card is a Dell Wireless 1350 WLAN PC Card. I will do another clean install of a Ubuntu, wiping everything.  I will specifically pay attention to the wireless behavior this time, and see if it gets picked up.  I have no data to lose, and the installation doesn't take long at all.  I will let you know how that turns out.

---

### Post by travlemon on 2010-09-14
> **MartijnV said:**
> Why are you using ndiswrapper drivers? What kind of wifi card do you have? My intel 2200BG card works "out of the box" And it was very easy to get my pc card with broadcom chipset working. No need of windows drivers. Maybe ndiswrapper is the cause?

Ok,  so I did another clean install of Ubuntu.  Upon signing in, it shows no wireless devices.  So I checked out the Hardware Drivers section to see if there were any drivers for it to be downloaded (I have it hard wired), and there are no drivers.  I also doubled checked that the card is enabled in BIOS.  

I am pretty much stumped on this.  It just doesn't seem like the card wants to enable itself so the OS can pick it up :-\

---

### Post by MartijnV on 2010-09-14
weird. According to [google](http://webcache.googleusercontent.com/search?q=cache:wLDJlL2hvLEJ:www.modem-help.co.uk/Dell/TrueMobile-1350-WLAN-PC-Card.html+Dell+Wireless+1350+WLAN+PC+Card+chipset&cd=10&hl=nl&ct=clnk&gl=nl) it has the broadcom BC4306sg chipset. It should work with the b43 driver? (fwcutter) But then you should have seen it in the "drivers" program. (i don't know the exact name in English, it's the same way you, for instance, would install the proprietary nvidia drivers)

What can you see in the logs? (messages in logviewer?)

---

### Post by travlemon on 2010-09-14
> **MartijnV said:**
> weird. According to [google]("http://webcache.googleusercontent.com/search?q=cache:wLDJlL2hvLEJ:www.modem-help.co.uk/Dell/TrueMobile-1350-WLAN-PC-Card.html+Dell+Wireless+1350+WLAN+PC+Card+chipset&cd=10&hl=nl&ct=clnk&gl=nl") it has the broadcom BC4306sg chipset. It should work with the b43 driver? (fwcutter) But then you should have seen it in the "drivers" program. (i don't know the exact name in English, it's the same way you, for instance, would install the proprietary nvidia drivers)

What can you see in the logs? (messages in logviewer?)

Hmm, there looks to be a ton of things in the messages section.  What exactly should I be looking for? It looks like a list of many things it detected, and other various hardware info.

---

### Post by travlemon on 2010-09-14
> **MartijnV said:**
> weird. According to [google]("http://webcache.googleusercontent.com/search?q=cache:wLDJlL2hvLEJ:www.modem-help.co.uk/Dell/TrueMobile-1350-WLAN-PC-Card.html+Dell+Wireless+1350+WLAN+PC+Card+chipset&cd=10&hl=nl&ct=clnk&gl=nl") it has the broadcom BC4306sg chipset. It should work with the b43 driver? (fwcutter) But then you should have seen it in the "drivers" program. (i don't know the exact name in English, it's the same way you, for instance, would install the proprietary nvidia drivers)

What can you see in the logs? (messages in logviewer?)

Also, I forgot to mention that if I search "latitude" in the Synaptic Package Manager, it finds something called "i8kutils".  It looks like it's geared towards making the FN key functions work properly on dell models.  I installed the package, but I have no clue how to use it.  Do you know anything about it?

---

### Post by MartijnV on 2010-09-14
Things like your wifi card being detected, detecting the broadcom chipset, requesting the firmware (and maybe not finding the firmware)
when i look at "dmesg" i find things like this for my intel card
```
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   21.697014] ipw2200 0000:02:06.0: firmware: requesting ipw2200-bss.fw
```

I only use the i8k utils to display the temperatures in the gnome hardware sensors applet.

[HOWTO: Install and configure i8kmon for configurable automatic fan speed control](http://ubuntuforums.org/showthread.php?t=842775&highlight=i8k)


(good luck, i'm going to sleep, shutdown-h now)

---

### Post by travlemon on 2010-09-14
> **MartijnV said:**
> Things like your wifi card being detected, detecting the broadcom chipset, requesting the firmware (and maybe not finding the firmware)
when i look at "dmesg" i find things like this for my intel card
```
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   21.697014] ipw2200 0000:02:06.0: firmware: requesting ipw2200-bss.fw
```I only use the i8k utils to display the temperatures in the gnome hardware sensors applet.

[HOWTO: Install and configure i8kmon for configurable automatic fan speed control]("http://ubuntuforums.org/showthread.php?t=842775&highlight=i8k")


(good luck, i'm going to sleep, shutdown-h now)

I am failing miserably on i8kutils.  I'm pretty sure the command I need to run is i8kbuttons, as I found a file with that name and assume it would be for the FN key functionality.  

As for log viewer, I've been searching and don't see anything at all in regards to the wireless card.

I'm completely stumped.  I know this card was working with XP before I formatted.  I think I am going to open it up on the bottom and double check that the card isn't loose.

---

### Post by MartijnV on 2010-09-15
The buttons on my C810 "just worked" without i8kutils.
Even if the card isn't working in ubuntu, you should at least see something in the logs regarding your card. Error messages, anything. When you can find absolutely nothing regarding your card, the chipset or anything with wifi, your card may be defective. In the bios you should see something regarding an enabled minipci or "unknown" card.

---

### Post by travlemon on 2010-09-16
> **MartijnV said:**
> The buttons on my C810 "just worked" without i8kutils.
Even if the card isn't working in ubuntu, you should at least see something in the logs regarding your card. Error messages, anything. When you can find absolutely nothing regarding your card, the chipset or anything with wifi, your card may be defective. In the bios you should see something regarding an enabled minipci or "unknown" card.

Thanks for responding.  I have determined that the card must be defective.  I eventually got that light to come on and got on wireless.  Wireless went out though, shortly after I got it working.  So I tried rebooting and it didn't come on again.  After rebooting many times, it seemed to work when it felt like it, but now it totally stopped working.  

I just don't think I'd be having this trouble if the card was definitely a good, non-defective card.  I'm going to cracked open the laptop and tried cleaning the contacts very carefully, but I got nothing.  

Now the only decision left to make is whether I should get another "minipci" wireless card to go inside the laptop, or just get one of those flash drive sized usb wifi adapters, so It's not restricted to one computer.

Anyway, thanks everyone for responding! I am going to mark this as solved, as I'm pretty sure it's just a defective card.  I'm probably going to try playing around with it a bit more just for kicks, I'll post back if I make any "breakthroughs".  Thanks again!

---

### Post by fiddler616 on 2010-10-31
I'm having a similar problem, except worse.

I got a Latidude D610 last year, and dual-booted XP and Jaunty (and later Crunchbang). Every now and then the wireless LED would turn off--and the card would stop working. Fn+F2 did not work in Linux, ever, and worked most of the time in XP (not always on the first try). Then, the LED turned off, and would not turn back on again. I've tried it in Windows, I've tried it from the BIOS, the light refuses to turn on, and so I'm left without a wireless card. Around the same time, a few of my USB ports gave up the ghost, and the PCMCIA slot died. So, do you think I have a legitimate hardware problem? Or is there some sort of kungfu magic I should try?

Thanks in advance.

---

### Post by PRC09 on 2010-10-31
You could try a Live cd and see if you have the same problems.If you are experiencing the same problems in both operating systems tho,then it is probably hardware failure....

---

### Post by fiddler616 on 2010-10-31
> **PRC09 said:**
> You could try a Live cd and see if you have the same problems.If you are experiencing the same problems in both operating systems tho,then it is probably hardware failure....

I actually wiped everything, installed Windows 2000, and then installed Crunchbang Statler (Debian-based instead of Ubuntu-based), and it's still not working. So....darn.

Update: I just took out the PCMCIA slot, since I was wondering how well it was connected. With it out, I was able to confirm that all the pins were entering my external wireless card. I then plugged the PCMCIA adapter back into the motherboard, and booted it up. nm-applet reports, correctly, that there is a wireless card attached, but says "wireless is disabled". I was about to ask you about that, but realized I should carry out my own investigations first. And...check out what nm-tool is reporting [parts may not be verbatim since I have to type it in by hand] :

```
- Device: eth0
Type:Wired
[etc]
- Device: wlan0
Type: 802.11 WiFi
Driver: b43
State: unavailable
Default: no
HW Address: 00:14[is it safe to publish all of this?]
Capabilities:
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points


- Device: wlan1
Type: 802.11 WiFi
Driver: b43
State: unavailable
Default: no
HW Address: 00:1C:[etc]
Capabilities:
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points
```

[s]Does this mean that it's recognizing one internal and one external wireless card?[/s]

Edit: Uh, it did this when the internal card was physically unplugged from the motherboard. So apparently it's recognizing the same PCMCIA card twice. And now that I think about it, nm-applet was doing the same thing.

---

### Post by WmBill on 2011-03-30
> **travlemon said:**
> Hey everybody,

I was just recently given a Dell Latitude D610 from someone who didn't want it.  It came with Windows XP Pro on it, and I logged in real quick to check things out.  Wireless was working as it should and the FN + F2 key combination was enabling/disabling the wireless card as it is supposed to.

Installed a fresh copy of Ubuntu 10.04 and wiped the entire disk to use with Ubuntu.  Upon setting everything up, I installed ndiswrapper and installed the driver for this laptop's wireless card.  I am familiar with ndiswrapper and have used it many times, so I know my workflow with that was correct.

After installing the driver, I couldn't find the device anywhere in network manager.  I noticed the WiFi light is not turned on, and thus probably the root of my problem here.  I tried pressing FN + F2 (the wireless enable/disable key combo for this model laptop), and I get no response.  The light WiFi light does not come on.  I've seen on other forums that the light may not come on, but wireless may still be enabled.  

I've double checked so many things, but the system just doesn't seem to want to enable this device.  In the long run, it seems as though this is not a driver issue, but just a matter of getting the darn wireless card to enable, so the system can recognize it.

Does anyone know how to address this? I've googled my brains out and searched the forums, and the closest thing I've found was aircraft manager.  However, another forum suggested that aircraft-manager is only for 2 specific Dell mini models, which may explain why it won't open for me.

Anyway, thank you in advance! Any suggestions are more than appreciated!

I, too, recently purchased a used Dell Latitude d610 from Ebay.  The XP OS had been wiped clean and I installed Ubuntu 10.10.  I can't get the wireless connection to work.  I've tried everything and Googled my brains out.  Did you ever find a solution to this problem?  From the thread is appears the problem is solved...but not really since you think it is a faulty wireless card.

Please let me know if you uncovered a solution.

WmBill

---

### Post by mylittletom on 2011-04-28
For anyone still having problem of Dell D610 wireless ,

I tried many ways to fix it unsuccessfully for weeks  until I installed Ubuntu Natty 11.04 and went to System>Windows Wireless Drivers , pointed to the file  bmwl5.inf of  Dell D610 Drivers CD.  Then it worked ! 

My Dell D610 wireless card is Broadcome 4138  (Airforce One 54g).

---

### Post by youpankeys on 2011-09-16
Hi folks !!! For someone that still have problem with wireless drivers on any kind of dell latitude or inspiron, the only thing to to do is install firmware b43 installer. It is simple just tape it on synaptic manager or ubuntu software center search. That's all!!!!
youpankeys wrote
 




> **travlemon said:**
> Hey everybody,

I was just recently given a Dell Latitude D610 from someone who didn't want it.  It came with Windows XP Pro on it, and I logged in real quick to check things out.  Wireless was working as it should and the FN + F2 key combination was enabling/disabling the wireless card as it is supposed to.

Installed a fresh copy of Ubuntu 10.04 and wiped the entire disk to use with Ubuntu.  Upon setting everything up, I installed ndiswrapper and installed the driver for this laptop's wireless card.  I am familiar with ndiswrapper and have used it many times, so I know my workflow with that was correct.

After installing the driver, I couldn't find the device anywhere in network manager.  I noticed the WiFi light is not turned on, and thus probably the root of my problem here.  I tried pressing FN + F2 (the wireless enable/disable key combo for this model laptop), and I get no response.  The light WiFi light does not come on.  I've seen on other forums that the light may not come on, but wireless may still be enabled.  

I've double checked so many things, but the system just doesn't seem to want to enable this device.  In the long run, it seems as though this is not a driver issue, but just a matter of getting the darn wireless card to enable, so the system can recognize it.

Does anyone know how to address this? I've googled my brains out and searched the forums, and the closest thing I've found was aircraft manager.  However, another forum suggested that aircraft-manager is only for 2 specific Dell mini models, which may explain why it won't open for me.

Anyway, thank you in advance! Any suggestions are more than appreciated!

---

### Post by youpankeys on 2011-09-16
I forgot something important. Next step after install the firmware will be restart the computer. Good luck!!!!
youpankeys!!!

---

### Post by lnxusr351 on 2011-09-21
> **youpankeys said:**
> Hi folks !!! For someone that still have problem with wireless drivers on any kind of dell latitude or inspiron, the only thing to to do is install firmware b43 installer. It is simple just tape it on synaptic manager or ubuntu software center search. That's all!!!!
youpankeys wrote

Thank you very much for this.... I have had a real trying time to get the wireless up on here, and bingo, works fantastic.

---

### Post by rhce2be on 2012-04-04
> **youpankeys said:**
> Hi folks !!! For someone that still have problem with wireless drivers on any kind of dell latitude or inspiron, the only thing to to do is install firmware b43 installer. It is simple just tape it on synaptic manager or ubuntu software center search. That's all!!!!
youpankeys wrote

I'm still having this problem with the wireless driver on a Dell Lat. D610...I've installed the b43* software, in fact I have all packages installed below...

$ dpkg --list *b43*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                                     Version                                                       Description
 +++-======================-======================-===============================================
ii  b43-fwcutter                                                             1:014-9                                                           Utility for extracting Broadcom 43xx firmware
rc  firmware-b43-installer                  1:014-9                                                           Installer package for firmware for the b43 driver
ii  firmware-b43-lpphy-ins                  1:014-9                                                         Installer package for firmware for the b43 driver (LP-PHY ve
ii  firmware-b43legacy-ins                 1:014-9                                                         Installer package for firmware for the b43legacy driver


can anyone please tell me how to solve this...? It's something I'm working on for my company...any help would be greatly appreciated

---

### Post by ericv222 on 2012-04-22
I had a similar problem with my Dell laptop.  I could see the broadcom card in dmesg.  The light would not turn on.  Pushing Fn+F2 would not help.  If I rebooted into windows, I could turn the wifi (and light) on.  Then it would stay on when I rebooted back into linux (centos).  

This is what I did to fix:
rfkill list    (will show if the card has hard or soft blocks on it, or both)
My wifi was blocked
rfkill unblock all    (which did not do anything initially)
Then I hit Fn+F2      (that unblocked the hard block)
Then  rfkill unblock all  a second time
That did the trick.  The little wifi light came on and I was connected via wifi again.

Hope that works for you

- Eric

[email]ericv@iserverwatch.com[/email]

---

### Post by Curious65 on 2012-12-23
just got a used d610 with a wiped HDD. installed Ubuntu 10.10 and thanks to the folks here i got my wifi to work. it was more a case of not seeing the password protected router due to password issues but the posts here helped point me on the right direction.

so thanks.

---

