---
title: "XSane in 8.10"
date: 2009-05-11
forum: General Help
---

### Post by M4rotku on 2009-05-11
Hello all,

I recently (2 days ago) upgraded to 8.10.  Previous to the upgrade, the XSane application (though fickle) would at least work with one of my scanners via the wireless network.  When it would start up, it would list this scanner along with a scanner which I assumed to be my built-in webcam.  The webcam option has never worked and so I just assumed that xsane was mistakingly interpreting my webcam as a scanner.  However, the actual scanner has always worked more or less.

Now that I've upgraded, I get the following error when trying to start XSane.

> Failed to open device 'v4l:/dev/video0':
Invalid argument.

I think it's trying to open my webcam and failing because the webcam is not a scanner.  Is there any way that I can go into a configuration file and tell it to ignore 'v4l:/dev/video0'?

much thanks,
M4rotku

---

### Post by M4rotku on 2009-05-13
bump

---

### Post by jasc on 2009-05-14
Did you try turning the scanner on?

---

### Post by M4rotku on 2009-05-14
Yes, the scanner was on.  That doesn't seem to be the issue though.  I was receiving the error from my webcam, not the scanner.  XSane didn't get far enough along in its processes to receive an error from the scanner.

Sorry if the above post was confusing.

---

### Post by soro2005 on 2009-05-14
What's the output of
```
scanimage -L
```
on a command line?

---

### Post by M4rotku on 2009-05-14
Output:

> $ scanimage -L
device `v4l:/dev/video0' is a Noname HP Webcam virtual device


---

### Post by soro2005 on 2009-05-14
Looks very much like your scanner isn't recognized. What model is it?

---

### Post by M4rotku on 2009-05-14
I've used it before.  Idk if it's not recognized or if the webcam is just blocking it.  The model is:  HP Photosmart 2710.  It's a multipurpose and I can print from it just fine.

---

### Post by soro2005 on 2009-05-14
xsane is just a graphical frontend to sane, the scanning system. I don't think that your hypothesis is right and xsane tries to initialize the camera and so doesn't get around to listing the scanner. The scanimage -L thing should output all the devices known to sane. The fact that the scanner is not there pretty much suggests that it is not found. Which can happen after an upgrade, either b/c there's a regression and it doesn't work any more (unfortunately happens), or b/c there is a residual configuration in the way. Perhaps, one of the relevant libraries has also been uninstalled.

Can you make sure that you have the package hplip installed, and if you have, can you reinstall it and then try again?

If I'm right, this is not going to work any better for you. But my favorite scanning program is gscan2pdf. It absolutely rrrrrrrrrrrrrocks, particularly if you're scanning texts (as opposed to images which may need more control of the quality).

---

### Post by soro2005 on 2009-05-14
Also, can you try out whether it works if you use a USB cable? In which case you'd have a networking issue, not a sane/printer driver issue.

By the way, your printer model is [listed as fully supported](http://hplipopensource.com/hplip-web/models/photosmart/photosmart_2700_series.html). What do you mean that it worked "more or less" in the past?

---

### Post by M4rotku on 2009-05-14
Now that I think about it, when I upgraded, I may have replaced the current xsane files with the new ones.  I wasn't really thinking about it doing something like this.  Now that I look back, it's kinda obvious that it wasn't a good idea.

In that case, I would just have to reinstall it as a scanner.  But I thought that it was installed as a scanner automatically when I installed the printer as a multifunction.

---

### Post by soro2005 on 2009-05-14
It should be automatically installed as *both* scanner and printer by hplip. xsane is just the graphical frontend. Reinstalling xsane, or a different version of it, is not going to change anything. The package that's doing the lifting is called sane. and it uses whatever it finds as a scanner or image acquisition device (hence the webcam). It doesn't find your printer, which means that, either, the connection doesn't work, or the printer/scanner driver (hplip) is not installed correctly.

Xsane will give you the selection dialog again once the scanner is properly recognized. Don't worry about it for the time being. Rather use a USB cable, and reinstall hplip and hplip-data. If the printer prints, then the driver is more likely the problem.

---

### Post by M4rotku on 2009-06-14
Update:  Alright guys, I think it's not so much a driver issue with the actual scanner.  I think it's that the webcam is not being recognized and that causes the problem to close before it gets to the scanner.

Hence the:

> Failed to open device 'v4l:/dev/video0'
Invalid argument

Error that I keep getting.  I really need this scanner to work now b/c I actually have to scan something to send in to work.

Much thanks,
M4rotku

---

### Post by M4rotku on 2009-06-15
bump

---

### Post by M4rotku on 2009-06-17
bump

---

### Post by M4rotku on 2009-06-20
bump

---

### Post by M4rotku on 2009-06-21
bump

---

### Post by Potters Son on 2009-08-15
I get the same problem here. I have an HP Pavilion dv6000 with integrated webcam, and XSane has always crashed with the same error. Today, I bought an HP Deskjet F4400 and it prints fine. However, XSane STILL crashes with the same error that you're getting.

Idea: on the command line, I found that XSane takes an optional [DEVICE] argument. However, so far I have been unable to find something that it'll take.

---

### Post by Potters Son on 2009-08-15
Just found the answer to my problem. The version of HPLIP (HP Linux Imaging and Printing... the driver) which ships with Ubuntu (v.3.9.2) does not support my model of Deskjet. Instead, I had to go to [http://hplipopensource.com/](http://hplipopensource.com/) to download and install the newest driver (at the time of this writing, v.3.9.8 ).

Since the printer/scanner was a newer version than what my version of HPLIP supported, the HPLIP backend (used by both CUPS and XSane) refused to detect the printer when I tried to add it in System > Administration > Printing. Instead, I used the HAL (which is only used on CUPS, apparently) backend, which *did* automatically detect the printer. Hence, I could print but not scan.

XSane, in turn, crashed because 1) it only detected the webcam  and 2) it assumed that the webcam was the only thing you'd want to use, so 3) it went ahead and tried to use the webcam, crashing the program.

The only thing to do at that point was to go behind Synaptic's back (sorry, APT) and install the shell script on HP's open source website. [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

