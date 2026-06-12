---
title: "Wireless Lights deactivated in 8.04 on Inspiron 1420n"
date: 2008-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by frbe0101 on 2008-04-28
After getting my sound fixed, I notice another problem: the wireless light on the laptop don't blink or turn on when connected to a wireless network, minor problem as the wireless works fine. Any ideas on how the get it to work again?

---

### Post by LiquidIQ on 2008-04-28
Yea I noticed that, but Bluetooth is on.

There's gotta be a switch somewhere in some config file, hah.

---

### Post by Keyper7 on 2008-04-28
Help us to help you: at least say what is your wireless card...

Anyway, based on the problem description, I'm guessing it's an Intel 3945. If it is, the current iwl3945 driver supplied with Hardy does not support the LED. Fortunately, the updated driver, which does support it, is available via backporting. Just open a terminal and type:

sudo apt-get install linux-backports-modules-hardy

Now disconnect from your wireless network and reload the module with the following commands:

sudo modprobe -r iwl3945
sudo modprobe iwl3945

That should ensure you're now using the new driver. Connect to your wireless network again and the LED should shine.

The current driver does not support traffic blinking yet, though. They're working on it.

---

### Post by neptho on 2008-04-28
> **Keyper7 said:**
> The current driver does not support traffic blinking yet, though. They're working on it.

I pray they make this a config variable for modprobe.  The blue LEDs on my 1400 are blinding at night and at the worst location they could be.  So long as my hand hovers over the keyboard, it's fine, but move it, ahh, blind!

---

### Post by robbie75 on 2008-04-29
> **Keyper7 said:**
> Help us to help you: at least say what is your wireless card...

Anyway, based on the problem description, I'm guessing it's an Intel 3945. If it is, the current iwl3945 driver supplied with Hardy does not support the LED. Fortunately, the updated driver, which does support it, is available via backporting. Just open a terminal and type:

sudo apt-get install linux-backports-modules-hardy

Now disconnect from your wireless network and reload the module with the following commands:

sudo modprobe -r iwl3945
sudo modprobe iwl3945

That should ensure you're now using the new driver. Connect to your wireless network again and the LED should shine.

The current driver does not support traffic blinking yet, though. They're working on it.

Thanks to your suggestion my LED now is working again.
But it's very weird: the led worked just a few reboots after the upgrade to gutsy...then after a suspend it suddenly stopped... :-?

---

### Post by nwdz on 2008-04-29
hmmm...does this really works...the led was working but when i pressed the button...now the wireless is not even turning on..

---

### Post by LiquidIQ on 2008-04-29
> **Keyper7 said:**
> backporting. 

Thanks for that. My other question is, if I install backports, what other drivers is it upgrading that might be working fine? Thanks.

---

### Post by frbe0101 on 2008-04-29
Well the wireless still works, thanks, but I do miss it blinking, now it's just steadily on when ever the card is active, not if it is connected, it would be nice if we could tone the brightness down on the light. Please reply when you guys got the next driver which restores the lights fully (if not better).

---

### Post by notwen on 2008-04-29
Hip, glad you posted this.  Will try this when I get home.  Any other drivers on the Inspiron 1420n that may be affected by enabling the backports repo?

---

### Post by Keyper7 on 2008-04-29
> **robbie75 said:**
> Thanks to your suggestion my LED now is working again.
But it's very weird: the led worked just a few reboots after the upgrade to gutsy...then after a suspend it suddenly stopped... :-?

Just stopped after the suspend? I mean, did it work again after a reboot?

> **nwdz said:**
> hmmm...does this really works...the led was working but when i pressed the button...now the wireless is not even turning on..

Did it work after a reboot? I think the current driver has some issues with the kill switch, that might be the problem.

> **LiquidIQ said:**
> Thanks for that. My other question is, if I install backports, what other drivers is it upgrading that might be working fine? Thanks.
> **notwen said:**
> Hip, glad you posted this.  Will try this when I get home.  Any other drivers on the Inspiron 1420n that may be affected by enabling the backports repo?

Here's the list of relevant files from linux-backports-modules-2.6.24-16-generic:

/lib/firmware/2.6.24-16-generic/iwlwifi-4965-1-lbm.ucode
/lib/modules/2.6.24-16-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
/lib/modules/2.6.24-16-generic/updates/wireless/iwlwifi/iwlwifi/compatible/iwl4965.ko
/lib/modules/2.6.24-16-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_mac80211.ko
/lib/modules/2.6.24-16-generic/updates/wireless/iwlwifi/mac80211/compatible/net/mac80211/iwlwifi_rc80211_simple.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/mac80211/rt2x_mac80211.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2400pci.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2500pci.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2500usb.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2x00lib.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2x00pci.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt2x00usb.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt61pci.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/rt2x00/rt73usb.ko
/lib/modules/2.6.24-16-generic/updates/wireless/rt2x00/wireless/rt2x_cfg80211.ko

> **neptho said:**
> I pray they make this a config variable for modprobe.  The blue LEDs on my 1400 are blinding at night and at the worst location they could be.  So long as my hand hovers over the keyboard, it's fine, but move it, ahh, blind!
> **frbe0101 said:**
> Well the wireless still works, thanks, but I do miss it blinking, now it's just steadily on when ever the card is active, not if it is connected, it would be nice if we could tone the brightness down on the light. Please reply when you guys got the next driver which restores the lights fully (if not better).

I didn't check if there's a launchpad entry about the led intensity and blinking. If there isn't, we should open one.

---

### Post by mtbsoft on 2008-04-30
> **Keyper7 said:**
> Help us to help you: at least say what is your wireless card...

<snip>

sudo apt-get install linux-backports-modules-hardy

Now disconnect from your wireless network and reload the module with the following commands:

sudo modprobe -r iwl3945
sudo modprobe iwl3945
The light and software switch on my Inspiron 9400 doesn't work since the upgrade but the wireless itself does - the card is a Broadcom (BCM4401-B0) which people seem to say doesn't work.

Would I be likely to get the light and switch working if I backport too?  If it doesn't, could you please tell me how easy it would be to undo the backport (just uninstall it?).

---

### Post by Keyper7 on 2008-04-30
Sorry, mtbsoft, there does not seem to be a broadcom driver in the backport modules package.

---

### Post by Mr_Congeniality on 2008-04-30
running Ubuntu 7.10 here, with iwl3945 on a Vostro 1500.  My only problem seems to be the wireless light.  Oh, and I can't sleep.  Will taking some Claritin knock me out? xD

Oh and also, I tried doing sudo modprobe -r iwl3945 and sudo modprobe iwl3945 and that did nothing but shut down my wireless and my network manager couldn't recognize it again to get it back.

---

### Post by mtbsoft on 2008-04-30
> **Keyper7 said:**
> Sorry, mtbsoft, there does not seem to be a broadcom driver in the backport modules package.
Ah well, the light and switch I can live without since at least the card works!

Thanks anyway.

---

### Post by Keyper7 on 2008-04-30
> **Mr_Congeniality said:**
> running Ubuntu 7.10 here, with iwl3945 on a Vostro 1500.  My only problem seems to be the wireless light.  Oh, and I can't sleep.  Will taking some Claritin knock me out? xD

Oh and also, I tried doing sudo modprobe -r iwl3945 and sudo modprobe iwl3945 and that did nothing but shut down my wireless and my network manager couldn't recognize it again to get it back.

The updated drivers who recognize the light do not ship with Gutsy, I believe. You might try to download the hardy linux-backports-modules package from packages.ubuntu.com and installing it manually, but don't blame me if this screws up your system. =P

If you want to stick with Gutsy, ask in launchpad to backport the updated drivers to Gutsy (if they didn't already).

---

### Post by Gooler on 2008-04-30
Just wanted to say that this also works on the XPS 1330 with 4965AGN card (on Kubuntu 8.04 amd64)

Thanks for the tip.

---

### Post by neur0 on 2008-07-23
Thanks, this worked on my Vostro 1310 also after the restart.

---

### Post by mtbsoft on 2008-07-23
> **Keyper7 said:**
> Sorry, mtbsoft, there does not seem to be a broadcom driver in the backport modules package.
Interestingly I got a subscription e-mail from this thread this morning which made me notice... that the light is now on!!!  I'm guessing that a recent update must have included a fix but I hadn't noticed - I'm a very happy camper now as the soft-key now works as expected and I have my indicator light... even if I do ignore it!

Thanks again for your efforts.

---

### Post by damn66 on 2008-07-24
tks..it works for my M1210 3945 Xubuntu 8.04 as well.

---

### Post by Keyper7 on 2008-07-26
> **mtbsoft said:**
> Interestingly I got a subscription e-mail from this thread this morning which made me notice... that the light is now on!!!  I'm guessing that a recent update must have included a fix but I hadn't noticed - I'm a very happy camper now as the soft-key now works as expected and I have my indicator light... even if I do ignore it!

Thanks again for your efforts.

Hey, that's great! Good to hear.

By the way, for the Intel users out there, I've heard that the iwlwifi drivers in the 2.6.26 kernel supports traffic blinking out-of-the-box, so with a little bit of luck we'll have perfect LED support in Intrepid (and perhaps even in Debian Lenny stable, which will probably have 2.6.26). :)

---

### Post by mtbsoft on 2008-10-16
Not quite sure what is the cause of the change, I pulled some updates last night and updated the ATI drivers today, but...

...the WiFi light is now blinking.  Now I know that some people want this but, frankly, I find it incredibly annoying on my 9400 because of the size and location of the light.  

I know I've got the WiFi activity because of Conky and the fact that the browser is returning results with no cable in the back, I don't need a stupid blink, blink all the time.

Please tell me it can be made to stop blinking and just be on or off... and how to do it.

---

