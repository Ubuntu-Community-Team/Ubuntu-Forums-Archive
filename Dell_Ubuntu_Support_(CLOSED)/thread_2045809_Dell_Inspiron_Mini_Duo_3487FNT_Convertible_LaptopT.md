---
title: "Dell Inspiron Mini Duo 3487FNT Convertible Laptop/Tablet"
date: 2012-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hank22077 on 2012-08-21
I recently purchased a Dell Inspiron Mini Duo 3487FNT Convertible Laptop/Tablet. The specs: 

Intel Atom N550 Processor (1.5GHz); 2GB RAM; 320GB Hard Drive; Wireless  802.11n / Bluetooth Combo Card; 10.1" Widescreen HD (1366X768 )  Multi-Touch Display; Integrated Intel NM10 Express graphics; and Windows  7 Home Premium pre-installed.

I decided to dual boot with Ubuntu 12.04LTS. BUT, I'm having some issues.I partitioned my hard drive to allocate space for Ubuntu 12.04LTS.
Booted using USB port/flash drive. 
Was prompted during install to connect to my wireless router; and, everything went well, for a few days.

Now, however, each time I try to use Ubuntu the signal goes in and out, I'll have to re-enter the passcode, etc.
The wireless connection on Windows 7 has no issues; and, my kids share an old laptop with Windows XP, which has no issues.

I'm not real keen on this, but it seemed that Ubuntu had saved my  wireless connection during install, and was automatically connecting to  it just fine for the first few days. Now, I can't keep the connection.

Any insight out there?



:confused:

Thanks!

---

### Post by Favux on 2012-08-22
Are you saying when you first boot it connects but then later you lose it?  Does that happen after a sleep or hibernation?

If you have to enter the password every time when it first starts then check in Network Manager that the password is still there and saved.  Because entering it in the prompt Network Manager gives you during Desktop start up doesn't save it.  That happens to me occasionally.  I think the most recent was about a week ago and it seems to me there was a Network Manager update around the same time.  After entering the password a few times I finally opened up Network Manager and found out it wasn't saved.  So I entered it and saved it and was good to go.

---

### Post by hank22077 on 2012-08-22
No, unfortunately, it will often go in and out during regular use.
I have saved it and checked the box to automatically connect.
Did you ever experience that?

Thanks for helping.

---

### Post by Favux on 2012-08-22
Not on my tablet PC.  Originally it was a real problem child because it had a Broadcom chipset and I had to tweak the WPA2 security settings to get it to work.  Quite the pain to figure it out.

I have started to experience signal dropping and coming back on my ARM touchscreen slote and that is frustrating so I know how you're feeling.  I've been wondering if it is hardware related.

Unfortunately I'm not a wireless guru.  There used to be several who hung out on the forums and were very helpful.  You'd just post your question on their thread.  Haven't seen them around much lately.  I guess folks don't have as much trouble since Broadcom got their act together.

Even if they don't respond their threads still have a bunch of useful diagnostics you can run through.  For example what does your Wireless 802.11n / Bluetooth Combo Card show up as when you run **lspci** in a terminal?  Be nice to have the OEM and any other info. that provides to google with.

---

### Post by hank22077 on 2012-08-22
WOW!

I don even know what all this means:


 lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Multimedia controller: Broadcom Corporation BCM70015 Video Decoder [Crystal HD]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


:confused:

---

### Post by Favux on 2012-08-22
Well for wireless it looks like this is the line:
```
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```
So you have a **Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)** 802.11n wifi chipset.  Now you can tell folks what your hardware is which helps them help you and you have something to google with and see if others are having the same problem and how they fixed it.  :)

---

### Post by hank22077 on 2012-08-22
Good. Thank you very much.
I'll use that to try to find answers.

Much appreciated...btw, is any of that info potentially risky to have on here for 'snoopers'?

---

### Post by Favux on 2012-08-22
No.  Now if you were posting passwords in the clear...  :)

---

### Post by hank22077 on 2012-08-22
Haha, ok;
just wondered, if the details could be used to get through my router firewall.
Glad it can't

Thanks

---

### Post by hank22077 on 2012-08-26
Well, I'm not sure how it happened, but this seems to have resolved itself, for now.
I'll keep this open, til I'm sure I have no more issues.
Thanks.

---

