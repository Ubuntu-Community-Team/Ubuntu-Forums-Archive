---
title: "FlightGear 1.9.1's F-14b Tomcat"
date: 2012-07-04
forum: Gaming &amp; Leisure
---

### Post by Johnny M! on 2012-07-04
Howdy Free FlightGear Flyers,

Me Stuff:
Ubuntu 10.04
FlightGear 1.9.1-1

My Version of FlightGear includes a very Nice F-14b Tomcat (Tom Cruise not Included - if he was I'd make him sit in the Back); and Yes - I've read the README.help text file included.

My Question:  Can you (and if so how) sweep the Wings Aft (for Low Drag Hi-Speed) and back again Forward (for more Lift - Slow Speed TO & Land).   In the nice looking 3D Cockpit - I see the Wing-sweep Gauge - but NO Wing-sweep Contol Lever.

My guess is: There is NO Wing-Sweep in this Model.  A Shame - but still a super nice legendary Navy Fighter (for Free).

Any Confirmation out There?
Thanks in Advance !

BVR
Johnny M!

PS:  I've also noticed that additional Down-Loaded (Free FlightGear) Aircraft 
[http://www.flightgear.org/download/aircraft-v2-6/](http://www.flightgear.org/download/aircraft-v2-6/)
for newer versions of FlighGear 2.0, 2.4, 2.6 are not compatible (do NOT Work)
with my older version of FlightGear (1.9.1-1).
But that is the Default Version of FlighGear loaded by Ubuntu 10.04.
Hoping the Software Install Tool would link to a newer version of FlightGear.
My Guess is that by best bet is to go Ubuntu 12.04 (but I like 10.04!).

---

### Post by Sealbhach on 2012-07-05
As far as I can tell, the wings sweep back automatically once you reach high speeds. You can get a newer version of Flightgear from the Playdeb website.

.

---

### Post by Johnny M! on 2012-07-05
Hey [Sealbhach]("http://ubuntuforums.org/member.php?u=562588") 
Thank You for the Info !!!
:guitar:


I did a little research and did a little closer observation:

- You are correct (I had forgotten) that the F-14 Variable Geometry Wings are Automatically controlled based on airspeed and alpha I guess; unlike the F-111 that uses manually controlled Pilot commands to sweep the wings.

- F-14b Wing Sweep Range at Forward Setting (20 degree aft) and at most Rearward setting (68 degrees aft).

- Looking closely at FlightGear's F-14b, the Wings do Sweep, but rather in-perceivably slow - at 600KIAS the wings look like they have swept about 15 degrees back from their forward setting.    

- I'd like to see if the Wings would sweep further aft at Higher Speeds; but the default Fuel Load is only 1,900 pounds - that's only about 1,5 minutes of Flight Time in Full Afterburner.  So after I accelerate to about 600KIAS - I flame-out.

*** Anyone know how to load more JP-5 ??


About the new versions of FlightGear at:
[http://www.playdeb.net/software/FlightGear](http://www.playdeb.net/software/FlightGear)

I'm sort of a Rookie with Ubuntu - if Ubuntu Software Center or the Synaptic Package Manager would pull a new Version (of FlightGear)  in for me, I could manage; but using purely "Terminal" Command Line commands to extract and install deb packages has me spooked.   I've seen FlightGear Forum feedback that Command Line install are challenging for novices like myself.

No Guts - No Glory
I might try just for the FUN of it.
What the Hell - Wish me Well !


BVR
Johnny M!

PS: Need some :lolflag:

---

### Post by Johnny M! on 2012-07-05
[COLOR=Blue][B]Next Update in my Tomcat Saga
=======================[/B][/COLOR]

[COLOR=Purple]**Fuel Load and Wing Sweep:**[/COLOR]

Figured out how to add more Fuel:  Equipment - Fuel & Payload
Why default Fuel <2,000lb; don't know ?

Set Fuel at 6,000lb - lit the Burners - and hoped the "Blessed Lady of Acceleration" wouldn't fail me.

She didn't - the F-14b accelerated to Super (about 500 ft AGL and 800 KIAS) and the Wings did Sweep FULL AFT !!!!!

Then I picked up some oscillations, and the Right Wing separated from the formation (yeah - the Right Wing fell off).   Uncontrollable Right Roll into the Drink - end of that Mission.


**[COLOR=Purple]Upgrade to a Newer Version of FlightGear:[/COLOR]**

[COLOR=Black]Over at:
[http://www.playdeb.net/software/FlightGear](http://www.playdeb.net/software/FlightGear)[/COLOR]

it shows that for Ubuntu 10.04 they have FlightGear version 2.0.0-1 available (and compatible) via the "apturl" Install method.    My older version is FlightGear 1.9.1-1.  So I clicked - YES, go ahead and Install.    At the end of the Install process, it says I already have FlightGear installed and the new version install is Terminated.  Checking Synaptic Package Manager - FlightGear is still the older version.

Do I need to uninstall 1.9.1-1 before Ubuntu 10.04 will accept the  Newer (2.0.0=-1) Version??????


Any Help Appreciated !

BVR
Johnny M!
):P

---

### Post by Sealbhach on 2012-07-06
Hmmm, it shouldn't matter if you already have Flightgear installed. Just make sure you have the playdeb package installed from here:

[http://www.playdeb.net/updates/Ubuntu/11.10](http://www.playdeb.net/updates/Ubuntu/11.10)

then run sudo apt-get update to refresh your software list, then install flightgear using Synaptic.

.

---

### Post by Johnny M! on 2012-07-07
Thanks Sealbhach !

Got your Link:  [http://www.playdeb.net/updates/Ubuntu/11.10](http://www.playdeb.net/updates/Ubuntu/11.10)
and
Found this One: [http://www.andrewferrier.com/blog/2011/08/17/compiling-flightgear-2-4-0-for-ubuntu-10-04/](http://www.andrewferrier.com/blog/2011/08/17/compiling-flightgear-2-4-0-for-ubuntu-10-04/)

I've wrestled (now for a few hours) with my Ubuntu 10.04 Install to upgrade my natively installed FlightGear 1.9.1-1 to FlightGear Version 2+;
but no Luck  - Just Frustration.

I've tried Upgrading via:
- Synaptic Package Manager
- Ubuntu Software Center
- apturl - [http://www.playdeb.net/software/FlightGear](http://www.playdeb.net/software/FlightGear)
- Terminal (with my limited Command Line Skills)

Here are some of the Install Errors related to upgrading in Package Manager:
(See attached Screenshot Picture)
Package Manager Errors:

flightgear:
 Depends: libopenscenegraph80  but it is not installable
  Depends: libstdc++6 (>=4.6) but 4.4.3-4ubuntu5.1 is to be installed
 Depends: simgear2.6.0 but it is not going to be installed

simgear2.6.0:
  Depends: libjpeg62 (>=6b1) but 6b-15ubuntu1 is to be installed
 Depends: libopenscenegraph80  but it is not installable
  Depends: libstdc++6 (>=4.6) but 4.4.3-4ubuntu5.1 is to be installed

simgear2.4.0:
  Depends: libjpeg62 (>=6b1) but 6b-15ubuntu1 is to be installed
 Depends: libopenscenegraph80  but it is not installable
  Depends: libstdc++6 (>=4.6) but 4.4.3-4ubuntu5.1 is to be installed

Needs all this Stuff (and More):

6b-15ubuntu1
libopenscenegraph80    
  Needs:  libavcodec53    
  Needs:  libavutil51
  Needs: multiarch-support
  Needs: libc6
4.4.3-4ubuntu5.1

???????????????????????????

========================================

Seems like there are multiple upon multiple dependencies that I'm missing; I spent an hour on: [http://packages.debian.org](http://packages.debian.org) just chasing one missing Package after another - with no end in Sight
Suspect my System is telling me:
[I][B][COLOR=Purple]
If you want a Newer Version of FlightGear .....
.... Upgrade to a Newer Version of Ubuntu !!!!!!!!!![/COLOR][/B][/I]

Back to FlightGear 1.9.1-1
I do Love my F-14b Tomcat

BVR
Johnny M!

---

### Post by Johnny M! on 2012-07-07
The Saga Continues:

After excruciating attempts to upgrade FlightGear; my Ubuntu 10.04 Build got FlightGear and it's Components so corrupted that I had to do an entire (Acronis TrueImage Home) Image recovery of my entire Ubuntu Partition to regain functionality with FlightGear.

It shouldn't be this hard;
But it is !

I'm going to stick with FlightGear 1.9.1-1.  I discovered that FlightGear 2.0 Aircraft here:
[http://flightgear.org/legacy-Downloads/aircraft-2.0.0/](http://flightgear.org/legacy-Downloads/aircraft-2.0.0/)
seem to be compatible with my Install.
Lots of Cool Aerospace Vehicles to choose from.

I'll worry about upgrading FlightGear when I go Ubuntu 12/13 !

BVR
Johnny M!

PS: Gotta go Fly X-Plane 9 or 10 now.  See you in the Air !):P

---

