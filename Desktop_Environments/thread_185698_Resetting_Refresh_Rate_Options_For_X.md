---
title: "Resetting Refresh Rate Options For X"
date: 2006-06-01
forum: Desktop Environments
---

### Post by QuacoreZX on 2006-06-01
Well, what I want to do is be able to select more options for my monitor's screen refresh rate, as that of 60 Hz is simply unacceptable when using games, Compiz/Xgl, and HDTV Files.  Right now, it seems I only have one refresh rate option per Resolution in my System -> Preferences -> Screen Resolution (1600x1200 @ 65Hz, 1280x960 @ 60Hz, and 1024x768/800x600/640x480 @ 85Hz), which is just plain wrong.

Yes, I did a "sudo dpkg-reconfigure xserver-xorg" using "nvidia" as my video module, yes, I have manually set my xorg.conf for proper monitor Horizontal and Vertical refresh rates, but all amounts to nothing.  Could anyone help me about manually resetting these options?

---

### Post by tseliot on 2006-06-01
Edit your xorg.conf
sudo nano -w /etc/X11/xorg.conf

Get to the Section Screen
and set you resolution and refresh rate in the following way:

The part in red is the refresh rate. In the example below I set the resolution to 1280x1024 at 75hz ( = 1280x1024_75)

```
Section "Screen"
    Identifier  	"Screen[0]"
    Device      	"Device[0]"
    Monitor     	"Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024[COLOR="Red"]_75[/COLOR]" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024[COLOR="Red"]_75[/COLOR]" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

---

### Post by QuacoreZX on 2006-06-01
wait, is the second section, "SubSection "Display"", needed, or can I get away with just changing the Section "Screen" areas?

---

### Post by tseliot on 2006-06-01
[QUOTE=QuacoreZX]wait, is the second section, "SubSection "Display"", needed, or can I get away with just changing the Section "Screen" areas?[/QUOTE]
My bad, it was a mistake, no 2nd section is needed

---

### Post by QuacoreZX on 2006-06-01
actually, it didn't work.  The resolution I used to do that just disappeared from the menu altogether >_<.  Perhaps I need to change my horizontal/vertical refresh frequencies?

---

### Post by tseliot on 2006-06-02
[QUOTE=QuacoreZX]actually, it didn't work.  The resolution I used to do that just disappeared from the menu altogether >_<.  Perhaps I need to change my horizontal/vertical refresh frequencies?[/QUOTE]
My bad again (I needed to get some sleep :p  )

Keep the lines I suggested before and add the following to the Section Device:
```
Option "UseEDID" "False"
```

Then restart the Xserver and see if anything changes

---

### Post by QuacoreZX on 2006-06-04
Still nothing...if I add anything to the end of my resolutions like "_75", that option simply disappears from my Screen Resolution options.

---

### Post by Sean-Michael on 2006-06-05
This worked to help with my problem, now my screen shows correctly the desktop!

Thankyou tseliot for your helpful post!

---

### Post by jerrykenny on 2006-11-13
Thats brill T.S. I've never seen xorg.conf inputs like that.

Quakore, if you cant get that to work, try installing the "nvidia-legacy" kernel interface and glx drivers (as a pair), that worked well on this machine here with the exact same prob.

Sorry for the delay, have been unfaithful and sleeping around with Gentoo lately :oops:

---

