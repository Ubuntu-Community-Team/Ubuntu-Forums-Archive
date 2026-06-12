---
title: "applications crashing cause unknown"
date: 2010-10-09
forum: Desktop Environments
---

### Post by complience on 2010-10-09
I am getting random crashes happening to my applications (firefox, chrome, chromium, mythtv)

I can not identify the cause, the final log output will often shown a segmentation fault, below is the log from the last time chrome crashed - it doesnt seem to like something and once it built up i think it just gives up.

```


Oct  9 18:41:21 antec-ubuntu kernel: [ 1591.489951] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct  9 18:41:26 antec-ubuntu kernel: [ 1596.600248] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1713
Oct  9 18:41:26 antec-ubuntu kernel: [ 1596.600597] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:41:52 antec-ubuntu kernel: [ 1621.796397] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:41:52 antec-ubuntu kernel: [ 1621.796739] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:41:52 antec-ubuntu kernel: [ 1622.301655] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct  9 18:41:57 antec-ubuntu kernel: [ 1627.411925] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1421
Oct  9 18:42:07 antec-ubuntu kernel: [ 1637.427526] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:42:07 antec-ubuntu kernel: [ 1637.427875] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:42:54 antec-ubuntu kernel: [ 1683.689361] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1384
Oct  9 18:42:54 antec-ubuntu kernel: [ 1683.733815] __ratelimit: 21 callbacks suppressed
Oct  9 18:42:54 antec-ubuntu kernel: [ 1683.733826] chromium-browse[2189]: segfault at 77f954872110 ip 00007ff9614a923d sp 00007fffa9458ee0 error 4 in chromium-browser[7ff9606de000+2ca8000]
Oct  9 18:44:54 antec-ubuntu kernel: [ 1803.685685] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:46:16 antec-ubuntu kernel: [ 1886.583169] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct  9 18:46:22 antec-ubuntu kernel: [ 1891.693426] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1610
Oct  9 18:46:32 antec-ubuntu kernel: [ 1901.709028] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1384
Oct  9 18:46:32 antec-ubuntu kernel: [ 1901.709960] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:46:32 antec-ubuntu kernel: [ 1901.880032] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct  9 18:46:37 antec-ubuntu kernel: [ 1906.904780] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1421
Oct  9 18:46:47 antec-ubuntu kernel: [ 1916.915308] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1421
Oct  9 18:46:57 antec-ubuntu kernel: [ 1926.926478] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:46:57 antec-ubuntu kernel: [ 1926.926789] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:47:24 antec-ubuntu kernel: [ 1954.062316] chromium-browse[2511]: segfault at 77f965a63b59 ip 00007ff961d31b35 sp 00007fffa9457e70 error 4 in chromium-browser[7ff9606de000+2ca8000]
Oct  9 18:47:32 antec-ubuntu kernel: [ 1961.784709] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct  9 18:47:37 antec-ubuntu kernel: [ 1966.890386] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1760
Oct  9 18:47:37 antec-ubuntu kernel: [ 1966.890738] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:47:52 antec-ubuntu kernel: [ 1981.897690] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1384
Oct  9 18:47:52 antec-ubuntu kernel: [ 1981.897998] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:48:04 antec-ubuntu kernel: [ 1993.673635] nm-dispatcher.a[2632]: segfault at 77a612f5be98 ip 00007fa612f6b750 sp 00007fff850a8d00 error 4 in ld-2.11.1.so[7fa612f5d000+20000]
Oct  9 18:48:54 antec-ubuntu kernel: [ 2043.688848] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:49:34 antec-ubuntu kernel: [ 2083.690737] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1425
Oct  9 18:50:34 antec-ubuntu kernel: [ 2143.687998] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:50:54 antec-ubuntu kernel: [ 2163.939174] lo: Disabled Privacy Extensions
Oct  9 18:51:54 antec-ubuntu kernel: [ 2223.689828] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:53:34 antec-ubuntu kernel: [ 2323.690718] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:55:34 antec-ubuntu kernel: [ 2443.689267] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:56:16 antec-ubuntu kernel: [ 2486.196486] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:56:16 antec-ubuntu kernel: [ 2486.196819] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:56:20 antec-ubuntu kernel: [ 2489.990101] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct  9 18:56:25 antec-ubuntu kernel: [ 2495.100401] ===>rt_ioctl_giwscan. 7(7) BSS returned, data->length = 1234
Oct  9 18:57:34 antec-ubuntu kernel: [ 2563.691765] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:57:54 antec-ubuntu kernel: [ 2584.095237] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:57:54 antec-ubuntu kernel: [ 2584.095576] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:57:56 antec-ubuntu kernel: [ 2585.983407] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct  9 18:58:01 antec-ubuntu kernel: [ 2591.090702] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 18:58:01 antec-ubuntu kernel: [ 2591.091037] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 18:59:34 antec-ubuntu kernel: [ 2683.690112] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 19:01:34 antec-ubuntu kernel: [ 2803.692183] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 19:03:34 antec-ubuntu kernel: [ 2923.690810] ===>rt_ioctl_giwscan. 8(8) BSS returned, data->length = 1384
Oct  9 19:04:28 antec-ubuntu kernel: [ 2978.094247] ===>rt_ioctl_giwscan. 6(6) BSS returned, data->length = 1047
Oct  9 19:04:28 antec-ubuntu kernel: [ 2978.094603] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 19:04:30 antec-ubuntu kernel: [ 2979.974798] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Oct  9 19:04:35 antec-ubuntu kernel: [ 2985.084782] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 19:04:35 antec-ubuntu kernel: [ 2985.084925] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=7)
Oct  9 19:05:34 antec-ubuntu kernel: [ 3043.690095] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1571
Oct  9 19:05:50 antec-ubuntu kernel: [ 3060.564190] chromium-browse[2112]: segfault at 774cb609ef68 ip 00007f4cadc046dc sp 00007fff2bc52960 error 6 in libglib-2.0.so.0.2400.1[7f4cadba8000+db000]

```

---

### Post by inobe on 2010-10-09
atheros driver & chrome "problem" maybe

upgrading kernel to 2.6.34rc7 a few claim it fixing the issue, some turned off bookmark sync.....

here's the bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546871](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546871)

i started here

[http://www.google.com/search?q=chrome+ERROR!!!+RTMPCancelTimer+failed%2C&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=chrome+ERROR!!!+RTMPCancelTimer+failed%2C&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

and looked here

[http://www.google.com/search?q=chrome+ERROR!!!+RTMPCancelTimer+failed%2C&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#sclient=psy&hl=en&safe=active&client=firefox-a&hs=4G0&rls=org.mozilla:en-US%3Aofficial&source=hp&q=ERROR!!!+RTMPCancelTimer+failed%2C&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=9f2370386c77b788](http://www.google.com/search?q=chrome+ERROR!!!+RTMPCancelTimer+failed%2C&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#sclient=psy&hl=en&safe=active&client=firefox-a&hs=4G0&rls=org.mozilla:en-US%3Aofficial&source=hp&q=ERROR!!!+RTMPCancelTimer+failed%2C&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=9f2370386c77b788)

---

### Post by complience on 2010-10-09
Hi inobe

Thanks for your help but I really dont think this is a 'chrome' specific issue because other applications are randomly crashing also. MythTV, FF, Chromium.

I have a feeling the browsers are crashing when they encounter flash or some other media embedded in certain pages.

---

### Post by inobe on 2010-10-09
> **complience said:**
> Hi inobe

Thanks for your help but I really dont think this is a 'chrome' specific issue because other applications are randomly crashing also. MythTV, FF, Chromium.

I have a feeling the browsers are crashing when they encounter flash or some other media embedded in certain pages.

lets assume it's a kernel module, we can upgrade the kernel with fingers crossed.

you can give me your make and model of pc and 

```
lspci
```

obviously it's some driver

---

### Post by complience on 2010-10-10
lspci
```
00:00.0 Host bridge: ATI Technologies Inc RD890 Northbridge only single slot PCI-e GFX Hydra part (rev 02)
00:02.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port D)
00:05.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port E)
00:06.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port F)
00:07.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port G)
00:09.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
04:00.0 Network controller: RaLink RT2860
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
08:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
08:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
08:06.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
08:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
09:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)
09:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02)

```

---

### Post by complience on 2010-10-10
I think the kernel upgrade might be a good idea

Ive read that other people who encountered the RTMPcancanceltimer error shown in my logs found changing the kernel helped.

apparently its a wifi issue - which would make sense because i often have alot problems with continually dropping my connection and the browsers crashing.

ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!

---

### Post by inobe on 2010-10-10
> **complience said:**
> I think the kernel upgrade might be a good idea

Ive read that other people who encountered the RTMPcancanceltimer error shown in my logs found changing the kernel helped.

apparently its a wifi issue - which would make sense because i often have alot problems with continually dropping my connection and the browsers crashing.

ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!

let us know how that works, this may be useful for many.

---

### Post by complience on 2010-10-11
how should I go about upgrading the kernal?

would installing the latest 10.10 do the trick?

---

### Post by vek on 2010-10-11
10.10 does have a much more modern kernel.

Have you tried running memtestx86?  It should be in your boot options - when this happened to me it turned out to be bad RAM reads due to motherboard malfunction.  It would be fine for 1 or 2 tests in MEMTEST but then suddenly the bad reads would reveal themselves 20 minutes into the test.  Even if it shows up that everythings fine it really is good to get a baseline sanity check.

---

### Post by complience on 2010-10-11
I have run memory tests - all clean.

And changed the memory and motherboard twice.

:mad: so getting fairly vexed ](*,)

---

