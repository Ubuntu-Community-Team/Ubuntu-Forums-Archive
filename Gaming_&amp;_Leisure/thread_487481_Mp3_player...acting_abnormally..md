---
title: "Mp3 player...acting abnormally."
date: 2007-06-29
forum: Gaming &amp; Leisure
---

### Post by Alucard_Duskmoon on 2007-06-29
Hi, I have a Samsung YP-TJ9 MP3 player. (It recognizes it as an MTP player in Windows.) My problem starts when I plug it in. It reads it as connected then flashes to the "Samsung" screen then it will show it as being "not connected". It will repeat that over and over until I unplug it from my computer. It will charge normally but Ubuntu won't recognize it. (Using 7.04) Anyone have any suggestions on what I could do? (Btw, i'm still learning about linux so if I ask for you to simplify somthing please don't get upset with me.) If anyone has the same problem or could help please post.
Thanks.

---

### Post by Anonymvs on 2007-06-29
Did the mp3 player need any special software in windows, or did you just drag and drop files onto it?
If it's the latter, open "Computer" and see if it shows up when your screen says it is connected, it should as a harddrive.

---

### Post by Alucard_Duskmoon on 2007-06-29
Yea, it did come with software but It also worked with Windows Media Player.

---

### Post by Anonymvs on 2007-06-29
Try installing Banshee, it's in my mind the best media player out there, and it supports practically everything, ipods, podcasts, etc.  If there was a nice graphical music player that would work with your mp3 player, Banshee would be my bet.

if WMP supported it, I'd also look through the manual as I think it's pretty likely that your mp3 player just needs the music dragged and dropped onto it's harddrive to work, in that case, just mount and copy what you want then unmount.

---

### Post by hikaricore on 2007-06-29
Open a terminal, plug in the usb device, wait for a minute or so then type:

```
dmesg
```

You should see some output about usb devices at the bottom, copy and past it here and hopefully someone can point you in the right direction.

---

### Post by Alucard_Duskmoon on 2007-06-29
Heres what it said when I ran dmesg

```
[15524.673685] usb 4-2: new high speed USB device using ehci_hcd and address 104
[15524.813667] usb 4-2: configuration #1 chosen from 1 choice
[15529.453919] usb 4-2: USB disconnect, address 104
[15535.689039] usb 4-2: new high speed USB device using ehci_hcd and address 105
[15535.829064] usb 4-2: configuration #1 chosen from 1 choice
[15540.449325] usb 4-2: USB disconnect, address 105
[15546.848294] usb 4-2: new high speed USB device using ehci_hcd and address 106
[15546.988301] usb 4-2: configuration #1 chosen from 1 choice
[15551.728471] usb 4-2: USB disconnect, address 106
[15558.123484] usb 4-2: new high speed USB device using ehci_hcd and address 107
[15558.263551] usb 4-2: configuration #1 chosen from 1 choice
[15562.891672] usb 4-2: USB disconnect, address 107
[15569.290525] usb 4-2: new high speed USB device using ehci_hcd and address 108
[15569.430488] usb 4-2: configuration #1 chosen from 1 choice
[15574.054677] usb 4-2: USB disconnect, address 108
[15580.449533] usb 4-2: new high speed USB device using ehci_hcd and address 109
[15580.585482] usb 4-2: configuration #1 chosen from 1 choice
[15585.293683] usb 4-2: USB disconnect, address 109
[15591.692472] usb 4-2: new high speed USB device using ehci_hcd and address 110
[15591.832394] usb 4-2: configuration #1 chosen from 1 choice
[15596.468551] usb 4-2: USB disconnect, address 110
[15602.867240] usb 4-2: new high speed USB device using ehci_hcd and address 111
[15603.011266] usb 4-2: configuration #1 chosen from 1 choice
[15607.635278] usb 4-2: USB disconnect, address 111
[15614.030245] usb 4-2: new high speed USB device using ehci_hcd and address 112
[15614.170184] usb 4-2: configuration #1 chosen from 1 choice
[15618.874467] usb 4-2: USB disconnect, address 112
[15625.265477] usb 4-2: new high speed USB device using ehci_hcd and address 113
[15625.401477] usb 4-2: configuration #1 chosen from 1 choice
[15630.069638] usb 4-2: USB disconnect, address 113
[15636.460631] usb 4-2: new high speed USB device using ehci_hcd and address 114
[15636.600679] usb 4-2: configuration #1 chosen from 1 choice
[15641.240869] usb 4-2: USB disconnect, address 114
[15647.631818] usb 4-2: new high speed USB device using ehci_hcd and address 115
[15647.771843] usb 4-2: configuration #1 chosen from 1 choice
[15652.403945] usb 4-2: USB disconnect, address 115
[15658.798891] usb 4-2: new high speed USB device using ehci_hcd and address 116
[15658.938870] usb 4-2: configuration #1 chosen from 1 choice
[15663.810965] usb 4-2: USB disconnect, address 116
[15670.201956] usb 4-2: new high speed USB device using ehci_hcd and address 117
[15670.342000] usb 4-2: configuration #1 chosen from 1 choice
[15674.969993] usb 4-2: USB disconnect, address 117
[15681.364965] usb 4-2: new high speed USB device using ehci_hcd and address 118
[15681.509010] usb 4-2: configuration #1 chosen from 1 choice
[15686.137172] usb 4-2: USB disconnect, address 118
[15692.528041] usb 4-2: new high speed USB device using ehci_hcd and address 119
[15692.668052] usb 4-2: configuration #1 chosen from 1 choice
[15697.368177] usb 4-2: USB disconnect, address 119
[15703.759184] usb 4-2: new high speed USB device using ehci_hcd and address 120
[15703.895177] usb 4-2: configuration #1 chosen from 1 choice
[15708.563749] usb 4-2: USB disconnect, address 120
[15714.954346] usb 4-2: new high speed USB device using ehci_hcd and address 121
[15715.094309] usb 4-2: configuration #1 chosen from 1 choice
[15719.730405] usb 4-2: USB disconnect, address 121
[15726.117015] usb 4-2: new high speed USB device using ehci_hcd and address 122
[15726.256974] usb 4-2: configuration #1 chosen from 1 choice
[15730.969013] usb 4-2: USB disconnect, address 122
[15737.355830] usb 4-2: new high speed USB device using ehci_hcd and address 123
[15737.495870] usb 4-2: configuration #1 chosen from 1 choice
[15742.131805] usb 4-2: USB disconnect, address 123
[15748.518360] usb 4-2: new high speed USB device using ehci_hcd and address 124
[15748.658381] usb 4-2: configuration #1 chosen from 1 choice
[15753.282502] usb 4-2: USB disconnect, address 124
[15759.669273] usb 4-2: new high speed USB device using ehci_hcd and address 125
[15759.805294] usb 4-2: configuration #1 chosen from 1 choice
[15764.501490] usb 4-2: USB disconnect, address 125
[15770.884490] usb 4-2: new high speed USB device using ehci_hcd and address 126
[15771.024467] usb 4-2: configuration #1 chosen from 1 choice
[15775.732697] usb 4-2: USB disconnect, address 126
[15782.115690] usb 4-2: new high speed USB device using ehci_hcd and address 127
[15782.251710] usb 4-2: configuration #1 chosen from 1 choice
[15786.919912] usb 4-2: USB disconnect, address 127
[15793.302894] usb 4-2: new high speed USB device using ehci_hcd and address 2
[15793.438906] usb 4-2: configuration #1 chosen from 1 choice
[15798.067182] usb 4-2: USB disconnect, address 2
[15804.446217] usb 4-2: new high speed USB device using ehci_hcd and address 3
[15804.586162] usb 4-2: configuration #1 chosen from 1 choice
[15809.294430] usb 4-2: USB disconnect, address 3
[15815.673466] usb 4-2: new high speed USB device using ehci_hcd and address 4
[15815.809419] usb 4-2: configuration #1 chosen from 1 choice
[15820.437745] usb 4-2: USB disconnect, address 4
[15826.820781] usb 4-2: new high speed USB device using ehci_hcd and address 5
[15826.960777] usb 4-2: configuration #1 chosen from 1 choice
[15831.593031] usb 4-2: USB disconnect, address 5
[15837.972055] usb 4-2: new high speed USB device using ehci_hcd and address 6
[15838.112003] usb 4-2: configuration #1 chosen from 1 choice
[15842.816244] usb 4-2: USB disconnect, address 6
[15849.191216] usb 4-2: new high speed USB device using ehci_hcd and address 7
[15849.327382] usb 4-2: configuration #1 chosen from 1 choice
[15853.959385] usb 4-2: USB disconnect, address 7
[15860.334326] usb 4-2: new high speed USB device using ehci_hcd and address 8
[15860.474303] usb 4-2: configuration #1 chosen from 1 choice
[15865.150347] usb 4-2: USB disconnect, address 8
[15871.525337] usb 4-2: new high speed USB device using ehci_hcd and address 9
[15871.661297] usb 4-2: configuration #1 chosen from 1 choice
[15876.369521] usb 4-2: USB disconnect, address 9
[15882.744569] usb 4-2: new high speed USB device using ehci_hcd and address 10
[15882.884524] usb 4-2: configuration #1 chosen from 1 choice
[15887.796631] usb 4-2: USB disconnect, address 10
[15894.175638] usb 4-2: new high speed USB device using ehci_hcd and address 11
[15894.315638] usb 4-2: configuration #1 chosen from 1 choice
[15898.947845] usb 4-2: USB disconnect, address 11
[15905.326691] usb 4-2: new high speed USB device using ehci_hcd and address 12
[15905.466676] usb 4-2: configuration #1 chosen from 1 choice
[15910.086880] usb 4-2: USB disconnect, address 12
[15916.461855] usb 4-2: new high speed USB device using ehci_hcd and address 13
[15916.601819] usb 4-2: configuration #1 chosen from 1 choice
[15921.309965] usb 4-2: USB disconnect, address 13
[15927.680924] usb 4-2: new high speed USB device using ehci_hcd and address 14
[15927.817019] usb 4-2: configuration #1 chosen from 1 choice
[15932.449125] usb 4-2: USB disconnect, address 14
[15938.820080] usb 4-2: new high speed USB device using ehci_hcd and address 15
[15938.960065] usb 4-2: configuration #1 chosen from 1 choice
[15943.628288] usb 4-2: USB disconnect, address 15
[15949.999243] usb 4-2: new high speed USB device using ehci_hcd and address 16
[15950.135266] usb 4-2: configuration #1 chosen from 1 choice
[15954.835417] usb 4-2: USB disconnect, address 16
[15961.206372] usb 4-2: new high speed USB device using ehci_hcd and address 17
[15961.346345] usb 4-2: configuration #1 chosen from 1 choice
[15965.978609] usb 4-2: USB disconnect, address 17
[15972.349645] usb 4-2: new high speed USB device using ehci_hcd and address 18
[15972.489685] usb 4-2: configuration #1 chosen from 1 choice
[15977.117897] usb 4-2: USB disconnect, address 18
[15983.484859] usb 4-2: new high speed USB device using ehci_hcd and address 19
[15983.620829] usb 4-2: configuration #1 chosen from 1 choice
[15988.328991] usb 4-2: USB disconnect, address 19
[15994.699939] usb 4-2: new high speed USB device using ehci_hcd and address 20
[15994.839947] usb 4-2: configuration #1 chosen from 1 choice
[15999.468137] usb 4-2: USB disconnect, address 20
[16005.831033] usb 4-2: new high speed USB device using ehci_hcd and address 21
[16005.967055] usb 4-2: configuration #1 chosen from 1 choice
[16010.595268] usb 4-2: USB disconnect, address 21
[16016.962186] usb 4-2: new high speed USB device using ehci_hcd and address 22
[16017.102228] usb 4-2: configuration #1 chosen from 1 choice
[16021.842326] usb 4-2: USB disconnect, address 22
[16028.205259] usb 4-2: new high speed USB device using ehci_hcd and address 23
[16028.345252] usb 4-2: configuration #1 chosen from 1 choice
[16033.053459] usb 4-2: USB disconnect, address 23
[16039.420508] usb 4-2: new high speed USB device using ehci_hcd and address 24
[16039.560427] usb 4-2: configuration #1 chosen from 1 choice
[16044.200760] usb 4-2: USB disconnect, address 24
[16050.567755] usb 4-2: new high speed USB device using ehci_hcd and address 25
[16050.707748] usb 4-2: configuration #1 chosen from 1 choice
[16055.343898] usb 4-2: USB disconnect, address 25
[16061.710709] usb 4-2: new high speed USB device using ehci_hcd and address 26
[16061.858697] usb 4-2: configuration #1 chosen from 1 choice
[16066.566909] usb 4-2: USB disconnect, address 26
[16072.933950] usb 4-2: new high speed USB device using ehci_hcd and address 27
[16073.073966] usb 4-2: configuration #1 chosen from 1 choice
[16077.706235] usb 4-2: USB disconnect, address 27
[16084.065293] usb 4-2: new high speed USB device using ehci_hcd and address 28
[16084.205330] usb 4-2: configuration #1 chosen from 1 choice
[16088.845551] usb 4-2: USB disconnect, address 28
[16095.208598] usb 4-2: new high speed USB device using ehci_hcd and address 29
[16095.356587] usb 4-2: configuration #1 chosen from 1 choice
[16100.368567] usb 4-2: USB disconnect, address 29
[16106.731632] usb 4-2: new high speed USB device using ehci_hcd and address 30
[16106.871636] usb 4-2: configuration #1 chosen from 1 choice
[16111.507906] usb 4-2: USB disconnect, address 30
[16117.862936] usb 4-2: new high speed USB device using ehci_hcd and address 31
[16118.002874] usb 4-2: configuration #1 chosen from 1 choice
[16122.647143] usb 4-2: USB disconnect, address 31
[16129.010079] usb 4-2: new high speed USB device using ehci_hcd and address 32
[16129.150112] usb 4-2: configuration #1 chosen from 1 choice
[16133.862213] usb 4-2: USB disconnect, address 32
[16140.221111] usb 4-2: new high speed USB device using ehci_hcd and address 33
[16140.361067] usb 4-2: configuration #1 chosen from 1 choice
[16144.997343] usb 4-2: USB disconnect, address 33
[16151.352391] usb 4-2: new high speed USB device using ehci_hcd and address 34
[16151.488424] usb 4-2: configuration #1 chosen from 1 choice
[16156.116661] usb 4-2: USB disconnect, address 34
[16162.475707] usb 4-2: new high speed USB device using ehci_hcd and address 35
[16162.615647] usb 4-2: configuration #1 chosen from 1 choice
[16167.311932] usb 4-2: USB disconnect, address 35
[16173.662994] usb 4-2: new high speed USB device using ehci_hcd and address 36
[16173.803050] usb 4-2: configuration #1 chosen from 1 choice
[16178.551181] usb 4-2: USB disconnect, address 36
[16184.902425] usb 4-2: new high speed USB device using ehci_hcd and address 37
[16185.038217] usb 4-2: configuration #1 chosen from 1 choice
[16189.658523] usb 4-2: USB disconnect, address 37
[16196.017582] usb 4-2: new high speed USB device using ehci_hcd and address 38
[16196.157619] usb 4-2: configuration #1 chosen from 1 choice
[16200.793863] usb 4-2: USB disconnect, address 38
[16207.152930] usb 4-2: new high speed USB device using ehci_hcd and address 39
[16207.292935] usb 4-2: configuration #1 chosen from 1 choice
[16212.001128] usb 4-2: USB disconnect, address 39
[16218.356177] usb 4-2: new high speed USB device using ehci_hcd and address 40
[16218.492193] usb 4-2: configuration #1 chosen from 1 choice
[16223.120442] usb 4-2: USB disconnect, address 40
[16229.479373] usb 4-2: new high speed USB device using ehci_hcd and address 41
[16229.619389] usb 4-2: configuration #1 chosen from 1 choice
[16234.255616] usb 4-2: USB disconnect, address 41
[16240.610484] usb 4-2: new high speed USB device using ehci_hcd and address 42
[16240.750471] usb 4-2: configuration #1 chosen from 1 choice
[16245.462642] usb 4-2: USB disconnect, address 42
[16251.821669] usb 4-2: new high speed USB device using ehci_hcd and address 43
[16251.961623] usb 4-2: configuration #1 chosen from 1 choice
[16256.633782] usb 4-2: USB disconnect, address 43
[16262.988731] usb 4-2: new high speed USB device using ehci_hcd and address 44
[16263.128717] usb 4-2: configuration #1 chosen from 1 choice
[16267.764917] usb 4-2: USB disconnect, address 44
[16274.123960] usb 4-2: new high speed USB device using ehci_hcd and address 45
[16274.271993] usb 4-2: configuration #1 chosen from 1 choice
[16278.980174] usb 4-2: USB disconnect, address 45
[16285.331228] usb 4-2: new high speed USB device using ehci_hcd and address 46
[16285.471268] usb 4-2: configuration #1 chosen from 1 choice
[16290.099494] usb 4-2: USB disconnect, address 46
[16296.450559] usb 4-2: new high speed USB device using ehci_hcd and address 47
[16296.590599] usb 4-2: configuration #1 chosen from 1 choice
[16301.222841] usb 4-2: USB disconnect, address 47
[16307.581845] usb 4-2: new high speed USB device using ehci_hcd and address 48
[16307.725854] usb 4-2: configuration #1 chosen from 1 choice
[16312.358114] usb 4-2: USB disconnect, address 48
[16318.709177] usb 4-2: new high speed USB device using ehci_hcd and address 49
[16318.849319] usb 4-2: configuration #1 chosen from 1 choice
[16323.553410] usb 4-2: USB disconnect, address 49
[16329.900479] usb 4-2: new high speed USB device using ehci_hcd and address 50
[16330.040496] usb 4-2: configuration #1 chosen from 1 choice
[16334.716728] usb 4-2: USB disconnect, address 50
[16341.071796] usb 4-2: new high speed USB device using ehci_hcd and address 51
[16341.207812] usb 4-2: configuration #1 chosen from 1 choice
[16345.848056] usb 4-2: USB disconnect, address 51
[16352.195127] usb 4-2: new high speed USB device using ehci_hcd and address 52
[16352.335148] usb 4-2: configuration #1 chosen from 1 choice
[16357.051346] usb 4-2: USB disconnect, address 52
[16363.394425] usb 4-2: new high speed USB device using ehci_hcd and address 53
[16363.534385] usb 4-2: configuration #1 chosen from 1 choice
[16368.174689] usb 4-2: USB disconnect, address 53
[16374.517765] usb 4-2: new high speed USB device using ehci_hcd and address 54
[16374.653702] usb 4-2: configuration #1 chosen from 1 choice
[16379.282038] usb 4-2: USB disconnect, address 54
[16385.633117] usb 4-2: new high speed USB device using ehci_hcd and address 55
[16385.773059] usb 4-2: configuration #1 chosen from 1 choice
[16390.485329] usb 4-2: USB disconnect, address 55
[16396.832405] usb 4-2: new high speed USB device using ehci_hcd and address 56
[16396.972474] usb 4-2: configuration #1 chosen from 1 choice
[16401.604674] usb 4-2: USB disconnect, address 56
[16407.947760] usb 4-2: new high speed USB device using ehci_hcd and address 57
[16408.083789] usb 4-2: configuration #1 chosen from 1 choice
[16412.752012] usb 4-2: USB disconnect, address 57
[16419.099075] usb 4-2: new high speed USB device using ehci_hcd and address 58
[16419.239055] usb 4-2: configuration #1 chosen from 1 choice
[16423.951301] usb 4-2: USB disconnect, address 58
[16430.294370] usb 4-2: new high speed USB device using ehci_hcd and address 59
[16430.434307] usb 4-2: configuration #1 chosen from 1 choice
[16435.130598] usb 4-2: USB disconnect, address 59
[16441.469675] usb 4-2: new high speed USB device using ehci_hcd and address 60
[16441.605609] usb 4-2: configuration #1 chosen from 1 choice
[16446.233949] usb 4-2: USB disconnect, address 60
[16452.577028] usb 4-2: new high speed USB device using ehci_hcd and address 61
[16452.716992] usb 4-2: configuration #1 chosen from 1 choice
[16457.349302] usb 4-2: USB disconnect, address 61
[16463.692382] usb 4-2: new high speed USB device using ehci_hcd and address 62
[16463.832397] usb 4-2: configuration #1 chosen from 1 choice
[16468.536599] usb 4-2: USB disconnect, address 62
[16474.875675] usb 4-2: new high speed USB device using ehci_hcd and address 63
[16475.015614] usb 4-2: configuration #1 chosen from 1 choice
[16479.651958] usb 4-2: USB disconnect, address 63
[16485.991029] usb 4-2: new high speed USB device using ehci_hcd and address 64
[16486.130978] usb 4-2: configuration #1 chosen from 1 choice
[16490.803286] usb 4-2: USB disconnect, address 64
[16497.142348] usb 4-2: new high speed USB device using ehci_hcd and address 65
[16497.282505] usb 4-2: configuration #1 chosen from 1 choice
[16501.978577] usb 4-2: USB disconnect, address 65
[16508.309664] usb 4-2: new high speed USB device using ehci_hcd and address 66
[16508.449624] usb 4-2: configuration #1 chosen from 1 choice
[16513.077942] usb 4-2: USB disconnect, address 66
[16519.421014] usb 4-2: new high speed USB device using ehci_hcd and address 67
[16519.564946] usb 4-2: configuration #1 chosen from 1 choice
[16524.197290] usb 4-2: USB disconnect, address 67
[16530.528367] usb 4-2: new high speed USB device using ehci_hcd and address 68
[16530.668453] usb 4-2: configuration #1 chosen from 1 choice
[16535.372588] usb 4-2: USB disconnect, address 68
[16541.703679] usb 4-2: new high speed USB device using ehci_hcd and address 69
[16541.843612] usb 4-2: configuration #1 chosen from 1 choice
[16546.479951] usb 4-2: USB disconnect, address 69
[16552.819037] usb 4-2: new high speed USB device using ehci_hcd and address 70
[16552.959043] usb 4-2: configuration #1 chosen from 1 choice
[16557.587311] usb 4-2: USB disconnect, address 70
[16563.918390] usb 4-2: new high speed USB device using ehci_hcd and address 71
[16564.058347] usb 4-2: configuration #1 chosen from 1 choice
[16568.734643] usb 4-2: USB disconnect, address 71
[16575.065715] usb 4-2: new high speed USB device using ehci_hcd and address 72
[16575.205743] usb 4-2: configuration #1 chosen from 1 choice
[16579.909940] usb 4-2: USB disconnect, address 72
[16586.237032] usb 4-2: new high speed USB device using ehci_hcd and address 73
[16586.373046] usb 4-2: configuration #1 chosen from 1 choice
[16591.013307] usb 4-2: USB disconnect, address 73
[16597.348381] usb 4-2: new high speed USB device using ehci_hcd and address 74
[16597.488407] usb 4-2: configuration #1 chosen from 1 choice
[16602.120664] usb 4-2: USB disconnect, address 74
[16608.451748] usb 4-2: new high speed USB device using ehci_hcd and address 75
[16608.591807] usb 4-2: configuration #1 chosen from 1 choice
[16613.296083] usb 4-2: USB disconnect, address 75
[16619.623067] usb 4-2: new high speed USB device using ehci_hcd and address 76
[16619.759147] usb 4-2: configuration #1 chosen from 1 choice
[16624.391336] usb 4-2: USB disconnect, address 76
[16630.722413] usb 4-2: new high speed USB device using ehci_hcd and address 77
[16630.862448] usb 4-2: configuration #1 chosen from 1 choice
[16635.482697] usb 4-2: USB disconnect, address 77
[16641.813789] usb 4-2: new high speed USB device using ehci_hcd and address 78
[16641.953814] usb 4-2: configuration #1 chosen from 1 choice
[16646.697981] usb 4-2: USB disconnect, address 78
[16653.025063] usb 4-2: new high speed USB device using ehci_hcd and address 79
[16653.161056] usb 4-2: configuration #1 chosen from 1 choice
[16657.789348] usb 4-2: USB disconnect, address 79
[16664.116499] usb 4-2: new high speed USB device using ehci_hcd and address 80
[16664.256385] usb 4-2: configuration #1 chosen from 1 choice
[16668.888709] usb 4-2: USB disconnect, address 80
[16675.215793] usb 4-2: new high speed USB device using ehci_hcd and address 81
[16675.355771] usb 4-2: configuration #1 chosen from 1 choice
[16680.060013] usb 4-2: USB disconnect, address 81
[16686.383106] usb 4-2: new high speed USB device using ehci_hcd and address 82
[16686.519127] usb 4-2: configuration #1 chosen from 1 choice
[16691.151370] usb 4-2: USB disconnect, address 82
[16697.474475] usb 4-2: new high speed USB device using ehci_hcd and address 83
[16697.614411] usb 4-2: configuration #1 chosen from 1 choice
[16702.234766] usb 4-2: USB disconnect, address 83
[16708.561841] usb 4-2: new high speed USB device using ehci_hcd and address 84
[16708.701967] usb 4-2: configuration #1 chosen from 1 choice
[16713.334125] usb 4-2: USB disconnect, address 84
[16719.657220] usb 4-2: new high speed USB device using ehci_hcd and address 85
[16719.797267] usb 4-2: configuration #1 chosen from 1 choice
[16724.541402] usb 4-2: USB disconnect, address 85
[16730.864498] usb 4-2: new high speed USB device using ehci_hcd and address 86
[16731.004435] usb 4-2: configuration #1 chosen from 1 choice
[16735.624785] usb 4-2: USB disconnect, address 86
[16741.947872] usb 4-2: new high speed USB device using ehci_hcd and address 87
[16742.087962] usb 4-2: configuration #1 chosen from 1 choice
[16746.712157] usb 4-2: USB disconnect, address 87
[16753.031243] usb 4-2: new high speed USB device using ehci_hcd and address 88
[16753.171188] usb 4-2: configuration #1 chosen from 1 choice
[16757.875454] usb 4-2: USB disconnect, address 88
[16764.194551] usb 4-2: new high speed USB device using ehci_hcd and address 89
[16764.338483] usb 4-2: configuration #1 chosen from 1 choice
[16768.958834] usb 4-2: USB disconnect, address 89
[16775.277924] usb 4-2: new high speed USB device using ehci_hcd and address 90
[16775.417943] usb 4-2: configuration #1 chosen from 1 choice
[16780.054197] usb 4-2: USB disconnect, address 90
[16786.365306] usb 4-2: new high speed USB device using ehci_hcd and address 91
[16786.505341] usb 4-2: configuration #1 chosen from 1 choice
[16791.213521] usb 4-2: USB disconnect, address 91
[16797.536607] usb 4-2: new high speed USB device using ehci_hcd and address 92
[16797.684570] usb 4-2: configuration #1 chosen from 1 choice
[16802.352848] usb 4-2: USB disconnect, address 92
[16808.667942] usb 4-2: new high speed USB device using ehci_hcd and address 93
[16808.803950] usb 4-2: configuration #1 chosen from 1 choice
[16813.436223] usb 4-2: USB disconnect, address 93
[16819.747337] usb 4-2: new high speed USB device using ehci_hcd and address 94
[16819.887353] usb 4-2: configuration #1 chosen from 1 choice
[16824.603537] usb 4-2: USB disconnect, address 94
[16830.914634] usb 4-2: new high speed USB device using ehci_hcd and address 95
[16831.050651] usb 4-2: configuration #1 chosen from 1 choice
[16835.758694] usb 4-2: USB disconnect, address 95
[16842.077401] usb 4-2: new high speed USB device using ehci_hcd and address 96
[16842.217353] usb 4-2: configuration #1 chosen from 1 choice
[16846.853590] usb 4-2: USB disconnect, address 96
[16853.168613] usb 4-2: new high speed USB device using ehci_hcd and address 97
[16853.308592] usb 4-2: configuration #1 chosen from 1 choice
[16857.940855] usb 4-2: USB disconnect, address 97
[16864.255937] usb 4-2: new high speed USB device using ehci_hcd and address 98
[16864.395901] usb 4-2: configuration #1 chosen from 1 choice
[16869.108161] usb 4-2: USB disconnect, address 98
[16875.419221] usb 4-2: new high speed USB device using ehci_hcd and address 99
[16875.559172] usb 4-2: configuration #1 chosen from 1 choice
[16880.227410] usb 4-2: USB disconnect, address 99
[16886.538380] usb 4-2: new high speed USB device using ehci_hcd and address 100
[16886.678463] usb 4-2: configuration #1 chosen from 1 choice
[16891.326554] usb 4-2: USB disconnect, address 100
[16897.637529] usb 4-2: new high speed USB device using ehci_hcd and address 101
[16897.777507] usb 4-2: configuration #1 chosen from 1 choice
[16902.481734] usb 4-2: USB disconnect, address 101
[16908.796713] usb 4-2: new high speed USB device using ehci_hcd and address 102
[16908.936668] usb 4-2: configuration #1 chosen from 1 choice
[16913.568760] usb 4-2: USB disconnect, address 102
[16919.883822] usb 4-2: new high speed USB device using ehci_hcd and address 103
[16920.023817] usb 4-2: configuration #1 chosen from 1 choice
[16924.648069] usb 4-2: USB disconnect, address 103
[16930.963127] usb 4-2: new high speed USB device using ehci_hcd and address 104
[16931.099227] usb 4-2: configuration #1 chosen from 1 choice
[16935.807297] usb 4-2: USB disconnect, address 104
[16942.118343] usb 4-2: new high speed USB device using ehci_hcd and address 105
[16942.258274] usb 4-2: configuration #1 chosen from 1 choice
[16946.894528] usb 4-2: USB disconnect, address 105
[16953.197381] usb 4-2: new high speed USB device using ehci_hcd and address 106
[16953.333578] usb 4-2: configuration #1 chosen from 1 choice
[16958.009316] usb 4-2: USB disconnect, address 106
[16964.316379] usb 4-2: new high speed USB device using ehci_hcd and address 107
[16964.456339] usb 4-2: configuration #1 chosen from 1 choice
[16969.088654] usb 4-2: USB disconnect, address 107
[16975.395757] usb 4-2: new high speed USB device using ehci_hcd and address 108
[16975.531683] usb 4-2: configuration #1 chosen from 1 choice
[16980.239960] usb 4-2: USB disconnect, address 108
[16986.551075] usb 4-2: new high speed USB device using ehci_hcd and address 109
[16986.691105] usb 4-2: configuration #1 chosen from 1 choice
[16991.323346] usb 4-2: USB disconnect, address 109
[16997.630369] usb 4-2: new high speed USB device using ehci_hcd and address 110
[16997.770346] usb 4-2: configuration #1 chosen from 1 choice
[17002.390591] usb 4-2: USB disconnect, address 110
[17008.693670] usb 4-2: new high speed USB device using ehci_hcd and address 111
[17008.829673] usb 4-2: configuration #1 chosen from 1 choice
[17013.537878] usb 4-2: USB disconnect, address 111
[17019.844976] usb 4-2: new high speed USB device using ehci_hcd and address 112
[17019.984984] usb 4-2: configuration #1 chosen from 1 choice
[17024.617252] usb 4-2: USB disconnect, address 112
[17030.920291] usb 4-2: new high speed USB device using ehci_hcd and address 113
[17031.060264] usb 4-2: configuration #1 chosen from 1 choice
[17035.720531] usb 4-2: USB disconnect, address 113
[17042.019636] usb 4-2: new high speed USB device using ehci_hcd and address 114
[17042.155672] usb 4-2: configuration #1 chosen from 1 choice
[17046.855857] usb 4-2: USB disconnect, address 114
[17053.158953] usb 4-2: new high speed USB device using ehci_hcd and address 115
[17053.298924] usb 4-2: configuration #1 chosen from 1 choice
[17057.943211] usb 4-2: USB disconnect, address 115
[17064.246315] usb 4-2: new high speed USB device using ehci_hcd and address 116
[17064.386324] usb 4-2: configuration #1 chosen from 1 choice
[17069.022576] usb 4-2: USB disconnect, address 116
[17075.321712] usb 4-2: new high speed USB device using ehci_hcd and address 117
[17075.457693] usb 4-2: configuration #1 chosen from 1 choice
[17080.165882] usb 4-2: USB disconnect, address 117
[17086.472979] usb 4-2: new high speed USB device using ehci_hcd and address 118
[17086.612977] usb 4-2: configuration #1 chosen from 1 choice
[17091.313189] usb 4-2: USB disconnect, address 118
[17097.616311] usb 4-2: new high speed USB device using ehci_hcd and address 119
[17097.756295] usb 4-2: configuration #1 chosen from 1 choice
[17102.392570] usb 4-2: USB disconnect, address 119
[17108.691681] usb 4-2: new high speed USB device using ehci_hcd and address 120
[17108.827713] usb 4-2: configuration #1 chosen from 1 choice
[17113.495889] usb 4-2: USB disconnect, address 120
[17119.794911] usb 4-2: new high speed USB device using ehci_hcd and address 121
[17119.935009] usb 4-2: configuration #1 chosen from 1 choice
[17124.646955] usb 4-2: USB disconnect, address 121
[17130.941995] usb 4-2: new high speed USB device using ehci_hcd and address 122
[17131.081942] usb 4-2: configuration #1 chosen from 1 choice
[17135.706259] usb 4-2: USB disconnect, address 122
[17142.001262] usb 4-2: new high speed USB device using ehci_hcd and address 123
[17142.141278] usb 4-2: configuration #1 chosen from 1 choice
[17146.777519] usb 4-2: USB disconnect, address 123
[17153.076598] usb 4-2: new high speed USB device using ehci_hcd and address 124
[17153.216617] usb 4-2: configuration #1 chosen from 1 choice
[17158.192562] usb 4-2: USB disconnect, address 124
[17164.483639] usb 4-2: new high speed USB device using ehci_hcd and address 125
[17164.619575] usb 4-2: configuration #1 chosen from 1 choice
[17169.251905] usb 4-2: USB disconnect, address 125
[17175.546962] usb 4-2: new high speed USB device using ehci_hcd and address 126
[17175.687013] usb 4-2: configuration #1 chosen from 1 choice
[17180.319205] usb 4-2: USB disconnect, address 126
[17186.614319] usb 4-2: new high speed USB device using ehci_hcd and address 127
[17186.754291] usb 4-2: configuration #1 chosen from 1 choice
[17191.506486] usb 4-2: USB disconnect, address 127
[17197.797598] usb 4-2: new high speed USB device using ehci_hcd and address 2
[17197.933626] usb 4-2: configuration #1 chosen from 1 choice
[17202.565866] usb 4-2: USB disconnect, address 2
[17208.856905] usb 4-2: new high speed USB device using ehci_hcd and address 3
[17208.996817] usb 4-2: configuration #1 chosen from 1 choice
[17213.633094] usb 4-2: USB disconnect, address 3
[17219.920185] usb 4-2: new high speed USB device using ehci_hcd and address 4
[17220.060198] usb 4-2: configuration #1 chosen from 1 choice
[17224.760398] usb 4-2: USB disconnect, address 4
[17231.055500] usb 4-2: new high speed USB device using ehci_hcd and address 5
[17231.203446] usb 4-2: configuration #1 chosen from 1 choice
[17235.911685] usb 4-2: USB disconnect, address 5
[17242.202630] usb 4-2: new high speed USB device using ehci_hcd and address 6
[17242.342576] usb 4-2: configuration #1 chosen from 1 choice
[17246.978799] usb 4-2: USB disconnect, address 6
[17253.265776] usb 4-2: new high speed USB device using ehci_hcd and address 7
[17253.401807] usb 4-2: configuration #1 chosen from 1 choice
[17258.029922] usb 4-2: USB disconnect, address 7
[17264.320648] usb 4-2: new high speed USB device using ehci_hcd and address 8
[17264.460669] usb 4-2: configuration #1 chosen from 1 choice
[17269.192548] usb 4-2: USB disconnect, address 8
[17275.483457] usb 4-2: new high speed USB device using ehci_hcd and address 9
[17275.623458] usb 4-2: configuration #1 chosen from 1 choice
[17280.259705] usb 4-2: USB disconnect, address 9
[17286.542765] usb 4-2: new high speed USB device using ehci_hcd and address 10
[17286.682808] usb 4-2: configuration #1 chosen from 1 choice
[17291.326990] usb 4-2: USB disconnect, address 10
[17297.618060] usb 4-2: new high speed USB device using ehci_hcd and address 11
[17297.762047] usb 4-2: configuration #1 chosen from 1 choice
[17302.470134] usb 4-2: USB disconnect, address 11
[17308.757209] usb 4-2: new high speed USB device using ehci_hcd and address 12
[17308.897245] usb 4-2: configuration #1 chosen from 1 choice
[17313.521475] usb 4-2: USB disconnect, address 12
[17319.804593] usb 4-2: new high speed USB device using ehci_hcd and address 13
[17319.940533] usb 4-2: configuration #1 chosen from 1 choice
[17324.572820] usb 4-2: USB disconnect, address 13
[17330.859878] usb 4-2: new high speed USB device using ehci_hcd and address 14
[17330.999858] usb 4-2: configuration #1 chosen from 1 choice
[17335.704004] usb 4-2: USB disconnect, address 14
[17341.986920] usb 4-2: new high speed USB device using ehci_hcd and address 15
[17342.123080] usb 4-2: configuration #1 chosen from 1 choice
[17346.791003] usb 4-2: USB disconnect, address 15
[17353.073877] usb 4-2: new high speed USB device using ehci_hcd and address 16
[17353.213899] usb 4-2: configuration #1 chosen from 1 choice
[17357.842034] usb 4-2: USB disconnect, address 16
[17364.121140] usb 4-2: new high speed USB device using ehci_hcd and address 17
[17364.257120] usb 4-2: configuration #1 chosen from 1 choice
[17368.885398] usb 4-2: USB disconnect, address 17

```
There might be more, but I couldn't copy it before it disappeared.

---

### Post by khabarkhan on 2007-06-30
Hello guys. I am new user of Linux and have same problem in Ubuntu 7.04 and [Ubuntustudio ]("http://ubuntustudio.org")7.04 too  with my mp3 player (Samsung yp-t9j).

I think it's a problem of OS ,not software.Because when I plugged my mp3 player in Ubuntu it didn't charge correctly ,that means something is wrong with USB port in OS .( I think Ubuntu could not recognize usb port WHEN mp3 player was plugged to usb port.)

I haven't this problem with [FaunOS]("http://www.faunos.com") Linux. When I used Faunos Linux and  plugged that mp3 player to usb port ,  Faunos Linux recognize it and shown in storage device as  "Digital camera" !! and MP3 player started to charge generally and  I could copy and paste and delete music from/to mp3 player/computer.

Thanks for your help Ubuntu gigs. (;

---

