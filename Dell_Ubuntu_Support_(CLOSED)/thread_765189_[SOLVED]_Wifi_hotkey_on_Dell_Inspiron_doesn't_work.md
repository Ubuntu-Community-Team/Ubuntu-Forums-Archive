---
title: "[SOLVED] Wifi hotkey on Dell Inspiron doesn't work in 8.04"
date: 2008-04-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by EvenStevens on 2008-04-24
It worked perfectly fine in 7.10 but now after updating to 8.04...the wifi light doesn't illuminate.
I can "see" the networks but it doesn't connect at all.

How can I fix this :-\

Cheers.

Also, using lshal -m when I press Fn+F2, it says "bluetooth"

When I press Fn+F10, it says "Eject-close-cd" but the CD tray doesn't pop out.

All other keys work, brightness, volume etc.

---

### Post by notwen on 2008-04-24
Which model Inspiron are you running?  Were you using a custom Dell Ubuntu image if one was made for you specific model?  Which wireless card does your machine have, Dell or Intel?

---

### Post by EvenStevens on 2008-04-24
I'm almost certain it's an Intel card. In Windows, it uses the intel wireless manager as default.

And it's a Dell 640m

I was using the x86 image from the main Ubuntu website.

---

### Post by notwen on 2008-04-24
> **EvenStevens said:**
> And specific Ubuntu images? Where can I get these?

The custom Dell Ubuntu images are only available for the N-Series models Dell ships w/ Ubuntu pre-installed.  

Let's figure out your wireless, open up a terminal and type in the following command and paste the output back here:

```
lspci | grep Intel
```

I think the 640m is similar to the Inspiron e1405 and uses Dell wireless, which is more than likely a re-labeled Broadcom wireless card.  Do you recall whether or not you used restricted drivers in Gutsy?

---

### Post by EvenStevens on 2008-04-24
steve@steve-laptop:~$ lspci | grep Intel
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


I notice the last entry says Intel Wireless...so I guess it is wireless.

I remember a restricted Wifi driver used in 7.04, but in 7.10 everything worked out of the box.


EDIT: Something funny just happened, I rebooted and the wireless network connected (Without a wifi key! :-\). The wifi light remained off. When I pressed Fn F2, it disconnected. Then when I pressed it again, nothing happened - it stayed disconnected...

---

### Post by notwen on 2008-04-24
My Inpsiron 1420n has the same card, I know Dell recommended blacklisting the ipw module for this card, replacing it w/ the iwl module for stability issues.  Once I switched over to the iwl module my wifi indicator LED no longer lit up either while the laptop was indeed connected wirelessly.  Let's see what module Hardy is using by default.  Type the following command into term and paste the output back here please.

```
lsmod | egrep 'Module|iwl|ipw'
```

Glad that your wireless appears to at least be functioning, hopefully we can work on making it stable and working as it used to.

---

### Post by EvenStevens on 2008-04-24
```
steve@steve-laptop:~$ lsmod | egrep 'Module|iwl|ipw'
Module               Size    Used by
iwl3945              89844   0
iwlwifi mac80211     219108  1 iwl3945
cfg80211             15112   1 iwlwifi_mac80211

```
Hmm...

---

### Post by notwen on 2008-04-24
It looks as if they've kept the iwl module in use for Hardy, I wonder if Dell is able to somehow relate the iwl module to the wifi LEDs on our machines.  

Have you check under System--->Administration---Restricted Drivers to see if your wireless is using the restricted driver?  My Inpsiron 1420n will automatically search for my previous SSID and connect as I bring it down and back up again.

---

### Post by EvenStevens on 2008-04-24
Nothing shows up under the proprietary drivers box. :-\

Right now Wi-fi is connected and has been for the past hour or so. Yet the LED still doesn't show.

---

### Post by notwen on 2008-04-24
My Intel 3945 card shows up as 'enabled' but not in use under Restricted Drivers.  Odd indeed.  I'm starting to wonder if the LED signal is directly related to the ipw module being used as I can swap back to the ipw and my LED works.  It boggles the mind.  Maybe someone w/ more knowledge of this can comment on this and possibly get us our LED working again.

---

### Post by El Lance-O on 2008-04-25
I am running on an Inspiron 1505 and I get the same problem. Networks are fine, but the light isn't on anymore as described.

I wonder...

---

### Post by Tulsapoke on 2008-04-25
Wifi on my E1505 also had no way to turn on the the Wifi LED.  I could see networks but it would not connect.  I booted up to an older kernel and it works fine.  I hope they get this fixed soon so I can use the new kernel.  I have the Intel 3945 Wifi chip.

---

### Post by neptho on 2008-04-26
I can confirm that the light does not work with the iwl3945 driver; it only works with the ipw3945 (proprietary) driver.   ipw3945 has been the bane of my existence since '06.

---

### Post by anuban on 2008-04-27
> **Tulsapoke said:**
> Wifi on my E1505 also had no way to turn on the the Wifi LED.  I could see networks but it would not connect.  I booted up to an older kernel and it works fine.  I hope they get this fixed soon so I can use the new kernel.  I have the Intel 3945 Wifi chip.

I also had the same problem and the command mentioned above gives me the same results for Intel.  But my LEDs are working and even Fn+F2 also works to enable and disable Wifi.  I am using Dell Inspiron E1505 with dual boot Windows Vista.
How I got it to work:

[LIST=1]
[*]Go to Synaptic Package Manager and
[*]Search for 'backport-modules'.  Lot of entries will be there.
[*]Select the 'linux-backports-modules-hardy-generic' for installation.  That will install one more entry for you.
[*]Restart your computer.
[*]Your wifi LED should be working now.
[/LIST]
Enjoy...:guitar:

---

### Post by EvenStevens on 2008-04-27
Oh my God, that worked like a charm for my 640m.

Thankyou, oh God-like being.

---

### Post by anuban on 2008-04-29
> **EvenStevens said:**
> Oh my God, that worked like a charm for my 640m.

Thankyou, oh God-like being.


Good to know that helped.
If that issue is resolved.  Can you please mark this thread solved.:)

TIA

---

### Post by bjtuna on 2008-05-18
This seemed to solve the LED problem on my E1405 (which I believe is the same as the 640m).

---

### Post by nrayever on 2008-05-20
> **anuban said:**
> I also had the same problem and the command mentioned above gives me the same results for Intel.  But my LEDs are working and even Fn+F2 also works to enable and disable Wifi.  I am using Dell Inspiron E1505 with dual boot Windows Vista.
How I got it to work:

[LIST=1]
[*]Go to Synaptic Package Manager and
[*]Search for 'backport-modules'.  Lot of entries will be there.
[*]Select the 'linux-backports-modules-hardy-generic' for installation.  That will install one more entry for you.
[*]Restart your computer.
[*]Your wifi LED should be working now.
[/LIST]
Enjoy...:guitar:

i will have to try it when i arrive at home. this is just a note so i can find this thread again xD.

nrayever

---

### Post by dupin on 2008-05-20
The LED issue is a problem with iwl3945 driver. I've been using it for 5 months now, with out LED and had no problems.
I'll try this solution, and see what happens.
I'd like to know if changes iwl3945 back to ipw3945 (at sourceforge says it is no longer mantained).

---

