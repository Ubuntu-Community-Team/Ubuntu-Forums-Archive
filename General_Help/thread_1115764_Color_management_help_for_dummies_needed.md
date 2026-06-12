---
title: "Color management help for dummies needed"
date: 2009-04-04
forum: General Help
---

### Post by 37fleetwood on 2009-04-04
I'm kinda new to Linux and not altogether stupid but so far everything I've been able to find on the web about color management in Linux makes no sense to me. people start assuming I know what things are and what certain abbreviations mean and I don't. the only thing I'm familiar with is the old Photoshop deal where you slide the slider until you couldn't see the lines anymore. ok, after you stop laughing please help those of us who don't know this stuff and just tell us what we need and what to do. be specific don't assume I know anything. I'm just really disappointed with how crappy the prints are coming from my new camera through my new printer. the scanner looks no better.
thanks in advance
Scott;)

---

### Post by joeyknuccione on 2009-04-04
My other reply seems to be missing, so here goes again...

>I'm not a pro but I have some experience in this<

I recommend you get the manuals for the various products, read them and apply
Tutorials can help, just google your issue

Proper camera settings to begin with will be important. (Mine always seem to wash out due to overexposure, but I'm getting much better)

Ink quality could be a factor.

What photo-editor do you use? In gimp there is an option under Colors>Levels...

Play around with the various sliders here.

If you can be more specific with your color issues, I may can offer more specific advice.

---

### Post by lovinglinux on 2009-04-04
> **joeyknuccione said:**
> My other reply seems to be missing, so here goes again...

>I'm not a pro but I have some experience in this<

I recommend you get the manuals for the various products, read them and apply
Tutorials can help, just google your issue

Proper camera settings to begin with will be important. (Mine always seem to wash out due to overexposure, but I'm getting much better)

Ink quality could be a factor.

What photo-editor do you use? In gimp there is an option under Colors>Levels...

Play around with the various sliders here.

If you can be more specific with your color issues, I may can offer more specific advice.

Adjusting color in the software is not a solution. It might help if the original image is overexposed, but the problem the OP is experiencing here is due to the lack of color calibration. His photos appears good in the monitor, but washed out when printed. This happens because each hardware (camera, monitor, printer, scanner) has it's own way of managing colors, so you need to calibrate them to talk with each other and apply the correct color adjustments.

Color management is achieved using color profiles, so the monitor has a color profile, so does the camera and the printer. Sometimes you can download them, but if not then you need to create them. The camera probably uses sRGB, which is the basic profile for jpegs. The monitor profile can be created using a software tool, where you need to adjust color, brightness and contrast by visual comparison, or using specialized hardware that detect the color from the monitor. 

For more information on color calibration in Linux visit [http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management)

---

### Post by 37fleetwood on 2009-04-04
> **lovinglinux said:**
> Adjusting color in the software is not a solution. It might help if the original image is overexposed, but the problem the OP is experiencing here is due to the lack of color calibration. His photos appears good in the monitor, but washed out when printed. This happens because each hardware (camera, monitor, printer, scanner) has it's own way of managing colors, so you need to calibrate them to talk with each other and apply the correct color adjustments.

Color management is achieved using color profiles, so the monitor has a color profile, so does the camera and the printer. Sometimes you can download them, but if not then you need to create them. The camera probably uses sRGB, which is the basic profile for jpegs. The monitor profile can be created using a software tool, where you need to adjust color, brightness and contrast by visual comparison, or using specialized hardware that detect the color from the monitor. 

For more information on color calibration in Linux visit [http://en.wikipedia.org/wiki/Linux_color_management](http://en.wikipedia.org/wiki/Linux_color_management)

You have me exactly right!
so here are my questions please don't go to fast but also don't leave anything out:
I understand the concept of ICC Profiles, where do I find them for my hardware, and how do I use them once I have them?
what program/s will I need?
is there some suite I can install to walk me through this and determine the correct settings? (I know sounds like Windows, but really wouldn't that make more sense?)
do I really need to get the hickeymadoobobber thing that hangs on my screen and measures the exact output, can't I just get close?
my current prints are so far off from what is on the screen it's ridiculous. straight from the camera (Canon Digital Rebel XT) to the printer (Canon MP190) is terrible. get this from the scanner to the printer (it's an all in one!) is really bad looking.
definitely what I see is not what I get. I really want to get better consistency from this thing. I can't go on reprinting and readjusting and reprinting and readjusting, the cost of ink alone!](*,)

---

### Post by lovinglinux on 2009-04-04
> **37fleetwood said:**
> I understand the concept of ICC Profiles, where do I find them for my hardware, and how do I use them once I have them?

Gimp and DigiKam have a color management section in their preferences, where you can activate it and load the profiles. As far as I know, this is all you need to do if you have them. If you don't, then try downloading them from the manufacturers web sites. Unfortunately, it has been a while since I needed color management and I never tried on Linux, so I don't even know if Ubuntu comes with common profiles installed.

You can calibrate your monitor using these:

[http://www.photofriday.com/calibrate.php](http://www.photofriday.com/calibrate.php)
[http://www.drycreekphoto.com/Learn/Calibration/monitor_black.htm](http://www.drycreekphoto.com/Learn/Calibration/monitor_black.htm)
[http://www.drycreekphoto.com/Learn/Calibration/monitor_sensitivity.html](http://www.drycreekphoto.com/Learn/Calibration/monitor_sensitivity.html)
[http://www.drycreekphoto.com/Learn/Calibration/monitor_gradient.htm](http://www.drycreekphoto.com/Learn/Calibration/monitor_gradient.htm)
[http://desktoppub.about.com/od/visualmonitor/Visual_Monitor_Calibration_Tests.htm](http://desktoppub.about.com/od/visualmonitor/Visual_Monitor_Calibration_Tests.htm)

Read more:
[http://www.drycreekphoto.com/Learn/monitor_calibration.htm](http://www.drycreekphoto.com/Learn/monitor_calibration.htm)
[http://www.normankoren.com/makingfineprints1A.html](http://www.normankoren.com/makingfineprints1A.html)
[http://desktoppub.about.com/cs/colorcalibration/a/cal_monitor.htm](http://desktoppub.about.com/cs/colorcalibration/a/cal_monitor.htm)

---

