---
title: "Annoying Resolution Problem on Jaunty"
date: 2009-05-20
forum: General Help
---

### Post by b@sh_n3rd on 2009-05-20
Hi..I've got Jaunty on my PC with an Intel i845 and have configured my xorg.conf using [*this*]("http://ubuntuforums.org/showthread.php?t=1130582") thread. My video works marvellously on Jaunty however and I'm currently using the Linux 2.6.30rc6 Kernel (Bleeding Edge Method). Here's my problem, I've configured my display for, 1280x1024 (5:4) at 60Hz. Xorg detects my monitor as, SAMSUNG 16" and the options available aren't exactly the same as I used to have on XP...Anyways, when I boot my PC, *sometimes*, my desktop resolution is less than what I've selected but the "Display Preferences" dialog box shows it as "1280x1024 (5:4)". Here's my xorg.conf file;```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        BusId           "PCI:0:2"
        Option          "AccelMethod"                   "uxa"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "false"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```How can I set Xorg to stay permanently at the given resolution? And as I recall, on XP I could set the refresh rate up to 85Hz at this resolution, but on Ubuntu, only 60Hz is available...My monitor is a, "Samsung Magic SyncMaster CDP17S1(G)". Thanks for any help...

---

### Post by CatKiller on 2009-05-20
You could put the correct HorizSync and VertRefresh ranges in the "Monitor" Section. You should be able to get these values from the manual for your monitor.

---

### Post by Legace on 2009-05-20
Try to add the following into the Screen section.
*```

	SubSection "Display"
		Modes      "1280x1024"
	EndSubSection
```

---

### Post by b@sh_n3rd on 2009-05-21
I tried editing my xorg.conf as shown above, today when I booted my PC..X wouldn't load, so I removed that once again...

CatKiller, thanks, I'll check on that...I have to find the manual first :D

---

### Post by tempesta72 on 2009-06-02
hy, i'm looking for your xorg.conf file and perhaps I found an error. In section 'Device', you specify a BusID "PCI:0:2" that is not correctly. The BusID should be like this: BusID    "PCI:1:5:0"; I think you've lost a number. Please, confirm your BusID typing this command:
'lspci -d 102b:* [Enter]'
 
you will obtain a string like '0000:01:00.0 VGA...' : in this case the correct BusID is PCI:1:0:0.
 
bye, I hope this is usefull for you.

---

### Post by b@sh_n3rd on 2009-06-03
> **tempesta72 said:**
> hy, i'm looking for your xorg.conf file and perhaps I found an error. In section 'Device', you specify a BusID "PCI:0:2" that is not correctly. The BusID should be like this: BusID    "PCI:1:5:0"; I think you've lost a number. Please, confirm your BusID typing this command:
'lspci -d 102b:* [Enter]'
 
you will obtain a string like '0000:01:00.0 VGA...' : in this case the correct BusID is PCI:1:0:0.
 
bye, I hope this is usefull for you.

yeah, that's how I found my BusID in the first place. However, the command you gave me lists my 2nd video adapter...(I've got two which is why I've added the BusID option :D)...
```
# lspci | grep VGA
``` This code, on the other hand provides the following, ```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
01:02.0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique] (rev 03)

```
I wasn't sure how to put that BusID in xorg.conf. When trying, what exists is what works...Please look at the above output and let me know on the correct way of setting the BusID. (My pc works well without it too, but I put it coz of my second adapter)

PS: My resolution trouble hasn't recurred for some time now, ever since I tried the newer kernels...

---

### Post by tempesta72 on 2009-06-03
According to your post, BusID on xorg.conf must be:
1st controller: BusID    "PCI:0:2:0"
2nd controller: BusID   "PCI:1:2:0"

But so I note you've 2 graphic cards on your PC, I'm right?? In this case you will have two 'Device' section on you xorg.conf.

---

### Post by Yellow Pasque on 2009-06-03
60Hz CRT? Ugh, my eyes! :P
Generate the mode you want:
```
cvt -v 1280 1024 85
```
Copy and paste the resulting modeline into the Monitor section. Also, specify the VertRefresh and Horizsync as suggested.

Also, you can play around with the xrandr command-line utility.

---

