---
title: "Ubuntu desktop problem"
date: 2007-01-29
forum: Desktop Environments
---

### Post by Tiesto on 2007-01-29
Hello, i installed ubuntu 6.10 (i think thats the version) and i have a problem with my desktop which i actually think is a nvidia problem. The problem is that the desktop is not centered as it should be but more towards the right and out of the screen. I had this problem with Suse linux too actually. Can anyone help? Thnx!

And another one, the system cannot see my external usb hard disk. Any clues?

Thnx again everyone!

---

### Post by scrooge_74 on 2007-01-29
Can you adjust your monitor?

If you have an Nvidia card this site could help you  [http://albertomilone.com/latestrepo.html](http://albertomilone.com/latestrepo.html)


About your external disk, did you try booting with it already attach? Any changes when attaching it latter?

you can do a dmesg command from a terminal window after you plug it in and see if the last lines it says anything about it.

---

### Post by Tiesto on 2007-01-31
Sorry it took me so long to reply mate!

Yes i can adjust my monitor but i wonder if there is a way to permanently fix the problem. Do you think i should update the Nvidia drivers? Generally, what would you do in my position?

About the disk, i ve tried everything you write above and there are no changes at all. I did the command and the last lines say the usb ports are fine (or something like that). However, some lines above that it says that some other usb ports have a problem. I really doubt it is a port problem because the disk works fine in Windows.

If you want me to tell you exactly what those lines say, tell me.

Any clues generally?

---

### Post by scrooge_74 on 2007-01-31
You should try to use the correct drivers so you can use your video card to the full, if you dont have the 3D enable your PC could hang just by trying a 3D screensaver

I think you need to post the results of the dmesg to see what it says about the usb ports

---

### Post by Tiesto on 2007-01-31
ok, right now i started ubuntu, the screen looks fine! Anyway, do you know where can i find the Nvidia FX5200 drivers apart form the nvidia website (the categories are too vague there).

Here are the results of the command:

{[17179606.308000] NET: Registered protocol family 31
[17179606.308000] Bluetooth: HCI device and connection manager initialized
[17179606.308000] Bluetooth: HCI socket layer initialized
[17179606.344000] Bluetooth: L2CAP ver 2.8
[17179606.344000] Bluetooth: L2CAP socket layer initialized
[17179606.364000] Bluetooth: RFCOMM socket layer initialized
[17179606.364000] Bluetooth: RFCOMM TTY layer initialized
[17179606.364000] Bluetooth: RFCOMM ver 1.7
[17179607.700000] usb 4-5: new high speed USB device using ehci_hcd and address 71
[17179608.204000] usb 4-5: new high speed USB device using ehci_hcd and address 72
[17179608.708000] usb 4-5: new high speed USB device using ehci_hcd and address 73
[17179610.220000] usb 4-5: new high speed USB device using ehci_hcd and address 78
[17179611.732000] usb 4-5: new high speed USB device using ehci_hcd and address 80
[17179612.236000] usb 4-5: new high speed USB device using ehci_hcd and address 81
[17179612.992000] usb 4-5: new high speed USB device using ehci_hcd and address 83
[17179613.496000] usb 4-5: new high speed USB device using ehci_hcd and address 84
[17179614.000000] usb 4-5: new high speed USB device using ehci_hcd and address 85
[17179614.756000] usb 4-5: new high speed USB device using ehci_hcd and address 86
[17179615.260000] usb 4-5: new high speed USB device using ehci_hcd and address 87
[17179615.764000] usb 4-5: new high speed USB device using ehci_hcd and address 88
[17179616.520000] usb 4-5: new high speed USB device using ehci_hcd and address 90
[17179617.528000] usb 4-5: new high speed USB device using ehci_hcd and address 91
[17179618.032000] usb 4-5: new high speed USB device using ehci_hcd and address 92
[17179618.788000] usb 4-5: new high speed USB device using ehci_hcd and address 93
[17179619.292000] usb 4-5: new high speed USB device using ehci_hcd and address 94
[17179620.048000] usb 4-5: new high speed USB device using ehci_hcd and address 95
[17179620.552000] usb 4-5: new high speed USB device using ehci_hcd and address 96
[17179622.568000] usb 4-5: new high speed USB device using ehci_hcd and address 103
[17179623.576000] usb 4-5: new high speed USB device using ehci_hcd and address 104
[17179624.584000] usb 4-5: new high speed USB device using ehci_hcd and address 105
[17179626.096000] usb 4-5: new high speed USB device using ehci_hcd and address 110
[17179626.852000] usb 4-5: new high speed USB device using ehci_hcd and address 112
[17179627.860000] usb 4-5: new high speed USB device using ehci_hcd and address 115
[17179628.364000] usb 4-5: new high speed USB device using ehci_hcd and address 116
[17179629.372000] usb 4-5: new high speed USB device using ehci_hcd and address 117
[17179629.876000] usb 4-5: new high speed USB device using ehci_hcd and address 118
[17179630.884000] usb 4-5: new high speed USB device using ehci_hcd and address 121
[17179631.640000] usb 4-5: new high speed USB device using ehci_hcd and address 123
[17179632.648000] usb 4-5: new high speed USB device using ehci_hcd and address 124
[17179633.404000] usb 4-5: new high speed USB device using ehci_hcd and address 126
[17179634.160000] usb 4-5: new high speed USB device using ehci_hcd and address 2
[17179634.664000] usb 4-5: new high speed USB device using ehci_hcd and address 3
[17179635.168000] usb 4-5: new high speed USB device using ehci_hcd and address 4
[17179635.672000] usb 4-5: new high speed USB device using ehci_hcd and address 5
[17179637.436000] usb 4-5: new high speed USB device using ehci_hcd and address 10
[17179637.940000] usb 4-5: new high speed USB device using ehci_hcd and address 11
[17179638.696000] usb 4-5: new high speed USB device using ehci_hcd and address 12
[17179639.200000] usb 4-5: new high speed USB device using ehci_hcd and address 13
[17179639.704000] usb 4-5: new high speed USB device using ehci_hcd and address 14
[17179640.208000] usb 4-5: new high speed USB device using ehci_hcd and address 15
[17179641.468000] usb 4-5: new high speed USB device using ehci_hcd and address 19
[17179642.476000] usb 4-5: new high speed USB device using ehci_hcd and address 21
[17179642.980000] usb 4-5: new high speed USB device using ehci_hcd and address 22
[17179643.736000] usb 4-5: new high speed USB device using ehci_hcd and address 23
[17179644.608000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179644.720000] usb 4-5: new high speed USB device using ehci_hcd and address 24
[17179645.592000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179645.704000] usb 4-5: new high speed USB device using ehci_hcd and address 25
[17179646.112000] usb 4-5: device not accepting address 25, error -71
[17179646.508000] usb 4-5: new high speed USB device using ehci_hcd and address 27
[17179647.012000] usb 4-5: new high speed USB device using ehci_hcd and address 28
[17179647.516000] usb 4-5: new high speed USB device using ehci_hcd and address 29
[17179648.388000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179648.776000] usb 4-5: new high speed USB device using ehci_hcd and address 31
[17179650.288000] usb 4-5: new high speed USB device using ehci_hcd and address 33
[17179651.160000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179651.548000] usb 4-5: new high speed USB device using ehci_hcd and address 35
[17179653.060000] usb 4-5: new high speed USB device using ehci_hcd and address 37
[17179653.564000] usb 4-5: new high speed USB device using ehci_hcd and address 38
[17179654.320000] usb 4-5: new high speed USB device using ehci_hcd and address 39
[17179654.824000] usb 4-5: new high speed USB device using ehci_hcd and address 40
[17179655.832000] usb 4-5: new high speed USB device using ehci_hcd and address 43
[17179657.092000] usb 4-5: new high speed USB device using ehci_hcd and address 44
[17179657.596000] usb 4-5: new high speed USB device using ehci_hcd and address 45
[17179658.100000] usb 4-5: new high speed USB device using ehci_hcd and address 46
[17179658.856000] usb 4-5: new high speed USB device using ehci_hcd and address 47
[17179659.612000] usb 4-5: new high speed USB device using ehci_hcd and address 49
[17179660.368000] usb 4-5: new high speed USB device using ehci_hcd and address 51
[17179660.872000] usb 4-5: new high speed USB device using ehci_hcd and address 52
[17179661.744000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179661.856000] usb 4-5: new high speed USB device using ehci_hcd and address 53
[17179662.888000] usb 4-5: new high speed USB device using ehci_hcd and address 56
[17179663.392000] usb 4-5: new high speed USB device using ehci_hcd and address 57
[17179663.896000] usb 4-5: new high speed USB device using ehci_hcd and address 58
[17179664.400000] usb 4-5: new high speed USB device using ehci_hcd and address 59
[17179666.164000] usb 4-5: new high speed USB device using ehci_hcd and address 65
[17179667.172000] usb 4-5: new high speed USB device using ehci_hcd and address 66
[17179668.180000] usb 4-5: new high speed USB device using ehci_hcd and address 67
[17179669.052000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179669.440000] usb 4-5: new high speed USB device using ehci_hcd and address 69
[17179670.196000] usb 4-5: new high speed USB device using ehci_hcd and address 71
[17179670.700000] usb 4-5: new high speed USB device using ehci_hcd and address 72
[17179671.456000] usb 4-5: new high speed USB device using ehci_hcd and address 74
[17179672.464000] usb 4-5: new high speed USB device using ehci_hcd and address 76
[17179673.220000] usb 4-5: new high speed USB device using ehci_hcd and address 78
[17179673.724000] usb 4-5: new high speed USB device using ehci_hcd and address 79
[17179674.228000] usb 4-5: new high speed USB device using ehci_hcd and address 80
[17179675.488000] usb 4-5: new high speed USB device using ehci_hcd and address 84
[17179676.748000] usb 4-5: new high speed USB device using ehci_hcd and address 85
[17179677.504000] usb 4-5: new high speed USB device using ehci_hcd and address 87
[17179678.008000] usb 4-5: new high speed USB device using ehci_hcd and address 88
[17179678.512000] usb 4-5: new high speed USB device using ehci_hcd and address 89
[17179679.268000] usb 4-5: new high speed USB device using ehci_hcd and address 91
[17179680.528000] usb 4-5: new high speed USB device using ehci_hcd and address 92
[17179681.788000] usb 4-5: new high speed USB device using ehci_hcd and address 93
[17179682.796000] usb 4-5: new high speed USB device using ehci_hcd and address 94
[17179683.300000] usb 4-5: new high speed USB device using ehci_hcd and address 95
[17179684.056000] usb 4-5: new high speed USB device using ehci_hcd and address 97
[17179684.928000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179685.040000] usb 4-5: new high speed USB device using ehci_hcd and address 98
[17179686.324000] usb 4-5: new high speed USB device using ehci_hcd and address 99
[17179686.828000] usb 4-5: new high speed USB device using ehci_hcd and address 100
[17179687.584000] usb 4-5: new high speed USB device using ehci_hcd and address 102
[17179688.088000] usb 4-5: new high speed USB device using ehci_hcd and address 103
[17179689.096000] usb 4-5: new high speed USB device using ehci_hcd and address 105
[17179690.104000] usb 4-5: new high speed USB device using ehci_hcd and address 108
[17179690.976000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179691.088000] usb 4-5: new high speed USB device using ehci_hcd and address 109
[17179691.868000] usb 4-5: new high speed USB device using ehci_hcd and address 110
[17179692.372000] usb 4-5: new high speed USB device using ehci_hcd and address 111
[17179692.876000] usb 4-5: new high speed USB device using ehci_hcd and address 112
[17179693.884000] usb 4-5: new high speed USB device using ehci_hcd and address 114
[17179694.892000] usb 4-5: new high speed USB device using ehci_hcd and address 115
[17179695.396000] usb 4-5: new high speed USB device using ehci_hcd and address 116
[17179695.900000] usb 4-5: new high speed USB device using ehci_hcd and address 117
[17179696.404000] usb 4-5: new high speed USB device using ehci_hcd and address 118
[17179697.160000] usb 4-5: new high speed USB device using ehci_hcd and address 119
[17179698.168000] usb 4-5: new high speed USB device using ehci_hcd and address 120
[17179699.428000] usb 4-5: new high speed USB device using ehci_hcd and address 124
[17179700.184000] usb 4-5: new high speed USB device using ehci_hcd and address 126
[17179700.940000] usb 4-5: new high speed USB device using ehci_hcd and address 127
[17179702.704000] usb 4-5: new high speed USB device using ehci_hcd and address 5
[17179703.208000] usb 4-5: new high speed USB device using ehci_hcd and address 6
[17179704.216000] usb 4-5: new high speed USB device using ehci_hcd and address 9
[17179704.972000] usb 4-5: new high speed USB device using ehci_hcd and address 10
[17179705.728000] usb 4-5: new high speed USB device using ehci_hcd and address 12
[17179706.232000] usb 4-5: new high speed USB device using ehci_hcd and address 13
[17179706.736000] usb 4-5: new high speed USB device using ehci_hcd and address 14
[17179707.492000] usb 4-5: new high speed USB device using ehci_hcd and address 15
[17179708.752000] usb 4-5: new high speed USB device using ehci_hcd and address 16
[17179709.508000] usb 4-5: new high speed USB device using ehci_hcd and address 17
[17179710.012000] usb 4-5: new high speed USB device using ehci_hcd and address 18
[17179712.028000] usb 4-5: new high speed USB device using ehci_hcd and address 24
[17179712.532000] usb 4-5: new high speed USB device using ehci_hcd and address 25
[17179713.036000] usb 4-5: new high speed USB device using ehci_hcd and address 26
[17179714.044000] usb 4-5: new high speed USB device using ehci_hcd and address 27
[17179715.556000] usb 4-5: new high speed USB device using ehci_hcd and address 31
[17179716.312000] usb 4-5: new high speed USB device using ehci_hcd and address 33
[17179717.572000] usb 4-5: new high speed USB device using ehci_hcd and address 35
[17179718.580000] usb 4-5: new high speed USB device using ehci_hcd and address 38
[17179719.336000] usb 4-5: new high speed USB device using ehci_hcd and address 40
[17179720.092000] usb 4-5: new high speed USB device using ehci_hcd and address 42
[17179721.100000] usb 4-5: new high speed USB device using ehci_hcd and address 43
[17179721.604000] usb 4-5: new high speed USB device using ehci_hcd and address 44
[17179722.108000] usb 4-5: new high speed USB device using ehci_hcd and address 45
[17179722.612000] usb 4-5: new high speed USB device using ehci_hcd and address 46
[17179724.124000] usb 4-5: new high speed USB device using ehci_hcd and address 49
[17179725.132000] usb 4-5: new high speed USB device using ehci_hcd and address 52
[17179726.644000] usb 4-5: new high speed USB device using ehci_hcd and address 55
[17179727.148000] usb 4-5: new high speed USB device using ehci_hcd and address 56
[17179727.652000] usb 4-5: new high speed USB device using ehci_hcd and address 57
[17179728.156000] usb 4-5: new high speed USB device using ehci_hcd and address 58
[17179728.912000] usb 4-5: new high speed USB device using ehci_hcd and address 60
[17179729.416000] usb 4-5: new high speed USB device using ehci_hcd and address 61
[17179730.676000] usb 4-5: new high speed USB device using ehci_hcd and address 65
[17179731.684000] usb 4-5: new high speed USB device using ehci_hcd and address 66
[17179732.944000] usb 4-5: new high speed USB device using ehci_hcd and address 68
[17179733.952000] usb 4-5: new high speed USB device using ehci_hcd and address 69
[17179734.708000] usb 4-5: new high speed USB device using ehci_hcd and address 71
[17179735.464000] usb 4-5: new high speed USB device using ehci_hcd and address 73
[17179735.968000] usb 4-5: new high speed USB device using ehci_hcd and address 74
[17179736.724000] usb 4-5: new high speed USB device using ehci_hcd and address 75
[17179737.732000] usb 4-5: new high speed USB device using ehci_hcd and address 76
[17179738.740000] usb 4-5: new high speed USB device using ehci_hcd and address 79
[17179739.496000] usb 4-5: new high speed USB device using ehci_hcd and address 81
[17179741.260000] usb 4-5: new high speed USB device using ehci_hcd and address 84
[17179741.764000] usb 4-5: new high speed USB device using ehci_hcd and address 85
[17179742.268000] usb 4-5: new high speed USB device using ehci_hcd and address 86
[17179742.772000] usb 4-5: new high speed USB device using ehci_hcd and address 87
[17179743.528000] usb 4-5: new high speed USB device using ehci_hcd and address 89
[17179744.284000] usb 4-5: new high speed USB device using ehci_hcd and address 91
[17179745.292000] usb 4-5: new high speed USB device using ehci_hcd and address 93
[17179746.048000] usb 4-5: new high speed USB device using ehci_hcd and address 95
[17179746.804000] usb 4-5: new high speed USB device using ehci_hcd and address 97
[17179748.316000] usb 4-5: new high speed USB device using ehci_hcd and address 99
[17179748.820000] usb 4-5: new high speed USB device using ehci_hcd and address 100
[17179749.576000] usb 4-5: new high speed USB device using ehci_hcd and address 102
[17179750.584000] usb 4-5: new high speed USB device using ehci_hcd and address 105
[17179751.456000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179752.096000] usb 4-5: new high speed USB device using ehci_hcd and address 108
[17179752.852000] usb 4-5: new high speed USB device using ehci_hcd and address 110
[17179753.860000] usb 4-5: new high speed USB device using ehci_hcd and address 112
[17179754.868000] usb 4-5: new high speed USB device using ehci_hcd and address 115
[17179755.372000] usb 4-5: new high speed USB device using ehci_hcd and address 116
[17179756.380000] usb 4-5: new high speed USB device using ehci_hcd and address 117
[17179757.136000] usb 4-5: new high speed USB device using ehci_hcd and address 119
[17179758.396000] usb 4-5: new high speed USB device using ehci_hcd and address 120
[17179758.900000] usb 4-5: new high speed USB device using ehci_hcd and address 121
[17179759.656000] usb 4-5: new high speed USB device using ehci_hcd and address 122
[17179760.160000] usb 4-5: new high speed USB device using ehci_hcd and address 123
[17179761.168000] usb 4-5: new high speed USB device using ehci_hcd and address 126
[17179761.924000] usb 4-5: new high speed USB device using ehci_hcd and address 2
[17179762.680000] usb 4-5: new high speed USB device using ehci_hcd and address 4
[17179763.436000] usb 4-5: new high speed USB device using ehci_hcd and address 6
[17179764.948000] usb 4-5: new high speed USB device using ehci_hcd and address 8
[17179765.704000] usb 4-5: new high speed USB device using ehci_hcd and address 9
[17179766.712000] usb 4-5: new high speed USB device using ehci_hcd and address 10
[17179767.216000] usb 4-5: new high speed USB device using ehci_hcd and address 11
[17179767.972000] usb 4-5: new high speed USB device using ehci_hcd and address 12
[17179768.980000] usb 4-5: new high speed USB device using ehci_hcd and address 15
[17179769.484000] usb 4-5: new high speed USB device using ehci_hcd and address 16
[17179770.356000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179770.744000] usb 4-5: new high speed USB device using ehci_hcd and address 18
[17179771.248000] usb 4-5: new high speed USB device using ehci_hcd and address 19
[17179771.752000] usb 4-5: new high speed USB device using ehci_hcd and address 20
[17179772.256000] usb 4-5: new high speed USB device using ehci_hcd and address 21
[17179773.012000] usb 4-5: new high speed USB device using ehci_hcd and address 23
[17179773.884000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179773.996000] usb 4-5: new high speed USB device using ehci_hcd and address 24
[17179775.028000] usb 4-5: new high speed USB device using ehci_hcd and address 25
[17179775.784000] usb 4-5: new high speed USB device using ehci_hcd and address 27
[17179777.296000] usb 4-5: new high speed USB device using ehci_hcd and address 32
[17179778.052000] usb 4-5: new high speed USB device using ehci_hcd and address 34
[17179778.808000] usb 4-5: new high speed USB device using ehci_hcd and address 36
[17179779.816000] usb 4-5: new high speed USB device using ehci_hcd and address 38
[17179780.320000] usb 4-5: new high speed USB device using ehci_hcd and address 39
[17179780.824000] usb 4-5: new high speed USB device using ehci_hcd and address 40
[17179781.832000] usb 4-5: new high speed USB device using ehci_hcd and address 43
[17179783.092000] usb 4-5: new high speed USB device using ehci_hcd and address 44
[17179783.848000] usb 4-5: new high speed USB device using ehci_hcd and address 46
[17179784.720000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179784.832000] usb 4-5: new high speed USB device using ehci_hcd and address 47
[17179785.612000] usb 4-5: new high speed USB device using ehci_hcd and address 49
[17179786.116000] usb 4-5: new high speed USB device using ehci_hcd and address 50
[17179787.376000] usb 4-5: new high speed USB device using ehci_hcd and address 53
[17179787.880000] usb 4-5: new high speed USB device using ehci_hcd and address 54
[17179788.888000] usb 4-5: new high speed USB device using ehci_hcd and address 55
[17179789.760000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179789.872000] usb 4-5: new high speed USB device using ehci_hcd and address 56
[17179790.400000] usb 4-5: new high speed USB device using ehci_hcd and address 57
[17179791.408000] usb 4-5: new high speed USB device using ehci_hcd and address 58
[17179792.164000] usb 4-5: new high speed USB device using ehci_hcd and address 60
[17179792.920000] usb 4-5: new high speed USB device using ehci_hcd and address 62
[17179794.180000] usb 4-5: new high speed USB device using ehci_hcd and address 66
[17179794.936000] usb 4-5: new high speed USB device using ehci_hcd and address 68
[17179795.692000] usb 4-5: new high speed USB device using ehci_hcd and address 70
[17179796.448000] usb 4-5: new high speed USB device using ehci_hcd and address 71
[17179797.456000] usb 4-5: new high speed USB device using ehci_hcd and address 73
[17179797.960000] usb 4-5: new high speed USB device using ehci_hcd and address 74
[17179798.968000] usb 4-5: new high speed USB device using ehci_hcd and address 76
[17179800.228000] usb 4-5: new high speed USB device using ehci_hcd and address 79
[17179801.488000] usb 4-5: new high speed USB device using ehci_hcd and address 80
[17179802.360000] hub 4-0:1.0: Cannot enable port 5.  Maybe the USB cable is bad?
[17179802.472000] usb 4-5: new high speed USB device using ehci_hcd and address 81}

Actually, it seems i was wrong about the last lines!

Any better now?

Thnx mate!

---

### Post by scrooge_74 on 2007-01-31
As far as I know you have to use the drivers from the Nvidia website, it did happen to me that  my system is suppose to have one thing, I downloaded what were suppose to be the drivers to the card I have, but the system told me I had to use a different set of drivers.

I really dont know what is suppose to be wrong with the usb disk, have you try reading the disk after booting from a Live CD?

 It says you may have a bad cable, but if you say it works under windows I doubt that should be an issue.  Try a Live CD it could be something with the system config

---

