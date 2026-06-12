---
title: "wifi on my  mini 10v stopped working on 10.10, and works sometimes on pinguy os"
date: 2010-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by teklife on 2010-11-17
after working fine right after the install of ubuntu 10.10, my wi-fi, now no longer works. 

mint 10, never worked out of the box.

pinguy os, wifi worked well right out of the box, but drops often, and usually when it does, i can no longer connect to, or detect any wireless networks. 

any ideas why?

surprising to me that in the latest ubuntu, the wireless worked in ubuntu proper, and pinguy os, but not mint... what's up with that? in the past, i think it was the other way around, mint worked with my broadcom wireless card, but not ubuntu (pinguy is new to me, and quite nice, but not without some niggles).

cheers,
ss

---

### Post by Megaptera on 2010-11-17
Hi,
Have you tried this guide?

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by teklife on 2011-01-04
thanks for the help megaptera, but since, at the time, a wired connection was not an option, that guide was useless to me. 

after months of distro hopping, i have finally settled on pinguy os... really love it; i think it's by far the best out of the box linux user experience. however, i have a problem with the wireless dropping on me and then i cannot reconnect or i have to do a bunch of stuff in order to get a wireless connection again, like rebooting several times. 

maybe i have not spent enough time out there, but when i go out to my brother's house in the suburbs the wireless behaves so much better. i have not had it drop out there, although i'm not on the computer as long either. there are only 2 networks out there, his and some neighbors with a very weak signal. where i live, in a small nyc building, there are a LOT of wireless networks (20+ sometimes); could that be why i'm getting disconnected so much and having trouble re-connecting? interference? if so, why would it not affect the same computer when i'm booted into the mac os side?

---

### Post by Bucky Ball on 2011-01-04
Teklife, are you using kernel 2.6.35-24???

There are known issues and currently active bug reports with this kernel. One of those issues is that the kernel is crashing Broadcom cards. Did it stop working after a kernel upgrade? Can you try 2.6.35-22 or 23, see if you have the same issue, and get back to us?

I would personally go for 10.04 LTS. More reliable for the moment and extra year's support over 10.10. :)

---

### Post by teklife on 2011-01-06
interestingly enough, i noticed that the wireless on my woman's netbook died immediately after an update, which updated the kernel from -23 to -24

i reverted to -23 and deleted the -24 kernel and it's working fine again (at least the wireless is) her wifi card is bcm4313, mine is bcm4312.

i am running -24, but my wireless actually works -for a bit anyways, vs nothing at all for her. on some networks it even works for a long period of time, and at my brothers house (few ssid's) seemed like it would work indefinitely. however, the circumstances at home are much different. 

thanks for the info. i had considered doing it, but since it works sometimes, vs not at all, never did. i will revert back to an older kernel and report back if the reliability of the signal changes. 

cheers

---

### Post by teklife on 2011-01-06
accidentally posted a huge reply twice. how do i delete a post?

---

### Post by teklife on 2011-01-06
this morning i booted up into the 2.6.35-23 kernel with high hopes that the wireless problem would be solved, as it was on my girl's netbook. alas, after no more than 10 minutes, my wireless connection dropped and i was not able to get connected again without several reboots. 

i'm new to linux, and only moderately computer savvy, so i'm not sure if this is all the relevant information needed to understand this problem better, but i have copied and pasted bits from the daemon.log and kern.log which i think might shed some light on this.

```
Jan  6 10:09:57 ss-pin kernel: [   27.552965] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
Jan  6 10:09:57 ss-pin kernel: [   27.821365] Skipping EDID probe due to cached edid
Jan  6 10:09:57 ss-pin kernel: [   27.853269] Skipping EDID probe due to cached edid
Jan  6 10:09:57 ss-pin kernel: [   27.995184] ppdev: user-space parallel port driver
Jan  6 10:09:58 ss-pin kernel: [   28.858512] vboxdrv: Found 2 processor cores.
Jan  6 10:09:58 ss-pin kernel: [   28.859143] vboxdrv: fAsync=0 offMin=0x180 offMax=0x30a8
Jan  6 10:09:58 ss-pin kernel: [   28.862426] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Jan  6 10:09:58 ss-pin kernel: [   28.862437] vboxdrv: Successfully loaded version 3.2.12 (interface 0x00140001).
Jan  6 10:09:59 ss-pin kernel: [   30.153149] Skipping EDID probe due to cached edid
Jan  6 10:09:59 ss-pin kernel: [   30.193500] Skipping EDID probe due to cached edid
Jan  6 10:09:59 ss-pin kernel: [   30.229221] Skipping EDID probe due to cached edid
Jan  6 10:10:01 ss-pin kernel: [   32.080543] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro,commit=0
Jan  6 10:10:02 ss-pin kernel: [   33.098824] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Jan  6 10:10:02 ss-pin kernel: [   33.119362] r8169 0000:04:00.0: eth0: link down
Jan  6 10:10:02 ss-pin kernel: [   33.119991] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  6 10:10:05 ss-pin kernel: [   35.829134] Skipping EDID probe due to cached edid
Jan  6 10:10:06 ss-pin kernel: [   36.413507] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Jan  6 10:10:09 ss-pin kernel: [   40.116130] Skipping EDID probe due to cached edid
Jan  6 10:11:04 ss-pin kernel: [   95.061921] wlan1: authenticate with 04:1e:64:9a:14:ad (try 1)
Jan  6 10:11:04 ss-pin kernel: [   95.069843] wlan1: authenticated
Jan  6 10:11:04 ss-pin kernel: [   95.070522] wlan1: associate with 04:1e:64:9a:14:ad (try 1)
Jan  6 10:11:04 ss-pin kernel: [   95.077150] wlan1: RX AssocResp from 04:1e:64:9a:14:ad (capab=0x431 status=0 aid=1)
Jan  6 10:11:04 ss-pin kernel: [   95.077161] wlan1: associated
Jan  6 10:11:04 ss-pin kernel: [   95.086365] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Jan  6 10:11:04 ss-pin kernel: [   95.086596] cfg80211: Calling CRDA for country: US
Jan  6 10:11:04 ss-pin kernel: [   95.127469] cfg80211: Received country IE:
Jan  6 10:11:04 ss-pin kernel: [   95.127481] cfg80211: Regulatory domain: US
Jan  6 10:11:04 ss-pin kernel: [   95.127487]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:11:04 ss-pin kernel: [   95.127496]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 3000 mBm)
Jan  6 10:11:04 ss-pin kernel: [   95.127503] cfg80211: CRDA thinks this should applied:
Jan  6 10:11:04 ss-pin kernel: [   95.127509] cfg80211: Regulatory domain: US
Jan  6 10:11:04 ss-pin kernel: [   95.127514]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:11:04 ss-pin kernel: [   95.127523]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  6 10:11:04 ss-pin kernel: [   95.127533]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Jan  6 10:11:04 ss-pin kernel: [   95.127542]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:04 ss-pin kernel: [   95.127552]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:04 ss-pin kernel: [   95.127561]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:04 ss-pin kernel: [   95.127571]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Jan  6 10:11:04 ss-pin kernel: [   95.127577] cfg80211: We intersect both of these and get:
Jan  6 10:11:04 ss-pin kernel: [   95.127584] cfg80211: Regulatory domain: 98
Jan  6 10:11:04 ss-pin kernel: [   95.127590]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:11:04 ss-pin kernel: [   95.127599]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  6 10:11:04 ss-pin kernel: [   95.127616] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
Jan  6 10:11:04 ss-pin kernel: [   95.127626] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
Jan  6 10:11:04 ss-pin kernel: [   95.127634] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
Jan  6 10:11:04 ss-pin kernel: [   95.127645] cfg80211: Current regulatory domain updated by AP to: US
Jan  6 10:11:04 ss-pin kernel: [   95.127653]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:11:04 ss-pin kernel: [   95.127663]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  6 10:11:04 ss-pin kernel: [   95.237134] padlock: VIA PadLock not detected.
Jan  6 10:11:14 ss-pin kernel: [  105.164170] wlan1: deauthenticating from 04:1e:64:9a:14:ad by local choice (reason=3)
Jan  6 10:11:14 ss-pin kernel: [  105.192356] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan  6 10:11:14 ss-pin kernel: [  105.192371] cfg80211: Restoring regulatory settings
Jan  6 10:11:14 ss-pin kernel: [  105.192381] cfg80211: Calling CRDA to update world regulatory domain
Jan  6 10:11:14 ss-pin kernel: [  105.204870] cfg80211: World regulatory domain updated:
Jan  6 10:11:14 ss-pin kernel: [  105.204881]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:11:14 ss-pin kernel: [  105.204893]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:14 ss-pin kernel: [  105.204903]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:14 ss-pin kernel: [  105.204912]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:14 ss-pin kernel: [  105.204921]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:14 ss-pin kernel: [  105.204930]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:15 ss-pin kernel: [  105.441390] Skipping EDID probe due to cached edid
Jan  6 10:11:15 ss-pin kernel: [  105.473334] Skipping EDID probe due to cached edid
Jan  6 10:11:15 ss-pin kernel: [  105.505038] wlan1: no IPv6 routers present
Jan  6 10:11:16 ss-pin kernel: [  107.137161] Skipping EDID probe due to cached edid
Jan  6 10:11:16 ss-pin kernel: [  107.177165] Skipping EDID probe due to cached edid
Jan  6 10:11:16 ss-pin kernel: [  107.217161] Skipping EDID probe due to cached edid
Jan  6 10:11:16 ss-pin kernel: [  107.253170] Skipping EDID probe due to cached edid
Jan  6 10:11:29 ss-pin kernel: [  119.721144] Skipping EDID probe due to cached edid
Jan  6 10:11:29 ss-pin kernel: [  119.761145] Skipping EDID probe due to cached edid
Jan  6 10:11:29 ss-pin kernel: [  119.796195] Skipping EDID probe due to cached edid
Jan  6 10:11:32 ss-pin kernel: [  122.896171] Skipping EDID probe due to cached edid
Jan  6 10:11:36 ss-pin kernel: [  127.225140] Skipping EDID probe due to cached edid
Jan  6 10:11:43 ss-pin kernel: [  133.754859] wlan1: authenticate with 04:1e:64:9a:14:ad (try 1)
Jan  6 10:11:43 ss-pin kernel: [  133.765250] wlan1: authenticated
Jan  6 10:11:43 ss-pin kernel: [  133.769459] wlan1: associate with 04:1e:64:9a:14:ad (try 1)
Jan  6 10:11:43 ss-pin kernel: [  133.776689] wlan1: RX AssocResp from 04:1e:64:9a:14:ad (capab=0x431 status=0 aid=1)
Jan  6 10:11:43 ss-pin kernel: [  133.776702] wlan1: associated
Jan  6 10:11:43 ss-pin kernel: [  133.779561] cfg80211: Calling CRDA for country: US
Jan  6 10:11:43 ss-pin kernel: [  133.875173] cfg80211: Received country IE:
Jan  6 10:11:43 ss-pin kernel: [  133.875184] cfg80211: Regulatory domain: US
Jan  6 10:11:43 ss-pin kernel: [  133.875191]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:11:43 ss-pin kernel: [  133.875201]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 3000 mBm)
Jan  6 10:11:43 ss-pin kernel: [  133.875208] cfg80211: CRDA thinks this should applied:
Jan  6 10:11:43 ss-pin kernel: [  133.875214] cfg80211: Regulatory domain: US
Jan  6 10:11:43 ss-pin kernel: [  133.875219]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:11:43 ss-pin kernel: [  133.875229]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  6 10:11:43 ss-pin kernel: [  133.875239]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Jan  6 10:11:43 ss-pin kernel: [  133.875249]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:43 ss-pin kernel: [  133.875259]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:43 ss-pin kernel: [  133.875269]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:11:43 ss-pin kernel: [  133.875279]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Jan  6 10:11:43 ss-pin kernel: [  133.875286] cfg80211: We intersect both of these and get:
Jan  6 10:11:43 ss-pin kernel: [  133.875293] cfg80211: Regulatory domain: 98
Jan  6 10:11:43 ss-pin kernel: [  133.875299]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:11:43 ss-pin kernel: [  133.875309]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  6 10:11:43 ss-pin kernel: [  133.875325] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
Jan  6 10:11:43 ss-pin kernel: [  133.875334] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
Jan  6 10:11:43 ss-pin kernel: [  133.875342] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
Jan  6 10:11:43 ss-pin kernel: [  133.875354] cfg80211: Current regulatory domain updated by AP to: US
Jan  6 10:11:43 ss-pin kernel: [  133.875360]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:11:43 ss-pin kernel: [  133.875371]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  6 10:13:11 ss-pin kernel: [  222.825496] CE: hpet increased min_delta_ns to 7500 nsec
Jan  6 10:16:32 ss-pin kernel: [  424.069054] CE: hpet increased min_delta_ns to 11250 nsec
Jan  6 10:27:03 ss-pin kernel: [ 1054.931820] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
Jan  6 10:27:03 ss-pin kernel: [ 1054.931848] b43-phy0 ERROR: This device does not support DMA on your system. Please use PIO instead.
Jan  6 10:27:03 ss-pin kernel: [ 1054.931865] b43-phy0: Controller RESET (DMA error) ...
Jan  6 10:27:03 ss-pin kernel: [ 1055.160308] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
Jan  6 10:27:09 ss-pin kernel: [ 1060.706994] b43-phy0: Controller restarted
Jan  6 10:27:11 ss-pin kernel: [ 1063.204082] No probe response from AP 04:1e:64:9a:14:ad after 500ms, disconnecting.
Jan  6 10:27:11 ss-pin kernel: [ 1063.256149] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan  6 10:27:11 ss-pin kernel: [ 1063.256174] cfg80211: Restoring regulatory settings
Jan  6 10:27:11 ss-pin kernel: [ 1063.256192] cfg80211: Calling CRDA to update world regulatory domain
Jan  6 10:27:12 ss-pin kernel: [ 1063.586660] cfg80211: World regulatory domain updated:
Jan  6 10:27:12 ss-pin kernel: [ 1063.586670]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:27:12 ss-pin kernel: [ 1063.586682]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1063.586692]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1063.586701]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1063.586711]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1063.586721]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1064.239918] wlan1: authenticate with 04:1e:64:9a:14:ad (try 1)
Jan  6 10:27:12 ss-pin kernel: [ 1064.241900] wlan1: authenticated
Jan  6 10:27:12 ss-pin kernel: [ 1064.242574] wlan1: associate with 04:1e:64:9a:14:ad (try 1)
Jan  6 10:27:12 ss-pin kernel: [ 1064.249481] wlan1: RX AssocResp from 04:1e:64:9a:14:ad (capab=0x431 status=0 aid=1)
Jan  6 10:27:12 ss-pin kernel: [ 1064.249493] wlan1: associated
Jan  6 10:27:12 ss-pin kernel: [ 1064.252266] cfg80211: Calling CRDA for country: US
Jan  6 10:27:12 ss-pin kernel: [ 1064.288850] cfg80211: Received country IE:
Jan  6 10:27:12 ss-pin kernel: [ 1064.288862] cfg80211: Regulatory domain: US
Jan  6 10:27:12 ss-pin kernel: [ 1064.288868]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288878]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (10000 mBi, 3000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288884] cfg80211: CRDA thinks this should applied:
Jan  6 10:27:12 ss-pin kernel: [ 1064.288890] cfg80211: Regulatory domain: US
Jan  6 10:27:12 ss-pin kernel: [ 1064.288895]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288905]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288914]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288924]     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288933]     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288942]     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288951]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288958] cfg80211: We intersect both of these and get:
Jan  6 10:27:12 ss-pin kernel: [ 1064.288964] cfg80211: Regulatory domain: 98
Jan  6 10:27:12 ss-pin kernel: [ 1064.288970]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288980]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  6 10:27:12 ss-pin kernel: [ 1064.288997] cfg80211: Disabling channel 2467 MHz on phy0 due to Country IE
Jan  6 10:27:12 ss-pin kernel: [ 1064.289115] cfg80211: Disabling channel 2472 MHz on phy0 due to Country IE
Jan  6 10:27:12 ss-pin kernel: [ 1064.289124] cfg80211: Disabling channel 2484 MHz on phy0 due to Country IE
Jan  6 10:27:12 ss-pin kernel: [ 1064.289134] cfg80211: Current regulatory domain updated by AP to: US
Jan  6 10:27:12 ss-pin kernel: [ 1064.289140]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:27:12 ss-pin kernel: [ 1064.289149]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Jan  6 10:27:17 ss-pin kernel: [ 1069.492110] No probe response from AP 04:1e:64:9a:14:ad after 500ms, disconnecting.
Jan  6 10:27:18 ss-pin kernel: [ 1069.517431] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan  6 10:27:18 ss-pin kernel: [ 1069.517446] cfg80211: Restoring regulatory settings
Jan  6 10:27:18 ss-pin kernel: [ 1069.517457] cfg80211: Calling CRDA to update world regulatory domain
Jan  6 10:27:18 ss-pin kernel: [ 1069.528735] cfg80211: World regulatory domain updated:
Jan  6 10:27:18 ss-pin kernel: [ 1069.528746]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  6 10:27:18 ss-pin kernel: [ 1069.528756]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:18 ss-pin kernel: [ 1069.528763]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:18 ss-pin kernel: [ 1069.528769]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:18 ss-pin kernel: [ 1069.528776]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:18 ss-pin kernel: [ 1069.528783]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  6 10:27:19 ss-pin kernel: [ 1070.925977] wlan1: authenticate with 04:1e:64:9a:14:ad (try 1)
Jan  6 10:27:19 ss-pin kernel: [ 1071.125130] wlan1: authenticate with 04:1e:64:9a:14:ad (try 2)
Jan  6 10:27:19 ss-pin kernel: [ 1071.325137] wlan1: authenticate with 04:1e:64:9a:14:ad (try 3)
Jan  6 10:27:20 ss-pin kernel: [ 1071.525049] wlan1: authentication with 04:1e:64:9a:14:ad timed out
```

```
Jan  6 10:42:20 ss-pin upstart-udev-bridge[418]: Env must be KEY=VALUE pairs
Jan  6 10:42:20 ss-pin init: ubiquity main process (1087) terminated with status 1
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> NetworkManager (version 0.8.1) is starting...
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> trying to start the modem manager...
Jan  6 10:42:20 ss-pin avahi-daemon[1123]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jan  6 10:42:20 ss-pin avahi-daemon[1123]: Successfully dropped root privileges.
Jan  6 10:42:20 ss-pin avahi-daemon[1123]: avahi-daemon 0.6.27 starting up.
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: init!
Jan  6 10:42:20 ss-pin avahi-daemon[1123]: Successfully called chroot().
Jan  6 10:42:20 ss-pin avahi-daemon[1123]: Successfully dropped remaining capabilities.
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: update_system_hostname
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPluginIfupdown: management mode: unmanaged
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan1, iface: wlan1)
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0)
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: end _init.
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  6 10:42:20 ss-pin avahi-daemon[1123]: No service file found in /etc/avahi/services.
Jan  6 10:42:20 ss-pin avahi-daemon[1123]: Network interface enumeration completed.
Jan  6 10:42:20 ss-pin avahi-daemon[1123]: Registering HINFO record with values 'I686'/'LINUX'.
Jan  6 10:42:20 ss-pin avahi-daemon[1123]: Server startup complete. Host name is ss-pin.local. Local service cookie is 2180257786.
Jan  6 10:42:20 ss-pin modem-manager: ModemManager (version 0.4) starting...
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    Ifupdown: get unmanaged devices count: 0
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: (168627024) ... get_connections.
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: (168627024) ... get_connections (managed=false): return empty list.
Jan  6 10:42:20 ss-pin NetworkManager[1103]:    Ifupdown: get unmanaged devices count: 0
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill2) (driver <unknown>)
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/compal-laptop/rfkill/rfkill0) (driver compal-laptop)
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin Option
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin SimTech
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin AnyData
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> Networking is enabled by state file
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin ZTE
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin Novatel
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin Generic
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> (wlan1): driver supports SSID scans (scan_capa 0x01).
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin Option High-Speed
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> (wlan1): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin Gobi
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> (wlan1): now managed
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 1 -> 2 (reason 2)
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin Huawei
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin Sierra
Jan  6 10:42:20 ss-pin NetworkManager[1103]: <info> (wlan1): bringing up device.
Jan  6 10:42:20 ss-pin modem-manager: Loaded plugin Longcheer
Jan  6 10:42:21 ss-pin modem-manager: Loaded plugin MotoC
Jan  6 10:42:21 ss-pin modem-manager: Loaded plugin Nokia
Jan  6 10:42:21 ss-pin modem-manager: Loaded plugin Ericsson MBM
Jan  6 10:42:21 ss-pin modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Jan  6 10:42:21 ss-pin modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Jan  6 10:42:21 ss-pin modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Jan  6 10:42:21 ss-pin modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Jan  6 10:42:21 ss-pin gdm-binary[1095]: WARNING: Unable to find users: no seat-id found
Jan  6 10:42:21 ss-pin init: apport pre-start process (1351) terminated with status 1
Jan  6 10:42:21 ss-pin acpid: starting up with proc fs
Jan  6 10:42:21 ss-pin acpid: 36 rules loaded
Jan  6 10:42:21 ss-pin init: apport post-stop process (1394) terminated with status 1
Jan  6 10:42:21 ss-pin acpid: waiting for events: event logging is off
Jan  6 10:42:21 ss-pin granola[1439]: Version 3.0.8 is starting.
Jan  6 10:42:21 ss-pin granola[1439]: Daemonizing
Jan  6 10:42:21 ss-pin granola[1443]: Using config file '/etc/granola.conf'
Jan  6 10:42:21 ss-pin granola[1443]: Set LogLevel to notice
Jan  6 10:42:21 ss-pin granola[1443]: Set Policy to MiserWare
Jan  6 10:42:22 ss-pin granola[1443]: Error changing file ownership: granola: no such user. Does this user exist?
Jan  6 10:42:22 ss-pin granola[1443]: Error changing owner of the scaling governor file (/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor) to user granola
Jan  6 10:42:22 ss-pin granola[1443]: Can't manage DVFS for any CPUs
Jan  6 10:42:22 ss-pin granola[1443]: Warning, could not set up a configuration for managing the CPUs
Jan  6 10:42:22 ss-pin granola[1443]: Failed to start, error initializing
Jan  6 10:42:22 ss-pin gdm-session-worker[1561]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 10:42:23 ss-pin gnome-session[1570]: EggSMClient-WARNING: Desktop file '/home/ss/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Jan  6 10:42:26 ss-pin polkitd[1679]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (wlan1): preparing device.
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (wlan1): deactivating device (reason: 2).
Jan  6 10:42:32 ss-pin NetworkManager[1103]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jan  6 10:42:32 ss-pin modem-manager: (net/vboxnet0): could not get port's parent device
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (eth0): carrier is OFF
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (eth0): now managed
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (eth0): bringing up device.
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (eth0): preparing device.
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (eth0): deactivating device (reason: 2).
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0
Jan  6 10:42:32 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Jan  6 10:42:32 ss-pin NetworkManager[1103]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <warn> /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> modem-manager is now available
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> Trying to start the supplicant...
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant manager state:  down -> idle
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 2 -> 3 (reason 0)
Jan  6 10:42:32 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant interface state:  starting -> ready
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Successfully called chroot.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Successfully dropped privileges.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Successfully limited resources.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Running.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Canary thread running.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Watchdog thread running.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Successfully made thread 1775 of process 1775 (n/a) owned by '1000' high priority at nice level -11.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Supervising 1 threads of 1 processes of 1 users.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Successfully made thread 1852 of process 1775 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Supervising 2 threads of 1 processes of 1 users.
Jan  6 10:42:33 ss-pin gnome-session[1570]: WARNING: Could not launch application '10f8a10dbcda708b27129432670512522000000026570044.desktop': Unable to start application: Failed to execute child process "mintMenu.py" (No such file or directory)
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Successfully made thread 1866 of process 1775 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:42:33 ss-pin rtkit-daemon[1783]: Supervising 3 threads of 1 processes of 1 users.
Jan  6 10:42:35 ss-pin init: plymouth-stop pre-start process (1928) terminated with status 1
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> Activation (wlan1) starting connection 'Auto :)'
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 3 -> 4 (reason 0)
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> Activation (wlan1/wireless): access point 'Auto :)' has security, but secrets are required.
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Jan  6 10:42:42 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Activation (wlan1/wireless): connection 'Auto :)' has security, and secrets exist.  No new secrets needed.
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Config: added 'ssid' value ':)'
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Config: added 'scan_ssid' value '1'
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Config: added 'psk' value '<omitted>'
Jan  6 10:43:07 ss-pin NetworkManager[1103]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:43:07 ss-pin NetworkManager[1103]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> Config: set interface ap_scan to 1
Jan  6 10:43:07 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  inactive -> scanning
Jan  6 10:43:09 ss-pin wpa_supplicant[1765]: Trying to associate with 04:1e:64:9a:14:ad (SSID=':)' freq=2462 MHz)
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  scanning -> associating
Jan  6 10:43:09 ss-pin wpa_supplicant[1765]: Associated with 04:1e:64:9a:14:ad
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  associating -> associated
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  associated -> 4-way handshake
Jan  6 10:43:09 ss-pin wpa_supplicant[1765]: WPA: Key negotiation completed with 04:1e:64:9a:14:ad [PTK=CCMP GTK=CCMP]
Jan  6 10:43:09 ss-pin wpa_supplicant[1765]: CTRL-EVENT-CONNECTED - Connection to 04:1e:64:9a:14:ad completed (auth) [id=0 id_str=]
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  4-way handshake -> group handshake
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  group handshake -> completed
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network ':)'.
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 5 -> 7 (reason 0)
Jan  6 10:43:09 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  6 10:43:10 ss-pin NetworkManager[1103]: <info> dhclient started with pid 2294
Jan  6 10:43:10 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Jan  6 10:43:10 ss-pin dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  6 10:43:10 ss-pin dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan  6 10:43:10 ss-pin dhclient: All rights reserved.
Jan  6 10:43:10 ss-pin dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  6 10:43:10 ss-pin dhclient: 
Jan  6 10:43:10 ss-pin dhclient: Listening on LPF/wlan1/70:1a:04:a0:c8:f3
Jan  6 10:43:10 ss-pin dhclient: Sending on   LPF/wlan1/70:1a:04:a0:c8:f3
Jan  6 10:43:10 ss-pin dhclient: Sending on   Socket/fallback
Jan  6 10:43:10 ss-pin dhclient: DHCPREQUEST of 10.0.1.8 on wlan1 to 255.255.255.255 port 67
Jan  6 10:43:10 ss-pin NetworkManager[1103]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
Jan  6 10:43:10 ss-pin avahi-daemon[1123]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::721a:4ff:fea0:c8f3.
Jan  6 10:43:10 ss-pin avahi-daemon[1123]: New relevant interface wlan1.IPv6 for mDNS.
Jan  6 10:43:10 ss-pin avahi-daemon[1123]: Registering new address record for fe80::721a:4ff:fea0:c8f3 on wlan1.*.
Jan  6 10:43:13 ss-pin dhclient: DHCPREQUEST of 10.0.1.8 on wlan1 to 255.255.255.255 port 67
Jan  6 10:43:13 ss-pin wpa_supplicant[1765]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  6 10:43:13 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  completed -> disconnected
Jan  6 10:43:14 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
Jan  6 10:43:15 ss-pin wpa_supplicant[1765]: Trying to associate with 04:1e:64:9a:14:ad (SSID=':)' freq=2462 MHz)
Jan  6 10:43:15 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  scanning -> associating
Jan  6 10:43:20 ss-pin dhclient: DHCPREQUEST of 10.0.1.8 on wlan1 to 255.255.255.255 port 67
Jan  6 10:43:25 ss-pin wpa_supplicant[1765]: Authentication with 04:1e:64:9a:14:ad timed out.
Jan  6 10:43:25 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  associating -> disconnected
Jan  6 10:43:25 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
Jan  6 10:43:27 ss-pin dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
Jan  6 10:43:29 ss-pin NetworkManager[1103]: <warn> (wlan1): link timed out.
Jan  6 10:43:30 ss-pin dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
Jan  6 10:43:33 ss-pin dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 6
Jan  6 10:43:39 ss-pin dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
Jan  6 10:43:41 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 7 -> 3 (reason 38)
Jan  6 10:43:41 ss-pin NetworkManager[1103]: <info> (wlan1): deactivating device (reason: 38).
Jan  6 10:43:41 ss-pin NetworkManager[1103]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 2294
Jan  6 10:43:41 ss-pin NetworkManager[1103]: <error> [1294328621.599942] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  6 10:43:41 ss-pin acpid: client connected from 2396[0:0]
Jan  6 10:43:41 ss-pin acpid: 1 client rule loaded
Jan  6 10:43:42 ss-pin NetworkManager[1103]: <error> [1294328622.588342] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  6 10:43:45 ss-pin gdm-simple-greeter[2433]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Jan  6 10:43:50 ss-pin gdm-session-worker[2436]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 10:43:53 ss-pin gdm-session-worker[2436]: pam_sm_authenticate: Called
Jan  6 10:43:53 ss-pin gdm-session-worker[2436]: pam_sm_authenticate: username = [ss]
Jan  6 10:43:53 ss-pin NetworkManager[1103]: <error> [1294328633.509934] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  6 10:43:53 ss-pin NetworkManager[1103]: <error> [1294328633.564451] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  6 10:43:54 ss-pin gnome-session[2467]: EggSMClient-WARNING: Desktop file '/home/ss/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Jan  6 10:43:54 ss-pin rtkit-daemon[1783]: Successfully made thread 2531 of process 2531 (n/a) owned by '1000' high priority at nice level -11.
Jan  6 10:43:54 ss-pin rtkit-daemon[1783]: Supervising 1 threads of 1 processes of 1 users.
Jan  6 10:43:55 ss-pin rtkit-daemon[1783]: Successfully made thread 2560 of process 2531 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:43:55 ss-pin rtkit-daemon[1783]: Supervising 2 threads of 1 processes of 1 users.
Jan  6 10:43:55 ss-pin rtkit-daemon[1783]: Successfully made thread 2561 of process 2531 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:43:55 ss-pin rtkit-daemon[1783]: Supervising 3 threads of 1 processes of 1 users.
Jan  6 10:43:55 ss-pin gnome-session[2467]: WARNING: Could not launch application '10f8a10dbcda708b27129432670512522000000026570044.desktop': Unable to start application: Failed to execute child process "mintMenu.py" (No such file or directory)
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> Activation (wlan1) starting connection 'Auto :)'
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 3 -> 4 (reason 0)
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> Activation (wlan1/wireless): access point 'Auto :)' has security, but secrets are required.
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Jan  6 10:44:03 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Activation (wlan1/wireless): connection 'Auto :)' has security, and secrets exist.  No new secrets needed.
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Config: added 'ssid' value ':)'
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Config: added 'scan_ssid' value '1'
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Config: added 'psk' value '<omitted>'
Jan  6 10:44:06 ss-pin NetworkManager[1103]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:44:06 ss-pin NetworkManager[1103]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> Config: set interface ap_scan to 1
Jan  6 10:44:06 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
Jan  6 10:45:06 ss-pin NetworkManager[1103]: <warn> Activation (wlan1/wireless): association took too long.
Jan  6 10:45:06 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Jan  6 10:45:06 ss-pin NetworkManager[1103]: <warn> Activation (wlan1/wireless): asking for new secrets
Jan  6 10:45:06 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  scanning -> disconnected
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Activation (wlan1/wireless): connection 'Auto :)' has security, and secrets exist.  No new secrets needed.
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Config: added 'ssid' value ':)'
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Config: added 'scan_ssid' value '1'
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Config: added 'psk' value '<omitted>'
Jan  6 10:45:10 ss-pin NetworkManager[1103]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:45:10 ss-pin NetworkManager[1103]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> Config: set interface ap_scan to 1
Jan  6 10:45:10 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
Jan  6 10:46:10 ss-pin NetworkManager[1103]: <warn> Activation (wlan1/wireless): association took too long.
Jan  6 10:46:10 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Jan  6 10:46:10 ss-pin NetworkManager[1103]: <warn> Activation (wlan1/wireless): asking for new secrets
Jan  6 10:46:10 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  scanning -> disconnected
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Activation (wlan1/wireless): connection 'Auto :)' has security, and secrets exist.  No new secrets needed.
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Config: added 'ssid' value ':)'
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Config: added 'scan_ssid' value '1'
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Config: added 'psk' value '<omitted>'
Jan  6 10:46:12 ss-pin NetworkManager[1103]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:46:12 ss-pin NetworkManager[1103]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:46:12 ss-pin NetworkManager[1103]: <info> Config: set interface ap_scan to 1
Jan  6 10:46:13 ss-pin NetworkManager[1103]: <info> (wlan1): supplicant connection state:  disconnected -> scanning

```

this the latest error i saw after losing wifi, not sure where this fits in, if at all.
```

Jan  6 11:19:06 ss-pin pulseaudio[1772]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Jan  6 11:19:06 ss-pin pulseaudio[1772]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Jan  6 11:19:06 ss-pin pulseaudio[1772]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Jan  6 11:19:15 ss-pin nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Jan  6 11:19:24 ss-pin nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Jan  6 11:21:29 ss-pin bonobo-activation-server (ss-2532): could not associate with desktop session: Error connecting: Connection refused
Jan  6 11:21:43 ss-pin pulseaudio[2716]: pid.c: Stale PID file, overwriting.
Jan  6 11:21:53 ss-pin nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Jan  6 11:22:03 ss-pin nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Jan  6 11:24:32 ss-pin pulseaudio[2716]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Jan  6 11:24:32 ss-pin pulseaudio[2716]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Jan  6 11:24:32 ss-pin pulseaudio[2716]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

```

```
an  6 10:00:06 ss-pin upstart-udev-bridge[423]: Env must be KEY=VALUE pairs
Jan  6 10:00:06 ss-pin init: ubiquity main process (1151) terminated with status 1
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> NetworkManager (version 0.8.1) is starting...
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Jan  6 10:00:06 ss-pin avahi-daemon[1171]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jan  6 10:00:06 ss-pin avahi-daemon[1171]: Successfully dropped root privileges.
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> trying to start the modem manager...
Jan  6 10:00:06 ss-pin avahi-daemon[1171]: avahi-daemon 0.6.27 starting up.
Jan  6 10:00:06 ss-pin avahi-daemon[1171]: Successfully called chroot().
Jan  6 10:00:06 ss-pin avahi-daemon[1171]: Successfully dropped remaining capabilities.
Jan  6 10:00:06 ss-pin avahi-daemon[1171]: No service file found in /etc/avahi/services.
Jan  6 10:00:06 ss-pin avahi-daemon[1171]: Network interface enumeration completed.
Jan  6 10:00:06 ss-pin avahi-daemon[1171]: Registering HINFO record with values 'I686'/'LINUX'.
Jan  6 10:00:06 ss-pin avahi-daemon[1171]: Server startup complete. Host name is ss-pin.local. Local service cookie is 1541145038.
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: init!
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: update_system_hostname
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPluginIfupdown: management mode: unmanaged
Jan  6 10:00:06 ss-pin modem-manager: ModemManager (version 0.4) starting...
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan1, iface: wlan1)
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0)
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: end _init.
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    Ifupdown: get unmanaged devices count: 0
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: (153414992) ... get_connections.
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: (153414992) ... get_connections (managed=false): return empty list.
Jan  6 10:00:06 ss-pin NetworkManager[1163]:    Ifupdown: get unmanaged devices count: 0
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill2) (driver <unknown>)
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/compal-laptop/rfkill/rfkill0) (driver compal-laptop)
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Option
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin SimTech
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin AnyData
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin ZTE
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Novatel
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Generic
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Option High-Speed
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Gobi
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Huawei
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Sierra
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Longcheer
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin MotoC
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> Networking is enabled by state file
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Nokia
Jan  6 10:00:06 ss-pin modem-manager: Loaded plugin Ericsson MBM
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> (wlan1): driver supports SSID scans (scan_capa 0x01).
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> (wlan1): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> (wlan1): now managed
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> (wlan1): device state change: 1 -> 2 (reason 2)
Jan  6 10:00:06 ss-pin NetworkManager[1163]: <info> (wlan1): bringing up device.
Jan  6 10:00:07 ss-pin modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Jan  6 10:00:07 ss-pin modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Jan  6 10:00:07 ss-pin modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Jan  6 10:00:07 ss-pin modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Jan  6 10:00:07 ss-pin gdm-binary[1161]: WARNING: Unable to find users: no seat-id found
Jan  6 10:00:07 ss-pin granola[1438]: Version 3.0.8 is starting.
Jan  6 10:00:07 ss-pin granola[1438]: Daemonizing
Jan  6 10:00:07 ss-pin granola[1440]: Using config file '/etc/granola.conf'
Jan  6 10:00:07 ss-pin granola[1440]: Set LogLevel to notice
Jan  6 10:00:07 ss-pin granola[1440]: Set Policy to MiserWare
Jan  6 10:00:07 ss-pin granola[1440]: Error changing file ownership: granola: no such user. Does this user exist?
Jan  6 10:00:07 ss-pin granola[1440]: Error changing owner of the scaling governor file (/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor) to user granola
Jan  6 10:00:07 ss-pin granola[1440]: Can't manage DVFS for any CPUs
Jan  6 10:00:07 ss-pin granola[1440]: Warning, could not set up a configuration for managing the CPUs
Jan  6 10:00:07 ss-pin granola[1440]: Failed to start, error initializing
Jan  6 10:00:07 ss-pin init: apport pre-start process (1399) terminated with status 1
Jan  6 10:00:07 ss-pin acpid: starting up with proc fs
Jan  6 10:00:07 ss-pin acpid: 36 rules loaded
Jan  6 10:00:07 ss-pin init: apport post-stop process (1488) terminated with status 1
Jan  6 10:00:07 ss-pin acpid: waiting for events: event logging is off
Jan  6 10:00:08 ss-pin gdm-binary[1161]: WARNING: GdmDisplay: display lasted 1.107857 seconds
Jan  6 10:00:08 ss-pin acpid: client connected from 1547[0:0]
Jan  6 10:00:08 ss-pin acpid: 1 client rule loaded
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (wlan1): preparing device.
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (wlan1): deactivating device (reason: 2).
Jan  6 10:00:12 ss-pin modem-manager: (net/vboxnet0): could not get port's parent device
Jan  6 10:00:12 ss-pin NetworkManager[1163]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (eth0): carrier is OFF
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (eth0): now managed
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (eth0): bringing up device.
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (eth0): preparing device.
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (eth0): deactivating device (reason: 2).
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0
Jan  6 10:00:12 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Jan  6 10:00:12 ss-pin NetworkManager[1163]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <warn> /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> modem-manager is now available
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> Trying to start the supplicant...
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (wlan1): supplicant manager state:  down -> idle
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (wlan1): device state change: 2 -> 3 (reason 0)
Jan  6 10:00:12 ss-pin NetworkManager[1163]: <info> (wlan1): supplicant interface state:  starting -> ready
Jan  6 10:00:14 ss-pin init: plymouth-stop pre-start process (1730) terminated with status 1
Jan  6 10:02:22 ss-pin init: ubiquity main process (965) terminated with status 1
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> NetworkManager (version 0.8.1) is starting...
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> trying to start the modem manager...
Jan  6 10:02:22 ss-pin avahi-daemon[977]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: init!
Jan  6 10:02:22 ss-pin avahi-daemon[977]: Successfully dropped root privileges.
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: update_system_hostname
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPluginIfupdown: management mode: unmanaged
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0)
Jan  6 10:02:22 ss-pin avahi-daemon[977]: avahi-daemon 0.6.27 starting up.
Jan  6 10:02:22 ss-pin modem-manager: ModemManager (version 0.4) starting...
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: end _init.
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  6 10:02:22 ss-pin NetworkManager[970]:    Ifupdown: get unmanaged devices count: 0
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: (137149264) ... get_connections.
Jan  6 10:02:22 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: (137149264) ... get_connections (managed=false): return empty list.
Jan  6 10:02:22 ss-pin avahi-daemon[977]: Successfully called chroot().
Jan  6 10:02:22 ss-pin avahi-daemon[977]: Successfully dropped remaining capabilities.
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Option
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin SimTech
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin AnyData
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin ZTE
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Novatel
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Generic
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Option High-Speed
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Gobi
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Huawei
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Sierra
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Longcheer
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin MotoC
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Nokia
Jan  6 10:02:22 ss-pin modem-manager: Loaded plugin Ericsson MBM
Jan  6 10:02:22 ss-pin modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Jan  6 10:02:22 ss-pin modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Jan  6 10:02:22 ss-pin modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Jan  6 10:02:22 ss-pin modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Jan  6 10:02:22 ss-pin NetworkManager[970]:    Ifupdown: get unmanaged devices count: 0
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/compal-laptop/rfkill/rfkill0) (driver compal-laptop)
Jan  6 10:02:22 ss-pin avahi-daemon[977]: No service file found in /etc/avahi/services.
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> Networking is enabled by state file
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (eth0): carrier is OFF
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (eth0): now managed
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (eth0): bringing up device.
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (eth0): preparing device.
Jan  6 10:02:22 ss-pin avahi-daemon[977]: Network interface enumeration completed.
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (eth0): deactivating device (reason: 2).
Jan  6 10:02:22 ss-pin avahi-daemon[977]: Registering HINFO record with values 'I686'/'LINUX'.
Jan  6 10:02:22 ss-pin avahi-daemon[977]: Server startup complete. Host name is ss-pin.local. Local service cookie is 2720517713.
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0
Jan  6 10:02:22 ss-pin upstart-udev-bridge[424]: Env must be KEY=VALUE pairs
Jan  6 10:02:22 ss-pin gdm-binary[969]: WARNING: Unable to find users: no seat-id found
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> modem-manager is now available
Jan  6 10:02:22 ss-pin NetworkManager[970]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> Trying to start the supplicant...
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill2) (driver <unknown>)
Jan  6 10:02:22 ss-pin init: apport pre-start process (1124) terminated with status 1
Jan  6 10:02:22 ss-pin acpid: starting up with proc fs
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (wlan1): driver supports SSID scans (scan_capa 0x01).
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (wlan1): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (wlan1): now managed
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (wlan1): device state change: 1 -> 2 (reason 2)
Jan  6 10:02:22 ss-pin NetworkManager[970]: <info> (wlan1): bringing up device.
Jan  6 10:02:22 ss-pin acpid: 36 rules loaded
Jan  6 10:02:22 ss-pin acpid: waiting for events: event logging is off
Jan  6 10:02:22 ss-pin acpid: client connected from 1149[0:0]
Jan  6 10:02:22 ss-pin acpid: 1 client rule loaded
Jan  6 10:02:22 ss-pin init: apport post-stop process (1182) terminated with status 1
Jan  6 10:02:23 ss-pin granola[1285]: Version 3.0.8 is starting.
Jan  6 10:02:23 ss-pin granola[1285]: Daemonizing
Jan  6 10:02:23 ss-pin granola[1295]: Using config file '/etc/granola.conf'
Jan  6 10:02:23 ss-pin granola[1295]: Set LogLevel to notice
Jan  6 10:02:23 ss-pin granola[1295]: Set Policy to MiserWare
Jan  6 10:02:23 ss-pin granola[1295]: Error changing file ownership: granola: no such user. Does this user exist?
Jan  6 10:02:23 ss-pin granola[1295]: Error changing owner of the scaling governor file (/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor) to user granola
Jan  6 10:02:23 ss-pin granola[1295]: Can't manage DVFS for any CPUs
Jan  6 10:02:23 ss-pin granola[1295]: Warning, could not set up a configuration for managing the CPUs
Jan  6 10:02:23 ss-pin granola[1295]: Failed to start, error initializing
Jan  6 10:02:23 ss-pin gdm-session-worker[1555]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 10:02:25 ss-pin gnome-session[1572]: EggSMClient-WARNING: Desktop file '/home/ss/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Jan  6 10:02:26 ss-pin polkitd[1681]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jan  6 10:02:28 ss-pin NetworkManager[970]: <info> (wlan1): preparing device.
Jan  6 10:02:28 ss-pin NetworkManager[970]: <info> (wlan1): deactivating device (reason: 2).
Jan  6 10:02:28 ss-pin modem-manager: (net/vboxnet0): could not get port's parent device
Jan  6 10:02:28 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan1, iface: wlan1)
Jan  6 10:02:28 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Jan  6 10:02:28 ss-pin NetworkManager[970]: <warn> /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Jan  6 10:02:28 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Jan  6 10:02:28 ss-pin NetworkManager[970]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Jan  6 10:02:28 ss-pin NetworkManager[970]: <info> (wlan1): supplicant interface state:  starting -> ready
Jan  6 10:02:28 ss-pin NetworkManager[970]: <info> (wlan1): device state change: 2 -> 3 (reason 42)
Jan  6 10:02:28 ss-pin rtkit-daemon[1771]: Successfully called chroot.
Jan  6 10:02:28 ss-pin rtkit-daemon[1771]: Successfully dropped privileges.
Jan  6 10:02:28 ss-pin rtkit-daemon[1771]: Successfully limited resources.
Jan  6 10:02:28 ss-pin rtkit-daemon[1771]: Running.
Jan  6 10:02:28 ss-pin rtkit-daemon[1771]: Canary thread running.
Jan  6 10:02:28 ss-pin rtkit-daemon[1771]: Watchdog thread running.
Jan  6 10:02:28 ss-pin rtkit-daemon[1771]: Successfully made thread 1769 of process 1769 (n/a) owned by '1000' high priority at nice level -11.
Jan  6 10:02:28 ss-pin rtkit-daemon[1771]: Supervising 1 threads of 1 processes of 1 users.
Jan  6 10:02:29 ss-pin rtkit-daemon[1771]: Successfully made thread 1844 of process 1769 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:02:29 ss-pin rtkit-daemon[1771]: Supervising 2 threads of 1 processes of 1 users.
Jan  6 10:02:29 ss-pin gnome-session[1572]: WARNING: Could not launch application '1083fbd852720ffd2f129430059114628900000027530044.desktop': Unable to start application: Failed to execute child process "mintMenu.py" (No such file or directory)
Jan  6 10:02:29 ss-pin rtkit-daemon[1771]: Successfully made thread 1853 of process 1769 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:02:29 ss-pin rtkit-daemon[1771]: Supervising 3 threads of 1 processes of 1 users.
Jan  6 10:02:31 ss-pin init: plymouth-stop pre-start process (1923) terminated with status 1
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> Activation (wlan1) starting connection 'Auto :)'
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> (wlan1): device state change: 3 -> 4 (reason 0)
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> Activation (wlan1/wireless): access point 'Auto :)' has security, but secrets are required.
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Jan  6 10:02:39 ss-pin NetworkManager[970]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:03:10 ss-pin NetworkManager[970]: <info> (wlan1): device state change: 6 -> 3 (reason 38)
Jan  6 10:03:10 ss-pin NetworkManager[970]: <info> (wlan1): deactivating device (reason: 38).
Jan  6 10:03:10 ss-pin acpid: client 1149[0:0] has disconnected
Jan  6 10:03:10 ss-pin acpid: client connected from 2345[0:0]
Jan  6 10:03:10 ss-pin acpid: 1 client rule loaded
Jan  6 10:03:18 ss-pin gdm-simple-greeter[2390]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Jan  6 10:03:22 ss-pin gdm-session-worker[2392]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 10:03:24 ss-pin gdm-session-worker[2392]: pam_sm_authenticate: Called
Jan  6 10:03:24 ss-pin gdm-session-worker[2392]: pam_sm_authenticate: username = [ss]
Jan  6 10:03:27 ss-pin gnome-session[2424]: EggSMClient-WARNING: Desktop file '/home/ss/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Jan  6 10:03:30 ss-pin gnome-session[2424]: WARNING: Could not launch application '1083fbd852720ffd2f129430059114628900000027530044.desktop': Unable to start application: Failed to execute child process "mintMenu.py" (No such file or directory)
Jan  6 10:05:14 ss-pin acpid: client 2345[0:0] has disconnected
Jan  6 10:05:14 ss-pin acpid: client connected from 3061[0:0]
Jan  6 10:05:14 ss-pin acpid: 1 client rule loaded
Jan  6 10:05:19 ss-pin gdm-simple-greeter[3104]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Jan  6 10:05:23 ss-pin gdm-session-worker[3106]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 10:05:27 ss-pin gdm-session-worker[3106]: pam_sm_authenticate: Called
Jan  6 10:05:27 ss-pin gdm-session-worker[3106]: pam_sm_authenticate: username = [ss]
Jan  6 10:05:28 ss-pin gnome-session[3138]: EggSMClient-WARNING: Desktop file '/home/ss/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Jan  6 10:05:30 ss-pin rtkit-daemon[1771]: Successfully made thread 3205 of process 3205 (n/a) owned by '1000' high priority at nice level -11.
Jan  6 10:05:30 ss-pin rtkit-daemon[1771]: Supervising 1 threads of 1 processes of 1 users.
Jan  6 10:05:30 ss-pin rtkit-daemon[1771]: Successfully made thread 3224 of process 3205 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:05:30 ss-pin rtkit-daemon[1771]: Supervising 2 threads of 1 processes of 1 users.
Jan  6 10:05:30 ss-pin rtkit-daemon[1771]: Successfully made thread 3228 of process 3205 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:05:30 ss-pin rtkit-daemon[1771]: Supervising 3 threads of 1 processes of 1 users.
Jan  6 10:05:31 ss-pin gnome-session[3138]: WARNING: Could not launch application '1083fbd852720ffd2f129430059114628900000027530044.desktop': Unable to start application: Failed to execute child process "mintMenu.py" (No such file or directory)
Jan  6 10:09:56 ss-pin upstart-udev-bridge[417]: Env must be KEY=VALUE pairs
Jan  6 10:09:56 ss-pin init: ubiquity main process (1128) terminated with status 1
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> NetworkManager (version 0.8.1) is starting...
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> trying to start the modem manager...
Jan  6 10:09:56 ss-pin avahi-daemon[1145]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Jan  6 10:09:56 ss-pin avahi-daemon[1145]: Successfully dropped root privileges.
Jan  6 10:09:56 ss-pin avahi-daemon[1145]: avahi-daemon 0.6.27 starting up.
Jan  6 10:09:56 ss-pin modem-manager: ModemManager (version 0.4) starting...
Jan  6 10:09:56 ss-pin avahi-daemon[1145]: Successfully called chroot().
Jan  6 10:09:56 ss-pin avahi-daemon[1145]: Successfully dropped remaining capabilities.
Jan  6 10:09:56 ss-pin avahi-daemon[1145]: No service file found in /etc/avahi/services.
Jan  6 10:09:56 ss-pin avahi-daemon[1145]: Network interface enumeration completed.
Jan  6 10:09:56 ss-pin avahi-daemon[1145]: Registering HINFO record with values 'I686'/'LINUX'.
Jan  6 10:09:56 ss-pin avahi-daemon[1145]: Server startup complete. Host name is ss-pin.local. Local service cookie is 106107131.
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Option
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin SimTech
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin AnyData
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin ZTE
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Novatel
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Generic
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Option High-Speed
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Gobi
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Huawei
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Sierra
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Longcheer
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin MotoC
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Nokia
Jan  6 10:09:56 ss-pin modem-manager: Loaded plugin Ericsson MBM
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  6 10:09:56 ss-pin modem-manager: (tty/ttyS0): port's parent platform driver is not whitelisted
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: init!
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: update_system_hostname
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPluginIfupdown: management mode: unmanaged
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan1, iface: wlan1)
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/net/wlan1, iface: wlan1): no ifupdown configuration found.
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0)
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: end _init.
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Jan  6 10:09:56 ss-pin modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Jan  6 10:09:56 ss-pin modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Jan  6 10:09:56 ss-pin modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    Ifupdown: get unmanaged devices count: 0
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: (162213200) ... get_connections.
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: (162213200) ... get_connections (managed=false): return empty list.
Jan  6 10:09:56 ss-pin NetworkManager[1131]:    Ifupdown: get unmanaged devices count: 0
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/ssb0:0/ieee80211/phy0/rfkill2) (driver <unknown>)
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/compal-laptop/rfkill/rfkill0) (driver compal-laptop)
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> WiFi enabled by radio killswitch; enabled by state file
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> WWAN enabled by radio killswitch; enabled by state file
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> WiMAX enabled by radio killswitch; enabled by state file
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> Networking is enabled by state file
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> (wlan1): driver supports SSID scans (scan_capa 0x01).
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> (wlan1): new 802.11 WiFi device (driver: 'b43' ifindex: 3)
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> (wlan1): now managed
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 1 -> 2 (reason 2)
Jan  6 10:09:56 ss-pin NetworkManager[1131]: <info> (wlan1): bringing up device.
Jan  6 10:09:56 ss-pin gdm-binary[1133]: WARNING: Unable to find users: no seat-id found
Jan  6 10:09:57 ss-pin init: apport pre-start process (1300) terminated with status 1
Jan  6 10:09:57 ss-pin acpid: starting up with proc fs
Jan  6 10:09:57 ss-pin acpid: 36 rules loaded
Jan  6 10:09:57 ss-pin acpid: waiting for events: event logging is off
Jan  6 10:09:57 ss-pin init: apport post-stop process (1339) terminated with status 1
Jan  6 10:09:57 ss-pin acpid: client connected from 1308[0:0]
Jan  6 10:09:57 ss-pin acpid: 1 client rule loaded
Jan  6 10:09:57 ss-pin granola[1392]: Version 3.0.8 is starting.
Jan  6 10:09:57 ss-pin granola[1392]: Daemonizing
Jan  6 10:09:57 ss-pin granola[1397]: Using config file '/etc/granola.conf'
Jan  6 10:09:57 ss-pin granola[1397]: Set LogLevel to notice
Jan  6 10:09:57 ss-pin granola[1397]: Set Policy to MiserWare
Jan  6 10:09:57 ss-pin granola[1397]: Error changing file ownership: granola: no such user. Does this user exist?
Jan  6 10:09:57 ss-pin granola[1397]: Error changing owner of the scaling governor file (/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor) to user granola
Jan  6 10:09:57 ss-pin granola[1397]: Can't manage DVFS for any CPUs
Jan  6 10:09:57 ss-pin granola[1397]: Warning, could not set up a configuration for managing the CPUs
Jan  6 10:09:57 ss-pin granola[1397]: Failed to start, error initializing
Jan  6 10:09:58 ss-pin gdm-session-worker[1540]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 10:09:59 ss-pin gnome-session[1568]: EggSMClient-WARNING: Desktop file '/home/ss/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Jan  6 10:10:01 ss-pin polkitd[1666]: started daemon version 0.96 using authority implementation `local' version `0.96'
Jan  6 10:10:02 ss-pin modem-manager: (net/vboxnet0): could not get port's parent device
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (wlan1): preparing device.
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (wlan1): deactivating device (reason: 2).
Jan  6 10:10:02 ss-pin NetworkManager[1131]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (eth0): carrier is OFF
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (eth0): now managed
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (eth0): bringing up device.
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (eth0): preparing device.
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (eth0): deactivating device (reason: 2).
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0/net/eth0
Jan  6 10:10:02 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0)
Jan  6 10:10:02 ss-pin NetworkManager[1131]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/vboxnet0, iface: vboxnet0): no ifupdown configuration found.
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <warn> /sys/devices/virtual/net/vboxnet0: couldn't determine device driver; ignoring...
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> modem-manager is now available
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> Trying to start the supplicant...
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant manager state:  down -> idle
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 2 -> 3 (reason 0)
Jan  6 10:10:02 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant interface state:  starting -> ready
Jan  6 10:10:02 ss-pin rtkit-daemon[1768]: Successfully called chroot.
Jan  6 10:10:02 ss-pin rtkit-daemon[1768]: Successfully dropped privileges.
Jan  6 10:10:02 ss-pin rtkit-daemon[1768]: Successfully limited resources.
Jan  6 10:10:02 ss-pin rtkit-daemon[1768]: Running.
Jan  6 10:10:02 ss-pin rtkit-daemon[1768]: Watchdog thread running.
Jan  6 10:10:02 ss-pin rtkit-daemon[1768]: Canary thread running.
Jan  6 10:10:03 ss-pin rtkit-daemon[1768]: Successfully made thread 1762 of process 1762 (n/a) owned by '1000' high priority at nice level -11.
Jan  6 10:10:03 ss-pin rtkit-daemon[1768]: Supervising 1 threads of 1 processes of 1 users.
Jan  6 10:10:03 ss-pin rtkit-daemon[1768]: Successfully made thread 1839 of process 1762 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:10:03 ss-pin rtkit-daemon[1768]: Supervising 2 threads of 1 processes of 1 users.
Jan  6 10:10:03 ss-pin gnome-session[1568]: WARNING: Could not launch application '1017dea49ab84a68b9129432634844054300000031380044.desktop': Unable to start application: Failed to execute child process "mintMenu.py" (No such file or directory)
Jan  6 10:10:03 ss-pin rtkit-daemon[1768]: Successfully made thread 1850 of process 1762 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:10:03 ss-pin rtkit-daemon[1768]: Supervising 3 threads of 1 processes of 1 users.
Jan  6 10:10:05 ss-pin init: plymouth-stop pre-start process (1910) terminated with status 1
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> Activation (wlan1) starting connection 'Auto :)'
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 3 -> 4 (reason 0)
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> Activation (wlan1/wireless): access point 'Auto :)' has security, but secrets are required.
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Jan  6 10:10:12 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Activation (wlan1/wireless): connection 'Auto :)' has security, and secrets exist.  No new secrets needed.
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Config: added 'ssid' value ':)'
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Config: added 'scan_ssid' value '1'
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Config: added 'psk' value '<omitted>'
Jan  6 10:11:03 ss-pin NetworkManager[1131]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:11:03 ss-pin NetworkManager[1131]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> Config: set interface ap_scan to 1
Jan  6 10:11:03 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  inactive -> scanning
Jan  6 10:11:04 ss-pin wpa_supplicant[1744]: Trying to associate with 04:1e:64:9a:14:ad (SSID=':)' freq=2462 MHz)
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  scanning -> associating
Jan  6 10:11:04 ss-pin wpa_supplicant[1744]: Associated with 04:1e:64:9a:14:ad
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  associating -> associated
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  associated -> 4-way handshake
Jan  6 10:11:04 ss-pin wpa_supplicant[1744]: WPA: Key negotiation completed with 04:1e:64:9a:14:ad [PTK=CCMP GTK=CCMP]
Jan  6 10:11:04 ss-pin wpa_supplicant[1744]: CTRL-EVENT-CONNECTED - Connection to 04:1e:64:9a:14:ad completed (auth) [id=0 id_str=]
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  4-way handshake -> group handshake
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  group handshake -> completed
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network ':)'.
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 5 -> 7 (reason 0)
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> dhclient started with pid 2333
Jan  6 10:11:04 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Jan  6 10:11:04 ss-pin dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  6 10:11:04 ss-pin dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan  6 10:11:04 ss-pin dhclient: All rights reserved.
Jan  6 10:11:04 ss-pin dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  6 10:11:04 ss-pin dhclient: 
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
Jan  6 10:11:05 ss-pin dhclient: Listening on LPF/wlan1/70:1a:04:a0:c8:f3
Jan  6 10:11:05 ss-pin dhclient: Sending on   LPF/wlan1/70:1a:04:a0:c8:f3
Jan  6 10:11:05 ss-pin dhclient: Sending on   Socket/fallback
Jan  6 10:11:05 ss-pin dhclient: DHCPREQUEST of 10.0.1.8 on wlan1 to 255.255.255.255 port 67
Jan  6 10:11:05 ss-pin dhclient: DHCPACK of 10.0.1.8 from 10.0.1.1
Jan  6 10:11:05 ss-pin dhclient: bound to 10.0.1.8 -- renewal in 43112 seconds.
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) started...
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info>   address 10.0.1.8
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info>   prefix 24 (255.255.255.0)
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info>   gateway 10.0.1.1
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info>   nameserver '10.0.1.1'
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info>   domain name 'nyc.rr.com'
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  6 10:11:05 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started...
Jan  6 10:11:05 ss-pin avahi-daemon[1145]: Joining mDNS multicast group on interface wlan1.IPv4 with address 10.0.1.8.
Jan  6 10:11:05 ss-pin avahi-daemon[1145]: New relevant interface wlan1.IPv4 for mDNS.
Jan  6 10:11:05 ss-pin avahi-daemon[1145]: Registering new address record for 10.0.1.8 on wlan1.IPv4.
Jan  6 10:11:06 ss-pin avahi-daemon[1145]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::721a:4ff:fea0:c8f3.
Jan  6 10:11:06 ss-pin avahi-daemon[1145]: New relevant interface wlan1.IPv6 for mDNS.
Jan  6 10:11:06 ss-pin avahi-daemon[1145]: Registering new address record for fe80::721a:4ff:fea0:c8f3 on wlan1.*.
Jan  6 10:11:06 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 7 -> 8 (reason 0)
Jan  6 10:11:06 ss-pin NetworkManager[1131]: <info> Policy set 'Auto :)' (wlan1) as default for IPv4 routing and DNS.
Jan  6 10:11:06 ss-pin NetworkManager[1131]: <info> Updating /etc/hosts with new system hostname
Jan  6 10:11:06 ss-pin NetworkManager[1131]: <info> Activation (wlan1) successful, device activated.
Jan  6 10:11:06 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete.
Jan  6 10:11:06 ss-pin nm-dispatcher.action: nm_dispatcher_action: Invalid connection: '(null)' / 'connection setting not found' invalid: 1
Jan  6 10:11:06 ss-pin nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
Jan  6 10:11:14 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 8 -> 3 (reason 38)
Jan  6 10:11:14 ss-pin NetworkManager[1131]: <info> (wlan1): deactivating device (reason: 38).
Jan  6 10:11:14 ss-pin NetworkManager[1131]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 2333
Jan  6 10:11:14 ss-pin avahi-daemon[1145]: Withdrawing address record for 10.0.1.8 on wlan1.
Jan  6 10:11:14 ss-pin avahi-daemon[1145]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 10.0.1.8.
Jan  6 10:11:14 ss-pin avahi-daemon[1145]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jan  6 10:11:14 ss-pin NetworkManager[1131]: <error> [1294326674.810959] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  6 10:11:14 ss-pin wpa_supplicant[1744]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  6 10:11:15 ss-pin acpid: client 1308[0:0] has disconnected
Jan  6 10:11:15 ss-pin acpid: client connected from 2408[0:0]
Jan  6 10:11:15 ss-pin acpid: 1 client rule loaded
Jan  6 10:11:15 ss-pin NetworkManager[1131]: <error> [1294326675.761341] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  6 10:11:17 ss-pin ntpdate[2458]: can't find host ntp.ubuntu.com
Jan  6 10:11:17 ss-pin ntpdate[2458]: no servers can be used, exiting
Jan  6 10:11:19 ss-pin gdm-simple-greeter[2466]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Jan  6 10:11:22 ss-pin gdm-session-worker[2475]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jan  6 10:11:25 ss-pin gdm-session-worker[2475]: pam_sm_authenticate: Called
Jan  6 10:11:25 ss-pin gdm-session-worker[2475]: pam_sm_authenticate: username = [ss]
Jan  6 10:11:26 ss-pin NetworkManager[1131]: <error> [1294326686.209473] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  6 10:11:26 ss-pin NetworkManager[1131]: <error> [1294326686.262591] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Jan  6 10:11:29 ss-pin gnome-session[2657]: EggSMClient-WARNING: Desktop file '/home/ss/.config/autostart/cairo-dock.desktop' has malformed Icon key 'cairo-dock.svg'(should not include extension)
Jan  6 10:11:29 ss-pin rtkit-daemon[1768]: Successfully made thread 2804 of process 2804 (n/a) owned by '1000' high priority at nice level -11.
Jan  6 10:11:29 ss-pin rtkit-daemon[1768]: Supervising 1 threads of 1 processes of 1 users.
Jan  6 10:11:30 ss-pin rtkit-daemon[1768]: Successfully made thread 2827 of process 2804 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:11:30 ss-pin rtkit-daemon[1768]: Supervising 2 threads of 1 processes of 1 users.
Jan  6 10:11:30 ss-pin gnome-session[2657]: WARNING: Could not launch application '1017dea49ab84a68b9129432634844054300000031380044.desktop': Unable to start application: Failed to execute child process "mintMenu.py" (No such file or directory)
Jan  6 10:11:30 ss-pin rtkit-daemon[1768]: Successfully made thread 2832 of process 2804 (n/a) owned by '1000' RT at priority 5.
Jan  6 10:11:30 ss-pin rtkit-daemon[1768]: Supervising 3 threads of 1 processes of 1 users.
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> Activation (wlan1) starting connection 'Auto :)'
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 3 -> 4 (reason 0)
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> Activation (wlan1/wireless): access point 'Auto :)' has security, but secrets are required.
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Jan  6 10:11:39 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Activation (wlan1/wireless): connection 'Auto :)' has security, and secrets exist.  No new secrets needed.
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Config: added 'ssid' value ':)'
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Config: added 'scan_ssid' value '1'
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Config: added 'psk' value '<omitted>'
Jan  6 10:11:41 ss-pin NetworkManager[1131]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:11:41 ss-pin NetworkManager[1131]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 10:11:41 ss-pin NetworkManager[1131]: <info> Config: set interface ap_scan to 1
Jan  6 10:11:42 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
Jan  6 10:11:43 ss-pin wpa_supplicant[1744]: Trying to associate with 04:1e:64:9a:14:ad (SSID=':)' freq=2462 MHz)
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  scanning -> associating
Jan  6 10:11:43 ss-pin wpa_supplicant[1744]: Associated with 04:1e:64:9a:14:ad
Jan  6 10:11:43 ss-pin wpa_supplicant[1744]: WPA: Key negotiation completed with 04:1e:64:9a:14:ad [PTK=CCMP GTK=CCMP]
Jan  6 10:11:43 ss-pin wpa_supplicant[1744]: CTRL-EVENT-CONNECTED - Connection to 04:1e:64:9a:14:ad completed (reauth) [id=0 id_str=]
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  associating -> associated
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  associated -> 4-way handshake
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  4-way handshake -> group handshake
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> (wlan1): supplicant connection state:  group handshake -> completed
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network ':)'.
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 5 -> 7 (reason 0)
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> dhclient started with pid 3037
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Jan  6 10:11:43 ss-pin dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  6 10:11:43 ss-pin dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan  6 10:11:43 ss-pin dhclient: All rights reserved.
Jan  6 10:11:43 ss-pin dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  6 10:11:43 ss-pin dhclient: 
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
Jan  6 10:11:43 ss-pin dhclient: Listening on LPF/wlan1/70:1a:04:a0:c8:f3
Jan  6 10:11:43 ss-pin dhclient: Sending on   LPF/wlan1/70:1a:04:a0:c8:f3
Jan  6 10:11:43 ss-pin dhclient: Sending on   Socket/fallback
Jan  6 10:11:43 ss-pin dhclient: DHCPREQUEST of 10.0.1.8 on wlan1 to 255.255.255.255 port 67
Jan  6 10:11:43 ss-pin dhclient: DHCPACK of 10.0.1.8 from 10.0.1.1
Jan  6 10:11:43 ss-pin dhclient: bound to 10.0.1.8 -- renewal in 36105 seconds.
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> (wlan1): DHCPv4 state changed preinit -> reboot
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) started...
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info>   address 10.0.1.8
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info>   prefix 24 (255.255.255.0)
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info>   gateway 10.0.1.1
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info>   nameserver '10.0.1.1'
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info>   domain name 'nyc.rr.com'
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) scheduled...
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Get) complete.
Jan  6 10:11:43 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started...
Jan  6 10:11:43 ss-pin avahi-daemon[1145]: Joining mDNS multicast group on interface wlan1.IPv4 with address 10.0.1.8.
Jan  6 10:11:43 ss-pin avahi-daemon[1145]: New relevant interface wlan1.IPv4 for mDNS.
Jan  6 10:11:43 ss-pin avahi-daemon[1145]: Registering new address record for 10.0.1.8 on wlan1.IPv4.
Jan  6 10:11:44 ss-pin NetworkManager[1131]: <info> (wlan1): device state change: 7 -> 8 (reason 0)
Jan  6 10:11:44 ss-pin NetworkManager[1131]: <info> Policy set 'Auto :)' (wlan1) as default for IPv4 routing and DNS.
Jan  6 10:11:44 ss-pin NetworkManager[1131]: <info> Activation (wlan1) successful, device activated.
Jan  6 10:11:44 ss-pin NetworkManager[1131]: <info> Activation (wlan1) Stage 5 of 5 (IP Configure Commit) complete.
Jan  6 10:11:55 ss-pin ntpdate[3204]: step time server 91.189.94.4 offset -1.142537 sec
```

here's what was just logged after i re-enabled networking. i disabled it since my connection dropped while i wrote this post. i am able to see available networks, but the notification icon just spins and spins and spins, only to eventually just show the disconnected icon.

```
Jan  6 11:44:11 ss-pin NetworkManager[1036]: <info> enable requested (sleeping: no  enabled: no)
Jan  6 11:44:11 ss-pin NetworkManager[1036]: <info> waking up and re-enabling...
Jan  6 11:44:11 ss-pin NetworkManager[1036]: <info> (wlan1): now managed
Jan  6 11:44:11 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 1 -> 2 (reason 2)
Jan  6 11:44:11 ss-pin NetworkManager[1036]: <info> (wlan1): bringing up device.
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> (wlan1): preparing device.
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> (wlan1): deactivating device (reason: 2).
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> (eth0): now managed
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> (eth0): bringing up device.
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> (eth0): preparing device.
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> (eth0): deactivating device (reason: 2).
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant interface state:  starting -> ready
Jan  6 11:44:17 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 2 -> 3 (reason 42)
Jan  6 11:44:17 ss-pin wpa_supplicant[1769]: Failed to initiate AP scan.
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> Activation (wlan1) starting connection 'Auto :)'
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 3 -> 4 (reason 0)
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> Activation (wlan1/wireless): access point 'Auto :)' has security, but secrets are required.
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Jan  6 11:44:18 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Activation (wlan1/wireless): connection 'Auto :)' has security, and secrets exist.  No new secrets needed.
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Config: added 'ssid' value ':)'
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Config: added 'scan_ssid' value '1'
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Config: added 'psk' value '<omitted>'
Jan  6 11:44:19 ss-pin NetworkManager[1036]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 11:44:19 ss-pin NetworkManager[1036]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 11:44:19 ss-pin NetworkManager[1036]: <info> Config: set interface ap_scan to 1
Jan  6 11:44:27 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  inactive -> scanning
Jan  6 11:44:28 ss-pin wpa_supplicant[1769]: Trying to associate with 04:1e:64:9a:14:ad (SSID=':)' freq=2462 MHz)
Jan  6 11:44:28 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  scanning -> associating
Jan  6 11:44:28 ss-pin wpa_supplicant[1769]: Associated with 04:1e:64:9a:14:ad
Jan  6 11:44:28 ss-pin wpa_supplicant[1769]: WPA: Key negotiation completed with 04:1e:64:9a:14:ad [PTK=CCMP GTK=CCMP]
Jan  6 11:44:28 ss-pin wpa_supplicant[1769]: CTRL-EVENT-CONNECTED - Connection to 04:1e:64:9a:14:ad completed (auth) [id=0 id_str=]
Jan  6 11:44:28 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  associating -> associated
Jan  6 11:44:28 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  associated -> 4-way handshake
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  4-way handshake -> group handshake
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  group handshake -> completed
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> Activation (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network ':)'.
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 5 -> 7 (reason 0)
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> dhclient started with pid 4746
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Jan  6 11:44:29 ss-pin dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan  6 11:44:29 ss-pin dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan  6 11:44:29 ss-pin dhclient: All rights reserved.
Jan  6 11:44:29 ss-pin dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  6 11:44:29 ss-pin dhclient: 
Jan  6 11:44:29 ss-pin NetworkManager[1036]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
Jan  6 11:44:29 ss-pin dhclient: Listening on LPF/wlan1/70:1a:04:a0:c8:f3
Jan  6 11:44:29 ss-pin dhclient: Sending on   LPF/wlan1/70:1a:04:a0:c8:f3
Jan  6 11:44:29 ss-pin dhclient: Sending on   Socket/fallback
Jan  6 11:44:29 ss-pin dhclient: DHCPREQUEST of 10.0.1.8 on wlan1 to 255.255.255.255 port 67
Jan  6 11:44:30 ss-pin avahi-daemon[1075]: Joining mDNS multicast group on interface wlan1.IPv6 with address fe80::721a:4ff:fea0:c8f3.
Jan  6 11:44:30 ss-pin avahi-daemon[1075]: New relevant interface wlan1.IPv6 for mDNS.
Jan  6 11:44:30 ss-pin avahi-daemon[1075]: Registering new address record for fe80::721a:4ff:fea0:c8f3 on wlan1.*.
Jan  6 11:44:32 ss-pin dhclient: DHCPREQUEST of 10.0.1.8 on wlan1 to 255.255.255.255 port 67
Jan  6 11:44:34 ss-pin wpa_supplicant[1769]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Jan  6 11:44:34 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  completed -> disconnected
Jan  6 11:44:34 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
Jan  6 11:44:35 ss-pin wpa_supplicant[1769]: Trying to associate with 04:1e:64:9a:14:ad (SSID=':)' freq=2462 MHz)
Jan  6 11:44:35 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  scanning -> associating
Jan  6 11:44:36 ss-pin dhclient: DHCPREQUEST of 10.0.1.8 on wlan1 to 255.255.255.255 port 67
Jan  6 11:44:45 ss-pin dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
Jan  6 11:44:45 ss-pin wpa_supplicant[1769]: Authentication with 04:1e:64:9a:14:ad timed out.
Jan  6 11:44:45 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  associating -> disconnected
Jan  6 11:44:45 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  disconnected -> scanning
Jan  6 11:44:48 ss-pin dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
Jan  6 11:44:49 ss-pin NetworkManager[1036]: <warn> (wlan1): link timed out.
Jan  6 11:44:55 ss-pin dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
Jan  6 11:45:10 ss-pin dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <warn> (wlan1): DHCPv4 request timed out.
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 4746
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 7 -> 9 (reason 5)
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <warn> Activation (wlan1) failed for access point (:))
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <info> Marking connection 'Auto :)' invalid.
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <warn> Activation (wlan1) failed.
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 9 -> 3 (reason 0)
Jan  6 11:45:14 ss-pin NetworkManager[1036]: <info> (wlan1): deactivating device (reason: 0).
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) starting connection 'Auto :)'
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 3 -> 4 (reason 0)
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1/wireless): access point 'Auto :)' has security, but secrets are required.
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 5 -> 6 (reason 0)
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 6 -> 4 (reason 0)
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> (wlan1): device state change: 4 -> 5 (reason 0)
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1/wireless): connection 'Auto :)' has security, and secrets exist.  No new secrets needed.
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Config: added 'ssid' value ':)'
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Config: added 'scan_ssid' value '1'
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Config: added 'psk' value '<omitted>'
Jan  6 11:45:39 ss-pin NetworkManager[1036]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 11:45:39 ss-pin NetworkManager[1036]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Jan  6 11:45:39 ss-pin NetworkManager[1036]: <info> Config: set interface ap_scan to 1
Jan  6 11:45:40 ss-pin NetworkManager[1036]: <info> (wlan1): supplicant connection state:  disconnected -> scanning

```

please excuse the massive amounts of log file viewer copy and  paste. i tried to make it neat by putting it in the code windows. i will edit out whichever parts are unnecessary. hope some of this helps and it's a simple solution.

---

### Post by teklife on 2011-02-03
i have spent countless hours searching google and reading dozens upon dozens of forum posts for answers, and trying the fixes, but nothing has solved this problem. i have also tried many other distros, and the only one in which the wireless worked, was pup-431bcm4312v3.iso, but i'm now having the same problems with that distro too.

i'm not sure if this has anything to do with it, but this mini dual boots mac os x 10.6 which works perfectly. i can leave it on for days and the wireless will never drop. however, when the wireless goes to **** on the linux side, it will usually affect it on the mac side, until i reboot several times, while killing the power during the multiple reboots.

since the wifi on the mac side works well, is it possible to use the mac side drivers somehow?? a la ndiswrapper. i tried following instructions to use ndiswrapper, but couldn't get it working. 

with a perfectly working os x partition, and previously installed windows partitions working so well, i *could* just easily and happily use those os's on this mini, but i would prefer to use linux, even though at this point it has cost me literally hundreds of hours searching for a fix that is probably fairly simple. 

i can't  make sense of the error messages, but why wont linux play nice with this bcm4312 (14e4 4315 rev 01) wireless card??

i have also tried installing the wl drivers, but i cannot; i get an error message. 

why does this wireless work without any problems on mac or windows, but will not work for more than a few minutes on linux??? i want to use linux so bad as my main system, and i try to turn ppl on to it all the time, but sadly, i will have to give up using it myself if i can't get this wireless issue solved:( i've never had so much frustration with any os before, yet i would like to get this sorted and continue using ubuntu.

---

### Post by Bucky Ball on 2011-02-03
Hmm. Try uninstalling all drivers, all wlan0 references or any other wireless references in Network Manager or Wicd, whichever you are using, and all wireless details, disable all drivers for the card and switch the machine off. 

Boot it. 

I am assuming you have the correct information in Network Manager to match your router's details?

---

### Post by Ptero-4 on 2011-02-03
Can you try deleting all the wifi drivers and then try and get the windoze ones (use the other *NIX you have there to download the drivers). Once you have those drivers in a USB stick install ndiswrapper and ndisgtk (you might need to download it before rebooting back into ubuntu) and install the windoze drivers. If that doesn't work, well, guess you'll be using that "other" *NIX for your wireless internet stuff (at least it's not windoze).

---

### Post by teklife on 2011-02-13
> **Ptero-4 said:**
> Can you try deleting all the wifi drivers and then try and get the windoze ones (use the other *NIX you have there to download the drivers). Once you have those drivers in a USB stick install ndiswrapper and ndisgtk (you might need to download it before rebooting back into ubuntu) and install the windoze drivers. If that doesn't work, well, guess you'll be using that "other" *NIX for your wireless internet stuff (at least it's not windoze).

well, i've uninstalled all wireless drivers, found a .inf file for the windows wireless drivers for my bcm4312 (not easy) and used ndiswrapper (finally figured out how with the help of youtube and ndiswrapper GUI), and VOILA!! wireless working now.

i thought i had it solved finally, and was going to post a [SOLVED] with instructions for others with the problem, when suddenly wireless dropped and couldn't get back online without the usual tricks to get back online. it did last a bit longer, about 30 minutes or so, but this wont work for me. 

i have done many tweaks and configuring on my pinguy/ubuntu setup, and i'd prefer to use it over mac os x or windows, but sadly, looks like i'll have to delete the gnu/linux partition and use mac os, like ptero4 said :|, or maybe i'll just leave the partition, or copy it, and maybe use it another time, in case i stumble upon some fix. thanks for the help guys.

---

### Post by Bucky Ball on 2011-02-13
[http://www.tomshardware.com/forum/237028-50-ubuntu-mini-1000-wireless](http://www.tomshardware.com/forum/237028-50-ubuntu-mini-1000-wireless)

Check best answer, second post.

---

