---
title: "Dell XPS 15 L502X"
date: 2011-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Al-amin on 2011-10-21
Processor: intel(R) core(TM) i5-2410M CPU @ 2.30GHz
Installed memory (RAM): 4.00GB
Ubuntu 10.10 32-bit

Hello.... I just installed ubuntu 10.10, after the installation everything seems to be working just fine, but the wi-fi is not. When I press the dedicated button for the wi-fi, it does not turn on nor does it detect my router. I have seen other people with same problem with this laptop model. Is there a fix for this... Please let me know asap. I started using ubuntu in my previous laptop, ever since I started hating windows... So please help me out.

---

### Post by Hanine on 2011-10-22
Try the 11.10. It should work. If not. You have to report a hardware compatibility issue.

---

### Post by cozumel on 2011-10-22
I did a fresh install 11.10 x64 to L502x about a week ago. Detected my intel centrino no problem.  Just had to enter WPA key.  So maybe you should try 11.10 like Hanine says.

---

### Post by Al-amin on 2011-10-22
> **cozumel said:**
> I did a fresh install 11.10 x64 to L502x about a week ago. Detected my intel centrino no problem.  Just had to enter WPA key.  So maybe you should try 11.10 like Hanine says.


Thank you. should i download 64 bit or 32 bit.... the site says that 32 bit is recommended.... and what if i have the same problem after installing ubuntu 11.10...... is ur one working alright after installing ubuntu 11.10?

---

### Post by cozumel on 2011-10-22
Hi,

Out of interest, which site says you should install 32bit? (Link please)

I installed x64 as the laptop is x64 architecture.  Everything seems to be working so far.  The only glitches are TV card not working (Philips chipset not supported) and me fouling up the sound (but I will rectify).  Spending all my time trying to get Optimus NVidia working (and think I have it switching ok - just need to do some testing).

Anyhow, back to the Wifi.  I have the Intel Centrino 1030 wireless N / Bluetooth combo card and is working fine.  I setup the wireless WPA key from the LiveCD before install so that the Ubuntu installer could download updates during installation.  Then I had to reload the WPA key again after reboot once the install had completed.

---

### Post by Al-amin on 2011-10-22
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download). changing the WPA key meaning i have to change my routers password system?..... please specify. because i dont know much.... and thank you for your help so far. i have downloaded X64, now i need to burn it in a cd. now before i can install it i need to be clear about the WPA key.... and the things that are needed to be done..... thank you

---

### Post by cozumel on 2011-10-23
Okay.  Ubuntu recommends 32bit as it more likely to work with most systems but since you have x64 architecture I recommend x64 installation.

WPA key is an encryption key to protect your data and potential unauthorised access to your system via wireless.  Not all routers/devices have WPA key, yours might be WPA2 or WEP.  I have mine written down and it also on the back of my router.  Full description of encryption keys: [http://windows.microsoft.com/en-GB/windows7/Set-up-a-security-key-for-a-wireless-network]("http://windows.microsoft.com/en-GB/windows7/Set-up-a-security-key-for-a-wireless-network")

When you boot from your LiveCD into Ubuntu you will see an icon on the top indicator bar for wireless connections (by the volume and battery icons).  Right click on it and choose your router/network ID name.  You should then be asked for your encryption key which you need to enter and then you will be connected to internet.

Commence install.

---

### Post by Hanine on 2011-10-30
Hi back,

As said by Cozumel, just do an install of 11.10 (X64) not 32.
The Dell XPS L502X was tested and it is working fine.

Make sure to do an update after the fresh install.

Command:    sudo apt-get update

As for Optimus Nvidia Technology: Check Bumblebee project. It supports Nvidia Optimus for Ubuntu.

The remaining mystery about this system is the external screen through HDMI and Mini DisplayPort. None can tell if it is working or not under 11.10 (they don't under previous releases)!

---

### Post by 14quartz on 2012-02-20
May be this is not the correct thread but can anyone help m how to change the dedicated key combination for wifi in Dell XPS 15(ubuntu 11.10).

---

