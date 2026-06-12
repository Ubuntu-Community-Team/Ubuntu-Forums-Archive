---
title: "Mini 9 won't connect wirelessly after last batch of updates"
date: 2009-04-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by m_a_b on 2009-04-19
I have a Mini 9 that has been working flawlessly on my wireless network for about 5 months now.  Last night, I let it install updates and now when I tried to connect tot he network, it asks for the password and fails.  I even tried removing all of the security from my wireless connection, broadcasting the ssid, and removed mac filtering and it still will not connect.  At this point I don't know what to do.

---

### Post by m_a_b on 2009-04-19
oh, and looking at the system log, it says:

nm_device_wifi_disable_ encryption(): error setting key for device eth1: Invalid argument

among a whole bunch of other stuff about the activation failing, link timed out, supplicant connection state change, etc.

---

### Post by RedSingularity on 2009-04-20
I had the same problem on my WIND netbook.  Turns out after the kernel update i needed more up to date wireless drivers.  What is your wireless card?  "lspci" in the terminal??

---

### Post by ugm6hr on 2009-04-20
Are you using the standard Dell Ubuntu for Mini 9?

If so, mine continues to work OK.

Presumably, some setting got corrupted during update, or the updates did not complete properly.

Check to ensure you have sufficient HD space:

```
df -h
```

Then try booting into the old kernel, if you have space.

```
gksudo gedit /boot/grub/menu.lst
```

Change the timeout from 0 to 1 (on line 19), then Save
Reboot.

Press Escape at boot time to enter Grub, and select the older kernel (Ubuntu 8.04.1, kernel 2.6.24-19-lpia)

See if that works.

Report back with results.

---

### Post by m_a_b on 2009-04-20
the wireless card is a Broadcom BCM4312

---

### Post by RedSingularity on 2009-04-20
You using the 32 bit install correct?  I found a set of drivers for both.  Oh and have you checked you Hardware Drivers list?  System>Admin>Hardware Drivers.

---

### Post by m_a_b on 2009-04-20
I still have about 11 GB free and am using the standard dell ubuntu.

I booted to the old kernel and, for whatever reason, I am able to connect as long as I broadcast the SSID.  It has worked without broadcasting it since I've had it, but now it isn't.  After it connects I can disable broadcasting and it stays connected, but when I restart, it still won't connect.

When I restart in the new kernel, and the SSID broadcasting, it connects now, but when I disable the SSID broadcast, it still won't connect.

---

### Post by m_a_b on 2009-04-20
> **Shadow121 said:**
> You using the 32 bit install correct?  I found a set of drivers for both.  Oh and have you checked you Hardware Drivers list?  System>Admin>Hardware Drivers.

yes, it is just the standard version that came on it.  

I thought you fixed it because the proprietary driver wasn't in use, but after enabling it and restarting, I still have the same issue.

---

### Post by RedSingularity on 2009-04-20
So now the driver is enabled?  Did you hit the sequence of buttons on the keyboard to turn the adapter on?

---

### Post by m_a_b on 2009-04-20
I guess I can broadcast the SSID until I get this fixed, but I don't really want to leave it like that.  I noticed that one of my neighbors who never had any security set up is broadcasting the SSID "studlyhungwell" - I'm guessing that some kid took over his router!

---

### Post by m_a_b on 2009-04-20
> **Shadow121 said:**
> So now the driver is enabled?  Did you hit the sequence of buttons on the keyboard to turn the adapter on?

I just turned on the proprietary driver and it said to restart, so I did.  As long as my router broadcasts the SSID, I can connect.  Otherwise, it just keeps asking for the password.

---

### Post by RedSingularity on 2009-04-20
Did you try the "connect to hidden wireless network" option?  I am just taking guesses now.  I never worked with a hidden ssid network.

---

### Post by m_a_b on 2009-04-20
yes, it was set up that way.  I even deleted the old profile and made a new one.

---

### Post by ugm6hr on 2009-04-21
Hiding your SSID is not a useful security feature (feel free to do some research on this).

I have had previous problems with Network Manager and hidden SSIDs (I am surprised it worked for you before), and decided not to bother any more.

---

### Post by m_a_b on 2009-04-21
yeah, I know it isn't fail proof and is a pretty easy work around for someone to hack, but I figured that it is easy to do and, until now, didn't affect my connection, and was just one more thing someone had to overcome to hack my router.  I figured that as long as my neighbors have less security than me, then I am relatively safe!

I have used ubuntu on and off for about 3 years, and a few other flavors of linux for longer than that, and I have always used a hidden ssid without issue.

---

### Post by brianchidester on 2009-04-27
What type of encryption are you using?

---

### Post by anjilslaire on 2009-04-27
I've always hidden my SSID, and have no problems connecting to my router. My Mini 9 running 8.10, now 9.04 and seems to like WPA2 Personal.

Also, using MAC filtering is a good idea, too.

---

### Post by m_a_b on 2009-04-27
it is using wpa personal with tkip.

I also use mac filtering and typically hide the ssid.  Like I said, I've had no problems until recently.  I have a 2nd laptop with 8.10 on it and it doesn't have any issues with the hidden ssid either.

---

### Post by jkeating on 2009-04-28
I've had the same problems since updating.  My wireless network is WPA2-Personal with TKIP and also hiding the SSID.  I'm able to connect to the wireless network by first deleting the existing wireless entry and re-creating it.  it sometimes takes 2-3 attempts but eventually works.  a huge pain in the butt since i have to do it every time i power on...

---

### Post by anjilslaire on 2009-04-28
Strangely enough, my mini running 9.04 started acting up yesterday. It would connect to a WPA2 hidden SSID, but I could only browse for a few minutes before it died, yet the NM applet indicated it had full strength. After deleting the profile & recreating with reboots each time, it finally refused entirely, until I could only get it to connect with encryption off. Note, I also rebooted the router a few times to make sure everything was good.

Then suddeny this morning, I tried with a new profile encrypted again with WPA2 AES and hidden, and everything was fine, conecting very quickly.

My router hasn't been rebooted and reconfigured this much in a **long** time...

---

