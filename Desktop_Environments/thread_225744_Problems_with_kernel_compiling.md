---
title: "Problems with kernel compiling"
date: 2006-07-30
forum: Desktop Environments
---

### Post by mozE- on 2006-07-30
When I want to make xconfig I get these lines,so I want to ask is this normaly caused,because i can compile kernel in xconfig,but will be that compiled kernel good?


[HTML]
root@ubuntu:/usr/src/linux-2.6.17.7# make xconfig
scripts/kconfig/qconf arch/i386/Kconfig
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the aut hentication protocols specified are supported and host-based authentication  failed
#
# using defaults found in .config
#
.config:19:warning: trying to assign nonexistent symbol CLEAN_COMPILE
.config:39:warning: trying to assign nonexistent symbol KOBJECT_UEVENT
.config:53:warning: trying to assign nonexistent symbol CC_ALIGN_FUNCTIONS
.config:54:warning: trying to assign nonexistent symbol CC_ALIGN_LABELS
.config:55:warning: trying to assign nonexistent symbol CC_ALIGN_LOOPS
.config:56:warning: trying to assign nonexistent symbol CC_ALIGN_JUMPS
.config:66:warning: trying to assign nonexistent symbol OBSOLETE_MODPARM
.config:144:warning: trying to assign nonexistent symbol X86_UP_APIC_DEFAUL T_OFF
.config:166:warning: trying to assign nonexistent symbol 05GB
.config:167:warning: trying to assign nonexistent symbol 1GB
.config:168:warning: trying to assign nonexistent symbol 2GB
.config:169:warning: trying to assign nonexistent symbol 3GB
.config:210:warning: trying to assign nonexistent symbol ACPI_SBS
.config:220:warning: trying to assign nonexistent symbol ACPI_PCC
.config:221:warning: trying to assign nonexistent symbol ACPI_SONY
.config:229:warning: trying to assign nonexistent symbol ACPI_TC1100
.config:230:warning: trying to assign nonexistent symbol ACPI_INITRD
.config:231:warning: trying to assign nonexistent symbol ACPI_DEV
.config:303:warning: trying to assign nonexistent symbol PCI_LEGACY_PROC
.config:336:warning: trying to assign nonexistent symbol PCMCIA_PROBE_MEM
.config:477:warning: trying to assign nonexistent symbol IP_NF_MATCH_LIMIT
.config:479:warning: trying to assign nonexistent symbol IP_NF_MATCH_MAC
.config:480:warning: trying to assign nonexistent symbol IP_NF_MATCH_PKTTYP E
.config:481:warning: trying to assign nonexistent symbol IP_NF_MATCH_MARK
.config:482:warning: trying to assign nonexistent symbol IP_NF_MATCH_MULTIP ORT
.config:487:warning: trying to assign nonexistent symbol IP_NF_MATCH_AH_ESP
.config:488:warning: trying to assign nonexistent symbol IP_NF_MATCH_LENGTH
.config:490:warning: trying to assign nonexistent symbol IP_NF_MATCH_TCPMSS
.config:491:warning: trying to assign nonexistent symbol IP_NF_MATCH_HELPER
.config:492:warning: trying to assign nonexistent symbol IP_NF_MATCH_STATE
.config:493:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNTR ACK
.config:495:warning: trying to assign nonexistent symbol IP_NF_MATCH_PHYSDE V
.config:497:warning: trying to assign nonexistent symbol IP_NF_MATCH_REALM
.config:498:warning: trying to assign nonexistent symbol IP_NF_MATCH_SCTP
.config:499:warning: trying to assign nonexistent symbol IP_NF_MATCH_DCCP
.config:500:warning: trying to assign nonexistent symbol IP_NF_MATCH_COMMEN T
.config:501:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNMA RK
.config:502:warning: trying to assign nonexistent symbol IP_NF_MATCH_CONNBY TES
.config:504:warning: trying to assign nonexistent symbol IP_NF_MATCH_STRING
.config:510:warning: trying to assign nonexistent symbol IP_NF_TARGET_NFQUE UE
.config:527:warning: trying to assign nonexistent symbol IP_NF_TARGET_MARK
.config:528:warning: trying to assign nonexistent symbol IP_NF_TARGET_CLASS IFY
.config:530:warning: trying to assign nonexistent symbol IP_NF_TARGET_CONNM ARK
.config:533:warning: trying to assign nonexistent symbol IP_NF_TARGET_NOTRA CK
.config:543:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LIMIT
.config:544:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MAC
.config:549:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MULTI PORT
.config:551:warning: trying to assign nonexistent symbol IP6_NF_MATCH_MARK
.config:553:warning: trying to assign nonexistent symbol IP6_NF_MATCH_AHESP
.config:554:warning: trying to assign nonexistent symbol IP6_NF_MATCH_LENGT H
.config:556:warning: trying to assign nonexistent symbol IP6_NF_MATCH_PHYSD EV
.config:560:warning: trying to assign nonexistent symbol IP6_NF_TARGET_NFQU EUE
.config:562:warning: trying to assign nonexistent symbol IP6_NF_TARGET_MARK
.config:611:warning: trying to assign nonexistent symbol IP_DCCP_UNLOAD_HAC K
.config:830:warning: trying to assign nonexistent symbol IEEE80211_1_1_13
.config:831:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_C RYPT_WEP
.config:832:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_C RYPT_CCMP
.config:833:warning: trying to assign nonexistent symbol IEEE80211_1_1_13_C RYPT_TKIP
.config:896:warning: trying to assign nonexistent symbol MTD_CFI_AMDSTD_RET RY
.config:941:warning: trying to assign nonexistent symbol MTD_BLKMTD
.config:1045:warning: trying to assign nonexistent symbol BLK_DEV_CLOOP
.config:1056:warning: trying to assign nonexistent symbol BLK_DEV_GNBD
.config:1077:warning: trying to assign nonexistent symbol BLK_DEV_IDEACPI
.config:1086:warning: symbol value 'm' invalid for BLK_DEV_IDEPNP
.config:1118:warning: trying to assign nonexistent symbol PDC202XX_FORCE
.config:1161:warning: trying to assign nonexistent symbol SCSI_SPI2_ATTRS
.config:1169:warning: trying to assign nonexistent symbol SAS_CLASS
.config:1170:warning: trying to assign nonexistent symbol SAS_DEBUG
.config:1184:warning: trying to assign nonexistent symbol SCSI_AIC94XX
.config:1185:warning: trying to assign nonexistent symbol AIC94XX_DEBUG
.config:1204:warning: trying to assign nonexistent symbol SCSI_ARCMSR
.config:1226:warning: trying to assign nonexistent symbol SCSI_SATA_ACPI
.config:1274:warning: trying to assign nonexistent symbol SCSI_QLA2XXX
.config:1279:warning: trying to assign nonexistent symbol SCSI_QLA6312
.config:1382:warning: trying to assign nonexistent symbol IEEE1394_CMP
.config:1536:warning: trying to assign nonexistent symbol R1000
.config:1559:warning: trying to assign nonexistent symbol NET_IPG
.config:1610:warning: trying to assign nonexistent symbol IPW2100_FS_AMILO_ M7400
.config:1632:warning: trying to assign nonexistent symbol ADM8211
.config:1643:warning: trying to assign nonexistent symbol WLAN_NG
.config:1644:warning: trying to assign nonexistent symbol PRISM2
.config:1645:warning: trying to assign nonexistent symbol PRISM2_USB
.config:1646:warning: trying to assign nonexistent symbol PRISM2_PCI
.config:1647:warning: trying to assign nonexistent symbol PRISM2_PLX
.config:1648:warning: trying to assign nonexistent symbol PRISM2_CS
.config:1649:warning: trying to assign nonexistent symbol NET_ACX
.config:1650:warning: trying to assign nonexistent symbol NET_ACX_PCI
.config:1651:warning: trying to assign nonexistent symbol NET_ACX_USB
.config:1659:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
.config:1660:warning: trying to assign nonexistent symbol NET_RT2600
.config:1661:warning: trying to assign nonexistent symbol NET_RT2500
.config:1662:warning: trying to assign nonexistent symbol NET_RT2400
.config:1663:warning: trying to assign nonexistent symbol NET_RTL818X
.config:1664:warning: trying to assign nonexistent symbol NET_RTL8187
.config:1665:warning: trying to assign nonexistent symbol IPW3945
.config:1666:warning: trying to assign nonexistent symbol IPW3945_DEBUG
.config:1667:warning: trying to assign nonexistent symbol IPW3945_MONITOR
.config:1668:warning: trying to assign nonexistent symbol NET_MRV8K
.config:1717:warning: trying to assign nonexistent symbol VENDOR_SANGOMA
.config:1783:warning: trying to assign nonexistent symbol NDISWRAPPER
.config:1936:warning: trying to assign nonexistent symbol MISDN_DRV
.config:1937:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
.config:1938:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
.config:1939:warning: trying to assign nonexistent symbol MISDN_HFCPCI
.config:1940:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
.config:1941:warning: trying to assign nonexistent symbol MISDN_HFCUSB
.config:1942:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
.config:1943:warning: trying to assign nonexistent symbol MISDN_W6692
.config:1944:warning: trying to assign nonexistent symbol MISDN_DSP
.config:2023:warning: trying to assign nonexistent symbol INPUT_ACERHK
.config:2048:warning: trying to assign nonexistent symbol ECC
.config:2078:warning: trying to assign nonexistent symbol SERIAL_8250_ACPI
.config:2304:warning: trying to assign nonexistent symbol SENSORS_RTC8564
.config:2306:warning: trying to assign nonexistent symbol RTC_X1205_I2C
.config:2316:warning: trying to assign nonexistent symbol W1_MATROX
.config:2317:warning: trying to assign nonexistent symbol W1_DS9490
.config:2318:warning: trying to assign nonexistent symbol W1_DS9490_BRIDGE
.config:2319:warning: trying to assign nonexistent symbol W1_THERM
.config:2320:warning: trying to assign nonexistent symbol W1_SMEM
.config:2322:warning: trying to assign nonexistent symbol W1_DS2433_CRC
.config:2370:warning: trying to assign nonexistent symbol AVERATEC_5100P
.config:2371:warning: trying to assign nonexistent symbol PACKARDBELL_E5
.config:2425:warning: trying to assign nonexistent symbol VIDEO_AUDIO_DECOD ER
.config:2426:warning: trying to assign nonexistent symbol VIDEO_DECODER
.config:2522:warning: trying to assign nonexistent symbol DVB_TDA80XX
.config:2544:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C65 1
.config:2552:warning: trying to assign nonexistent symbol DVB_NXT2002
.config:2565:warning: trying to assign nonexistent symbol DXR3
.config:2566:warning: trying to assign nonexistent symbol EM8300
.config:2567:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
.config:2568:warning: trying to assign nonexistent symbol EM8300_UCODETIMEO UT
.config:2569:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
.config:2570:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
.config:2571:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
.config:2572:warning: trying to assign nonexistent symbol ADV717X
.config:2573:warning: trying to assign nonexistent symbol ADV717X_SWAP
.config:2574:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT 16BIT
.config:2575:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT PAL
.config:2576:warning: trying to assign nonexistent symbol BT865
.config:2602:warning: symbol value 'm' invalid for FB_VESA
.config:2623:warning: trying to assign nonexistent symbol FB_RADEON_OLD
.config:2631:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
.config:2650:warning: trying to assign nonexistent symbol FB_IMAC
.config:2700:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVE R
.config:2813:warning: trying to assign nonexistent symbol BT_ALSA
.config:2819:warning: trying to assign nonexistent symbol OBSOLETE_OSS_DRIV ER
.config:2887:warning: trying to assign nonexistent symbol OBSOLETE_OSS_USB_ DRIVER
.config:2928:warning: trying to assign nonexistent symbol USB_MTOUCH
.config:2929:warning: trying to assign nonexistent symbol USB_ITMTOUCH
.config:2930:warning: trying to assign nonexistent symbol USB_EGALAX
.config:2937:warning: trying to assign nonexistent symbol USB_SYNAPTICS
.config:2938:warning: trying to assign nonexistent symbol USB_CPADDEV
.config:2959:warning: trying to assign nonexistent symbol USB_QC
.config:2960:warning: trying to assign nonexistent symbol USB_SPCA5XX
.config:2961:warning: trying to assign nonexistent symbol USB_PODXTPRO
.config:2963:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
.config:2964:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
.config:2988:warning: trying to assign nonexistent symbol USB_EAGLE
.config:2989:warning: trying to assign nonexistent symbol USB_ZD1211
.config:2990:warning: trying to assign nonexistent symbol USB_ATMEL
.config:2991:warning: trying to assign nonexistent symbol USB_RT2570
.config:3199:warning: trying to assign nonexistent symbol RELAYFS_FS
.config:3208:warning: trying to assign nonexistent symbol ASFS_FS
.config:3209:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODE PAGE
.config:3210:warning: trying to assign nonexistent symbol ASFS_RW
.config:3229:warning: trying to assign nonexistent symbol SQUASHFS
.config:3230:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMP ATIBILITY
.config:3231:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMP ATIBILITY
.config:3239:warning: trying to assign nonexistent symbol UNION_FS
.config:3286:warning: trying to assign nonexistent symbol GFS_FS
.config:3287:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNE SS
.config:3408:warning: trying to assign nonexistent symbol SECURITY_REALTIME
.config:3473:warning: trying to assign nonexistent symbol CLUSTER

[/HTML]

---

### Post by taurus on 2006-07-30
They are just warnings, not error message!!!  Boot to your new kernel and see what happens.  As of always, keep the old working kernel in /boot/grub/menu.lst so in case you need to use it to boot your Ubuntu...

---

