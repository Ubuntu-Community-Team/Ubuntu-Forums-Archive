---
title: "Adding &quot;server layout&quot; in xorg.conf disables the SiS driver"
date: 2009-03-06
forum: Desktop Environments
---

### Post by afeasfaerw23231233 on 2009-03-06
I want to add some features on the touchpad so I follow the instruction of this howto [http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)
```

I add 

Section "ServerLayout"
	        InputDevice         "Synaptics Touchpad"
EndSection

```
restart X and the resolution becomes 800x600 max again. 
Is that because it overrides the SiS driver? 
Thanks in advance

---

### Post by afeasfaerw23231233 on 2009-03-08
bump

---

### Post by afeasfaerw23231233 on 2009-03-09
bump

---

### Post by afeasfaerw23231233 on 2009-04-02
bumpbump

---

### Post by bgerlich on 2009-04-02
Have you tried adding the "Screen" variable to ServerLayout ? I think it is required when manually defining the ServerLayout section...

---

### Post by afeasfaerw23231233 on 2009-05-07
Hi. The "screen" variable has been added. 

 Before the changes my xorg.conf is: 
```

Section "Device"
	Identifier	"Configured Video Device"
driver "sis"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Then according to this howto I add the following to my xorg.conf 
```

Section "InputDevice"
          Identifier "Synaptics Touchpad"
          Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"
          Option "LeftEdge"      	   "100"
	  Option "RightEdge"     	   "1100"
	  Option "TopEdge"       	   "50"
	  Option "BottomEdge"    	   "300"
	  Option "FingerLow"     	   "30"
	  Option "FingerHigh"    	   "40"
	  Option "MaxTapMove"              "100"
	  Option "TapButton1"    	   "1"
	  Option "TapButton2"    	   "3"
	  Option "TapButton3"    	   "2"
	  Option "MinSpeed"      	   "0.15"
	  Option "MaxSpeed"      	   "0.90"
	  Option "AccelFactor"   	   "0.10"
	  Option "VertScrollDelta"         "25"
	  Option "HorizScrollDelta"        "30"
EndSection

Section "ServerLayout"
	Identifier	    "Default Layout"
      **  Screen              "Default Screen"**
	InputDevice         "Generic Keyboard"
	InputDevice	    "Configured Mouse"
EndSection 
```
After I restart x the resolution becomes 800x600 and I think that the SiS driver has been overrided.

---

### Post by afeasfaerw23231233 on 2009-05-13
bump?

---

### Post by afeasfaerw23231233 on 2009-05-29
Bump

---

### Post by afeasfaerw23231233 on 2009-06-05
The problem solved after deleting 
```

	InputDevice         "Generic Keyboard"
	InputDevice	    "Configured Mouse"

```
Now I have a problem with touchpad border. Would anyone please tell me how to install ksynaptics? I've started a new thread here [http://ubuntuforums.org/showthread.php?t=1178958](http://ubuntuforums.org/showthread.php?t=1178958)
Thanks!

---

### Post by afeasfaerw23231233 on 2009-06-15
*removed*

---

### Post by afeasfaerw23231233 on 2009-06-26
This howto about synclient solved my problem:
[http://ubuntuforums.org/showthread.php?t=886449](http://ubuntuforums.org/showthread.php?t=886449)

---

