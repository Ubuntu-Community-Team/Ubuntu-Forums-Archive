---
title: "Problem with monitor refresh rate"
date: 2005-08-08
forum: Desktop Environments
---

### Post by BArS on 2005-08-08
In KDE it is 1024 on 768 with 85 rate, but then check it with help of monitor menu it shows 60.

How to change refresh rate to 85?

Video card is integrated.

---

### Post by heimo on 2005-08-08
I would try to edit xorg.conf and change lower limit of vertrefresh to over 60.
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by BArS on 2005-08-09
It doesn't help......

---

### Post by heimo on 2005-08-09
Well... Then I'd try changing it to
 ```
VertRefresh 85

``` 
and restart X (hit ctrl+alt+backspace)

Be sure how to edit xorg.conf in console in case something goes wrong.
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by BArS on 2005-08-09
my xorg.conf

```

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     85
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "SyncMaster"
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"

``` 

end so on....

---

### Post by heimo on 2005-08-09
And you still get only 60Hz? Check the post I linked, specifically the location of log file for X and see if you can figure out which "modes" are selected. If you can't make sense of that file, it'd be nice if you can attach it on this forum (please do not try to copy-paste, it's a big file).

---

### Post by BArS on 2005-08-09
Yes I still have 60Hz.....

I check the file you give, but no result.......   :neutral:

---

### Post by Gezzer on 2005-08-09
[QUOTE=BArS]Yes I still have 60Hz.....

I check the file you give, but no result.......   :neutral:[/QUOTE]
 try these settings
HorizSync       30-70
VertRefresh    40-90

---

### Post by Teroedni on 2005-08-09
Basr
What type of monitor do you have?
It may be that your monitor supports much more than 85 hertz on 1024*768.

---

### Post by BArS on 2005-08-10
Monitor: SyncMaster 793s
Video: SiS 651_661FX_741_760_M661FX_M661MX_M741_M760

---

### Post by Teroedni on 2005-08-10
The Samsung SyncMaster 793s is a 17-inch CRT monitor offering 0.23mm horizontal dot pitch, 30-70 kHz horizontal frequency, 50-160 Hz vertical frequency and a maximum 1280 x 1024 resolution.

So it looks very good
You have a good monitor and should be able too use 1280*1024 at75hz;)

I have to go to work but i will help you later today when im finnish at work

Have a nice day;)

---

### Post by heimo on 2005-08-10
[QUOTE=BArS]Monitor: SyncMaster 793s
[/QUOTE]

User manual (just for reference) 3.6MB pdf:
[http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=US&CttFileID=167129&CDCttType=UM&ModelType=C&ModelName=LE17LS7LK&VPath=UM%2f200402%2f20040227071901437_BH59-00362A-00Eng.pdf]("http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=US&CttFileID=167129&CDCttType=UM&ModelType=C&ModelName=LE17LS7LK&VPath=UM%2f200402%2f20040227071901437_BH59-00362A-00Eng.pdf")
 ```

HorizSync		   30-70
VertRefresh		   50-160
```

---

### Post by BArS on 2005-08-10
My xorg.conf

```

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync        30-70
        VertRefresh      50-160
        DisplaySize      312   234
        Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807
-HSync +Vsync
EndSection

```

---

### Post by heimo on 2005-08-10
It looks good. Could you attach xorgs log file?

---

### Post by BArS on 2005-08-10
Video Card: SiS651

---

### Post by BArS on 2005-08-10
Huraaaaaaaaaaaaaaaaaaaaaaa!!!!!!!!!!!!!    \\:D/  \\:D/ 

After logn time of  ](*,)  I can relax!!!!!!

First of all, the first link for users who has problems [http://www.x.org/X11R6.8.2/doc/](http://www.x.org/X11R6.8.2/doc/) 

And exactly, for users with video cards like my "SiS"

[http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml) 

The recept, I do:
```

**Debian Sarge (stable), Debian Sid (unstable), Ubuntu:**
Add the following to your **/etc/apt/sources.list**:
For binaries: **deb http://www.winischhofer.net/sis/debian/unstable ./**
For source: **deb-src http://www.winischhofer.net/sis/debian/unstable ./**

```

Install two packeges **x-driver-sis** and **sisctrl**

Exactly you need just **x-driver-sis**.

And correct xorg.conf

```

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "sis"
EndSection

``` 

That's all!!!

---

### Post by heimo on 2005-08-10
Great!

I wonder if [xserver-xorg-driver-sis package  ]("http://packages.ubuntu.com/breezy/x11/xserver-xorg-driver-sis")will solve your problem when Breezy is released? Hopefully. But for now, your solution and instructions are a great help for others in same situation. Thank you!


EDIT: Oh, one more question - which driver did you use before this new one?

---

### Post by BArS on 2005-08-10
I use VESA. The system find it.

---

