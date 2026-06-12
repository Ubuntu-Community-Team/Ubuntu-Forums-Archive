---
title: "External HD ieee1394 keeps bombing out - kernel bug??"
date: 2009-02-17
forum: General Help
---

### Post by Neural oD on 2009-02-17
Hi - this drive has been working fine, until recently. What I found is that it now disconnects itself. By this I mean that when I at first plug it in - it's recognized and is automatically mounted. But now twice today - it just vanishes. If I do a sudo fdisk -l - it doesn't even show up. this is the dmesg info:
```
 ieee1394: sbp2: Reconnected to SBP-2 device
[  190.784856] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  191.279285] ieee1394: sbp2: Reconnected to SBP-2 device
[  191.281570] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  218.375277] ieee1394: sbp2: Reconnected to SBP-2 device
[  218.377345] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  218.777324] ieee1394: sbp2: Reconnected to SBP-2 device
[  218.779503] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  219.174939] ieee1394: sbp2: Reconnected to SBP-2 device
[  219.177019] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  219.648027] ieee1394: sbp2: Reconnected to SBP-2 device
[  219.650103] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  220.180530] ieee1394: sbp2: Reconnected to SBP-2 device
[  220.183568] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  239.853932] ieee1394: sbp2: Reconnected to SBP-2 device
[  239.856948] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  311.617960] ieee1394: sbp2: Reconnected to SBP-2 device
[  311.621030] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[  550.960085] CE: hpet increasing min_delta_ns to 15000 nsec
[  885.236088] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[  918.472089] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[  952.236094] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[  983.016047] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1013.460093] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1044.665109] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1076.036106] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1107.648109] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1138.440122] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1170.828093] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1202.632091] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1243.180103] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1274.473061] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1305.897086] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1336.984053] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1391.948088] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1422.832108] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1453.625088] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1484.048114] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1514.492082] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1546.416125] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1577.476081] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1613.456178] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1613.458341] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1614.245584] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1614.248638] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1614.748373] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1614.751440] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1615.184198] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1615.186499] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1615.812112] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1615.814231] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1616.200905] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1616.203166] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1616.669514] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1616.671795] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1617.485489] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1617.487747] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1618.026305] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1618.029339] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1618.465442] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1618.467699] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1619.367904] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1619.370930] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1619.761150] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1619.763378] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1620.173022] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1620.175222] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1620.545515] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1620.547817] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1620.950220] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1620.953258] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1621.389110] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1621.392178] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1621.793020] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1621.795096] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1622.186069] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1622.189096] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1622.610060] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1622.613083] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1623.007716] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1623.010727] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1623.410654] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1623.413684] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1623.928345] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1623.930863] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1624.351075] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1624.354091] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1624.873102] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1624.875316] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1625.411039] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1625.413901] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1625.847641] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1625.849774] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1626.251082] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1626.254009] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1626.650049] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1626.653087] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1627.037466] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1627.039550] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1627.489351] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1627.491609] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1627.950288] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1627.953541] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1628.366333] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1628.368670] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1628.800227] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1628.802523] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1629.228492] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1629.230755] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1629.632490] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1629.635568] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1630.031890] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1630.034205] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1630.454728] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1630.457670] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1630.910867] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1630.913057] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1631.414259] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1631.417271] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1661.636121] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1843.665092] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1874.448084] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1906.204092] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 1937.217825] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1937.220076] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1937.627354] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1937.629505] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1938.125350] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1938.128388] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1938.718996] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1938.721286] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1939.182361] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1939.184625] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1939.695270] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1939.697545] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1940.131841] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1940.133915] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1940.538567] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1940.540817] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1940.946564] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1940.948828] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1941.434661] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1941.437676] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1941.913070] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1941.915938] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1942.333568] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1942.336585] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1942.757252] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1942.760256] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1943.619347] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1943.622343] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1944.532958] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1944.535194] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1945.008746] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1945.011144] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1945.397066] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1945.399339] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1946.368673] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1946.370913] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1946.963872] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1946.966173] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1947.486987] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1947.489267] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1948.029186] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1948.032300] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1948.414925] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1948.417219] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1948.968851] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1948.971019] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1949.394152] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1949.398508] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1949.775830] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1949.778861] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1950.602697] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1950.604941] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1951.035999] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1951.038249] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1951.662917] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1951.664985] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1952.077347] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1952.079569] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1952.568842] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1952.570910] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1953.261722] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1953.263987] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1953.847324] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1953.850159] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1954.368150] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1954.371172] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1954.950915] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1954.953819] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1955.830611] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1955.832918] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1956.437515] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1956.440542] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1956.832591] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1956.834846] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1957.224255] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1957.226330] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1957.974482] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1957.976740] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1958.487658] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1958.489908] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1959.360655] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1959.362950] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1959.769892] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1959.771972] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1960.462714] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1960.464994] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1960.931096] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1960.933359] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1961.507848] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1961.510867] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1962.192317] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1962.195338] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1962.614248] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1962.617442] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 1963.053136] ieee1394: sbp2: Reconnected to SBP-2 device
[ 1963.056189] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2012.904120] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 2043.561146] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 2075.309697] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 2107.968099] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 2140.741089] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 2172.516089] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 2204.665096] usb 7-3: reset high speed USB device using ehci_hcd and address 4
[ 2224.057661] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2224.059801] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2224.819976] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2224.822278] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2225.953464] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2225.955728] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2226.377974] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2226.381123] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2226.789526] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2226.791770] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2227.614432] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2227.617443] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2228.032202] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2228.035223] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2228.436413] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2228.438524] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2228.868973] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2228.871994] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2229.373548] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2229.375601] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2229.805142] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2229.807400] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2230.230878] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2230.233910] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2230.621566] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2230.623911] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2231.028082] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2231.031197] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2231.404090] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2231.406396] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2231.826375] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2231.829402] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2232.220659] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2232.222954] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2232.602799] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2232.606074] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2233.002379] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2233.005401] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2233.382081] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2233.385131] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2233.757780] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2233.759902] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2234.145307] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2234.147517] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2234.596362] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2234.598633] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2235.021930] ieee1394: sbp2: Reconnected to SBP-2 device
[ 2235.024103] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2265.040103] ieee1394: sbp2: aborting sbp2 command
[ 2265.040119] sd 6:0:0:0: [sdb] CDB: Read(10): 28 00 02 c0 a3 97 00 00 f8 00
[ 2265.040147] ieee1394: sbp2: hpsb_node_write failed.
[ 2265.040150] 
[ 2265.040176] ieee1394: sbp2: sbp2util_notify_fetch_agent failed.
[ 2275.041078] ieee1394: sbp2: aborting sbp2 command
[ 2275.041094] sd 6:0:0:0: [sdb] CDB: Test Unit Ready: 00 00 00 00 00 00
[ 2275.041118] ieee1394: sbp2: hpsb_node_write failed.
[ 2275.041120] 
[ 2275.041135] ieee1394: sbp2: reset requested
[ 2275.041139] ieee1394: sbp2: generating sbp2 fetch agent reset
[ 2275.041145] ieee1394: sbp2: hpsb_node_write failed.
[ 2275.041147] 
[ 2275.041168] ieee1394: sbp2: sbp2util_notify_fetch_agent failed.
[ 2285.041083] ieee1394: sbp2: aborting sbp2 command
[ 2285.041110] sd 6:0:0:0: [sdb] CDB: Test Unit Ready: 00 00 00 00 00 00
[ 2285.041156] ieee1394: sbp2: hpsb_node_write failed.
[ 2285.041158] 
[ 2285.041194] sd 6:0:0:0: Device offlined - not ready after error recovery
[ 2285.041238] sd 6:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
[ 2285.041247] end_request: I/O error, dev sdb, sector 46179223
[ 2285.041258] Buffer I/O error on device sdb1, logical block 5772395
[ 2285.041275] Buffer I/O error on device sdb1, logical block 5772396
[ 2285.041282] Buffer I/O error on device sdb1, logical block 5772397
[ 2285.041288] Buffer I/O error on device sdb1, logical block 5772398
[ 2285.041295] Buffer I/O error on device sdb1, logical block 5772399
[ 2285.041302] Buffer I/O error on device sdb1, logical block 5772400
[ 2285.041309] Buffer I/O error on device sdb1, logical block 5772401
[ 2285.041315] Buffer I/O error on device sdb1, logical block 5772402
[ 2285.041322] Buffer I/O error on device sdb1, logical block 5772403
[ 2285.041328] Buffer I/O error on device sdb1, logical block 5772404
[ 2285.041442] sd 6:0:0:0: rejecting I/O to offline device
[ 2285.041482] sd 6:0:0:0: rejecting I/O to offline device
[ 2285.041543] sd 6:0:0:0: rejecting I/O to offline device
[ 2285.041564] sd 6:0:0:0: rejecting I/O to offline device
[ 2285.041587] sd 6:0:0:0: rejecting I/O to offline device
[ 2285.041606] sd 6:0:0:0: rejecting I/O to offline device
[ 2285.041621] sd 6:0:0:0: rejecting I/O to offline device
[ 2285.063782] sd 6:0:0:0: rejecting I/O to offline device
[ 2285.064130] sd 6:0:0:0: rejecting I/O to offline device
[ 2285.067560] sd 6:0:0:0: rejecting I/O to offline device
[ 2345.358617] sd 6:0:0:0: rejecting I/O to offline device
[ 2345.358626] __ratelimit: 31 callbacks suppressed
[ 2345.358629] Buffer I/O error on device sdb1, logical block 5772395

```

has anyone come up against this problem. I personally think it maybe a kernel bug - but was wanting to find out if anyone knew anything. 

BTW - I think this happens after a large paste operation  - so maybe someone can emulate this. Here is my kernel info from uname -a
```
Linux nutter 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux
```

---

### Post by Neural oD on 2009-02-18
bump

---

