---
title: "Compiz + MergedFB giving me fits!"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by bohsocks on 2007-08-28
Hi.  For the longest time I have had an issue that I can't stand anymore.  I use a TV as a second monitor through MergedFB.  For the longest time, since I have this, I have been unable to run Compiz/Beryl/Emerald/Fusion whatever.  But recently I decided to scrap my dual-monitor setup to try Compiz.  And I LOVE IT.

So I have been trying to figure out what it is about my MergedFB that is causing Compiz to bug out.  You see what happens is that when I login to my two-screen output with Compiz running, it loads up fine, and when Compiz kicks in my computer bugs out with things just appearing to crunch together and nothing being where it should be.  

Usually it's even too messed up to navigate, so I have to go into recovery-mode and copy over my xorg.conf with my old one or remove Compiz before things go correctly.

So I've concluded (obviously) that these two things can't co-exist because of something in my MergedFB xorg.conf coding.... whether it be that I coded it "inefficiently" or something is left out or something needs to be tinkered.....

(Unless I'm missing some obscure Compiz setting that will make my life easier.... then please please someone correct me!)

So here is what I've changed in my xorg.conf for MergedFB:

```

Section "Device"
	Identifier	"ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]"
	Driver		"ati"
	BusID		"PCI:1:5:0"
Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "LeftOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "800x600-800x600" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
Horizsync    28-64 #You may wish to change the values to fit your specific monitor
    Vertrefresh    43-60
EndSection

```

Some notable things include:
[LIST]
[*]Only one display, monitor, screen, setion (As I was instructed to do in the MergedFB directions)
[*]No DRI
[*]DIfferent resolutions (Laptop 1280x800, TV 800x600)
[/LIST]

So can someone PLEASE tell me what to change (refresh rates) so I can get things working?  I've been trying trial-and-error myself but so far nothing I've done makes them co-exist and I have having to miss out on half my experience for the sake of the other half.

Thank you.  :)

---

### Post by bohsocks on 2007-08-28
Shove!

---

