---
title: "System hangs EVERY time I try to access the screensaver!"
date: 2005-12-05
forum: Desktop Environments
---

### Post by Orillian on 2005-12-05
Ok, every time I go into the screensaver section in the preferences, the screensaver window pops up and then the system hangs about 2-3 seconds after it loads and starts to preview the screensavers. 

It also seems like the the screensaver causes the system to hang when it comes up after the default 10 minutes, because if I let the screen go blank then the system no longer responds and I have to reboot it as well.

Would this have anything to do with my videocard drivers? I have yet to install the ATI drivers for my 9200SE that is in this machine.

I am hoping to use this machine as a dedicated BOINC machine and need to fix the screensaver issue so I can get it running when I'm not around! :)

O.

---

### Post by Orillian on 2005-12-05
I think some of the 3d screensavers are causing this crash to happen, but I'm not 100% sure! 

anyone have any input on this?

O.

---

### Post by Sutekh on 2005-12-05
If you haven't installed the video drivers for your ATI card, then I'd think it highly likely that that is what is causing your problems.  Especially if it happens for 3D screensavers.  

Is it neccessary to have a screensaver?  How about just have the PC turn the monitor off after a set time?  At least until you can install the ATI drivers.

---

### Post by Orillian on 2005-12-05
I'd have it do this but I can't get into the screensavers menu to turn it off. every time I try it hangs due to the preview feature. :(

Is there another way to turn off the screensaver?

O.

---

### Post by Ahrel on 2005-12-11
My system does it too.  Need to find out which screensaver it is exactly thats causing this problem.  Sometimes it will get to a certain one, and other times it will just lock up with my current screen (before it fades to black).

I have an ATi 9700 pro, using Breezy.  I installed the fglrx drivers to get some decent OpenGL performance...but I'm thinking of going back to the other ATi drivers, because at least then the openGL performance was just horrible instead of hit or miss :p.

Seriously though, if someone can help with this I'd be much obliged.  I'm new to linux and using it trying nto learn more about how it works (the xorg file still confuses the heck out of me, thank god for a near automatic setup process ;) ).

I've been searching some threads for this problem, and it seems like nobody has figured out exactly what is causing it (if its power management, which I have disabled -- or the screensavers themsels)?

---

### Post by kaamos on 2005-12-11
[QUOTE=Orillian]I'd have it do this but I can't get into the screensavers menu to turn it off. every time I try it hangs due to the preview feature. :(

Is there another way to turn off the screensaver?

O.[/QUOTE]

The configuration file is ~/.xscreensaver
This is my file with no screensaver, but a blank screen:
```

# XScreenSaver Preferences File
# Written by xscreensaver-demo 4.21 on Thu Nov 24 12:40:57 2005.
# http://www.jwz.org/xscreensaver/

timeout:	0:10:00
cycle:		0:10:00
lock:		False
lockTimeout:	0:00:00
passwdTimeout:	0:00:30
visualID:	default
installColormap:    True
verbose:	False
timestamp:	True
splash:		True
splashDuration:	0:00:05
quad:		False
demoCommand:	xscreensaver-demo
prefsCommand:	xscreensaver-demo -prefs
newLoginCommand:    gdmflexiserver -sl
newLoginCommand:    gdmflexiserver -sl
nice:		10
memoryLimit:	0
fade:		True
unfade:		True
fadeSeconds:	0:00:02
fadeTicks:	20
captureStderr:	False
ignoreUninstalledPrograms:False
font:		*-medium-r-*-140-*-m-*
dpmsEnabled:	True
dpmsStandby:	0:15:00
dpmsSuspend:	0:20:00
dpmsOff:	0:30:00
grabDesktopImages:  False
grabVideoFrames:    False
chooseRandomImages: False
imageDirectory:	

mode:		blank
selected:	141

textMode:	url
textLiteral:	XScreenSaver
textFile:	/usr/share/doc/xserver-common/copyright
textProgram:	fortune
textURL:	http://planet.ubuntu.com/rss20.xml

programs:								      \
-		 "Qix (solid)" 	qix -root -solid -segments 100		    \n\
-	   "Qix (transparent)" 	qix -root -count 4 -solid -transparent	    \n\
-		"Qix (linear)" 	qix -root -count 5 -solid -transparent	      \
				  -linear -segments 250 -size 100	    \n\
-		   "Qix (xor)" 	qix -root -linear -count 5 -size 200	      \
				  -spread 30 -segments 75 -solid -xor	    \n\
-	  "Attraction (balls)" 	attraction -root -mode balls		    \n\
-	  "Attraction (lines)" 	attraction -root -mode lines -points 3	      \
				  -segments 200				    \n\
-	   "Attraction (poly)" 	attraction -root -mode polygons		    \n\
-	"Attraction (splines)" 	attraction -root -mode splines -segments      \
				  300					    \n\
-	"Attraction (orbital)" 	attraction -root -mode lines -radius 300      \
				  -orbit -vmult 0.5			    \n\
-				pyro -root				    \n\
-				rocks -root				    \n\
-				helix -root				    \n\
-				pedal -root				    \n\
-				rorschach -root -offset 7		    \n\
-				hopalong -root				    \n\
-				greynetic -root				    \n\
-				imsmap -root				    \n\
				slidescreen -root			    \n\
-				decayscreen -root			    \n\
-				jigsaw -root				    \n\
-				blitspin -root -grab			    \n\
-				slip -root				    \n\
				distort -root				    \n\
				spotlight -root				    \n\
	      "Ripples (oily)" 	ripples -root -oily -light 2		    \n\
	      "Ripples (stir)" 	ripples -root -oily -light 2 -stir	    \n\
	   "Ripples (desktop)" 	ripples -root -water -light 6		    \n\
-				hypercube -root				    \n\
-				hyperball -root				    \n\
-				halo -root				    \n\
-				maze -root				    \n\
-				noseguy -root				    \n\
-				flame -root				    \n\
-				lmorph -root				    \n\
				deco -root				    \n\
-				moire -root				    \n\
-				moire2 -root				    \n\
-				lightning -root				    \n\
-				strange -root				    \n\
-				spiral -root				    \n\
-				laser -root				    \n\
-				grav -root				    \n\
-	       "Grav (trails)" 	grav -root -trail -decay		    \n\
-				drift -root				    \n\
-				ifs -root				    \n\
-				julia -root				    \n\
				penrose -root				    \n\
-				sierpinski -root			    \n\
				braid -root				    \n\
				galaxy -root				    \n\
-				bouboule -root				    \n\
				swirl -root				    \n\
-				flag -root				    \n\
-				sphere -root				    \n\
-				forest -root				    \n\
-				lisa -root				    \n\
-				lissie -root				    \n\
-				goop -root -max-velocity 0.5 -elasticity      \
				  0.9					    \n\
-				starfish -root				    \n\
-	     "Starfish (blob)" 	starfish -root -blob			    \n\
-				munch -root				    \n\
-				mismunch -root				    \n\
-				fadeplot -root				    \n\
-				coral -root -delay 0			    \n\
-				mountain -root				    \n\
-				triangle -root -delay 1			    \n\
-				worm -root				    \n\
-				rotor -root				    \n\
-				ant -root				    \n\
-				demon -root				    \n\
-				loop -root				    \n\
-				vines -root				    \n\
-				kaleidescope -root			    \n\
-				xjack -root				    \n\
				xlyap -root -randomize			    \n\
-				cynosure -root				    \n\
-				flow -root				    \n\
-				epicycle -root				    \n\
-				interference -root			    \n\
-				truchet -root -randomize		    \n\
-				bsod -root				    \n\
-				crystal -root				    \n\
-				discrete -root				    \n\
-				kumppa -root				    \n\
-				rd-bomb -root				    \n\
-	    "RD-Bomb (mobile)" 	rd-bomb -root -speed 1 -size 0.1	    \n\
				sonar -root				    \n\
-				t3d -root				    \n\
-				penetrate -root				    \n\
-				deluxe -root				    \n\
-				compass -root				    \n\
-				squiral -root				    \n\
-				xflame -root				    \n\
-				wander -root				    \n\
-	      "Wander (spots)" 	wander -root -advance 0 -size 10 -circles     \
				  -length 10000 -reset 100000		    \n\
-				critical -root				    \n\
-				phosphor -root				    \n\
-				xmatrix -root				    \n\
-				petri -root -size 2 -count 20		    \n\
-		     "Petri 2" 	petri -root -minlifespeed 0.02		      \
				  -maxlifespeed 0.03 -minlifespan 1	      \
				  -maxlifespan 1 -instantdeathchan 0	      \
				  -minorchan 0 -anychan 0.3		    \n\
				shadebobs -root				    \n\
-				ccurve -root				    \n\
-				blaster -root				    \n\
-				bumps -root				    \n\
-				xteevee -root				    \n\
-				xanalogtv -root				    \n\
-				xspirograph -root			    \n\
-				nerverot -root				    \n\
-	    "NerveRot (dense)" 	nerverot -root -count 1000		    \n\
-	    "NerveRot (thick)" 	nerverot -root -count 100 -line-width 4	      \
				  -max-nerve-radius 0.8 -nervousness 0.5      \
				  -db					    \n\
-				xrayswarm -root				    \n\
-	      "Zoom (Fatbits)" 	zoom -root				    \n\
-	       "Zoom (Lenses)" 	zoom -root -lenses			    \n\
-				rotzoomer -root				    \n\
-	  "RotZoomer (mobile)" 	rotzoomer -root -move			    \n\
-	   "RotZoomer (sweep)" 	rotzoomer -root -sweep			    \n\
-				whirlwindwarp -root			    \n\
-				whirlygig -root				    \n\
-				speedmine -root				    \n\
-		   "SpeedWorm" 	speedmine -root -worm			    \n\
-				vermiculate -root			    \n\
-				twang -root				    \n\
-				apollonian -root			    \n\
-				euler2d -root				    \n\
-	     "Euler2d (dense)" 	euler2d -root -count 4000 -eulertail 400      \
				  -ncolors 230				    \n\
-				juggle -root				    \n\
-				polyominoes -root			    \n\
-				thornbird -root				    \n\
-				fluidballs -root			    \n\
-				anemone -root				    \n\
-				halftone -root				    \n\
				metaballs -root				    \n\
-				eruption -root				    \n\
				popsquares -root			    \n\
-				barcode -root				    \n\
-				piecewise -root				    \n\
-				cloudlife -root				    \n\
-				fontglide -root -page			    \n\
-	"FontGlide (scroller)" 	fontglide -root -scroll			    \n\
-				apple2 -root				    \n\
-				bubbles -root				    \n\
-				pong -root -speed 8			    \n\
-				wormhole -root				    \n\
-				pacman -root				    \n\
				fuzzyflakes -root			    \n\
-				anemotaxis -root			    \n\
-				memscroller -root			    \n\
-				substrate -root				    \n\
-	 "Substrate (circles)" 	substrate -root -circle-percent 33	    \n\
-				intermomentary -root			    \n\
				fireworkx -root				    \n\
				fiberlamp -root				    \n\
-				boxfit -root				    \n\
- default-n: 			vidwhacker -root			    \n\
  GL: 				gears -root				    \n\
  GL: 	   "Gears (planetary)" 	gears -root -planetary			    \n\
  GL: 				superquadrics -root			    \n\
  GL: 				morph3d -root				    \n\
- GL: 				cage -root				    \n\
  GL: 				moebius -root				    \n\
- GL: 				stairs -root				    \n\
  GL: 				pipes -root				    \n\
- GL: 				sproingies -root			    \n\
- GL: 				rubik -root				    \n\
- GL: 				atlantis -root -gradient		    \n\
- GL: 				lament -root				    \n\
  GL: 				bubble3d -root				    \n\
- GL: 				glplanet -root				    \n\
  GL: 				flurry -root -preset random		    \n\
  GL: 				pulsar -root				    \n\
- GL: 	   "Pulsar (textures)" 	pulsar -root -texture -mipmap		      \
				  -texture_quality -light -fog		    \n\
- GL: 				extrusion -root				    \n\
  GL: 				sierpinski3d -root			    \n\
- GL: 				menger -root				    \n\
  GL: 				gflux -root				    \n\
- GL: 		"GFlux (grab)" 	gflux -root -mode grab			    \n\
  GL: 				stonerview -root			    \n\
- GL: 				starwars -root				    \n\
  GL: 				gltext -root				    \n\
  GL: 	      "GLText (clock)" 	gltext -text "%A%n%d %b %Y%n%r" -root	    \n\
  GL: 				molecule -root				    \n\
  GL: 	    "Molecule (lumpy)" 	molecule -root -no-bonds -no-labels	    \n\
- GL: 				dangerball -root			    \n\
  GL: 				circuit -root				    \n\
  GL: 				engine -root				    \n\
  GL: 				flipscreen3d -root			    \n\
  GL: 				glsnake -root -no-titles		    \n\
- GL: 				boxed -root				    \n\
- GL: 				glforestfire -root			    \n\
- GL: 	 "GLForestFire (rain)" 	glforestfire -root -count 0		    \n\
- GL: 				sballs -root				    \n\
- GL: 				cubenetic -root				    \n\
  GL: 				spheremonics -root			    \n\
  GL: 				lavalite -root				    \n\
  GL: 				queens -root				    \n\
  GL: 				endgame -root				    \n\
  GL: 				glblur -root				    \n\
  GL: 				atunnel -root				    \n\
  GL: 				flyingtoasters -root			    \n\
- GL: 				bouncingcow -root			    \n\
  GL: 				jigglypuff -root -random		    \n\
- GL: 				klein -root -random			    \n\
  GL: 	"HyperTorus (striped)" 	hypertorus -root			    \n\
  GL: 	  "HyperTorus (solid)" 	hypertorus -root -solid -transparent	    \n\
  GL: 				glmatrix -root				    \n\
  GL: 				cubestorm -root				    \n\
  GL: 				glknots -root				    \n\
- GL: 				blocktube -root				    \n\
  GL: 				flipflop -root				    \n\
  GL: 				antspotlight -root			    \n\
  GL: 				glslideshow -root			    \n\
  GL: 				polytopes -root				    \n\
  GL: 				gleidescope -root			    \n\
  GL: 				mirrorblob -root			    \n\
  GL: "MirrorBlob (color only)" mirrorblob -root -colour -no-texture	    \n\
  GL: 				blinkbox -root				    \n\
- GL: 				noof -root				    \n\
  GL: 				polyhedra -root				    \n\
  GL: 				antinspect -root			    \n\
- GL: 				providence -root			    \n\
- GL: 	"Pinion (large gears)" 	pinion -root				    \n\
- GL: 	"Pinion (small gears)" 	pinion -root -size 0.2 -scroll 0.3	    \n\
- GL: 				boing -root -lighting -smooth		    \n\
- GL: 				carousel -root				    \n\
- GL: 				fliptext -root				    \n\
-				xdaliclock -root -builtin3 -cycle	    \n\
- default-n: 			xearth -nofork -nostars -ncolors 50	      \
				  -night 3 -wait 0 -timewarp 400.0 -pos	      \
				  sunrel/38/-30				    \n\
-				xplanet -vroot -wait 1 -timewarp 90000	      \
				  -label -origin moon			    \n\
-				xmountains -b -M -Z 0 -r 1		    \n\
-	    "XMountains (top)" 	xmountains -b -M -Z 0 -r 1 -m		    \n\
-				xaos -root -autopilot -nogui -delay 10000     \
				  -maxframerate 30 -incoloring -1	      \
				  -outcoloring -1			    \n\
-				xfishtank -d -s				    \n\
-				xsnow					    \n\
-				goban -root				    \n\
-				electricsheep				    \n\
-				cosmos -root				    \n\
- GL: 				sphereEversion --root			    \n\
- GL: 				fireflies -root				    \n\


pointerPollTime:    0:00:05
pointerHysteresis:  10
windowCreationTimeout:0:00:30
initialDelay:	0:00:00
sgiSaverExtension:  True
xidleExtension:	True
GetViewPortIsFullOfLies:False
procInterrupts:	True
overlayStderr:	False

```

---

### Post by mtaege on 2006-08-21
Hi everyone,

I have had the same problem as descriped in the thread above (with the same ATI card). 

At least I find out an alternative way to deactivate the screensaver (but please note that I'm very new to Linux/Ubuntu/Gnome myself):

1) Open the GConf-Editor with *gconf-editor*

2) Go to */apps/gnome-screensaver/*

3) Remove the value of the key *themes*

After that, I was able to open the screensaver preferences without having the system hanging and there I could choose *empty screen*.

Hope I could help you,

Michael

---

