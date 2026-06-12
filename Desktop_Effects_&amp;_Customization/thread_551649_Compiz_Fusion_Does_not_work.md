---
title: "Compiz Fusion Does not work"
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by xelapond on 2007-09-15
I just reinstalled UBuntu on my computer, a first gen macbook pro, 2.0 Ghz, ATI Radeon X1600, 1 Gig ram.

I used this guide:

[http://ubuntuforums.org/showthread.php?t=463791](http://ubuntuforums.org/showthread.php?t=463791)

To install Ubntu and Compiz Fusion.  After I installed Compiz fusion, it just does not work.

**compiz --replace -c emerald**

/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity

and **emerald --replace**

(emerald:6684): Wnck-WARNING **: Unhandled action type (nil)
(emerald:6684): Wnck-WARNING **: Unhandled action type (nil)
(emerald:6684): Wnck-WARNING **: Unhandled action type (nil)
(emerald:6684): Wnck-WARNING **: Unhandled action type (nil)

And none of the desktop effects work.  Here are some diagnostic things i have read about in other threads that supposedly help you guys figure it out:

**fglrxinfo**

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6334 (8.34.8)

**egrep 'Composite|Section\ \"Device' /etc/X11/xorg.conf -A 10**

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection


Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
--
        Option          "Composite"     "0"
EndSection

Section "Extensions"
  Option "Composite" "0" 
EndSection

Any help would be greatly appriciated.  Also, just to let you know, in my previous Ubuntu install compiz fusion was running perfectly.

---

### Post by Forlong on 2007-09-15
The packages from Treviño's respository are broken (in case you didn't know: you installed development versions of Compiz).

Try disabling the screensaver plugin in ccsm - if this doesn't work disable some other plugins like 3D windos, opacify and water effect.

---

### Post by faceless-21 on 2007-09-15
Try using my tutorial here [http://ubuntuforums.org/showthread.php?t=551606&page=2](http://ubuntuforums.org/showthread.php?t=551606&page=2)  using the envy program to get your ATI drivers...

---

### Post by Forlong on 2007-09-15
Why would he want to install another driver, if he has issues with Compiz?
Sorry, but this makes no sense at all.


(and I'm not going to comment on the fact that "your tutorial" is suspiciously similar to mine. You should have at least the decency to give credit to other people's work when copying it)

---

### Post by faceless-21 on 2007-09-15
@Forlong
I said in my post that I used a tutorial that a friend(who is not in these forums that I know of) wrote for me...  Maybe he found yours and copy/pasted it into a document and sent it too me...  But I will ask him if he indeed wrote it.  And if he indeed did not, and you good sir, are the original author of the tutorial.  Then I will gladly "have the decency" to give you credit...
  And as for why he should install another driver?  That I am unsure is COMPLETELY necissary.  BUT I had to use the envy app to get the driver before compiz worked for me...  So that is just my thoughts on it.
  Also, I just looked at your tutorial.  And yes maybe it has some similarities, but it really doesn't look like a copy and paste too me.  
  And then you accuse me of copying someone elses work without crediting them...  When A: I did credit them in a sense.  And B: you didnt even ask if I did indeed copy it from your blog...  Which asking that in itself would be pointless for I gave someone else credit...

   But maybe you didnt really read it...  Here is how I started it off...
   "Ok... Well I am going to copy and paste a tutorial that my friend wrote me"
  I am new too linux, but not to forums or trying to be friendly or curtious...
  I would ask that before blindly accusing someone of "stealing" your work.  Ask them of where they aquired it.  Or at the very least, read what they wrote first.
  
  Have a great rest of your day,         
              Steveo

---

