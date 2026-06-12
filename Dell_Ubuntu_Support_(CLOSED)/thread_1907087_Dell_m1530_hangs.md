---
title: "Dell m1530 hangs"
date: 2012-01-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fpittel on 2012-01-10
I hope this isn't a Dell m1530 only problem but I upgraded my Dell to version 11.10 and noticed that the laptop "freezes" randomly. Most of the time it's while the laptop is in "sleep" mode but from time to time while I'm using it the glidepad simply stops responding, the mouse pointer doesn't move and the buttons stop responding but the keyboard still works. When it freezes while in sleep mode nothing works. When it freezes my only option is to hard reboot by pressing and holding the power button. Anyone else have this problem and better yet know of a solution. :-)

Frank

PS - I checked the logs and there's nothing logged relating to the hang.

---

### Post by fpittel on 2012-01-13
Mixed news. My machine hung and after power cycling the machine I saw an error in the kern.log that pointed to the lwagn driver. A bit of searching with google and it turns out I'm not the only one with the problem.

As there's no way to back out of the upgrade without losing everything on the laptop it looks like my only option is to wait for a fix. Not sure how long I'm going to be interested in living with this before moving to fedora.

Always prefered ubunta on my laptop. It's just useable as is. Oh Well.

---

### Post by mörgæs on 2012-01-13
If you are going to try something new, I would recommend Xubuntu. Has less of the infamous freezing problems.

---

### Post by varunendra on 2012-01-13
> **fpittel said:**
> I saw an error in the kern.log that pointed to the [COLOR=Red]**lwagn**[/COLOR] driver..
Did you mean iwlagn? If so, please post output of:
```
dmesg | grep -i iwlagn | tail -20
```

---

### Post by fpittel on 2012-01-13
> **varunendra said:**
> Did you mean iwlagn? If so, please post output of:
```
dmesg | grep -i iwlagn | tail -20
```

Sorry it was late and I had typed iwlagn so many time I would have thought it was in muscle memory! :D

The output is as follow:

```
[   29.675076] iwlagn 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   29.675116] iwlagn 0000:0b:00.0: setting latency timer to 64
[   29.675150] iwlagn 0000:0b:00.0: pci_resource_len = 0x00002000
[   29.675153] iwlagn 0000:0b:00.0: pci_resource_base = ffffc9000065c000
[   29.675156] iwlagn 0000:0b:00.0: HW Revision ID = 0x0
[   29.675353] iwlagn 0000:0b:00.0: irq 46 for MSI/MSI-X
[   29.675440] iwlagn 0000:0b:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   29.675565] iwlagn 0000:0b:00.0: L1 Enabled; Disabling L0S
[   29.700653] iwlagn 0000:0b:00.0: device EEPROM VER=0x11f, CALIB=0x4
[   29.700658] iwlagn 0000:0b:00.0: Device SKU: 0Xf0
[   29.700673] iwlagn 0000:0b:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   30.386147] iwlagn 0000:0b:00.0: loaded firmware version 8.83.5.1 build 33692
[   39.544117] iwlagn 0000:0b:00.0: L1 Enabled; Disabling L0S
[   39.547128] iwlagn 0000:0b:00.0: Radio type=0x0-0x2-0x0
[   39.701589] iwlagn 0000:0b:00.0: L1 Enabled; Disabling L0S
[   39.704651] iwlagn 0000:0b:00.0: Radio type=0x0-0x2-0x0
[  244.078218] iwlagn 0000:0b:00.0: Tx aggregation enabled on ra = 00:25:9c:39:38:09 tid = 0
```

Also for what it's worth I was running 9.X before the upgrade and the laptop was rock solid stable then.

Frank

---

### Post by varunendra on 2012-01-13
> **fpittel said:**
> Sorry it was late and I had typed iwlagn so many time I would have thought it was in muscle memory! :D

Muscles are subject to fatigue ;)

Anyway, there doesn't seem to be any error. I was (and to some extent still am) expecting it might be a particular wireless connectivity bug associated with iwlagn driver that I had seen a few weeks ago, but don't remember exactly what it was and what was the solution (there certainly was a solution though). Maybe we can find something relevant in the older dmesg file (dmesg.0), or in the normal dmesg message immediately after a restart when it freezes.

It may also help if you can post the error lines about iwlagn you found in kern.log.

And one more output this time:
```
lspci -nnk | grep -iA2 net
```

---

### Post by fpittel on 2012-01-13
> **varunendra said:**
> Muscles are subject to fatigue ;)

Anyway, there doesn't seem to be any error. I was (and to some extent still am) expecting it might be a particular wireless connectivity bug associated with iwlagn driver that I had seen a few weeks ago, but don't remember exactly what it was and what was the solution (there certainly was a solution though). Maybe we can find something relevant in the older dmesg file (dmesg.0), or in the normal dmesg message immediately after a restart when it freezes.

It may also help if you can post the error lines about iwlagn you found in kern.log.

And one more output this time:
```
lspci -nnk | grep -iA2 net
```

The output of the command is:
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
	Subsystem: Dell Device [1028:022e]
	Kernel driver in use: sky2
--
0b:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
	Subsystem: Intel Corporation Device [8086:1001]
	Kernel driver in use: iwlagn


Interestingly enough I only get anything in the kern.log rarely. My theory is the machine locks up tight which prevents the issue from being logged. After my post last night (my second post in the thread) I removed the wifi adaptor and went with wired network and it went without hanging. This to me confirms that it's an issue with the wifi adaptor or driver. I'm leaning to the driver because this wasn't an issue until I upgraded and then the prob turned up instantly.

From kern.log

```


Jan 10 22:06:41 fwp-laptop kernel: [   57.896044] wlan1: no IPv6 routers present
Jan 10 22:06:46 fwp-laptop kernel: [   63.048046] iwlagn 0000:0b:00.0: iwlagn_tx_agg_start on ra = 00:25:9c:39:38:09 tid = 0
Jan 10 22:14:11 fwp-laptop kernel: [  507.577728] iwlagn 0000:0b:00.0: GF was set with SGI:SISO
Jan 10 22:14:11 fwp-laptop kernel: [  507.730422] iwlagn 0000:0b:00.0: GF was set with SGI:SISO
Jan 10 22:14:26 fwp-laptop kernel: [  522.449564] iwlagn 0000:0b:00.0: GF was set with SGI:SISO
Jan 10 22:14:31 fwp-laptop kernel: [  527.444112] iwlagn 0000:0b:00.0: GF was set with SGI:SISO
Jan 10 22:14:37 fwp-laptop kernel: [  533.581649] iwlagn 0000:0b:00.0: GF was set with SGI:SISO
Jan 10 22:14:37 fwp-laptop kernel: [  533.591517] iwlagn 0000:0b:00.0: GF was set with SGI:SISO
Jan 10 23:21:18 fwp-laptop kernel: [ 4534.404050] iwlagn 0000:0b:00.0: iwlagn_tx_agg_start on ra = 00:25:9c:39:38:09 tid = 1
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804112] iwlagn 0000:0b:00.0: Microcode SW error detected.  Restarting 0x92000000.
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804123] iwlagn 0000:0b:00.0: Loaded firmware version: 8.83.5.1 build 33692
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804237] iwlagn 0000:0b:00.0: Start IWL Error Log Dump:
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804243] iwlagn 0000:0b:00.0: Status: 0x000412E4, count: 5
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804249] iwlagn 0000:0b:00.0: 0x00000005 | SYSASSERT                   
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804255] iwlagn 0000:0b:00.0: 0x000024EC | uPc
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804260] iwlagn 0000:0b:00.0: 0x000024C8 | branchlink1
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804265] iwlagn 0000:0b:00.0: 0x000024C8 | branchlink2
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804270] iwlagn 0000:0b:00.0: 0x00000916 | interruptlink1
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804274] iwlagn 0000:0b:00.0: 0x00000000 | interruptlink2
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804279] iwlagn 0000:0b:00.0: 0x000000FF | data1
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804283] iwlagn 0000:0b:00.0: 0x00000489 | data2
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804287] iwlagn 0000:0b:00.0: 0x00000489 | line
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804292] iwlagn 0000:0b:00.0: 0xE540424A | beacon time
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804297] iwlagn 0000:0b:00.0: 0x5E7F6DB6 | tsf low
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804301] iwlagn 0000:0b:00.0: 0x0000011B | tsf hi
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804306] iwlagn 0000:0b:00.0: 0x00000000 | time gp1
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804311] iwlagn 0000:0b:00.0: 0x3F0DB8EA | time gp2
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804316] iwlagn 0000:0b:00.0: 0x00000000 | time gp3
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804320] iwlagn 0000:0b:00.0: 0x00010853 | uCode version
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804325] iwlagn 0000:0b:00.0: 0x00000024 | hw version
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804329] iwlagn 0000:0b:00.0: 0x00480302 | board version
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804334] iwlagn 0000:0b:00.0: 0x0000001C | hcmd
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804339] iwlagn 0000:0b:00.0: CSR values:
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804343] iwlagn 0000:0b:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804374] iwlagn 0000:0b:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480302
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804401] iwlagn 0000:0b:00.0:          CSR_INT_COALESCING: 0X0000ff40
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804429] iwlagn 0000:0b:00.0:                     CSR_INT: 0X80000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804457] iwlagn 0000:0b:00.0:                CSR_INT_MASK: 0X00000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804485] iwlagn 0000:0b:00.0:           CSR_FH_INT_STATUS: 0X40010000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804512] iwlagn 0000:0b:00.0:                 CSR_GPIO_IN: 0X00000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804540] iwlagn 0000:0b:00.0:                   CSR_RESET: 0X00000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804568] iwlagn 0000:0b:00.0:                CSR_GP_CNTRL: 0X080403c5
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804595] iwlagn 0000:0b:00.0:                  CSR_HW_REV: 0X00000024
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804623] iwlagn 0000:0b:00.0:              CSR_EEPROM_REG: 0X00000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804634] iwlagn 0000:0b:00.0:               CSR_EEPROM_GP: 0X90000004
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804646] iwlagn 0000:0b:00.0:              CSR_OTP_GP_REG: 0X00060000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804673] iwlagn 0000:0b:00.0:                 CSR_GIO_REG: 0X00080042
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804701] iwlagn 0000:0b:00.0:            CSR_GP_UCODE_REG: 0X00003eeb
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804728] iwlagn 0000:0b:00.0:           CSR_GP_DRIVER_REG: 0X00000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804756] iwlagn 0000:0b:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804783] iwlagn 0000:0b:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804811] iwlagn 0000:0b:00.0:                 CSR_LED_REG: 0X00000058
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804838] iwlagn 0000:0b:00.0:        CSR_DRAM_INT_TBL_REG: 0X8810225e
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804866] iwlagn 0000:0b:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804894] iwlagn 0000:0b:00.0:             CSR_ANA_PLL_CFG: 0X00880300
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804921] iwlagn 0000:0b:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804949] iwlagn 0000:0b:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804954] iwlagn 0000:0b:00.0: FH register values:
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.804993] iwlagn 0000:0b:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X10234000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805016] iwlagn 0000:0b:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01031b20
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805039] iwlagn 0000:0b:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000030
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805061] iwlagn 0000:0b:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805084] iwlagn 0000:0b:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805107] iwlagn 0000:0b:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07430000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805129] iwlagn 0000:0b:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805152] iwlagn 0000:0b:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805174] iwlagn 0000:0b:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805244] iwlagn 0000:0b:00.0: Start IWL Event Log Dump: display last 20 entries
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805288] iwlagn 0000:0b:00.0: EVT_LOGT:1056862879:0x00000001:0219
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805323] iwlagn 0000:0b:00.0: EVT_LOGT:1056862880:0x01000051:0211
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805358] iwlagn 0000:0b:00.0: EVT_LOGT:1056862883:0x00000000:0212
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805393] iwlagn 0000:0b:00.0: EVT_LOGT:1056863307:0x00000000:0215
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805428] iwlagn 0000:0b:00.0: EVT_LOGT:1056863309:0x00000008:0220
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805446] iwlagn 0000:0b:00.0: EVT_LOGT:1056863329:0x00000000:0301
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805465] iwlagn 0000:0b:00.0: EVT_LOGT:1056863516:0x00000000:0355
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805483] iwlagn 0000:0b:00.0: EVT_LOGT:1056863855:0x02010300:0706
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805502] iwlagn 0000:0b:00.0: EVT_LOGT:1056863859:0x0000001c:0218
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805537] iwlagn 0000:0b:00.0: EVT_LOGT:1056863868:0x02010300:0725
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805571] iwlagn 0000:0b:00.0: EVT_LOGT:1056863869:0x00000000:0710
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805606] iwlagn 0000:0b:00.0: EVT_LOGT:1056863870:0x00000004:0729
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805640] iwlagn 0000:0b:00.0: EVT_LOGT:1056863871:0x5e702b4a:0729
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805675] iwlagn 0000:0b:00.0: EVT_LOGT:1056863890:0x000003ff:1062
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805710] iwlagn 0000:0b:00.0: EVT_LOGT:1056863893:0x02020202:1074
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805745] iwlagn 0000:0b:00.0: EVT_LOGT:1056863899:0x00000325:1074
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805779] iwlagn 0000:0b:00.0: EVT_LOGT:1056863903:0x00000000:1208
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805814] iwlagn 0000:0b:00.0: EVT_LOGT:1056863907:0x00000003:0733
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805832] iwlagn 0000:0b:00.0: EVT_LOGT:1056863909:0x00000004:0716
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.805851] iwlagn 0000:0b:00.0: EVT_LOGT:1057863919:0x00000000:0125
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.806276] ieee80211 phy0: Hardware restart was requested
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.870244] iwlagn 0000:0b:00.0: Stopping AGG while state not ON or starting
Jan 10 23:35:28 fwp-laptop kernel: [ 5384.870254] iwlagn 0000:0b:00.0: queue number out of range: 0, must be 10 to 19
Jan 10 23:36:42 fwp-laptop kernel: [ 5458.964090] iwlagn 0000:0b:00.0: iwlagn_tx_agg_start on ra = 00:25:9c:39:38:09 tid = 0
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804044] iwlagn 0000:0b:00.0: Microcode SW error detected.  Restarting 0x92000000.
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804051] iwlagn 0000:0b:00.0: Loaded firmware version: 8.83.5.1 build 33692
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804337] iwlagn 0000:0b:00.0: Start IWL Error Log Dump:
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804341] iwlagn 0000:0b:00.0: Status: 0x000412E4, count: 5
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804345] iwlagn 0000:0b:00.0: 0x00000005 | SYSASSERT                   
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804348] iwlagn 0000:0b:00.0: 0x000024EC | uPc
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804351] iwlagn 0000:0b:00.0: 0x000024C8 | branchlink1
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804354] iwlagn 0000:0b:00.0: 0x000024C8 | branchlink2
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804357] iwlagn 0000:0b:00.0: 0x00000916 | interruptlink1
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804359] iwlagn 0000:0b:00.0: 0x00000000 | interruptlink2
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804362] iwlagn 0000:0b:00.0: 0x000000FF | data1
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804365] iwlagn 0000:0b:00.0: 0x00000489 | data2
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804367] iwlagn 0000:0b:00.0: 0x00000489 | line
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804370] iwlagn 0000:0b:00.0: 0xDC804DA9 | beacon time
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804373] iwlagn 0000:0b:00.0: 0x76A95257 | tsf low
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804375] iwlagn 0000:0b:00.0: 0x0000011B | tsf hi
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804378] iwlagn 0000:0b:00.0: 0x00000000 | time gp1
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804381] iwlagn 0000:0b:00.0: 0x182185D7 | time gp2
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804384] iwlagn 0000:0b:00.0: 0x00000000 | time gp3
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804386] iwlagn 0000:0b:00.0: 0x00010853 | uCode version
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804389] iwlagn 0000:0b:00.0: 0x00000024 | hw version
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804392] iwlagn 0000:0b:00.0: 0x00480302 | board version
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804395] iwlagn 0000:0b:00.0: 0x0A03001C | hcmd
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804397] iwlagn 0000:0b:00.0: CSR values:
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804400] iwlagn 0000:0b:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804429] iwlagn 0000:0b:00.0:        CSR_HW_IF_CONFIG_REG: 0X00480302
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804440] iwlagn 0000:0b:00.0:          CSR_INT_COALESCING: 0X0000ff40
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804447] iwlagn 0000:0b:00.0:                     CSR_INT: 0X90000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804459] iwlagn 0000:0b:00.0:                CSR_INT_MASK: 0X00000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804486] iwlagn 0000:0b:00.0:           CSR_FH_INT_STATUS: 0X40010000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804497] iwlagn 0000:0b:00.0:                 CSR_GPIO_IN: 0X00000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804508] iwlagn 0000:0b:00.0:                   CSR_RESET: 0X00000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804520] iwlagn 0000:0b:00.0:                CSR_GP_CNTRL: 0X080403c5
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804531] iwlagn 0000:0b:00.0:                  CSR_HW_REV: 0X00000024
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804543] iwlagn 0000:0b:00.0:              CSR_EEPROM_REG: 0X00000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804554] iwlagn 0000:0b:00.0:               CSR_EEPROM_GP: 0X90000004
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804561] iwlagn 0000:0b:00.0:              CSR_OTP_GP_REG: 0X00060000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804572] iwlagn 0000:0b:00.0:                 CSR_GIO_REG: 0X00080042
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804584] iwlagn 0000:0b:00.0:            CSR_GP_UCODE_REG: 0X0000eaf0
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804595] iwlagn 0000:0b:00.0:           CSR_GP_DRIVER_REG: 0X00000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804607] iwlagn 0000:0b:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804618] iwlagn 0000:0b:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804629] iwlagn 0000:0b:00.0:                 CSR_LED_REG: 0X00000058
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804641] iwlagn 0000:0b:00.0:        CSR_DRAM_INT_TBL_REG: 0X8810225e
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804652] iwlagn 0000:0b:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804660] iwlagn 0000:0b:00.0:             CSR_ANA_PLL_CFG: 0X00880300
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804671] iwlagn 0000:0b:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804682] iwlagn 0000:0b:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804685] iwlagn 0000:0b:00.0: FH register values:
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804746] iwlagn 0000:0b:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X10234000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804808] iwlagn 0000:0b:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X01031b20
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804872] iwlagn 0000:0b:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X000000b8
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804919] iwlagn 0000:0b:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80819104
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.804965] iwlagn 0000:0b:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805018] iwlagn 0000:0b:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07430000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805068] iwlagn 0000:0b:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805114] iwlagn 0000:0b:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805152] iwlagn 0000:0b:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805330] iwlagn 0000:0b:00.0: Start IWL Event Log Dump: display last 20 entries
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805391] iwlagn 0000:0b:00.0: EVT_LOGT:0403845918:0x000001da:0601
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805425] iwlagn 0000:0b:00.0: EVT_LOGT:0403845919:0x00000368:0632
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805476] iwlagn 0000:0b:00.0: EVT_LOGT:0403846027:0x00000113:0106
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805527] iwlagn 0000:0b:00.0: EVT_LOGT:0403846029:0x00000000:0301
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805561] iwlagn 0000:0b:00.0: EVT_LOGT:0403846216:0x00000000:0355
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805595] iwlagn 0000:0b:00.0: EVT_LOGT:0403848510:0x00000113:0106
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805629] iwlagn 0000:0b:00.0: EVT_LOGT:0403848512:0x00000000:0302
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805680] iwlagn 0000:0b:00.0: EVT_LOGT:0403848534:0x00000440:0323
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805729] iwlagn 0000:0b:00.0: EVT_LOGT:0403848538:0x00000000:0355
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805764] iwlagn 0000:0b:00.0: EVT_LOGT:0403848539:0x00000480:0367
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805799] iwlagn 0000:0b:00.0: EVT_LOGT:0403848540:0x00000814:0353
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805837] iwlagn 0000:0b:00.0: EVT_LOGT:0403848612:0x00000113:0106
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805872] iwlagn 0000:0b:00.0: EVJan 10 23:42:13 fwp-laptop kernel: [ 5789.805908] iwlagn 0000:0b:00.0: EVT_LOGT:0403848626:0x00002000:0350
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805943] iwlagn 0000:0b:00.0: EVT_LOGT:0403848828:0x00000113:0106
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.805976] iwlagn 0000:0b:00.0: EVT_LOGT:0403848830:0x00000000:0302
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.806012] iwlagn 0000:0b:00.0: EVT_LOGT:0403848842:0x00002000:0350
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.806046] iwlagn 0000:0b:00.0: EVT_LOGT:0403850128:0x000004b3:0511
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.806095] iwlagn 0000:0b:00.0: EVT_LOGT:0403850129:0x00000000:0512
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.806130] iwlagn 0000:0b:00.0: EVT_LOGT:0404850139:0x00000000:0125
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.806476] ieee80211 phy0: Hardware restart was requested
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.883296] iwlagn 0000:0b:00.0: Stopping AGG while state not ON or starting
Jan 10 23:42:13 fwp-laptop kernel: [ 5789.883303] iwlagn 0000:0b:00.0: queue number out of range: 0, must be 10 to 19
Jan 10 23:42:14 fwp-laptop kernel: [ 5790.688115] iwlagn 0000:0b:00.0: iwlagn_tx_agg_start on ra = 00:25:9c:39:38:09 tid = 0
Jan 10 23:45:34 fwp-laptop kernel: [ 5990.280092] iwlagn 0000:0b:00.0: GF was set with SGI:SISO
Jan 10 23:45:38 fwp-laptop kernel: [ 5994.446230] iwlagn 0000:0b:00.0: GF was set with SGI:SISO
Jan 10 23:45:42 fwp-laptop kernel: [ 5998.834155] iwlagn 0000:0b:00.0: GF was set with SGI:SISO
Jan 10 23:52:18 fwp-laptop kernel: [ 6394.742974] CE: hpet increased min_delta_ns to 20113 nsec
Jan 12 12:48:27 fwp-laptop kernel: imklog 5.8.1, log source = /proc/kmsg started.
Jan 12 12:48:27 fwp-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 12 12:48:27 fwp-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 12 12:48:27 fwp-laptop kernel: [    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
Jan 12 12:48:27 fwp-laptop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=b23784cc-3d42-4ba8-930a-42fe9b56d844 ro quiet splash vt.handoff=T_LOGT:0403848614:0x00000000:0302


```

The last few lines of course being the start of the reboot.

---

### Post by varunendra on 2012-01-14
As a quick shot purely based on guess, please try:
```

sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
..and see if there is any improvement. If yes, we'll need to make this change permanent. If not, a restart will reset the effects of above changes. Then please post outputs of the following (while you are connected via wifi, and have done a couple of minutes' browsing):

```
uname -rm
ifconfig -a
iwconfig
sudo lshw -C network
lsmod
```

---

### Post by fpittel on 2012-01-14
> **varunendra said:**
> As a quick shot purely based on guess, please try:
```

sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
..and see if there is any improvement. If yes, we'll need to make this change permanent. If not, a restart will reset the effects of above changes. Then please post outputs of the following (while you are connected via wifi, and have done a couple of minutes' browsing):

```
uname -rm
ifconfig -a
iwconfig
sudo lshw -C network
lsmod
```

I made the change but that seems to lock the speed to 54Mb and means I lose reason for spending money on a wifi hub and card that supports N. May be acceptable for the short term but hardly a long term fix. Don't know if this even fixes the problem (will know in the morning) of the laptop crashing but it's not a long term solution.

---

### Post by varunendra on 2012-01-14
> **fpittel said:**
> but it's not a long term solution.
..definitely not! It is just a temporary workaround until gets fixed. For the time being, please follow this to make the changes permanent (can undo by reverting the same changes, when you think it's fixed): [http://ubuntuforums.org/showpost.php?p=11360822&postcount=6](http://ubuntuforums.org/showpost.php?p=11360822&postcount=6)

I've read some posts that say it has been fixed in 3.2.x.x kernels, so you may try one of them by downloading and installing from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Hope you can confirm the 'real fix'. Please keep us posting of any updates you find.

---

### Post by fpittel on 2012-01-14
> **varunendra said:**
> ..definitely not! It is just a temporary workaround until gets fixed. For the time being, please follow this to make the changes permanent (can undo by reverting the same changes, when you think it's fixed): [http://ubuntuforums.org/showpost.php?p=11360822&postcount=6](http://ubuntuforums.org/showpost.php?p=11360822&postcount=6)

I've read some posts that say it has been fixed in 3.2.x.x kernels, so you may try one of them by downloading and installing from here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Hope you can confirm the 'real fix'. Please keep us posting of any updates you find.

Didn't see any instructions at the link for the kernel on how to actually install the new kernel. Does it go in as deb package? After a nights sleep I've decided that I can live with just "G" for 4-5 months at least before I'll need "N" for it's range so I'll just wait for the new kernel to come through in the upgrade process. I have to admit being a bit concerned about not seeing updates come through in the update manager. I may have to look into how it's configured. :D

In any case I'm sorry for any bad tone I had in my posts (venting a bit of frustration) and want to thank you for all your help.

---

### Post by varunendra on 2012-01-14
> **fpittel said:**
> In any case I'm sorry for any bad tone I had in my posts (venting a bit of frustration) and want to thank you for all your help.
You're welcome and the frustration is obvious and any consequent reactions are perfectly understandable. :)

As for the link to the kernel-ppa, scroll to the bottom of the linked page > click the latest 3.2 series directory for oneiric (assuming newer is better) > then download .deb files of both 'image' and 'headers' for your architecture (i386 for 32bit, or amd64 for 64bit).
As for now, this one seems to be the exact link for you: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/)

To install them, you just have to double-click them and proceed as prompted.

But be warned:

[LIST=1]
[*]I have never installed a kernel this way myself, so can't say if it has the potential to break things
[*]assuming it does have the potential to break the current setup, you might want to create a backup of the current installation using either [clonezilla]("http://clonezilla.org/clonezilla-live.php") or [remastersys]("http://www.geekconnection.org/remastersys/") (better- if the setup can fit on a DVD after necessary stripping). This way, you can always return to the present state in case things get worse (having a backup of a working system is always a good idea anyway)
[/LIST]

---

