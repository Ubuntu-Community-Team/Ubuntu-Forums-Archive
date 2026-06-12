---
title: "Vodafone K3760 USB modem stick"
date: 2009-05-29
forum: General Help
---

### Post by Grootbok on 2009-05-29
Hi, just got a vodafone K3760 USB modem stick and Ubuntu cannot recognise it. Vodafone tech support do not support any Linux platforms. Can anyone help me install it please? (oh and my skill set is slightly above Homer Simpson's);)

---

### Post by chicken159 on 2009-06-05
You need to install Vodafone Mobile Connect from Betavine. The files are here:  [https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

There's a couple of other packages you'll probably need, see the documentation for details - [https://forge.betavine.net/frs/download.php/429/INSTALL.txt](https://forge.betavine.net/frs/download.php/429/INSTALL.txt)


The version of Vodafone Mobile Connect you'll need is:
[https://forge.betavine.net/frs/download.php/503/vodafone-mobile-connect_svn20090502_all.deb](https://forge.betavine.net/frs/download.php/503/vodafone-mobile-connect_svn20090502_all.deb)


Then you'll need to install WICD (using Synaptic), which replaces Network Manager, since NM doesn't play nicely with the Vodafone Mobile Connect package...

There may be a couple of little problems along the way, but that's basically what worked for me...good luck!

---

### Post by marvin.engl on 2009-08-04
Following Chicken159's instructions worked fine for me. Thank you for putting them up, they were extremely helpful for me!

I got an Acer AspireOne 110L with Ubuntu 9.04 (plain, NOT UNR) installed.

Once I installed the packages (ozerocdoff, usbmodeswitch and vodafone-mobile-connect [all the latest versions]), I could connect to Vodafone mobile broadband.

However, once I could connect, the Vodafone token behaved erratic. It constantly came up with error messages like "Token is unplugged. Replug and try again", "Cannot connect, no carrier, etc."

The solution is simple. For some reason, Ubuntu does not like it when the K3760 dongle is plugged in when you boot. My guess is that the usbmodeswitch driver is still buggy. 

If this happens to you, try this:

1. Do NOT plug the K3760 token in when you boot.
2. Let Ubuntu finish booting without it.
3. Plug the token in
4. Wait until the light on the token has gone red, than flashing blue.
5. Start the Betavine driver
6. Click connect

I have done this for 2 weeks now, and it has worked every time.

Since the K3760 token is badly designed (the spring mechanism is a joke), I bought a USB extension cable and have permanently attached the token to it. This is eliminating the physical strain on the spring mechanism, since it stays plugged into the extension cable at all times and I plug in/remove the other end of the cable.

Good luck with your K3760 dongle. When it works, its great!

---

### Post by timswait on 2009-09-13
I can't find WICD in synaptic. I'm using Hardy Heron, do I need to upgrade to a later version of Ubuntu?

---

### Post by chicken159 on 2009-10-05
Good to hear the post was helpful - agree with the comment about only plugging it once fully up and logged in - and with regard to the dodgy switch, mine is permanently superglued in the open position! ;)

---

### Post by Zimmer on 2009-10-05
My K3565 worked with Betavine in 8.04. I moved to Jaunty 9.04 and the Network Manager recognised it  OOTB so no need for Betavine.

There are more threads about discussing the Vodafone USB sticks and tips on ways of topping up credit...

[http://ubuntuforums.org/showthread.php?t=1061368](http://ubuntuforums.org/showthread.php?t=1061368)

---

### Post by chicken159 on 2009-10-07
WARNING: KARMIC beta and Vodafone K3760 no longer functional.

OK - now I've installed Karmic beta, and my K3760 is now non-functional again. Would suggest avoid this combination until solved.
 
Either:
- with the latest version of usb-modeswitch from the repos and version 2.15.01-1 of VMC, VMC drops out. The final bit of the error is - [Failed to load application: list index out of range.]

- with the version of usb-modeswitch from Betavine (0.9.7), VMC loads and connects, but then some randome time later, between 10 seconds and a minute or so, I get a total system freeze and have to resort to the power button.

Anyone got similar issues or solution?

---

### Post by chicken159 on 2009-10-10
UPDATE: After some updates, hacking around and general frustration I have a solution!

Network manager now works fine - but for some reason I had to run the setup wizrad, go through all the way until the last setp where you choose your contract (PAYG, Copntract, etc...mine is contract) but select 'My contract is not listed..' and enter the apn manually as 'internet'. Bingo!

Not tried VMC since...

---

### Post by marvin.engl on 2009-11-06
Hi, has the Ubuntu 9.10 (Karmic Koala) issue be resolved in the released version?

I have upgraded my other machines to 9.10 without major problems. However, loosing mobile broadband on my netbook would be a pain ...

---

### Post by marvin.engl on 2009-11-22
> **marvin.engl said:**
> Hi, has the Ubuntu 9.10 (Karmic Koala) issue be resolved in the released version?

I have upgraded my other machines to 9.10 without major problems. However, loosing mobile broadband on my netbook would be a pain ...

To answer my own question: NO!

I have upgraded to Ubuntu 9.10. Now, as soon as I plug the K3670 in, Ubuntu freezes up. Quite an achievement, has never happened to me before ;-D

I installed all the latest packages from Betavine, but no avail. The problem persists. Might have to downgrade to Ubuntu 9.04 again ... pity!

In the meantime, I strongly advice against upgrading to 9.10 in you use a Vodafone K3760 and Betavine drivers.

---

### Post by reeboker on 2009-11-23
> **marvin.engl said:**
> 
I have upgraded to Ubuntu 9.10. Now, as soon as I plug the K3670 in, Ubuntu freezes up. Quite an achievement, has never happened to me before ;-D

I installed all the latest packages from Betavine, but no avail. The problem persists. Might have to downgrade to Ubuntu 9.04 again ... pity!


Yep, if you look around, there are a lot of people with this problem, including me. The freezes are random, so I think everyone should give it a try and see for them selves. Not everybody is experiencing this issue.;)

---

### Post by timswait on 2009-11-23
It works for me;) I installed 9.10 as an entirely fresh install on a new machine. Plugged the stick in and it immediately recognised it as a mass storage device and a modem (no need to mess about with USB modes to tell it it's not a CD drive). I used network manager to connect, went through the set up wizard, didn't even need to apply chicken159's trick, just went straight for Vodafone contract and it worked. No more messing about with Vodafone mobile connect, which I never much liked anyway. The only downside is that I can't find anywhere where it tells me how strong a signal I have, and whether I'm on 3G or GPRS (other than by looking at the colour of the LED on the stick). I briefly get a picture of the number of bars signal when it makes the connection, but then it vanishes and I can't see anyway to get it back.
Perhaps the best bet for people struggling with 9.10 is to remove all the packages you've previously put on (VMC, usb mode switch, CD-off, WICD and so on) and try with network manager instead?

---

### Post by alexfish on 2009-11-23
hi before you upgraded did you have usb modeswitch installed or any of the packages
  from beta vine / ?

also you can search this site for info and devices supported/ if you have install usb- modeswitch  it may need to be configured  / "[usb_modeswitch.conf]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf") " some times this file is empty

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

### Post by timswait on 2009-11-23
Are you asking me? This was a completely new install on a new machine. I had previously used 9.04 with VMC, modeswitch etc on a different laptop, I've not attempted to upgrade that on to Karmic as it's plodding away fine as it is, and it's my girlfriend's, and she won't be happy if I kill it!

---

### Post by alexfish on 2009-11-23
> **timswait said:**
> Are you asking me? This was a completely new install on a new machine. I had previously used 9.04 with VMC, modeswitch etc on a different laptop, I've not attempted to upgrade that on to Karmic as it's plodding away fine as it is, and it's my girlfriend's, and she won't be happy if I kill it!

 little giggle / reading the on the site / if use the config file it should not kill it
  easier than the udev/ 

  it also gives tips on how to de bug if you have problems


   good point quoted  "I briefly get a picture of the number of bars signal when it makes the connection, but then it vanishes and I can't see anyway to get it back."
       bet a lot of users never spotted that ?

---

### Post by marvin.engl on 2009-11-23
> **marvin.engl said:**
> To answer my own question: NO!

I have upgraded to Ubuntu 9.10. Now, as soon as I plug the K3670 in, Ubuntu freezes up. Quite an achievement, has never happened to me before ;-D

I installed all the latest packages from Betavine, but no avail. The problem persists. Might have to downgrade to Ubuntu 9.04 again ... pity!

In the meantime, I strongly advice against upgrading to 9.10 in you use a Vodafone K3760 and Betavine drivers.

Thanks for all the posts and an update on the Ubuntu 9.10/K3670 issue. I installed 9.10 from scratch, connected with the K3760 dongle, but ...

... now I need to boot with the K3760 dongle in, or else!

Basically: if I put the K3760 dongle in and boot, 9.10 recognises it "out of the box" and I can straight connect to Vodafone's mobile broadband.

If I connect the K3760 dongle AFTER booting, my machine hangs instantly. 

Therefore: the bright side of 9.10 is: a) no more Betavine drivers and b) you can leave the K3760 dongle in and boot.

The downside: inserting the dongle later freezes the machine.

In 9.04 it was a) I needed the Betavine drivers and b) could not boot with the K3760 dongle. 

Ergo ... play around and find the combination that works for you.

---

### Post by alexfish on 2009-11-23
dont know if this link will help

  thread here 
[http://ubuntuforums.org/showthread.php?t=1333179](http://ubuntuforums.org/showthread.php?t=1333179)  
 note comments by
@john bean 

 and

@stefcep 
 
may help

---

### Post by crayfish on 2009-11-24
I have 9.10 (Netbook edition) on a dell mini 9.  Using betavine's usb-modeswitch and vodafone-mobile-connect.  My system freezes after about a minute or so too.  However, interestingly I seem to be able to connect (running vmc as root), once connected I seem to be able to do multiple wget's of small sites without issue, but as soon as I try something more intensive (eg: download a large jpeg) it hangs.

This is really irritating, I've been trying to get the K3760 working for ages, does anyone know if theres likely to be a fix for this any time soon?

---

### Post by alexfish on 2009-12-01
> **timswait said:**
> It works for me;) I installed 9.10 as an entirely fresh install on a new machine. Plugged the stick in and it immediately recognised it as a mass storage device and a modem (no need to mess about with USB modes to tell it it's not a CD drive). I used network manager to connect, went through the set up wizard, didn't even need to apply chicken159's trick, just went straight for Vodafone contract and it worked. No more messing about with Vodafone mobile connect, which I never much liked anyway. The only downside is that I can't find anywhere where it tells me how strong a signal I have, and whether I'm on 3G or GPRS (other than by looking at the colour of the LED on the stick). I briefly get a picture of the number of bars signal when it makes the connection, but then it vanishes and I can't see anyway to get it back.
Perhaps the best bet for people struggling with 9.10 is to remove all the packages you've previously put on (VMC, usb mode switch, CD-off, WICD and so on) and try with network manager instead?


I have Posted A thread here to get  RE:Signal Strength

[COLOR=#816447]**[gnome]**[/COLOR] 			 			[Mobile Broadband :Adding the initial Signal Strength to the gnome-ppp connection log]("http://ubuntuforums.org/showthread.php?t=1342815")

---

### Post by marvin.engl on 2010-02-03
A quick update on Ubuntu 10.04 (Alpha 2). I downloaded the daily development image on Tuesday, 02 Feb 2010 and installed it on my netbook (Acer AspireOne 110L).

The K3760 dongle worked "out of the box" after I went through the Network Manager set-up dialogue. Same situation as with Ubuntu 9.10 after a clean install. 

The most challenging thing was to notice that the UK is logged as "Britain (UK)" in the Network Manager's database ;-) It took me a few minutes to realise this after I couldn't find it between "United Arab Emirates" and "United States" ;-)

Otherwise ... no problems whatsoever.

---

### Post by alexfish on 2010-02-03
> **marvin.engl said:**
> A quick update on Ubuntu 10.04 (Alpha 2). I downloaded the daily development image on Tuesday, 02 Feb 2010 and installed it on my netbook (Acer AspireOne 110L).

The K3760 dongle worked "out of the box" after I went through the Network Manager set-up dialogue. Same situation as with Ubuntu 9.10 after a clean install. 

The most challenging thing was to notice that the UK is logged as "Britain (UK)" in the Network Manager's database ;-) It took me a few minutes to realise this after I couldn't find it between "United Arab Emirates" and "United States" ;-)

Otherwise ... no problems whatsoever.

hi

are there any problems with the network manager IE : connecting to the Primary and Secondary Servers 

also are you using Automatic (PPP) address only or Automatic (PPP)

---

### Post by marvin.engl on 2010-02-04
> **alexfish said:**
> hi

are there any problems with the network manager IE : connecting to the Primary and Secondary Servers 

also are you using Automatic (PPP) address only or Automatic (PPP)

Hi Alex,

Sorry, but you lost me completely ... please refer to the left hand side, I am one of the "first cup of Ubuntu" newbies.

Trying to answer your questions:

**Network Manager problems**

Haven't noticed any. Only that the UK is labelled "Britain (UK)" is counter-intuitive, but not a real problem.

**Primary/Secondary servers**

Excuse my ignorance ... what's that?

**Automatic PPP**

I guess you are referring to the* point-to-point protocol* (ppp). I have auto-assigned IPs on, with no special settings.

As mentioned, the K3760 worked "out of the box" with Ubuntu 10.04, so I did not have to do any configuration (other than going through the *network manager* wizard).

Sorry if I mis-understood your questions. If you give me detailed instructions, I will try to provide more helpful answers.

Take care!
Martin

---

### Post by chicken159 on 2010-02-08
OK - so seems the problems are back with this K3760;

So all was fine with 9.10, just using network-manager without VMC. Until, that is, I got fed up with where I was working having a dodgy signal and it kept switching networks all the time. So I thought I'd reinstall VMC so I could force it to stick with 3g or GPRS. Since then I have been stuffed - between VMC and network manager I can mostly get it working - BUT (BIG BIG 'BUT'!!!) - only the first time I connect after installing. Second time round, with either VMC(alpha) or network-manager/modem-manager it recognises the K3760 but an attempt to connect fails - just a brief 'connecting' notification-icon and then a disconnected message. Uninstall, reinstall - works once. try again - fails. Getting rather frustrating.
So I've done an upgrade to Lucid alpha...still the same problem - fresh install of 10.04, thought my problems were over as it connected first time. Shut down, restart - connection fails. I am afraid to say I have had to resort to booting the laptop up into XP.


Note: There seems to be an issue with getting the SIM PIN used in the Lucid version of this problem - it doesn't ask for it, and doesn't use the PIN which is part of the connection-config. Deleting the configured connection and running through the 'New Connection' setup doesn't help. Believe this is Bug #509738. Don't know whether previous problems were the same thing, since they occurred during some updates (to support Wader-VMC). Anyway, a solution seems imminent - TEMPORARY SOLUTION - DISABLE PIN ON SIM (by sticking it in a phone and turning off SIM security).

Attached syslog...
Feb  8 11:40:46 ubuntu kernel: [ 6724.880225] usb 2-1: new high speed USB device using ehci_hcd and address 19
Feb  8 11:40:46 ubuntu kernel: [ 6725.033281] usb 2-1: configuration #1 chosen from 1 choice
Feb  8 11:40:46 ubuntu kernel: [ 6725.034695] hso 2-1:1.0: Not our interface
Feb  8 11:40:46 ubuntu kernel: [ 6725.036263] scsi52 : SCSI emulation for USB Mass Storage devices
Feb  8 11:40:46 ubuntu kernel: [ 6725.036521] usb-storage: device found at 19
Feb  8 11:40:46 ubuntu kernel: [ 6725.036527] usb-storage: waiting for device to settle before scanning
Feb  8 11:40:47 ubuntu kernel: [ 6726.182373] usb 2-1: USB disconnect, address 19
Feb  8 11:40:48 ubuntu kernel: [ 6726.484175] usb 2-1: new high speed USB device using ehci_hcd and address 20
Feb  8 11:40:48 ubuntu kernel: [ 6726.644915] usb 2-1: configuration #1 chosen from 1 choice
Feb  8 11:40:48 ubuntu kernel: [ 6726.665234] hso0: Disabled Privacy Extensions
Feb  8 11:40:48 ubuntu kernel: [ 6726.667929] hso 2-1:1.10: Not our interface
Feb  8 11:40:48 ubuntu kernel: [ 6726.667986] scsi58 : SCSI emulation for USB Mass Storage devices
Feb  8 11:40:48 ubuntu kernel: [ 6726.668821] usb-storage: device found at 20
Feb  8 11:40:48 ubuntu kernel: [ 6726.668824] usb-storage: waiting for device to settle before scanning
Feb  8 11:40:48 ubuntu NetworkManager: <info>  Found wwan radio killswitch rfkill10 (at /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/rfkill/rfkill10) (driver usb)
Feb  8 11:40:48 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.7/net/hso0, iface: hso0)
Feb  8 11:40:48 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.7/net/hso0, iface: hso0): no ifupdown configuration found.
Feb  8 11:40:48 ubuntu modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1 claimed port hso0
Feb  8 11:40:48 ubuntu modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1
Feb  8 11:40:48 ubuntu modem-manager: (ttyHS0) opening serial device...
Feb  8 11:40:48 ubuntu modem-manager: (ttyHS0): probe requested by plugin 'Option High-Speed'
Feb  8 11:40:48 ubuntu modem-manager: (ttyHS2) opening serial device...
Feb  8 11:40:48 ubuntu modem-manager: (ttyHS2): probe requested by plugin 'Option High-Speed'
Feb  8 11:40:48 ubuntu modem-manager: (ttyHS1) opening serial device...
Feb  8 11:40:48 ubuntu modem-manager: (ttyHS1): probe requested by plugin 'Option High-Speed'
Feb  8 11:40:48 ubuntu modem-manager: (ttyHS3) opening serial device...
Feb  8 11:40:48 ubuntu modem-manager: (ttyHS3): probe requested by plugin 'Option High-Speed'
Feb  8 11:40:48 ubuntu kernel: [ 6726.728656] usb 2-1: hso received invalid serial state notification
Feb  8 11:40:51 ubuntu modem-manager: (ttyHS2) closing serial device...
Feb  8 11:40:51 ubuntu modem-manager: (ttyHS1) closing serial device...
Feb  8 11:40:51 ubuntu modem-manager: (ttyHS3) closing serial device...
Feb  8 11:40:51 ubuntu modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1 as /org/freedesktop/ModemManager/Modems/7
Feb  8 11:40:51 ubuntu modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1 claimed port ttyHS2
Feb  8 11:40:51 ubuntu modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1 claimed port ttyHS1
Feb  8 11:40:51 ubuntu modem-manager: (Option High-Speed): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1 claimed port ttyHS3
Feb  8 11:40:51 ubuntu NetworkManager: <info>  (hso0): new GSM device (driver: 'hso')
Feb  8 11:40:51 ubuntu NetworkManager: <info>  (hso0): exported as /org/freedesktop/NetworkManager/Devices/10
Feb  8 11:40:51 ubuntu NetworkManager: <info>  (hso0): now managed
Feb  8 11:40:51 ubuntu NetworkManager: <info>  (hso0): device state change: 1 -> 2 (reason 2)
Feb  8 11:40:51 ubuntu NetworkManager: <info>  (hso0): deactivating device (reason: 2).
Feb  8 11:40:51 ubuntu NetworkManager: <info>  (hso0): device state change: 2 -> 3 (reason 0)
Feb  8 11:40:53 ubuntu kernel: [ 6731.662444] usb-storage: device scan complete
Feb  8 11:40:53 ubuntu kernel: [ 6731.663160] scsi 58:0:0:0: Direct-Access     ZCOption HSUPA Modem           PQ: 0 ANSI: 2
Feb  8 11:40:53 ubuntu kernel: [ 6731.664522] sd 58:0:0:0: Attached scsi generic sg2 type 0
Feb  8 11:40:53 ubuntu kernel: [ 6731.667191] sd 58:0:0:0: [sdb] Attached SCSI removable disk
Feb  8 11:41:00 ubuntu modem-manager: (ttyHS0) closing serial device...

Feb  8 11:46:20 ubuntu NetworkManager: <info>  Activation (hso0) starting connection 'Vodafone Contract'
Feb  8 11:46:20 ubuntu NetworkManager: <info>  (hso0): device state change: 3 -> 4 (reason 0)
Feb  8 11:46:20 ubuntu NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) scheduled...
Feb  8 11:46:20 ubuntu NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) started...
Feb  8 11:46:20 ubuntu NetworkManager: <info>  Activation (hso0) Stage 1 of 5 (Device Prepare) complete.
Feb  8 11:46:20 ubuntu modem-manager: (ttyHS2) opening serial device...
Feb  8 11:46:20 ubuntu modem-manager: Modem /org/freedesktop/ModemManager/Modems/7: state changed (disabled -> enabling)
Feb  8 11:46:21 ubuntu modem-manager: Modem /org/freedesktop/ModemManager/Modems/7: state changed (enabling -> enabled)
Feb  8 11:46:21 ubuntu modem-manager: Modem /org/freedesktop/ModemManager/Modems/7: state changed (enabled -> disabled)
Feb  8 11:46:21 ubuntu NetworkManager: <info>  (hso0): device state change: 4 -> 3 (reason 0)
Feb  8 11:46:21 ubuntu NetworkManager: <info>  (hso0): deactivating device (reason: 0).
Feb  8 11:46:21 ubuntu NetworkManager: <info>  Policy set '00:25:E7:16:CF:B4 PANU' (bnep0) as default for routing and DNS.
Feb  8 11:46:21 ubuntu NetworkManager: <WARN>  stage1_enable_done(): GSM modem enable failed: (32) SIM PIN required
Feb  8 11:46:21 ubuntu NetworkManager: <info>  (hso0): device state change: 3 -> 9 (reason 0)
Feb  8 11:46:21 ubuntu NetworkManager: <info>  Activation (hso0) failed.
Feb  8 11:46:21 ubuntu NetworkManager: <info>  (hso0): device state change: 9 -> 3 (reason 0)
Feb  8 11:46:21 ubuntu NetworkManager: <info>  (hso0): deactivating device (reason: 0).

---

### Post by marvin.engl on 2010-05-06
I installed Ubuntu 10.04 from scratch on my netbook over the weekend.

No problems with the K3760 dongle whatsoever, it worked "out of the box" without hitches.

Just do the normal System --> Preferences --> Network Connections dialogue, set up "mobile broadband", and ... voilà, you are off.

Also, plugging out/in is no longer an issue. You can pull the K3760 out and put it back in as often as you like, it doesn't hang up the system any longer.

---

