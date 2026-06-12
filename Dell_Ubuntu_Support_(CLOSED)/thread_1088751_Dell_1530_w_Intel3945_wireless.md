---
title: "Dell 1530 w/ Intel3945 wireless"
date: 2009-03-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ussndmac on 2009-03-06
I have been unsuccessful at getting wireless working on my Dell 1530.

I have done attempted many of the recommendations in various threads to no avail.

When the machine arrived from Dell it had Dell installed 8.04.

Since then the machine has been wiped and both vanilla Ubuntu and Ubuntu Studio 8.0.4 64bit has been installed. Currently the later.

Since removing the Dell installed 8.0.4 I have not been able to do wireless networking.

At this point the correct drivers are loaded, etc. and the system will see the wap. And, the wap log shows a connection.

But, there is no ip traffic, i.e. I can't ping anything on the net connected to the wap or the wap.

Does anyone know what Dell adds or backports to their install of Ubuntu?

Regards,
Mac

---

### Post by pytheas22 on 2009-03-06
Please connect to the AP, then post the output of these commands:
```

ifconfig
sudo iwlist scan
dmesg | grep -e wlan -e iwl
lshw -C Network
lspci -nn | grep -i -e ethernet -e wireless
uname -rm
```

Unfortunately I'm not sure where Dell gets its wireless drivers from, but I wouldn't think that the iwl3945 driver would be any different than the normal Linux one.  If you post the information requested above, we can try to figure out why you can't connect.

---

### Post by ussndmac on 2009-03-06
Thanks for having a look:

```

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:21:9b:e7:76:fc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13092269 (12.4 MB)  TX bytes:476284 (465.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86610 (84.5 KB)  TX bytes:86610 (84.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:c0:ab:f1  
          inet addr:192.168.53.13  Bcast:192.168.53.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-C0-AB-F1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0C:41:68:E7:99
                    ESSID:"macwap"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=95/100  Signal level=-34 dBm  Noise level=-127 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:tsf=000000000d8360d8


 dmesg | grep -e wlan -e iwl
[   26.998907] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   26.998913] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   26.999532] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   28.449625] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   28.450865] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   33.182128] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  459.882235] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  496.662989] wlan0: Initial auth_alg=0
[  496.662999] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  496.665422] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  496.665431] wlan0: authenticated
[  496.665435] wlan0: associate with AP 00:0c:41:68:e7:99
[  496.667084] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  496.667089] wlan0: AP denied association (code=18)
[  496.738309] wlan0: associate with AP 00:0c:41:68:e7:99
[  496.739609] wlan0: invalid aid value 0; bits 15:14 not set
[  496.739620] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=1 aid=0)
[  496.739624] wlan0: AP denied association (code=1)
[  496.822843] wlan0: associate with AP 00:0c:41:68:e7:99
[  496.825192] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  496.825200] wlan0: AP denied association (code=18)
[  496.891206] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  497.444290] wlan0: RX deauthentication from 00:0c:41:68:e7:99 (reason=16)
[  497.444299] wlan0: deauthenticated
[  502.377004] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  502.477209] wlan0: Initial auth_alg=0
[  502.477219] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  502.478184] wlan0: Initial auth_alg=0
[  502.478187] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  502.480959] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  502.480964] wlan0: authenticated
[  502.480966] wlan0: associate with AP 00:0c:41:68:e7:99
[  502.481824] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  502.483234] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  502.483237] wlan0: AP denied association (code=18)
[  502.621884] wlan0: associate with AP 00:0c:41:68:e7:99
[  502.626159] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  502.626170] wlan0: AP denied association (code=18)
[  502.678932] wlan0: associate with AP 00:0c:41:68:e7:99
[  502.681117] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  502.681126] wlan0: AP denied association (code=18)
[  502.737455] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  509.666944] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  509.716712] wlan0: Initial auth_alg=0
[  509.716722] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  509.718653] wlan0: Initial auth_alg=0
[  509.718659] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  509.718681] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  509.718683] wlan0: authenticated
[  509.718686] wlan0: associate with AP 00:0c:41:68:e7:99
[  509.721827] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  509.723236] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  509.724862] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  509.724864] wlan0: AP denied association (code=18)
[  509.810583] wlan0: associate with AP 00:0c:41:68:e7:99
[  509.811885] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  509.811905] wlan0: AP denied association (code=18)
[  509.875749] wlan0: associate with AP 00:0c:41:68:e7:99
[  509.877300] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  509.877309] wlan0: AP denied association (code=18)
[  509.939476] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  516.874150] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  516.924323] wlan0: Initial auth_alg=0
[  516.924330] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  516.925341] wlan0: Initial auth_alg=0
[  516.925346] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  516.927765] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  516.927771] wlan0: authenticated
[  516.927772] wlan0: associate with AP 00:0c:41:68:e7:99
[  516.929564] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  516.930282] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  516.930285] wlan0: AP denied association (code=18)
[  517.031546] wlan0: associate with AP 00:0c:41:68:e7:99
[  517.033178] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  517.033187] wlan0: AP denied association (code=18)
[  517.092687] wlan0: associate with AP 00:0c:41:68:e7:99
[  517.094206] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  517.094214] wlan0: AP denied association (code=18)
[  517.178018] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  523.209118] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  523.260585] wlan0: Initial auth_alg=0
[  523.260592] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  523.261464] wlan0: Initial auth_alg=0
[  523.261469] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  523.264102] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  523.264108] wlan0: authenticated
[  523.264110] wlan0: associate with AP 00:0c:41:68:e7:99
[  523.266059] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  523.266063] wlan0: AP denied association (code=18)
[  523.358752] wlan0: associate with AP 00:0c:41:68:e7:99
[  523.359984] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  523.359994] wlan0: AP denied association (code=18)
[  523.420209] wlan0: associate with AP 00:0c:41:68:e7:99
[  523.422348] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  523.422356] wlan0: AP denied association (code=18)
[  523.493066] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  528.711615] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  528.764521] wlan0: Initial auth_alg=0
[  528.764531] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  528.765572] wlan0: Initial auth_alg=0
[  528.765576] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  528.767242] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  528.767248] wlan0: authenticated
[  528.767250] wlan0: associate with AP 00:0c:41:68:e7:99
[  528.768787] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  528.770380] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  528.770382] wlan0: AP denied association (code=18)
[  528.864133] wlan0: associate with AP 00:0c:41:68:e7:99
[  528.865450] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  528.865460] wlan0: AP denied association (code=18)
[  528.923916] wlan0: associate with AP 00:0c:41:68:e7:99
[  528.925630] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  528.925639] wlan0: AP denied association (code=18)
[  528.983731] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  534.690315] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  534.745618] wlan0: Initial auth_alg=0
[  534.745624] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  534.746327] wlan0: Initial auth_alg=0
[  534.746331] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  534.748864] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  534.748869] wlan0: authenticated
[  534.748871] wlan0: associate with AP 00:0c:41:68:e7:99
[  534.751222] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  534.751225] wlan0: AP denied association (code=18)
[  534.885785] wlan0: associate with AP 00:0c:41:68:e7:99
[  534.887201] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  534.887210] wlan0: AP denied association (code=18)
[  534.967710] wlan0: associate with AP 00:0c:41:68:e7:99
[  534.969576] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  534.969584] wlan0: AP denied association (code=18)
[  535.057795] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  542.682001] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  542.744335] wlan0: Initial auth_alg=0
[  542.744340] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  542.745252] wlan0: Initial auth_alg=0
[  542.745256] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  542.747859] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  542.747865] wlan0: authenticated
[  542.747867] wlan0: associate with AP 00:0c:41:68:e7:99
[  542.749640] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  542.750658] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  542.750660] wlan0: AP denied association (code=18)
[  542.867094] wlan0: associate with AP 00:0c:41:68:e7:99
[  542.868587] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  542.868597] wlan0: AP denied association (code=18)
[  542.962690] wlan0: associate with AP 00:0c:41:68:e7:99
[  542.967317] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  542.967326] wlan0: AP denied association (code=18)
[  543.032158] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  552.681973] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  552.733963] wlan0: Initial auth_alg=0
[  552.733969] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  552.734798] wlan0: Initial auth_alg=0
[  552.734803] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  552.737654] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  552.737662] wlan0: authenticated
[  552.737665] wlan0: associate with AP 00:0c:41:68:e7:99
[  552.739567] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  552.739570] wlan0: AP denied association (code=18)
[  552.830131] wlan0: associate with AP 00:0c:41:68:e7:99
[  552.831643] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  552.831651] wlan0: AP denied association (code=18)
[  552.892498] wlan0: associate with AP 00:0c:41:68:e7:99
[  552.894166] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  552.894176] wlan0: AP denied association (code=18)
[  552.956746] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  558.674837] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  558.726412] wlan0: Initial auth_alg=0
[  558.726418] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  558.728158] wlan0: Initial auth_alg=0
[  558.728163] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  558.728676] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  558.728680] wlan0: authenticated
[  558.728682] wlan0: associate with AP 00:0c:41:68:e7:99
[  558.730164] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  558.732436] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  558.732441] wlan0: AP denied association (code=18)
[  558.827321] wlan0: associate with AP 00:0c:41:68:e7:99
[  558.829292] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  558.829300] wlan0: AP denied association (code=18)
[  558.889601] wlan0: associate with AP 00:0c:41:68:e7:99
[  558.891404] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  558.891413] wlan0: AP denied association (code=18)
[  558.956483] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  564.266085] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  564.320040] wlan0: Initial auth_alg=0
[  564.320046] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  564.321347] wlan0: Initial auth_alg=0
[  564.321352] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  564.321893] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  564.321897] wlan0: authenticated
[  564.321899] wlan0: associate with AP 00:0c:41:68:e7:99
[  564.324560] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  564.325751] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  564.325754] wlan0: AP denied association (code=18)
[  564.428392] wlan0: associate with AP 00:0c:41:68:e7:99
[  564.430263] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  564.430270] wlan0: AP denied association (code=18)
[  564.495151] wlan0: associate with AP 00:0c:41:68:e7:99
[  564.496865] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  564.496873] wlan0: AP denied association (code=18)
[  564.557641] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  570.584420] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  570.635609] wlan0: Initial auth_alg=0
[  570.635619] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  570.636665] wlan0: Initial auth_alg=0
[  570.636669] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  570.638791] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  570.638797] wlan0: authenticated
[  570.638799] wlan0: associate with AP 00:0c:41:68:e7:99
[  570.640784] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  570.640788] wlan0: AP denied association (code=18)
[  570.740798] wlan0: associate with AP 00:0c:41:68:e7:99
[  570.743185] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  570.743192] wlan0: AP denied association (code=18)
[  570.843951] wlan0: associate with AP 00:0c:41:68:e7:99
[  570.846231] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  570.846239] wlan0: AP denied association (code=18)
[  570.954429] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  577.174096] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  577.224499] wlan0: Initial auth_alg=0
[  577.224510] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  577.225446] wlan0: Initial auth_alg=0
[  577.225449] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  577.227280] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  577.227287] wlan0: authenticated
[  577.227289] wlan0: associate with AP 00:0c:41:68:e7:99
[  577.229108] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  577.229112] wlan0: AP denied association (code=18)
[  577.318477] wlan0: associate with AP 00:0c:41:68:e7:99
[  577.320260] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  577.320267] wlan0: AP denied association (code=18)
[  577.378454] wlan0: associate with AP 00:0c:41:68:e7:99
[  577.379853] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  577.379862] wlan0: AP denied association (code=18)
[  577.438936] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  583.030493] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  583.080670] wlan0: Initial auth_alg=0
[  583.080675] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  583.082414] wlan0: Initial auth_alg=0
[  583.082419] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  583.082436] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  583.082438] wlan0: authenticated
[  583.082440] wlan0: associate with AP 00:0c:41:68:e7:99
[  583.085148] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  583.089548] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  583.090627] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  583.090629] wlan0: AP denied association (code=18)
[  583.175574] wlan0: associate with AP 00:0c:41:68:e7:99
[  583.177359] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  583.177368] wlan0: AP denied association (code=18)
[  583.234789] wlan0: associate with AP 00:0c:41:68:e7:99
[  583.236175] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  583.236185] wlan0: AP denied association (code=18)
[  583.293510] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  589.431769] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  589.485055] wlan0: Initial auth_alg=0
[  589.485061] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  589.485987] wlan0: Initial auth_alg=0
[  589.485991] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  589.488591] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  589.488604] wlan0: authenticated
[  589.488606] wlan0: associate with AP 00:0c:41:68:e7:99
[  589.491072] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  589.492133] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  589.492136] wlan0: AP denied association (code=18)
[  589.639204] wlan0: associate with AP 00:0c:41:68:e7:99
[  589.640681] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  589.640691] wlan0: AP denied association (code=18)
[  589.791787] wlan0: associate with AP 00:0c:41:68:e7:99
[  589.794079] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  589.794087] wlan0: AP denied association (code=18)
[  589.882734] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  596.165746] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  596.214162] wlan0: Initial auth_alg=0
[  596.214167] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  596.215086] wlan0: Initial auth_alg=0
[  596.215090] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  596.216725] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  596.216731] wlan0: authenticated
[  596.216733] wlan0: associate with AP 00:0c:41:68:e7:99
[  596.218712] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  596.220589] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  596.220591] wlan0: AP denied association (code=18)
[  596.310415] wlan0: associate with AP 00:0c:41:68:e7:99
[  596.311819] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  596.311830] wlan0: AP denied association (code=18)
[  596.375997] wlan0: associate with AP 00:0c:41:68:e7:99
[  596.377428] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  596.377437] wlan0: AP denied association (code=18)
[  596.440738] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  602.834529] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  602.918959] wlan0: Initial auth_alg=0
[  602.918964] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  602.921052] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  602.921057] wlan0: authenticated
[  602.921059] wlan0: associate with AP 00:0c:41:68:e7:99
[  602.923080] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  602.923089] wlan0: AP denied association (code=18)
[  602.925294] wlan0: Initial auth_alg=0
[  602.925300] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  602.927295] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  602.927302] wlan0: authenticated
[  602.927304] wlan0: associate with AP 00:0c:41:68:e7:99
[  602.929444] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  602.929449] wlan0: AP denied association (code=18)
[  603.057774] wlan0: associate with AP 00:0c:41:68:e7:99
[  603.059225] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  603.059233] wlan0: AP denied association (code=18)
[  603.131706] wlan0: associate with AP 00:0c:41:68:e7:99
[  603.133056] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  603.133066] wlan0: AP denied association (code=18)
[  603.200639] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  608.540958] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  608.591997] wlan0: Initial auth_alg=0
[  608.592003] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  608.592675] wlan0: Initial auth_alg=0
[  608.592679] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  608.595918] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  608.595924] wlan0: authenticated
[  608.595926] wlan0: associate with AP 00:0c:41:68:e7:99
[  608.598155] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  608.598158] wlan0: AP denied association (code=18)
[  608.712104] wlan0: associate with AP 00:0c:41:68:e7:99
[  608.713938] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  608.713960] wlan0: AP denied association (code=18)
[  608.775183] wlan0: associate with AP 00:0c:41:68:e7:99
[  608.777333] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  608.777340] wlan0: AP denied association (code=18)
[  608.834848] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  615.994648] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  616.053749] wlan0: Initial auth_alg=0
[  616.053755] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  616.055384] wlan0: Initial auth_alg=0
[  616.055388] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  616.055404] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  616.055406] wlan0: authenticated
[  616.055408] wlan0: associate with AP 00:0c:41:68:e7:99
[  616.058432] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  616.059439] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  616.059442] wlan0: AP denied association (code=18)
[  616.171109] wlan0: associate with AP 00:0c:41:68:e7:99
[  616.172547] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  616.172556] wlan0: AP denied association (code=18)
[  616.240700] wlan0: associate with AP 00:0c:41:68:e7:99
[  616.242108] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  616.242116] wlan0: AP denied association (code=18)
[  616.311992] wlan0: association with AP 00:0c:41:68:e7:99 timed out
[  622.443246] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  622.491965] wlan0: Initial auth_alg=0
[  622.491974] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  622.492799] wlan0: Initial auth_alg=0
[  622.492803] wlan0: authenticate with AP 00:0c:41:68:e7:99
[  622.494569] wlan0: RX authentication from 00:0c:41:68:e7:99 (alg=0 transaction=2 status=0)
[  622.494575] wlan0: authenticated
[  622.494577] wlan0: associate with AP 00:0c:41:68:e7:99
[  622.496382] wlan0: authentication frame received from 00:0c:41:68:e7:99, but not in authenticate state - ignored
[  622.497986] wlan0: RX AssocResp from 00:0c:41:68:e7:99 (capab=0x1 status=18 aid=0)
[  622.497989] wlan0: AP denied association (code=18)

 lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e7:76:fc
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1f:3c:c0:ab:f1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.53.13 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

lspci -nn | grep -i -e ethernet -e wireless
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)

uname -rm
2.6.24-23-rt x86_64



```

---

### Post by pytheas22 on 2009-03-06
It looks like you're getting disconnected from the AP for some reason, although the specific source of the problem is unclear.  It may help if you used wicd instead of Network Manager to connect.  You can install wicd by typing:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.  Do you still lose the connection?

Also, I assume you have other computers connected to this AP and they don't have a problem, correct?  If not, you should try other machines just to rule out a problem on the AP's end (I spent many frustrating hours cursing Linux a couple months ago because my wireless kept cutting out, only to discover eventually that my router was just breaking).

Also, note that installing wicd will require you to uninstall Network Manager.  If you want NM back later, just type:
```

sudo apt-get install network-manager-gnome
```

---

### Post by ussndmac on 2009-03-07
Well, Wicd is already on the machine.

I don't remember un-installing NM though.

I did notice last night when getting the fodder from the various commands, that Wicd was connecting, disconnecting, and reconnecting repeatedly.

Yes, there are windows machines connected to the wap with no problem for, well, for years. With WEP.

At this point all security is OFF on the wap. And the windows pc is still working just fine (with it's security adjusted accordingly).

---

### Post by pytheas22 on 2009-03-07
If wicd doesn't work any better, I guess it's not Network Manager's fault.

You might have better luck if you compile the iwl3945 driver from source using the latest compat-wireless code from linuxwireless.org.  To do that, first download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2") and save it to your desktop.  Then run these commands:
```

cd ~/Desktop
sudo apt-get install build-essential
tar -xjvf compat-wireless-2.6.tar.bz2
cd compat-wireless*
make
sudo make unload
sudo make load
sudo make install
```

Then reboot.  Is the connection still flaky?

Another possible solution would be using the ipw3945 legacy driver instead of iwl3945.  There are instructions [here]("http://www.ubuntugeek.com/using-ipw3945-instead-iwl3945-in-hardy.html") for compiling ipw3945 on Hardy/Intrepid, but some of the links are broken, and I'm not sure if it will compile against the latest Intrepid kernel.  But you could try if you have a lot of time to kill.

---

### Post by ussndmac on 2009-03-19
For other reasons, I have recently installed Ubuntu Studio 8.10 with -rt kernel.

I didn't expect it to fix my wifi issue and indeed it din not. In fact, it added the twist that now my laptop hangs when I shutdown. I have to use the power switch at that point.

My question is do think I should just go ahead and try to build the source for iwl3945 to address the wifi issue at this point?

---

### Post by pytheas22 on 2009-03-19
Yes, I would try the commands from my last post to build iwl3945 from source.

As for the failure to shutdown, it's a common problem with some computers and has to do with apci issues.  There are usually ways to fix it, but we can deal with that once your wireless works.  For the time being, it's safe to power it down with the power button once Ubuntu has finished shutting down, however; it won't hurt anything.

---

### Post by ussndmac on 2009-03-19
curious behavior with the wired net now.

it's fine until I try to use ifconfig or network shutdown.

at which point it basically hangs and the mouse cursor, when moved updates in very slow jumps. and the terminal window where the command was entered is dead.

at this point I have to use the power switch to just shutdown.

---

### Post by pytheas22 on 2009-03-19
> curious behavior with the wired net now.

it's fine until I try to use ifconfig or network shutdown.

at which point it basically hangs and the mouse cursor, when moved updates in very slow jumps. and the terminal window where the command was entered is dead.

at this point I have to use the power switch to just shutdown.

That's strange, but it sounds like a bug with the ethernet driver is causing a kernel panic when you trying to bring the device down.  You could try to rmmod the ethernet module instead; it may help.  Otherwise, I would avoid using ifconfig to put the card down for the time being, and we can fix this problem later if it's important to you.

---

### Post by ussndmac on 2009-03-19
Actually, I use this system for recording.

large files, so the faster wired is used more.

Do I need to shut down wired to setup wireless?

---

### Post by pytheas22 on 2009-03-19
> Do I need to shut down wired to setup wireless?

No, you can compile the iwl3945 driver and scan for networks and all that while the wired is still up.  However, Ubuntu's NetworkManager by default will prefer a wired connection over wireless if both are available, so if you want to connect to a wireless network, you will need to bring the wired connection down.  You could always just unplug the wire, however.  It should also disconnect if you type:
```

sudo dhclient -r eth0
```

which will force the wired connection to give up its IP (assuming you use dynamic IPs served via dhcp), essentially taking eth0 down (I'm not sure if NetworkManager would automatically try to get a new IP for eth0).

---

### Post by ussndmac on 2009-03-20
Well compiling the module went ok. No errors and the wifi light came on which is new.

But, no connection. 

Didn't see netmanager or wicd so I first tried netmanager.

The machine hung on boot. Sometimes I could see errors indicating modprobe failed.

So I removed netmanager and tried wicd. Same results.

If the wifi switch is of it just hangs on boot.

---

### Post by ussndmac on 2009-03-20
I know all this stuff is set up in various files.

So I should be able to do, by hand with an editor, what all netman and wicd do. (Yes, my UNIX goes back to VI...)

Where can I find documentation that shows the sequence that these files are read and executed during boot?

And what needs to be in them for various thing to work?

---

### Post by pytheas22 on 2009-03-20
Sorry the newly compiled module doesn't work.  But at least the LED comes on; that's good.

There's a guide [here]("http://ubuntuforums.org/showthread.php?t=571188") on manual management of wireless connections.  It shows you how to get connected without using wicd or NetworkManager.

You should also be familiar with these files:

1. /etc/modprobe.d/blacklist - a list of modules to 'blacklist', preventing the system from loading them.  So if iwl3945 is causing the system to hang at boot, you could blacklist it so it doesn't get loaded until you decide to do so explicitly (by removing it from the blacklist and typing 'sudo modprobe iwl3945').

2. /etc/modules - list of modules to be loaded during boot.  If iwl3945 is on this list, it will always be loaded at boot, regardless of whether the system thinks it should be.  It's probably not on that list by default, however.

You can use the 'dmesg' command (or look at the system logs) to get information why the system is having problems loading iwl3945.

---

### Post by omarly on 2009-08-14
thxs. this did it for me. So far so good. (hope it stays!) 

fresh install of 9.04 with unstable wifi last days.

---

