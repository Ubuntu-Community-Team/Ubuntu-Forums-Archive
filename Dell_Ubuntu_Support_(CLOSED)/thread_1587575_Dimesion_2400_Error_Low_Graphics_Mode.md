---
title: "Dimesion 2400 Error Low Graphics Mode"
date: 2010-10-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cre8ive65 on 2010-10-03
Hi i switched to ubuntu about 4 moths ago and i'm lovin it!
But on my dell dimesion 2400, at random points the screen would go black and there would be white vertical bars flashing, so i took action and headed to the forums
 
I was told this found at this site [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1558917](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1558917)
 
> 
Hello,
 
I had similar problem when the screen would go blank but i would get vertical grey lines.
 
I have the following graphics card:
 
"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)"
 
To find out your graphics card type the following in termial:
 
Code:
lspci | grep VGA
apparently the driver which was in use "i915" was not working well with the xorg so i switched to "vesa" driver and since i have not ever had a problem.
 
Code:
sudo gedit /etc/X11/xorg.conf
The above command will show your current xorg.conf file, you want to change the Driver "whatever" to Driver "vesa"
 
or if its blank then copy/paste the following, save and reboot:
 
Code:
Section "Monitor" Identifier "Monitor0" VendorName "Unknown" ModelName "Unknown" HorizSync 30.0 - 110.0 VertRefresh 50.0 - 150.0 Option "DPMS"EndSectionSection "Device" Identifier "Device0" Driver "vesa"EndSectionSection "Screen" Identifier "Screen0" Device "Device0" Monitor "Monitor0" DefaultDepth 24 SubSection "Display" Depth 24 Modes "1280x1024" "1024x768" "800x600" "640x480" EndSubSectionEndSection
 

 
Now i did that, but my current xorg.conf was blank so i psted the code in and when i rebooted, a window on a black backround before the login screen, or the splash screen said that the following errors occured 
 
```
|EE| VESA |0|: Driver can't support depth 24
```
 
and
 
```
|EE| Screens found, but none have a usable configuration
```
 
I tried to run a session in low graphics mode but the screen goes black, any ideas?
Luckily i have stupid windows on this computer, so i can still go in and edit some files and the output of lspci | grep VGA is Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) the same as the guy who wrote the post
 
Thanks for your time and effort

---

### Post by cre8ive65 on 2010-10-07
Sorry, didnt read the entire forum, my problem might be solved

---

### Post by pricetech on 2010-10-07
If it is, please post the solution for others to benefit from.

---

### Post by cre8ive65 on 2010-10-11
ok heres what you do

> put a hash "#" before the default depth and also the horizontal and  vertical refresh rates to comment them out something like this...

     Code:
     Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    #HorizSync       30.0 - 75
    #VertRefresh     50.0 - 85
    #Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "vesa"
    Option       "UseFBDev" "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    #DefaultDepth    24
    SubSection     "Display"
        #Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection 

for the full post, visit [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1558917&page=2](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1558917&page=2)

---

