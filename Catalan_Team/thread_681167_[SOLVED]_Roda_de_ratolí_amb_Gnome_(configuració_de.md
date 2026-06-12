---
title: "[SOLVED] Roda de ratolí amb Gnome (configuració de número de línies)"
date: 2008-01-28
forum: Catalan Team
---

### Post by oksi on 2008-01-28
Hola, m'agradaria presentar un dubte de configuració del ratolí que tinc amb Gnome.

El cas és que m'agradaria configurar que per cada volta del "scroll" del ratolí em mogués més línies que les actuals. No sé si m'explico, Se'm fa bastant molest a l'hora de navegar tindre que donar tantes voltes al scroll per baixar les pàgines webs. Hi ha alguna manera de configurar-ho?

Moltíssimes gràcies.

---

### Post by CarlesOriol on 2008-01-29
No sé si et servirà de res però e copiat aquest tros de xorg.conf de la xarxa.
(per si algun parametre et pot servir de referència... tot i que jo no he vist una solució clara)

```

Section "InputDevice"
  Driver	"synaptics"
  Identifier	"Mouse[1]"
  Option	"InputFashion" "Mouse"
  Option	"Name" "AlpsPS/2 ALPS TouchPad"
  Option	"Vendor" "Sysp"
#  Option	"Protocol" "auto-dev"
#  Option	"Protocol" "event"
#  Option	"Device" "/dev/input/event1"
  Option	"Protocol" "imps/2"
  Option	"Device" "/dev/input/mice"
  Option	"Buttons" "8"
  Option	"ZAxisMapping"		"4 5 6 7"
	# Allows synclient to configure the driver in real time.
  Option	"SHMConfig"		"on"
	# Corners of Alps Glidepoint touchpad: 
	# Outer			(52,46-995,728)	Observed bounding box
	# Probably really	(0,0-1000,750)	Bezel covers some active area
	# Inner			(100,100-950,670) Outside this is a corner tap
  Option	"TopEdge"		"100"
  Option	"BottomEdge"		"670"
  Option	"LeftEdge"		"100"
  Option	"RightEdge"		"950"

	# "Speeds" are in screen pixels per pad unit.  Ratio scales with finger
	# speed: MinSpeed if slow, MaxSpeed if fast.  With driver 0.13.5,
	# units were different and 0.65, 0.15 were my preferred values.
  Option	"MaxSpeed"		"2.0"
  Option	"MinSpeed"		"0.5"
	# dS = change in screen pixels; dP = change in pad units per "packet"; 
	# A = AccelFactor.  Then dS = A * dP * dP but limited by 
	# {Min,Max}Speed * dP.  Packets come out a time dT apart, where we can 
	# only guess what dT is.  Empirically, A = 0.05 gives a speed of about 
	# 1.0, i.e. 1 pixel per pad unit, if you cross the pad in 1 second.
  Option	"AccelFactor"		"0.05"
	# X or Y pad motion for each scroll event (simulated button)
  Option	"VertScrollDelta"	"25"
  Option	"HorizScrollDelta"	"25"
        # If scroll speed (events/sec) is above this value for 4 successive
	# packets, scrolling continues until you tap.  0 -> disable.
  Option	"CoastingSpeed"		"3.0"

	# Edge motion speed scales with Z axis (pressure).  However, the
	# Alps pad poorly gives Z (compared to Synaptics), so this scaling
	# is not used.  Speed may be screen pixels/sec.
  Option	"EdgeMotionMinZ"	"65"
  Option	"EdgeMotionMaxZ"	"80"
  Option	"EdgeMotionMinSpeed"	"150"
  Option	"EdgeMotionMaxSpeed"	"150"
	# True -> use for normal movement, false -> only for dragging.
  Option	"EdgeMotionUseAlways"	"on"

	# What happens when you tap the {Left,Right}{Top,Bottom} corner or
	# tap inside with N fingers.  0 -> nothing, 1 = left button, 
	# 2 = middle button, 3 = right button.  The Alps pad cannot distinguish
	# multiple fingers.
  Option	"LBCornerButton"	"2"
  Option	"LTCornerButton"	"0"
  Option	"RBCornerButton"	"3"
  Option	"RTCornerButton"	"0"
  Option	"TapButton1"		"1"
  Option	"TapButton2"		"3"
  Option	"TapButton3"		"0"

	# If Z axis is above FingerHigh -> touch.  Below FingerLow -> release.
	# Unlike the Synaptics pad, on a tap the Alps pad sends one single
	# packet (hardware detection) with Z=16 followed 100 msec later by one 
	# in the exact same place with Z=0.  (Never < 90 msec, always < 110
	# msec.)  (There's a kernel patch to kludge around this.)
  Option	"FingerHigh"		"15"
  Option	"FingerLow"		"10"
	# (Note: defaults for the next 3 come out to 220 180 180 for Synaptics)
	# In order for a tap to be recognized:
	# Touch and release must be no more distant than this (pad units)
  Option	"MaxTapMove"		"200"
	# Release must follow touch no longer than this (msec)
	# NOTE! Change to 210 with Alps hardware tap patch mentioned above.
	# jimc uses 110 without the patch.
  Option	"MaxTapTime"		"210"
	# Second tap must follow release this closely to recognize double tap.
  Option	"MaxDoubleTapTime"	"150"
	# How long between emulated button-down and button-up events.  Should
	# be long enough so you can see the button change color.
  Option	"ClickTime"		"100"
	# If physical buttons 1 and 3 are hit within this time, do button 2.
  Option	"EmulateMidButtonTime"	"150"

	# 0 = enable, 1 = disable completely, 2 = only tapping is disabled
  Option	"TouchpadOff"		"0"
	# On -> drag continues until you tap a second time.
  Option	"LockedDrags"		"off"
# These features are not turned on.
  Option	"GuestMouseOff"		"off"
  Option	"CircularScrolling"	"off"
	# Angle in radians for each scroll event
  Option	"CircScrollDelta"	"0.2"
	# Where do you touch to start circular scroll?  0 -> any edge, 1 = top 
	# edge, 2 = top right corner, etc. around the edge of the pad up to
	# 8 = top left corner.
  Option	"CircScrollTrigger"	"0"
  Option	"PalmDetect"		"off"

EndSection
```

---

### Post by lluisanunez on 2008-01-29
[INDENT]*Se'm fa bastant molest a l'hora de navegar tindre que donar tantes voltes al scroll per baixar les pàgines webs. Hi ha alguna manera de configurar-ho?*[/INDENT]

A part de la configuració, un truc que vaig descobrir fa poc i que va molt rebé per als llargs scrolls (a qualsevol programa en linux): fer clic amb el botó del mig al final de la barra de desplaçament vertical (o al capdamunt), i hi vas de dret.

---

### Post by oksi on 2008-01-29
Gràcies, és una manera però s'ha de reconèixer que si la pàgina es força llarga has de ser molt acurat...

Gràcies també per la configuració de referència però m'he perdut amb tant paràmetre, sóc molt novell :S

Em sembla recordar que l'entorn KDE si que té una configuració gràfica del mouse on s'hi pot configurar això. Windos segur que ho té. ¿Serviria de alguna cosa carregar un live cd de Kubuntu i canviar el valor aquest i mirar quins canvis fa al xorg.conf?

---

### Post by CarlesOriol on 2008-01-30
Ok

Al firefox obre about:config

Cerca els paràmetres:
mousewheel.withnokey.sysnumlines
mousewheel.withnokey.numlines

Que indiquen el nombre de linies que es desplaçarà per unitat d'scroll i canvia'l pel que més t'agradi.

Ref: [https://answers.edge.launchpad.net/ubuntu/+question/9200](https://answers.edge.launchpad.net/ubuntu/+question/9200)

---

### Post by papapep on 2008-01-30
Bona aquesta, pol·liol!!! ;-)

---

### Post by oksi on 2008-01-31
Moltes gràcies, 

Ho heu provat? Es que jo he canviat els valors (el primer de -1 a 10 i el segon a true) però no fa absolutament res :S 

A vosaltres us funciona?

gràcies

---

### Post by CarlesOriol on 2008-01-31
mousewheel.withnokey.sysnumlines

Ha de ser FALSE

---

### Post by oksi on 2008-02-03
Moltes gràcies. Ara si que ho he aconseguit ;)

---

