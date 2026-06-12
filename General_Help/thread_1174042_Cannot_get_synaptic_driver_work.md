---
title: "Cannot get synaptic driver work"
date: 2009-05-30
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-05-30
Hi, I follow this guide [http://ubuntuforums.org/showthread.php?t=493758](http://ubuntuforums.org/showthread.php?t=493758)
but after logout and login it said X has problem and the screen resolution drops to 640x480! It seems that the SiS driver has been overrided. I undo the setting in Xorg.conf and reboot, everything returns normal again. What's my problem and how can I get synaptic driver works? 

Here's my original xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
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

I follow the guide and install the synaptic driver, and added the following to xorg.conf: 

```

Section "ServerLayout"
	Identifier	    "Default Layout"
        Screen              "Default Screen"
	InputDevice         "Generic Keyboard"
	InputDevice	    "Configured Mouse"
        InputDevice         "Synaptics Touchpad"
EndSection

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

```

Many thanks!

---

### Post by afeasfaerw23231233 on 2009-05-31
bump

---

### Post by afeasfaerw23231233 on 2009-06-03
bump

---

### Post by pauna on 2009-06-03
What do the X logs say (for example /var/log/Xorg.0.log) say when you use your invalid X config?

---

### Post by afeasfaerw23231233 on 2009-06-03
Hi.
It said

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux coppen-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun  3 21:01:41 2009
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined InputDevice "Generic Keyboard" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

[B]Fatal server error:
no screens found[/B]

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
```

"Fatal server error: no screens found"

---

### Post by afeasfaerw23231233 on 2009-06-04
Bump!

---

### Post by pauna on 2009-06-05
```

(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
	Undefined InputDevice "Generic Keyboard" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

```

Ok, you seem to be missing an InputDevice section for your "Generic Keyboard", which you have said in the ServerLayout section you're using. I think you can actually remove that line from the ServerLayout section, it probably works without it.

But if the snippets on your original post are your xorg.conf in its entirety, then you may be missing the Configured Mouse block as well? And that configuration block depends on your mouse characteristics.

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

### Post by afeasfaerw23231233 on 2009-06-26
This howto about synclient solved my problem:
[http://ubuntuforums.org/showthread.php?t=886449](http://ubuntuforums.org/showthread.php?t=886449)

---

