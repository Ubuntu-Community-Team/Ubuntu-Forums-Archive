---
title: "error trying to use any jump drive or fat32 or ntfs partitio"
date: 2009-06-02
forum: General Help
---

### Post by gabak on 2009-06-02
hi to all
here it is the picture
i hope somebody knows how to fix this

---

### Post by dcstar on 2009-06-03
> **gabak said:**
> hi to all
here it is the picture
i hope somebody knows how to fix this

Open a terminal and do this command when you after you plug in the drive and post the results:

```
dmesg
```

---

### Post by gabak on 2009-06-03
i did what u have told me that it show all this problem.
that's it



[829249.551077] wlan0: associated
[829267.548039] wlan0: No ProbeResp from current AP 00:0e:2e:4a:5c:77 - assume out of range
[829269.156832] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[829269.157038] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[829269.356440] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[829269.556064] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[829269.756040] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[829332.652616] wlan0: authenticate with AP 00:0f:66:db:59:c5
[829332.852042] wlan0: authenticate with AP 00:0f:66:db:59:c5
[829333.052047] wlan0: authenticate with AP 00:0f:66:db:59:c5
[829333.252049] wlan0: authentication with AP 00:0f:66:db:59:c5 timed out
[829344.176586] wlan0: direct probe to AP 00:0f:66:db:59:c5 try 1
[829344.184173] wlan0: direct probe to AP 00:0f:66:db:59:c5 try 1
[829344.384041] wlan0: direct probe to AP 00:0f:66:db:59:c5 try 2
[829344.584038] wlan0: direct probe to AP 00:0f:66:db:59:c5 try 3
[829344.784038] wlan0: direct probe to AP 00:0f:66:db:59:c5 timed out
[829357.248378] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[829357.450129] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[829357.648024] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[829357.848035] wlan0: authentication with AP 00:1f:c6:6d:68:26 timed out
[829364.683831] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[829364.880045] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[829365.080035] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[829365.280040] wlan0: authentication with AP 00:1f:c6:6d:68:26 timed out
[829368.356271] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829368.379878] wlan0: authenticated
[829368.379885] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829368.427972] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[829368.427977] wlan0: associated
[829385.566462] wlan0: disassociating by local choice (reason=3)
[829388.624307] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829388.824040] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829389.024236] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829389.224039] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[829398.600989] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829398.603241] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829398.691369] wlan0: authenticated
[829398.691378] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829398.888044] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829398.996050] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[829398.996055] wlan0: associated
[829402.825757] wlan0: disassociated
[829403.825358] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829404.024038] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829404.224334] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829404.424034] wlan0: association with AP 00:0e:2e:4a:5c:77 timed out
[829406.152899] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829406.153115] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829406.352027] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829406.552039] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829406.752053] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[829417.661278] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829417.661591] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829417.861127] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829418.060026] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829418.260039] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[829429.168527] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829429.168731] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829429.270509] wlan0: authenticated
[829429.270516] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829429.468032] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829429.668039] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829429.868028] wlan0: association with AP 00:0e:2e:4a:5c:77 timed out
[829440.685282] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829440.692198] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829440.697840] wlan0: authenticated
[829440.697843] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829440.712505] wlan0: RX ReassocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[829440.712509] wlan0: associated
[829500.838560] wlan0 direct probe responded
[829500.838567] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829500.841549] wlan0: authenticated
[829500.841552] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829500.856755] wlan0: RX ReassocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[829500.856758] wlan0: associated
[829503.785303] wlan0: disassociated
[829504.784037] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829504.785954] wlan0: deauthenticated
[829505.784032] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[829505.786426] wlan0 direct probe responded
[829505.786430] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[829505.788479] wlan0: authenticated
[829505.788482] wlan0: associate with AP 00:0e:2e:4a:5c:77
[829505.796948] wlan0: RX ReassocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[829505.796952] wlan0: associated
[830105.048123] [drm:i915_getparam] *ERROR* Unknown parameter 6
[830105.189396] [drm:i915_getparam] *ERROR* Unknown parameter 6
[830705.094648] [drm:i915_getparam] *ERROR* Unknown parameter 6
[831305.103808] [drm:i915_getparam] *ERROR* Unknown parameter 6
[831905.097801] [drm:i915_getparam] *ERROR* Unknown parameter 6
[905446.054447] CPU0 attaching NULL sched-domain.
[905446.071124] CPU0 attaching NULL sched-domain.
[905451.264071] wlan0: No ProbeResp from current AP 00:0e:2e:4a:5c:77 - assume out of range
[905452.909589] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[905452.916200] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[905453.116055] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[905453.316046] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[905453.518492] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[905524.693879] CPU0 attaching NULL sched-domain.
[905524.715474] CPU0 attaching NULL sched-domain.
[906187.900597] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906188.100041] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906188.300036] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906188.500032] wlan0: authentication with AP 00:1f:c6:6d:68:26 timed out
[906199.412841] wlan0: direct probe to AP 00:1f:c6:6d:68:26 try 1
[906199.420154] wlan0: direct probe to AP 00:1f:c6:6d:68:26 try 1
[906199.620038] wlan0: direct probe to AP 00:1f:c6:6d:68:26 try 2
[906199.820035] wlan0: direct probe to AP 00:1f:c6:6d:68:26 try 3
[906200.020033] wlan0: direct probe to AP 00:1f:c6:6d:68:26 timed out
[906210.932190] wlan0: direct probe to AP 00:1f:c6:6d:68:26 try 1
[906210.940186] wlan0: direct probe to AP 00:1f:c6:6d:68:26 try 1
[906210.950025] wlan0 direct probe responded
[906210.950031] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906211.148039] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906211.348042] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906211.548032] wlan0: authentication with AP 00:1f:c6:6d:68:26 timed out
[906222.436555] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906222.468071] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906222.668052] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906222.868054] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906223.068358] wlan0: authentication with AP 00:1f:c6:6d:68:26 timed out
[906233.948586] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906233.948790] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906234.148036] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906234.348036] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906234.548037] wlan0: authentication with AP 00:1f:c6:6d:68:26 timed out
[906245.468832] wlan0: direct probe to AP 00:1f:c6:6d:68:26 try 1
[906245.476145] wlan0: direct probe to AP 00:1f:c6:6d:68:26 try 1
[906245.493080] wlan0 direct probe responded
[906245.493085] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906245.692038] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906245.892035] wlan0: authenticate with AP 00:1f:c6:6d:68:26
[906246.092031] wlan0: authentication with AP 00:1f:c6:6d:68:26 timed out
[906249.357097] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906249.556115] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 2
[906249.756038] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 3
[906249.956039] wlan0: direct probe to AP 00:02:6f:3e:84:68 timed out
[906259.388622] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906259.397379] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906259.596031] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 2
[906259.796035] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 3
[906259.996040] wlan0: direct probe to AP 00:02:6f:3e:84:68 timed out
[906270.896947] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906270.904177] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906271.104039] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 2
[906271.304040] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 3
[906271.504031] wlan0: direct probe to AP 00:02:6f:3e:84:68 timed out
[906282.408600] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906282.416183] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906282.616793] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 2
[906282.816035] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 3
[906283.016032] wlan0: direct probe to AP 00:02:6f:3e:84:68 timed out
[906293.916595] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906293.924171] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906294.124040] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 2
[906294.324043] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 3
[906294.524033] wlan0: direct probe to AP 00:02:6f:3e:84:68 timed out
[906305.428595] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906305.436171] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906305.636032] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 2
[906305.836028] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 3
[906306.036035] wlan0: direct probe to AP 00:02:6f:3e:84:68 timed out
[906306.326522] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 1
[906306.524034] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 2
[906306.724034] wlan0: direct probe to AP 00:02:6f:3e:84:68 try 3
[906306.924035] wlan0: direct probe to AP 00:02:6f:3e:84:68 timed out
[908284.907268] [drm:i915_getparam] *ERROR* Unknown parameter 6
[911504.353057] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[911504.355643] wlan0 direct probe responded
[911504.355648] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[911504.357385] wlan0: authenticated
[911504.357388] wlan0: associate with AP 00:0e:2e:4a:5c:77
[911504.380064] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[911504.380068] wlan0: associated
[913501.893977] [drm:i915_getparam] *ERROR* Unknown parameter 6
[913503.014823] [drm:i915_getparam] *ERROR* Unknown parameter 6
[914102.097161] [drm:i915_getparam] *ERROR* Unknown parameter 6
[914702.094496] [drm:i915_getparam] *ERROR* Unknown parameter 6
[915302.096480] [drm:i915_getparam] *ERROR* Unknown parameter 6
[920451.545793] [drm:i915_getparam] *ERROR* Unknown parameter 6
[920451.856708] [drm:i915_getparam] *ERROR* Unknown parameter 6
[921535.196314] [drm:i915_getparam] *ERROR* Unknown parameter 6
[921535.722677] [drm:i915_getparam] *ERROR* Unknown parameter 6
[922135.449465] [drm:i915_getparam] *ERROR* Unknown parameter 6
[925015.367167] [drm:i915_getparam] *ERROR* Unknown parameter 6
[925015.689165] [drm:i915_getparam] *ERROR* Unknown parameter 6
[925825.417084] [drm:i915_getparam] *ERROR* Unknown parameter 6
[925825.827027] [drm:i915_getparam] *ERROR* Unknown parameter 6
[928986.290339] [drm:i915_getparam] *ERROR* Unknown parameter 6
[928986.815977] [drm:i915_getparam] *ERROR* Unknown parameter 6
[929586.416082] [drm:i915_getparam] *ERROR* Unknown parameter 6
[930186.417290] [drm:i915_getparam] *ERROR* Unknown parameter 6
[930786.418885] [drm:i915_getparam] *ERROR* Unknown parameter 6
[960391.236198] wlan0: No ProbeResp from current AP 00:0e:2e:4a:5c:77 - assume out of range
[960392.844520] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[960392.844725] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[960393.044799] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[960393.244036] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[960393.444024] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[960404.352609] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[960404.360161] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[960404.560026] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[960404.760036] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[960404.960035] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[960406.135018] wlan0 direct probe responded
[960406.135025] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[960406.234399] wlan0: authenticated
[960406.234406] wlan0: associate with AP 00:0e:2e:4a:5c:77
[960406.344163] wlan0: RX ReassocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[960406.344167] wlan0: associated
[960406.525220] wlan0: disassociating by local choice (reason=3)
[960409.580296] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[960409.581838] wlan0: authenticated
[960409.581842] wlan0: associate with AP 00:0e:2e:4a:5c:77
[960409.589656] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[960409.589660] wlan0: associated
[975254.896294] wlan0: No ProbeResp from current AP 00:0e:2e:4a:5c:77 - assume out of range
[975256.504810] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[975256.505014] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[975256.704035] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[975256.904042] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[975257.104031] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[975257.537581] wlan0 direct probe responded
[975257.537588] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[975257.736037] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[975257.936130] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[975258.136047] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[975268.016783] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[975268.016988] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[975268.073746] wlan0 direct probe responded
[975268.073753] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[975268.272025] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[975268.413536] wlan0: authenticated
[975268.413542] wlan0: associate with AP 00:0e:2e:4a:5c:77
[975268.612036] wlan0: associate with AP 00:0e:2e:4a:5c:77
[975268.812028] wlan0: associate with AP 00:0e:2e:4a:5c:77
[975269.012035] wlan0: association with AP 00:0e:2e:4a:5c:77 timed out
[975273.612322] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[975273.812136] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[975274.009976] wlan0: authenticated
[975274.009983] wlan0: associate with AP 00:0e:2e:4a:5c:77
[975274.208852] wlan0: associate with AP 00:0e:2e:4a:5c:77
[975274.409577] wlan0: associate with AP 00:0e:2e:4a:5c:77
[975274.609226] wlan0: association with AP 00:0e:2e:4a:5c:77 timed out
[975283.616626] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[975283.616830] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[975283.818228] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[975284.016030] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[975284.216037] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[975295.136165] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[975295.144949] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[975295.147424] wlan0 direct probe responded
[975295.147427] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[975295.149443] wlan0: authenticated
[975295.149447] wlan0: associate with AP 00:0e:2e:4a:5c:77
[975295.166354] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[975295.166357] wlan0: associated
[986926.405375] [drm:i915_getparam] *ERROR* Unknown parameter 6
[986927.374526] [drm:i915_getparam] *ERROR* Unknown parameter 6
[987526.469376] [drm:i915_getparam] *ERROR* Unknown parameter 6
[988126.487996] [drm:i915_getparam] *ERROR* Unknown parameter 6
[988726.505505] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1010794.148042] usb 1-8: new high speed USB device using ehci_hcd and address 4
[1010794.288839] usb 1-8: configuration #1 chosen from 1 choice
[1010794.316118] scsi4 : SCSI emulation for USB Mass Storage devices
[1010794.317307] usb-storage: device found at 4
[1010794.317321] usb-storage: waiting for device to settle before scanning
[1010799.325770] usb-storage: device scan complete
[1010799.327576] scsi 4:0:0:0: Direct-Access     Sony     Sony DSC         6.00 PQ: 0 ANSI: 0 CCS
[1010799.336195] sd 4:0:0:0: [sdb] 7954432 512-byte hardware sectors: (4.07 GB/3.79 GiB)
[1010799.366097] sd 4:0:0:0: [sdb] Write Protect is off
[1010799.366102] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[1010799.366105] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[1010799.388071] sd 4:0:0:0: [sdb] 7954432 512-byte hardware sectors: (4.07 GB/3.79 GiB)
[1010799.389314] sd 4:0:0:0: [sdb] Write Protect is off
[1010799.389317] sd 4:0:0:0: [sdb] Mode Sense: 00 00 00 00
[1010799.389320] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[1010799.389326]  sdb: sdb1
[1010799.392779] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[1010799.392862] sd 4:0:0:0: Attached scsi generic sg2 type 0
[1010941.818750] usb 1-8: USB disconnect, address 4
[1013102.413123] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1013102.718270] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1013702.513600] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1014302.510577] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1014902.536091] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1049346.643991] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1049346.957562] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1049946.757136] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1050546.742168] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1051146.775321] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1060401.252044] wlan0: No ProbeResp from current AP 00:0e:2e:4a:5c:77 - assume out of range
[1060402.866825] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1060402.867030] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1060403.064044] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[1060403.265304] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[1060403.464025] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[1060403.471099] wlan0 direct probe responded
[1060403.471106] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1060403.536894] wlan0: authenticated
[1060403.536901] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1060403.569259] wlan0: RX ReassocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[1060403.569264] wlan0: associated
[1061961.307054] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1061962.322689] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1062561.483227] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1063161.390177] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1063761.431901] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1065314.335936] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1067792.049084] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1067792.273389] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1068392.110026] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1068992.130202] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1069592.160784] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1073862.849754] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1073863.553788] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1074462.915661] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1075062.904090] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1082440.049282] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1082441.021963] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1083040.092030] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1087782.596696] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1087782.953920] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1088382.692997] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1091504.980046] wlan0: No ProbeResp from current AP 00:0e:2e:4a:5c:77 - assume out of range
[1091506.588587] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091506.588793] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091506.788048] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091506.988036] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091507.188044] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[1091518.104592] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091518.112182] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091518.265148] wlan0: authenticated
[1091518.265155] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1091518.464031] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1091518.664034] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1091518.864046] wlan0: association with AP 00:0e:2e:4a:5c:77 timed out
[1091523.648299] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091523.848043] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091524.048034] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091524.248034] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[1091533.652585] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1091533.660178] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1091533.696848] wlan0 direct probe responded
[1091533.696855] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1091533.702987] wlan0: authenticated
[1091533.702991] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1091533.900034] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1091534.045015] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[1091534.045020] wlan0: associated
[1094203.007546] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1094204.151485] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1098032.867721] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
[1098043.097641] type=1503 audit(1243825778.778:10): operation="syscall" name="mount" pid=12773 profile="/usr/share/gdm/guest-session/Xsession"
[1098043.217184] type=1503 audit(1243825778.898:11): operation="capable" name="dac_override" pid=12777 profile="/usr/share/gdm/guest-session/Xsession"
[1098043.217191] type=1503 audit(1243825778.898:12): operation="capable" name="dac_read_search" pid=12777 profile="/usr/share/gdm/guest-session/Xsession"
[1098043.218305] type=1503 audit(1243825778.898:13): operation="capable" name="dac_override" pid=12780 profile="/usr/share/gdm/guest-session/Xsession"
[1098043.218312] type=1503 audit(1243825778.898:14): operation="capable" name="dac_read_search" pid=12780 profile="/usr/share/gdm/guest-session/Xsession"
[1098053.102060] CPU0 attaching NULL sched-domain.
[1098053.116083] CPU0 attaching NULL sched-domain.
[1098079.152368] mtrr: no MTRR for c0000000,10000000 found
[1098082.439637] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1098232.421405] scim-bridge[9579]: segfault at c ip b7e7674c sp bfd205f8 error 4 in libscim-1.0.so.8.2.3[b7e1c000+c6000]
[1100895.534316] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1100896.736353] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1101495.590265] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1102095.589950] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1102695.602679] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1130816.162333] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1130816.850429] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1131416.230397] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1132016.212897] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1132616.230272] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1135591.917223] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1135593.049964] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1136191.969011] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1136791.968093] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1137391.969342] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1142638.852172] wlan0: No ProbeResp from current AP 00:0e:2e:4a:5c:77 - assume out of range
[1142640.472300] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1142640.488194] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1142640.688170] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[1142640.888024] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[1142641.088170] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[1142696.568297] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1142696.569788] wlan0: authenticated
[1142696.569792] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1142696.588371] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[1142696.588375] wlan0: associated
[1142708.588177] wlan0: No ProbeResp from current AP 00:0e:2e:4a:5c:77 - assume out of range
[1142710.197794] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1142710.198001] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1142710.201075] wlan0 direct probe responded
[1142710.201079] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1142710.203988] wlan0: authenticated
[1142710.203991] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1142710.220120] wlan0: RX ReassocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=13 aid=1)
[1142710.220124] wlan0: AP denied association (code=13)
[1142710.404174] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1142710.406158] wlan0: deauthenticated
[1142711.404178] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[1142711.406725] wlan0 direct probe responded
[1142711.406729] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1142711.408628] wlan0: authenticated
[1142711.408632] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1142711.423184] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=13 aid=1)
[1142711.423188] wlan0: AP denied association (code=13)
[1142711.608023] wlan0: association with AP 00:0e:2e:4a:5c:77 timed out
[1182382.892701] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1182382.894177] wlan0: authenticated
[1182382.894181] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1182382.913355] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[1182382.913360] wlan0: associated
[1183482.480882] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1183483.466890] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1184082.538571] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1186529.575993] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1186529.936855] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1187129.644676] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1187729.650378] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1188329.644577] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1222061.943032] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1222063.282852] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1222662.066841] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1222851.348371] wlan0: No ProbeResp from current AP 00:0e:2e:4a:5c:77 - assume out of range
[1222852.965296] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1222852.965533] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1222853.164087] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[1222853.364050] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[1222853.564054] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[1222853.831362] wlan0 direct probe responded
[1222853.831374] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222854.031790] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222854.228047] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222854.428624] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[1222864.488772] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1222864.489000] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1222864.688049] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[1222864.888470] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[1222865.089922] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[1222869.930172] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222870.128051] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222870.328053] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222870.528053] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[1222879.893016] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222879.893242] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222880.092052] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222880.292055] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222880.492053] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[1222891.429451] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222891.429685] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222891.628043] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222891.828046] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222892.028048] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[1222902.949160] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1222902.949388] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1222903.148509] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[1222903.348051] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[1222903.548045] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[1222920.997051] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1222920.997280] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 1
[1222921.196209] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 2
[1222921.396055] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 try 3
[1222921.596215] wlan0: direct probe to AP 00:0e:2e:4a:5c:77 timed out
[1222921.864678] wlan0 direct probe responded
[1222921.864691] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222922.064052] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222922.264061] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1222922.469663] wlan0: authentication with AP 00:0e:2e:4a:5c:77 timed out
[1223262.074534] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1223862.068222] [drm:i915_getparam] *ERROR* Unknown parameter 6
[1302833.444798] wlan0: authenticate with AP 00:0e:2e:4a:5c:77
[1302833.451469] wlan0: authenticated
[1302833.451479] wlan0: associate with AP 00:0e:2e:4a:5c:77
[1302833.469454] wlan0: RX AssocResp from 00:0e:2e:4a:5c:77 (capab=0x411 status=0 aid=1)
[1302833.469461] wlan0: associated

---

