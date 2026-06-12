---
title: "xscreensaver locks screen soon after login"
date: 2008-09-25
forum: Desktop Environments
---

### Post by hollowhead on 2008-09-25
I've been putting up with this problem for months and I'm sick of it, I assume there is a way to stop it happening.... Since I upgraded to hardy and put the xscreensaver back on I've had this problem that did not occur 7.10 etc.  To describe (usually) after a minute (sometime 10 minutes) or so after login after boot the screensaver activates and the screen locks so I have to enter my password to unlock.  Googling the problem seems to turn up references to crash type locks, this is not what happens.  Also it only happens that once per boot enter the password and it doesn't happen again.  Nor does it happen if I log out and log in.  My settings are for the screensaver are blank after 1 min cycle after 1 min and lock after 30 minutes.  I assume there is a setting gconf editor somewhere.  Ps Iwant the screensaver to load automatically on boot just not lock until 30 minutes are up.  Ta in advance.

---

### Post by p_quarles on 2008-09-25
Nope, there are no Gconf settings. X-Screensaver is not a Gnome program. 

Could you post the contents of the following file?:
```
~/.xscreensaver
```

---

### Post by hollowhead on 2008-09-25
Thanks for reply here it is...

 XScreenSaver Preferences File
# Written by xscreensaver-demo 5.04 for nrh1 on Thu Sep 25 14:43:03 2008.
# [http://www.jwz.org/xscreensaver/](http://www.jwz.org/xscreensaver/)

timeout:	0:01:00
cycle:		0:01:00
lock:		True
lockTimeout:	0:30:00
passwdTimeout:	0:00:30
visualID:	default
installColormap:    True
verbose:	False
timestamp:	True
splash:		True
splashDuration:	0:00:05
demoCommand:	xscreensaver-demo
prefsCommand:	xscreensaver-demo -prefs
nice:		10
memoryLimit:	0
fade:		True
unfade:		True
fadeSeconds:	0:00:02
fadeTicks:	20
captureStderr:	True
ignoreUninstalledPrograms:False
font:		*-medium-r-*-140-*-m-*
dpmsEnabled:	False
dpmsStandby:	1:00:00
dpmsSuspend:	1:00:00
dpmsOff:	2:00:00
grabDesktopImages:  True
grabVideoFrames:    False
chooseRandomImages: True
imageDirectory:	/usr/share/backgrounds

mode:		random
selected:	-1

textMode:	date
textLiteral:	XScreenSaver
textFile:	/usr/share/doc/xserver-common/copyright
textProgram:	fortune
textURL:	[http://fridge.ubuntu.com/node/feed](http://fridge.ubuntu.com/node/feed)

programs:								      \
		 "Qix (solid)" 	qix -root -solid -segments 100		    \n\
	   "Qix (transparent)" 	qix -root -count 4 -solid -transparent	    \n\
		"Qix (linear)" 	qix -root -count 5 -solid -transparent	      \
				  -linear -segments 250 -size 100	    \n\
  Best: 	   "Qix (xor)" 	qix -root -count 5 -segments 75 -spread	      \
				  30 -size 200 -color-shift 25 -solid	      \
				  -xor -gravity				    \n\
	  "Attraction (balls)" 	attraction -root -mode balls -points 200      \
				  -size 100 -viscosity 0 -threshold 74	      \
				  -segments 964 -delay 0 -colors 249	      \
				  -color-shift 22 -orbit -radius 680	      \
				  -vmult 5				    \n\
	  "Attraction (lines)" 	attraction -root -mode tails -points 3	      \
				  -viscosity 0.4096 -threshold 452	      \
				  -segments 723 -delay 5542 -colors 253	      \
				  -color-shift 14 -radius 20		    \n\
	   "Attraction (poly)" 	attraction -root -mode splines		    \n\
-	"Attraction (splines)" 	attraction -root -mode splines -segments      \
				  300					    \n\
	"Attraction (orbital)" 	attraction -root -mode lines -radius 300      \
				  -orbit -vmult 0.5			    \n\
				pyro -root -scatter 400			    \n\
				rocks -root -3d -colors 255		    \n\
-				helix -root				    \n\
				pedal -root				    \n\
				rorschach -root -offset 7		    \n\
				hopalong -root				    \n\
				greynetic -root -delay 41391		    \n\
				imsmap -root -iterations 4 -ncolors 225	    \n\
				slidescreen -root			    \n\
				decayscreen -root			    \n\
				jigsaw -root -delay 0			    \n\
				blitspin -root -grab			    \n\
				slip -root				    \n\
				distort -root				    \n\
				spotlight -root				    \n\
	      "Ripples (oily)" 	ripples -root -oily -light 2		    \n\
	      "Ripples (stir)" 	ripples -root -light 2 -stir -oily	      \
				  -colors 255				    \n\
	   "Ripples (desktop)" 	ripples -root -water -light 6		    \n\
-				hypercube -root				    \n\
				hyperball -root -delay 1242 -yw 20 -yz 20     \
				  -zw 20				    \n\
				halo -root				    \n\
				maze -root				    \n\
  Best: 			noseguy -root				    \n\
				flame -root				    \n\
				lmorph -root				    \n\
				deco -root -smooth-colors -golden-ratio	      \
				  -mondrian				    \n\
				moire -root				    \n\
-				moire2 -root -delay 78545 -ncolors 255	    \n\
-				lightning -root				    \n\
-				strange -root				    \n\
-				spiral -root				    \n\
				laser -root				    \n\
				grav -root				    \n\
	       "Grav (trails)" 	grav -root -count 21 -delay 11642 -decay      \
				  -trail -ncolors 255			    \n\
				drift -root				    \n\
				ifs -root -delay 5902 -functions 5	      \
				  -detail 7 -mode 0			    \n\
				julia -root				    \n\
				penrose -root				    \n\
-				sierpinski -root			    \n\
-				braid -root				    \n\
-				galaxy -root				    \n\
				bouboule -root				    \n\
				swirl -root				    \n\
-				flag -root				    \n\
				sphere -root -delay 0 -ncolors 255	    \n\
				forest -root -delay 475524 -ncolors 12	    \n\
-				lisa -root				    \n\
				lissie -root				    \n\
				goop -root -max-velocity 0.5 -elasticity      \
				  0.9					    \n\
				starfish -root				    \n\
	     "Starfish (blob)" 	starfish -root -delay 19270 -thickness 18   \n\
				munch -root				    \n\
				mismunch -root -simul 18 -no-xor	    \n\
				fadeplot -root				    \n\
-				coral -root -delay 0			    \n\
				mountain -root -count 101 -delay 1045	      \
				  -ncolors 255				    \n\
				triangle -root -delay 1			    \n\
-				worm -root				    \n\
-				rotor -root				    \n\
-				demon -root				    \n\
				loop -root				    \n\
-				vines -root				    \n\
				kaleidescope -root -symmetry 20 -ntrails      \
				  748					    \n\
				xjack -root				    \n\
				xlyap -root -randomize			    \n\
				cynosure -root				    \n\
				flow -root -delay 8591 -ncolors 255 -size     \
				  -20 -no-rotate -no-ride -no-box	    \n\
				epicycle -root				    \n\
				interference -root			    \n\
				truchet -root -randomize		    \n\
				bsod -root -atari -no-linux -no-hppalinux     \
				  -no-solaris				    \n\
				crystal -root				    \n\
				discrete -root -cycles 7099 -delay 10446      \
				  -ncolors 231				    \n\
				kumppa -root				    \n\
				rd-bomb -root				    \n\
	    "RD-Bomb (mobile)" 	rd-bomb -root -speed 1 -size 0.1	    \n\
-				sonar -root				    \n\
-				t3d -root -delay 14309 -wobble 2.7561	      \
				  -cycle 49.2683			    \n\
-				penetrate -root				    \n\
				deluxe -root				    \n\
				compass -root				    \n\
				squiral -root				    \n\
-				xflame -root				    \n\
-				wander -root				    \n\
	      "Wander (spots)" 	wander -root -density 7 -reset 2077553	      \
				  -length 62611 -delay 17 -circles -size      \
				  20 -advance 86			    \n\
-				critical -root				    \n\
				phosphor -root				    \n\
				xmatrix -root				    \n\
				petri -root -delay 0 -size 2 -count 16	      \
				  -diaglim 1 -anychan 0.0245 -minorchan	      \
				  0.1702 -instantdeathchan 1		      \
				  -minlifespeed 1 -maxlifespeed 0.0556	      \
				  -mindeathspeed 0.8889 -maxdeathspeed	      \
				  0.1389 -minlifespan 2280 -maxlifespan 0   \n\
		     "Petri 2" 	petri -root -anychan 0.3 -minorchan 0	      \
				  -instantdeathchan 0 -minlifespeed 0.02      \
				  -maxlifespeed 0.03 -minlifespan 1	      \
				  -maxlifespan 1			    \n\
				shadebobs -root -ncolors 255 -count 17	      \
				  -delay 16463				    \n\
				ccurve -root				    \n\
				blaster -root				    \n\
				bumps -root				    \n\
-				xteevee -root				    \n\
				xanalogtv -root				    \n\
				xspirograph -root -delay 1 -layers 3	    \n\
				nerverot -root				    \n\
-	    "NerveRot (dense)" 	nerverot -root -count 1000		    \n\
	    "NerveRot (thick)" 	nerverot -root -count 100 -line-width 4	      \
				  -max-nerve-radius 0.8 -nervousness 0.5      \
				  -db					    \n\
-				xrayswarm -root -delay 5828		    \n\
	      "Zoom (Fatbits)" 	zoom -root -lenses -pixwidth 3		    \n\
	       "Zoom (Lenses)" 	zoom -root -lenses			    \n\
				rotzoomer -root -n 21 -move		    \n\
	  "RotZoomer (mobile)" 	rotzoomer -root -move			    \n\
	   "RotZoomer (sweep)" 	rotzoomer -root -sweep			    \n\
-				whirlwindwarp -root			    \n\
				whirlygig -root -xamplitude 6 -yamplitude     \
				  6 -trail 1 -explain			    \n\
-				speedmine -root				    \n\
		   "SpeedWorm" 	speedmine -root -worm			    \n\
  Color: 			vermiculate -root			    \n\
				twang -root				    \n\
				apollonian -root -ncolors 255 -delay 298387 \n\
-				euler2d -root				    \n\
-	     "Euler2d (dense)" 	euler2d -root -count 4000 -eulertail 400      \
				  -ncolors 230				    \n\
				juggle -root -count 57 -tail 49		    \n\
  Best: 			polyominoes -root -cycles 1223 -delay	      \
				  36861 -ncolors 255			    \n\
				thornbird -root -cycles 1000 -delay 6536    \n\
				fluidballs -root			    \n\
-				anemone -root				    \n\
				halftone -root -count 51 -spacing 27	      \
				  -sizefactor 2.5402			    \n\
				metaballs -root				    \n\
-				eruption -root -particles 2000 -cooloff 9     \
				  -heat 218 -gravity 1 -delay 18800	      \
				  -cycles 1057				    \n\
				popsquares -root -delay 20000 -ncolors 511  \n\
-				barcode -root				    \n\
				piecewise -root -delay 10909 -count 10	      \
				  -minradius 0.2253 -maxradius 0.3589	    \n\
				cloudlife -root				    \n\
				fontglide -root -page			    \n\
-	"FontGlide (scroller)" 	fontglide -root -program		      \
				  "/home/nrh1/Oo/writer docs/other/caring     \
				  for God's world.rtf"			    \n\
				apple2 -root -slideshow			    \n\
				bubbles -root -broken -3D -trails	    \n\
				pong -root				    \n\
				wormhole -root				    \n\
				pacman -root -size 201			    \n\
				fuzzyflakes -root -arms 8 -thickness 23	      \
				  -bthickness 28 -radius 48 -layers 7	      \
				  -delay 26119 -speed 6 -random-colors	    \n\
				anemotaxis -root -delay 38108 -distance	      \
				  219 -sources 79 -searchers 85		    \n\
-				memscroller -root			    \n\
				substrate -root				    \n\
	 "Substrate (circles)" 	substrate -root -circle-percent 33	    \n\
				intermomentary -root -num-discs 401	      \
				  -draw-delay 10541			    \n\
				interaggregate -root -growth-delay 17027    \n\
				fireworkx -root -noflash		    \n\
				fiberlamp -root				    \n\
				boxfit -root				    \n\
				celtic -root				    \n\
- default-n: 			webcollage -root			    \n\
- default-n:  "WebCollage (whacked)"					      \
				  webcollage -root -filter 'vidwhacker	      \
				  -stdin -stdout'			    \n\
- default-n: 			vidwhacker -root			    \n\
- GL: 				gears -root				    \n\
  GL: 	   "Gears (planetary)" 	gears -root -planetary			    \n\
  GL: 				superquadrics -root			    \n\
  GL: 				morph3d -root				    \n\
  GL: 				cage -root				    \n\
  GL: 				moebius -root				    \n\
  GL: 				stairs -root -delay 0			    \n\
- GL: 				pipes -root -count 0			    \n\
  GL: 				sproingies -root			    \n\
  GL: 				rubik -root				    \n\
  GL: 				atlantis -root -whalespeed 1000 -cycles	      \
				  1000 -size 10000 -count 21 -gradient	    \n\
  GL: 				lament -root				    \n\
  GL: 				bubble3d -root -no-transparent		    \n\
- GL: 				glplanet -root				    \n\
  GL: 				flurry -root -preset psychedelic	    \n\
- GL: 				pulsar -root				    \n\
- GL: 	   "Pulsar (textures)" 	pulsar -root -texture -mipmap		      \
				  -texture_quality -light -fog		    \n\
  GL: 				extrusion -root -delay 26880		    \n\
- GL: 				sierpinski3d -root			    \n\
- GL: 				menger -root -delay 40094 -depth 7	    \n\
- GL: 				gflux -root				    \n\
  GL: 		"GFlux (grab)" 	gflux -root -mode grab			    \n\
  GL: 				stonerview -root			    \n\
- GL: 				starwars -root				    \n\
  GL: 				gltext -root				    \n\
  GL: 	      "GLText (clock)" 	gltext -text "%A%n%d %b %Y%n%r" -root	    \n\
  GL: 				molecule -root -no-labels -no-atoms	      \
				  -molecule "/home/nrh1/protein database      \
				  files/"				    \n\
  GL: 				dangerball -root -delay 50000 -speed 0	    \n\
- GL: 				circuit -root				    \n\
  GL: 				engine -root				    \n\
  GL: 				flipscreen3d -root			    \n\
  GL: 				glsnake -root				    \n\
  GL: 				boxed -root				    \n\
- GL: 				glforestfire -root			    \n\
- GL: 	 "GLForestFire (rain)" 	glforestfire -root -count 0		    \n\
  GL: 				sballs -root				    \n\
  GL: 				cubenetic -root -delay 34701 -count 20	      \
				  -wave-speed 142 -wave-radius 569 -waves     \
				  18					    \n\
  GL: 				spheremonics -root -wander		    \n\
  GL: 				lavalite -root				    \n\
  GL: 				queens -root				    \n\
  GL: 				endgame -root				    \n\
- GL: 				glblur -root				    \n\
- GL: 				atunnel -root				    \n\
  GL: 				flyingtoasters -root -nslices 46	    \n\
  GL: 				bouncingcow -root -count 9		    \n\
  GL: 				jigglypuff -root -spherism 1000 -spooky 9     \
				  -color flowerbox			    \n\
  GL: 				klein -root -speed 234			    \n\
  GL: 	"HyperTorus (striped)" 	hypertorus -root			    \n\
  GL: 	  "HyperTorus (solid)" 	hypertorus -root -solid -transparent	    \n\
  GL: 				glmatrix -root				    \n\
- GL: 				cubestorm -root				    \n\
  GL: 				glknots -root				    \n\
  GL: 				blocktube -root -no-texture		    \n\
- GL: 				flipflop -root				    \n\
- GL: 				antspotlight -root			    \n\
  GL: 				glslideshow -root			    \n\
  GL: 				polytopes -root				    \n\
  GL: 				gleidescope -root			    \n\
  GL: 				mirrorblob -root			    \n\
  GL: "MirrorBlob (color only)" mirrorblob -root -colour -no-texture	    \n\
  GL: 				blinkbox -root				    \n\
  GL: 				noof -root				    \n\
  GL: 				polyhedra -root				    \n\
  GL: 				antinspect -root			    \n\
- GL: 				providence -root			    \n\
  GL: 	"Pinion (large gears)" 	pinion -root				    \n\
- GL: 	"Pinion (small gears)" 	pinion -root -size 0.2 -scroll 0.3	      \
				  -max-rpm 2000				    \n\
  GL: 				boing -root -lighting -smooth		    \n\
  GL: 				carousel -root -no-titles		    \n\
  GL: 				fliptext -root				    \n\
  GL: 				antmaze -root				    \n\
  GL: 				tangram -root				    \n\
  GL: 				crackberg -root -visibility 0.7655	      \
				  -nsubdivs 5 -flat -lit -letterbox	      \
				  -color random				    \n\
  GL: 				glhanoi -root				    \n\
  GL: 				cube21 -root -colormode six		    \n\
- GL: 				timetunnel -root -start 8.1395		      \
				  -changetime 3.4884			    \n\
  GL: 				juggler3d -root				    \n\
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
				cwaves -root				    \n\
				m6502 -root				    \n\
				abstractile -root -tile flat		    \n\
				ant -root				    \n\
  GL: 				hypertorus -root			    \n\
  GL: 				topblock -root -follow -blob -override	    \n\
  GL: 				glschool -root -nfish 500 -delay 10377	      \
				  -avoidfact 0.5189 -matchfact 0.4387	      \
				  -centerfact 0.2736 -targetfact 358 -fog   \n\
  GL: 				glcells -root				    \n\
  GL: 				voronoi -root				    \n\
  GL: 				moebiusgears -root			    \n\
  GL: 				lockward -root				    \n\


pointerPollTime:    0:00:05
pointerHysteresis:  10
windowCreationTimeout:0:00:30
initialDelay:	0:00:00
sgiSaverExtension:  True
xidleExtension:	True
GetViewPortIsFullOfLies:False
procInterrupts:	True
overlayStderr:	True

---

### Post by p_quarles on 2008-09-25
Well, I don't see anything wrong there. 

You're not trying to run it as root, are you?

---

### Post by hollowhead on 2008-09-26
No.

---

### Post by p_quarles on 2008-09-26
> **hollowhead said:**
> No.
All right, then this is kind of puzzling. My next best guesses are that this has to do with either:
1) A bug or configuration error in your X server
2) A bug in your version of Xscreensaver
3) A conflict with something else in your desktop setup. 

I can't help much with 1, but I might be able to help narrow down the problem if you tell me which version of Xscreensaver you run and what desktop environment/window manager you run, and whether or not it's possible you have anything else running that would manage dpms or authentication.

---

### Post by hollowhead on 2008-10-04
Thanks for reply sorry about the delay in mine.  I'm using xscreensaver 5.04 and gnome 2.22.3 metacity 1.2.22.0 compiz 1.0.7.4 and avant 0.31 hardy 8.04 fully up to date.  Ta.

---

### Post by Chito on 2009-01-12
I think I know what your problem is but first. Which screensaver do you have it on? is it "molecule" by any chance. 

I had a problem with the same screensaver, it locks my computer completely, nothing works, the mouse moves, but can't click on nothing, and the keyboards locks too. and after so many tries and so many commands, there is a simple way to stop it. You might loose some screensaver and maybe some cool pictures that come with it, but is worth it. Follow the steps. 

I have Ubuntu 8.10 and it work for me, try it:

SYSTEM>ADMINISTRATION>SYNAPTIC PACKAGE MANAGER> "look for the search box and type"xscreensaver" then look for the xscreensaver files that are mark with a different color box, those are the packages you have, click on all the boxes you have in your system. A mssg box would appear "Click on "To be remove" and then press "APPLY" 

The package will be removed. and your problem will stop. 

You can reinstall it if you want to, by following the same steps.

Good Luck.

---

### Post by altavatar on 2011-05-03
I've been experiencing the same issue.

My environment:

Debian Wheezy
XFCE 4.8
xscreensaver 5.11-1+b1

It *is* really annoying. Any help would be appreciated. Thx.

---

