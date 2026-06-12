---
title: "Problem with disk, often unmounting"
date: 2008-12-07
forum: General Help
---

### Post by rado3105 on 2008-12-07
Hi I have USB disk connected to my server and it used to unmount it automatically, it writes some errors, using dmesg.
Restarting server solve the problem. 
> 
[   42.040606] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[   42.043255] sd 0:0:0:0: [sda] Write Protect is off
[   42.043261] sd 0:0:0:0: [sda] Mode Sense: 00 38 00 00
[   42.043266] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   42.053500] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors (1000205 MB)
[   42.058839] sd 0:0:0:0: [sda] Write Protect is off
[   42.058850] sd 0:0:0:0: [sda] Mode Sense: 00 38 00 00
[   42.058855] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   42.058930]  sda: sda1
[   42.205607] sd 0:0:0:0: [sda] Attached SCSI disk
[   42.358502] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   42.630436] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   42.630602] PCI: Setting latency timer of device 0000:00:07.5 to 64
[   43.958511] loop: module loaded
[   44.029810] lp0: using parport0 (interrupt-driven).
[   44.523054] Adding 240932k swap on /dev/hda5.  Priority:-1 extents:1 across:240932k
[   45.037245] EXT3 FS on hda1, internal journal
[   49.838956] eth0: no IPv6 routers present
[  164.917031] kjournald starting.  Commit interval 5 seconds
[  164.935957] EXT3 FS on sda1, internal journal
[  164.935974] EXT3-fs: mounted filesystem with ordered data mode.
[99055.108330] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[99065.368982] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[99101.606015] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[99101.735897] usb 1-1: device descriptor read/64, error -71
[99101.975676] usb 1-1: device descriptor read/64, error -71
[99102.205471] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[99102.335346] usb 1-1: device descriptor read/64, error -71
[99102.575128] usb 1-1: device descriptor read/64, error -71
[99102.804919] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[99103.224544] usb 1-1: device not accepting address 2, error -71
[99103.344436] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[99103.764044] usb 1-1: device not accepting address 2, error -71
[99103.764129] usb 1-1: USB disconnect, address 2
[99103.764565] sd 0:0:0:0: scsi: Device offlined - not ready after error recovery
[99103.773320] sd 0:0:0:0: [sda] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[99103.773347] end_request: I/O error, dev sda, sector 1402994767
[99103.773400] sd 0:0:0:0: [sda] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
[99103.773407] end_request: I/O error, dev sda, sector 40095
[99103.773534] Buffer I/O error on device sda1, logical block 5006
[99103.773566] lost page write due to I/O error on sda1
[99103.773575] Aborting journal on device sda1.
[99103.773612] journal commit I/O error
[99103.773666] Buffer I/O error on device sda1, logical block 1027
[99103.773689] lost page write due to I/O error on sda1
[99103.798773] EXT3-fs error (device sda1): ext3_get_inode_loc: unable to read inode block - inode=87687169, block=175374338
[99103.798834] Remounting filesystem read-only
[99103.801179] scsi 0:0:0:0: rejecting I/O to dead device
[99103.801211] Buffer I/O error on device sda1, logical block 0
[99103.801233] lost page write due to I/O error on sda1
[99103.801382] scsi 0:0:0:0: rejecting I/O to dead device
[99103.801410] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.801469] scsi 0:0:0:0: rejecting I/O to dead device
[99103.801494] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.801548] scsi 0:0:0:0: rejecting I/O to dead device
[99103.801573] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.801630] scsi 0:0:0:0: rejecting I/O to dead device
[99103.801654] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.801708] scsi 0:0:0:0: rejecting I/O to dead device
[99103.801733] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.801786] scsi 0:0:0:0: rejecting I/O to dead device
[99103.801810] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.801862] scsi 0:0:0:0: rejecting I/O to dead device
[99103.801886] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.801940] scsi 0:0:0:0: rejecting I/O to dead device
[99103.801964] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802016] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802041] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802096] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802121] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802173] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802198] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802249] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802273] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802325] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802349] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802404] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802429] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802482] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802506] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802558] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802583] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802635] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802659] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802712] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802736] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802790] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802815] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802870] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802894] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.802947] scsi 0:0:0:0: rejecting I/O to dead device
[99103.802971] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803024] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803048] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803100] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803124] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803177] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803201] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803254] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803279] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803331] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803355] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803409] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803433] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803485] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803510] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803562] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803586] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803638] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803662] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803717] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803741] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803793] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803818] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803870] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803894] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.803946] scsi 0:0:0:0: rejecting I/O to dead device
[99103.803970] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.819471] scsi 0:0:0:0: rejecting I/O to dead device
[99103.819505] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.819563] scsi 0:0:0:0: rejecting I/O to dead device
[99103.819589] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.819642] scsi 0:0:0:0: rejecting I/O to dead device
[99103.819667] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.819719] scsi 0:0:0:0: rejecting I/O to dead device
[99103.819744] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.819798] scsi 0:0:0:0: rejecting I/O to dead device
[99103.819822] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.819876] scsi 0:0:0:0: rejecting I/O to dead device
[99103.819900] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.820635] scsi 0:0:0:0: rejecting I/O to dead device
[99103.820659] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.820712] scsi 0:0:0:0: rejecting I/O to dead device
[99103.820736] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.820790] scsi 0:0:0:0: rejecting I/O to dead device
[99103.820814] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.820866] scsi 0:0:0:0: rejecting I/O to dead device
[99103.820891] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.820944] scsi 0:0:0:0: rejecting I/O to dead device
[99103.820968] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.831631] scsi 0:0:0:0: rejecting I/O to dead device
[99103.831908] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[99103.832044] scsi 0:0:0:0: rejecting I/O to dead device
[99103.838563] scsi 0:0:0:0: rejecting I/O to dead device
[99103.914014] usb 1-1: new full speed USB device using uhci_hcd and address 3
[99104.043796] usb 1-1: device descriptor read/64, error -71
[99104.283577] usb 1-1: device descriptor read/64, error -71
[99104.513362] usb 1-1: new full speed USB device using uhci_hcd and address 4
[99104.643247] usb 1-1: device descriptor read/64, error -71
[99104.883028] usb 1-1: device descriptor read/64, error -71
[99105.112841] usb 1-1: new full speed USB device using uhci_hcd and address 5
[99105.532439] usb 1-1: device not accepting address 5, error -71
[99105.652333] usb 1-1: new full speed USB device using uhci_hcd and address 6
[99106.071942] usb 1-1: device not accepting address 6, error -71
[103409.060161] scsi 0:0:0:0: rejecting I/O to dead device
[103409.060224] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[103409.060806] scsi 0:0:0:0: rejecting I/O to dead device
[103409.084738] scsi 0:0:0:0: rejecting I/O to dead device
[105310.473112] scsi 0:0:0:0: rejecting I/O to dead device
[105310.473174] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[120791.318028] scsi 0:0:0:0: rejecting I/O to dead device
[120791.318686] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[127711.033130] scsi 0:0:0:0: rejecting I/O to dead device
[127711.033395] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[127711.033903] scsi 0:0:0:0: rejecting I/O to dead device
[127711.035180] scsi 0:0:0:0: rejecting I/O to dead device
[127711.081364] scsi 0:0:0:0: rejecting I/O to dead device
[127711.082048] scsi 0:0:0:0: rejecting I/O to dead device
[127711.083287] scsi 0:0:0:0: rejecting I/O to dead device
[127711.083813] scsi 0:0:0:0: rejecting I/O to dead device
[127711.084976] scsi 0:0:0:0: rejecting I/O to dead device
[127711.086492] scsi 0:0:0:0: rejecting I/O to dead device
[127711.087035] scsi 0:0:0:0: rejecting I/O to dead device
[127711.088287] scsi 0:0:0:0: rejecting I/O to dead device
[127711.088908] scsi 0:0:0:0: rejecting I/O to dead device
[127711.090084] scsi 0:0:0:0: rejecting I/O to dead device
[127712.514671] scsi 0:0:0:0: rejecting I/O to dead device
[127923.973001] scsi 0:0:0:0: rejecting I/O to dead device
[127923.973264] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[127923.973936] scsi 0:0:0:0: rejecting I/O to dead device
[127924.365442] scsi 0:0:0:0: rejecting I/O to dead device
[127924.461718] scsi 0:0:0:0: rejecting I/O to dead device
[127924.461778] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[127924.461898] scsi 0:0:0:0: rejecting I/O to dead device
[128471.776475] scsi 0:0:0:0: rejecting I/O to dead device
[128471.839895] scsi 0:0:0:0: rejecting I/O to dead device
[128471.872017] scsi 0:0:0:0: rejecting I/O to dead device
[135033.707131] scsi 0:0:0:0: rejecting I/O to dead device
[135033.716298] scsi 0:0:0:0: rejecting I/O to dead device
[135033.720078] scsi 0:0:0:0: rejecting I/O to dead device
[135048.871824] scsi 0:0:0:0: rejecting I/O to dead device
[135048.878514] scsi 0:0:0:0: rejecting I/O to dead device
[135048.883671] scsi 0:0:0:0: rejecting I/O to dead device
[135821.821564] scsi 0:0:0:0: rejecting I/O to dead device
[135822.073054] scsi 0:0:0:0: rejecting I/O to dead device
[136656.524584] scsi 0:0:0:0: rejecting I/O to dead device
[136658.220490] scsi 0:0:0:0: rejecting I/O to dead device
[136678.019501] scsi 0:0:0:0: rejecting I/O to dead device
[136678.145675] scsi 0:0:0:0: rejecting I/O to dead device
[139522.898764] scsi 0:0:0:0: rejecting I/O to dead device
[139524.402798] scsi 0:0:0:0: rejecting I/O to dead device
[139543.273461] scsi 0:0:0:0: rejecting I/O to dead device
[139543.412335] scsi 0:0:0:0: rejecting I/O to dead device
[139564.754536] scsi 0:0:0:0: rejecting I/O to dead device
[139564.890788] scsi 0:0:0:0: rejecting I/O to dead device
[140668.554006] scsi 0:0:0:0: rejecting I/O to dead device
[140668.592787] scsi 0:0:0:0: rejecting I/O to dead device
[140888.269761] scsi 0:0:0:0: rejecting I/O to dead device
[140888.270481] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[140888.271309] scsi 0:0:0:0: rejecting I/O to dead device
[140888.274645] scsi 0:0:0:0: rejecting I/O to dead device
[140888.282823] scsi 0:0:0:0: rejecting I/O to dead device
[140888.284656] scsi 0:0:0:0: rejecting I/O to dead device
[141686.276975] scsi 0:0:0:0: rejecting I/O to dead device
[141686.396059] scsi 0:0:0:0: rejecting I/O to dead device
[141693.078812] scsi 0:0:0:0: rejecting I/O to dead device
[141693.172373] scsi 0:0:0:0: rejecting I/O to dead device
[141703.125070] scsi 0:0:0:0: rejecting I/O to dead device
[141703.252185] scsi 0:0:0:0: rejecting I/O to dead device
[141887.097881] scsi 0:0:0:0: rejecting I/O to dead device
[141887.313147] scsi 0:0:0:0: rejecting I/O to dead device
[141900.254874] scsi 0:0:0:0: rejecting I/O to dead device
[141900.381720] scsi 0:0:0:0: rejecting I/O to dead device
[142041.826244] scsi 0:0:0:0: rejecting I/O to dead device
[142041.833279] scsi 0:0:0:0: rejecting I/O to dead device
[142041.837505] scsi 0:0:0:0: rejecting I/O to dead device
[142184.956136] scsi 0:0:0:0: rejecting I/O to dead device
[142185.129565] scsi 0:0:0:0: rejecting I/O to dead device
[142185.155907] scsi 0:0:0:0: rejecting I/O to dead device
[144200.710568] scsi 0:0:0:0: rejecting I/O to dead device
[144200.747131] scsi 0:0:0:0: rejecting I/O to dead device
[144200.770289] scsi 0:0:0:0: rejecting I/O to dead device
[144490.657431] scsi 0:0:0:0: rejecting I/O to dead device
[144490.664020] scsi 0:0:0:0: rejecting I/O to dead device
[144490.673624] scsi 0:0:0:0: rejecting I/O to dead device
[145086.948861] scsi 0:0:0:0: rejecting I/O to dead device
[145086.948924] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[145086.951732] scsi 0:0:0:0: rejecting I/O to dead device
[145086.951791] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[145121.257247] scsi 0:0:0:0: rejecting I/O to dead device
[145121.263984] scsi 0:0:0:0: rejecting I/O to dead device
[145121.327936] scsi 0:0:0:0: rejecting I/O to dead device
[147099.368564] scsi 0:0:0:0: rejecting I/O to dead device
[147099.394078] scsi 0:0:0:0: rejecting I/O to dead device
[148931.415644] scsi 0:0:0:0: rejecting I/O to dead device
[148931.440160] scsi 0:0:0:0: rejecting I/O to dead device
[152131.345139] scsi 0:0:0:0: rejecting I/O to dead device
[152131.576122] scsi 0:0:0:0: rejecting I/O to dead device
[152131.872767] scsi 0:0:0:0: rejecting I/O to dead device
[152132.430691] scsi 0:0:0:0: rejecting I/O to dead device
[152934.904414] scsi 0:0:0:0: rejecting I/O to dead device
[152934.930532] scsi 0:0:0:0: rejecting I/O to dead device
[152935.544615] scsi 0:0:0:0: rejecting I/O to dead device
[154310.201099] scsi 0:0:0:0: rejecting I/O to dead device
[154310.291721] scsi 0:0:0:0: rejecting I/O to dead device
[154310.341466] scsi 0:0:0:0: rejecting I/O to dead device
[154311.639902] scsi 0:0:0:0: rejecting I/O to dead device
[155688.428264] scsi 0:0:0:0: rejecting I/O to dead device
[155688.428545] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.766974] scsi 0:0:0:0: rejecting I/O to dead device
[155842.767037] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.769602] scsi 0:0:0:0: rejecting I/O to dead device
[155842.769661] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.773610] scsi 0:0:0:0: rejecting I/O to dead device
[155842.773669] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.776153] scsi 0:0:0:0: rejecting I/O to dead device
[155842.776212] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.778306] scsi 0:0:0:0: rejecting I/O to dead device
[155842.778366] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.780445] scsi 0:0:0:0: rejecting I/O to dead device
[155842.780503] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.782599] scsi 0:0:0:0: rejecting I/O to dead device
[155842.782658] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.784745] scsi 0:0:0:0: rejecting I/O to dead device
[155842.784803] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.786980] scsi 0:0:0:0: rejecting I/O to dead device
[155842.787040] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.789356] scsi 0:0:0:0: rejecting I/O to dead device
[155842.789415] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.791777] scsi 0:0:0:0: rejecting I/O to dead device
[155842.791837] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155842.794114] scsi 0:0:0:0: rejecting I/O to dead device
[155842.794172] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155843.852673] scsi 0:0:0:0: rejecting I/O to dead device
[155843.852734] EXT3-fs error (device sda1): ext3_find_entry: reading directory #2 offset 0
[155843.958990] scsi 0:0:0:0: rejecting I/O to dead device

Can you tell me how to solve it?

---

### Post by lovelyvik293 on 2008-12-07
Please have a look at 
[http://ubuntuforums.org/archive/index.php/t-797789.html](http://ubuntuforums.org/archive/index.php/t-797789.html)
It might help.

---

