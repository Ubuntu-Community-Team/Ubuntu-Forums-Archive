---
title: "Help With Nikon Coolpix 880"
date: 2009-05-25
forum: General Help
---

### Post by izizzle on 2009-05-25
Ok. So, today I plugged in my Coolpix 880 camera into the computer, and surprisingly, Ubuntu did not recognize it. I don't know much about Ubuntu and cameras, so I was hoping someone here at the forums could help me out. 

Thanks.

---

### Post by Champain on 2009-05-25
Try downloading a program called DigiKam, under the Add/Remove section. After you have it plug in your camera, open the program go to import -> Camera Add -> Add Camera -> find your camera on the list (I saw it on there) -> then auto detect. The rest should work its self out.
What I like to use for my cameras is a usb card reader, it copies at faster speeds than just plugging your camera in. Extremely useful if you shoot in RAW.  ;)

---

### Post by izizzle on 2009-05-25
Hey Champain I'll try installing Digikam. The coolpix 880 uses a Compact Flash card and I plugged in the CF reader with the card inside it without luck. I guess if the camera works then it's all well and good. :D

---

### Post by izizzle on 2009-05-25
Alright. I tried DigiKam and it detected the camera fine but when I try to access the camera, I get the following:

"Failed to connect to the camera. Please make sure it is connected properly and turned on. Would you like to try again?"

---

### Post by Champain on 2009-05-25
When you connect it and turn it on, is it in image viewing mode. Most cameras only connect via usb when in that mode. Also you could try selecting the Nikon Coolpix 885(PTP mode) from the list. Not trying to make you look like an idiot here, but are you using a usb port from the back panel of your tower? If you are, try using a different one.

---

### Post by benerivo on 2009-05-25
Camera's can be a little difficult. I would recommend gthumb.

---

### Post by izizzle on 2009-05-25
I tried everything you guys suggested. I even tried GThumb without any luck. I know the camera is in computer syncing mode because there is a circulating rectangle in the info area of the camera. Any ideas?

---

### Post by Champain on 2009-05-25
I found some drivers for ubuntu you could try them out.
[http://www.drivers.mrjuan.com/driver-5351-coolpix-880.html](http://www.drivers.mrjuan.com/driver-5351-coolpix-880.html)
I'm running out of ideas though, has the camera worked with another OS before?

---

### Post by izizzle on 2009-05-25
The download is broken. The alternative download link brings me Nikon's website. This camera has worked with Windows XP previously.

Looks like I'll just have to fiddle around with it until it works or until I get tired of trying. 

Thanks for the help guys! It's very much appreciated.

---

### Post by unutbu on 2009-05-25
Have you tried this?

First install the gphoto2 package from the official repos.
Plug the camera into a USB port.
Turn the camera on.
Then open a terminal and type:
```

cd Pictures
/usr/bin/gphoto2 --port usb: --force-overwrite --get-all-files
```
If all goes well, the pictures should be downloaded into ~/Pictures.

---

### Post by izizzle on 2009-05-25
I get the following error:```
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
```

---

### Post by unutbu on 2009-05-25
When you turn the camera on, does a window pop up asking if you would like F-Spot or some other program to download the pictures?
If so, click "Cancel". Then run the "gphoto2" command from the terminal.

---

### Post by izizzle on 2009-05-25
No other window pops up when I turn on the camera.

---

### Post by unutbu on 2009-05-25
Okay, if the camera is already in use, perhaps the card's contents are already mounted in ~/.gvfs. Perhaps open a file browser, press Ctrl-h to show so-called "hidden dot-files", and look for the .gvfs directory in your home account.

---

### Post by izizzle on 2009-05-25
Nope. Nothing there either.

---

### Post by dsaronin on 2010-01-05
izizzle,
I've been having similar problems with Nikon CoolPix 880 and gphoto2 (i'm using Ubuntu 9.10 karmic).

you need to be as superuser when running the gphoto2 commands .. so do 
  sudo gphoto2 <command whatever>

that will get you past that "already in use" error.

example: 
  sudo gphoto2 --camera "Nikon CoolPix 880" --port usb: --list-files

should show you available files
or 

  sudo gphoto2 --auto-detect

should find your Coolpix connected on a usb port:

Model                          Port                                            
----------------------------------------------------------
Nikon CoolPix 880              usb:          

I'm still having some problems reading, but I think it might be because my camera was purchased in japan and the file information is in Japanese!  I'm still trying to figure out how to get around that.

---

### Post by dsaronin on 2010-01-06
Here's something else I found at ([http://www.ubuntugeek.com/some-of-known-ubuntu-904jaunty-jackalope-bugs-with-workarounds.html](http://www.ubuntugeek.com/some-of-known-ubuntu-904jaunty-jackalope-bugs-with-workarounds.html))

2) Camera doesn’t mount when connected and switched on in Ubuntu 9.04(Jaunty)

Bug Details

Camera doesn’t mount when connected and switched on in Ubuntu 9.04(Jaunty)

Workaround

Quick fix:

Run the command from your terminal

sudo killall gvfs-gphoto2-volume-monitor

then connect the camera.

Long-term fix:

Prevent the process from starting Using the following command

sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor


I didn't try the logterm fix, but the sudo killall gvfs-gphoto2-volume-monitor sure cleared out that already in use error.

---

### Post by gigioneumatica on 2010-05-27
Hi Izzile,

Could you make your coolpix 880 work?
i had thge same problem... I'm new in ubuntu 10, and I trying to figure this old hardware incompatibilities out...
Regards...

---

