---
title: "iwl3945 error &amp; froozen desktop."
date: 2009-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by redmi on 2009-08-17
Hi, I have a dell inspiron 1525 (ubuntu pre-installed). Now I have problems with the iwl3945. First of all I can connect and I can open firefox (or another browser), dmesg says:

[  842.081963] wlan0: Initial auth_alg=0
[  842.081973] wlan0: direct probe to AP 00:b0:0c:02:18:9c try 1
[  842.084603] wlan0 direct probe responded
[  842.084615] wlan0: authenticate with AP 00:b0:0c:02:18:9c
[  842.086372] wlan0: RX authentication from 00:b0:0c:02:18:9c (alg=0 transaction=2 status=0)
[  842.086382] wlan0: authenticated
[  842.086387] wlan0: associate with AP 00:b0:0c:02:18:9c
[  842.090691] wlan0: RX AssocResp from 00:b0:0c:02:18:9c (capab=0x11 status=0 aid=1)
[  842.090699] wlan0: associated
[  842.090717] wlan0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 txop=0
[  842.092829] wlan0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 txop=0
[  842.092944] wlan0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 txop=94
[  842.093022] wlan0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 txop=47
[  842.097646] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  842.622354] wlan0: RX protected frame, but have no key
[  843.127148] wlan0: RX protected frame, but have no key
[  843.233649] padlock: VIA PadLock not detected.
[  844.623813] wlan0: RX protected frame, but have no key
[  862.182913] wlan0: no IPv6 routers present

that's okey, but after two minutes or so (just googling) I get

[ 1394.771705] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[ 1396.755640] iwl3945: Can't stop Rx DMA.
[ 1396.916666] Registered led device: iwl-phy0:radio
[ 1396.916688] Registered led device: iwl-phy0:assoc
[ 1396.916707] Registered led device: iwl-phy0:RX
[ 1396.916724] Registered led device: iwl-phy0:TX

and then desktop froozes, I can close windows, but I can't start any program (including programs in console, except dmesg and top), I can't restart X and I have to turn off by pressing the power button (no other thing works).

I've tried a solution posted [here]("http://ubuntuforums.org/showthread.php?t=820297"), but it doesn't work.

Thank you for your time, and sorry for my bad english.

---

