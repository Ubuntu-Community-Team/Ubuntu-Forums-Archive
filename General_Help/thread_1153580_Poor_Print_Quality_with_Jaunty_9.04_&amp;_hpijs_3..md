---
title: "Poor Print Quality with Jaunty 9.04 &amp; hpijs 3.9.2"
date: 2009-05-08
forum: General Help
---

### Post by aotf01 on 2009-05-08
I have a HP Photosmart 7660 printer, a PC with Ubuntu 8.10, and a PC with Ubuntu 9.04 (upgraded from 8.10).

When I print from my 8.10 computer with the setting 1200 dpi Photo the printer prints at 1200 dpi Photo; however, when printing from the upgraded 9.04 PC with hpijs 3.9.2 it only prints at 300 dpi.

I have tried the Foomatic/hpijs 2.8.7 driver with the same results. I ran the Printer Configuration -> Help -> Troubleshoot program and found the following difference in the info being sent to the printer.

8.10
```

'D [08/May/2009:18:27:47 -0500] [Job 74] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dPDFSETTINGS=/printer -r1200 -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 - -',

'D [08/May/2009:18:27:49 -0500] [Job 74] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDuplex=false -r1200 -sIjsParams=Quality:Quality=3,Quality:ColorMode=2,Quality:MediaType=2,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-s2ZQC1',

```

9.04
```

'D [07/May/2009:19:37:24 -0500] [Job 136] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dDoNumCopies -dPDFSETTINGS=/printer -r1200 -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 - -',

'D [07/May/2009:19:37:27 -0500] [Job 136] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=ijs -sIjsServer=hpijs -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sDeviceManufacturer="HEWLETT-PACKARD" -sDeviceModel="deskjet 5600" -dDuplex=false -r300 -sIjsParams=Quality:Quality=0,Quality:ColorMode=2,Quality:MediaType=0,Quality:PenSet=2,PS:MediaPosition=7 -dIjsUseOutputFD -sOutputFile=-   /var/spool/cups/tmp/foomatic-e9tqZo',

```


When sent to ps2pdf13 they both are at 1200 dpi (-r1200) but on 9.04 gs is telling it to be 300 dpi (-r300 Quality=0 MediaType=0). Can someone point me to some info on how to tell the printer to print at the correct resolution?

Thanks

---

### Post by todak on 2009-05-08
There are a couple of ways. The first will force the printer to print at the requested resolution all the time. First, go to **System> Administration> Printing**. Select your printer and right-click and choose **Properties**. On the left side of the window that appears, choose **Printer Options**. Scroll down to **Printout Mode** and click the box under that header. You will be presented with a list of options concerning resolution. Choose one then click the **Apply** button and then **OK**. The selected resolution will be permanent for all of your print jobs, unless you temporarily change the default for a particular print job as needed in the following: Choose **Print...** in the **File** menu of the app you wish to print from. In the window that appears, choose your printer in the **General** tab. Next, select the **Advanced** tab. Under the heading **Printout Mode** there is a spinner to select your print resolution for this particular print job (or subsequent jobs using the same app, if you have not closed the app). That is the method to use for default override. I prefer to leave the printer settings at their default so that I am not hosing down the paper with ink that I do not need to waste just to print a text document. If I need to print hi-res, then I use the override method for that particular hi-res job. Hope this helps!

---

### Post by aotf01 on 2009-05-13
I had already tried adjusting the **Printout Mode** settings many times without any success. I was able to get it partially working by installing the Foomatic/hpijs 2.8.7 driver and rebooting. I then reinstalled the hpijs 3.9.2 driver and rebooted and now the **Printout Mode** settings seem to be working correctly in OpenOffice but still only print in low resolution from the pdf Document Viewer 2.26.1. (The pdf viewer also prints 180 degrees rotated compared to OpenOffice)

---

