---
title: "My Flightgear doesn't look nearly this good"
date: 2011-01-17
forum: Gaming &amp; Leisure
---

### Post by Newbie2910 on 2011-01-17
Just installed Flightgear and have been having lots of fun with it.

Running on Ubuntu 10.04, with 3GB of ram, on a Dell Inspiron (2 years old).

When I run the game, my graphics don't look anything like this:
[http://forums.flightsim.com/vbfs/attachment.php?attachmentid=50843&stc=1&d=1260172646](http://forums.flightsim.com/vbfs/attachment.php?attachmentid=50843&stc=1&d=1260172646)

Mine look more like a 1995 version of Flight Simulator.

So, is my issue my laptop's video card or something else?

Thanks in advance.

---

### Post by mastablasta on 2011-01-18
what card do you have? ATI?
 
If so you need to do some tweaking, before the full graphics are shown...

---

### Post by mips on 2011-01-18
Did you download the additional planes & world scenery?
If you didn't it's going to look a bit bland/old.

[http://www.flightgear.org/Downloads/scenery.html](http://www.flightgear.org/Downloads/scenery.html)
[http://www.flightgear.org/Downloads/aircraft-2.0.0/](http://www.flightgear.org/Downloads/aircraft-2.0.0/)

---

### Post by mips on 2011-01-18
Double post.

---

### Post by ubudog on 2011-01-18
Are you sure you have the latest version (2.0)?  If you do, try the development version.  There are some improvements there.  And it could just be your graphics card.  :(

---

### Post by Newbie2910 on 2011-01-18
I have a Dell Inspiron laptop, about a year and a half old.  Here's the info on the driver:

me@Lee:~$ sudo lshw -C video
[sudo] password for me: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:f6c00000-f6ffffff memory:e0000000-efffffff(prefetchable) ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff

Also, the Package Manager shows I have version 1.9.1.  If there was a newer version, wouldn't package manager automatically install it?  Sorry, I'm pretty new to Ubuntu.

Oh, and I downloaded and am using the Lockheed Constellation 1049.

My command line is:
fgfs --aircraft=Lockheed1049 --geometry=1280x800

Here's a screenshot of mine, in approximately the same shot:
[IMG]http://i302.photobucket.com/albums/nn102/csa_forever_2008/1049/1049.png[/IMG]

---

### Post by ubudog on 2011-01-19
Ah, it appears you don't have the latest version.  You can get it here:

[http://www.playdeb.net/updates/ubuntu/10.10/?q=FlightGear](http://www.playdeb.net/updates/ubuntu/10.10/?q=FlightGear)

The instructions are pretty straitforward, but make sure you uninstall the old version before starting.  Good luck!  

Also, those graphics could just be that plane.  Have you tried any others?

---

### Post by mastablasta on 2011-01-19
also don't expect a lot from Intel Graphics chip :-)

---

### Post by Newbie2910 on 2011-01-19
Tried to install 2.0 but I get this:

Can not install 'flightgear' (E:Unable to correct problems, you have held broken packages.) 

This is after the installer loads ok and I download the 2.0 Flightgear.  It asks me if I want to install it and of course I answer yes.

Ugh. thought?

So then I updated the flightgear base.  Worked ok.  But when I try to install Flightgear (again using Synaptic Package Manager) I get this error:
flightgear:
 Depends: libopenscenegraph65 (>=2.8.3) but it is not installable
 Depends: libopenthreads13 (>=2.8.3) but it is not installable
 Depends: simgear2.0.0 but it is not going to be installed

---

### Post by Quadunit404 on 2011-01-19
That looks like Microsoft Flight Simulator X in DX10 mode with some custom AI traffic, scenery and a payware Connie to me. I have a hella powerful PC and to me FlightGear looks like this:

[[IMG]http://i563.photobucket.com/albums/ss76/Quadunit404/th_Tu-154KaiTak.png[/IMG]](http://i563.photobucket.com/albums/ss76/Quadunit404/Tu-154KaiTak.png)

(That's a clickable thumbnail btw, and that blue thing isn't normally there, Shutter was just being a bitch on me when I took that screenshot.)

---

### Post by ubudog on 2011-01-19
> **Quadunit404 said:**
> That looks like Microsoft Flight Simulator X in DX10 mode with some custom AI traffic, scenery and a payware Connie to me. I have a hella powerful PC and to me FlightGear looks like this:

[[IMG]http://i563.photobucket.com/albums/ss76/Quadunit404/th_Tu-154KaiTak.png[/IMG]](http://i563.photobucket.com/albums/ss76/Quadunit404/Tu-154KaiTak.png)

(That's a clickable thumbnail btw, and that blue thing isn't normally there, Shutter was just being a bitch on me when I took that screenshot.)

Hmm, I also have a hella of a powerful laptop, but FlightGear looks way better.  I will try to get a screenshot soon.

---

### Post by Quadunit404 on 2011-01-20
Oh, I forgot I had turned down the shaders from 5 to 3 due to lag (FlightGear tends to drop to around ~12 - 15FPS when I go near buildings) so that probably wasn't a good example :lol: I'll get a better screenshot soon.

---

### Post by Quadunit404 on 2011-01-20
Dah, double post.

---

### Post by ubudog on 2011-01-20
Ok cool.

---

### Post by Quadunit404 on 2011-01-20
I won't likely have school tomorrow due to the incoming snow so I'll update my FlightGear Git installation and take a screenshot somewhere that won't cause me to drop below ~20FPS.

---

### Post by ubudog on 2011-01-20
Cool.  That's what I love to do on snowdays... mess around in FG's code...  :-)

---

### Post by Quadunit404 on 2011-01-21
Well everything but fgdata updated... damn Git won't let me update it because I changed preferences.xml #-o

Looks like I'll have to delete fgdata (AFTER backing up important things like scenery and aircraft!) and get it from Git again :|

---

### Post by ubudog on 2011-01-21
> **Quadunit404 said:**
> Well everything but fgdata updated... damn Git won't let me update it because I changed preferences.xml #-o

Looks like I'll have to delete fgdata (AFTER backing up important things like scenery and aircraft!) and get it from Git again :|

Huh.  Ouch.  :(

---

### Post by Quadunit404 on 2011-01-22
Suddenly, I remembered that I just had one custom plane (that Tu-154B in that screenshot) which I already had backed up and all the scenery was obtained through fgrun :lol: so I can just get it back if I wanted.

I'll just update the whole thing to the latest Git because last time I updated everything individually I broke several things involving FlightGear and had to reinstall it.

---

### Post by Newbie2910 on 2011-01-22
I was able to get version 2.0 loaded today.  I had to add the software repository getdeb games to my system; then the 2.0 upgrade went flawlessly.

The scenery is a lot better, and the Connie looks a little nicer.  I am guessing that (as I am using a laptop and can't upgrade the video card) there's not much more I can do.  (Now if only we could get the engine flames :-)

[IMG]http://i302.photobucket.com/albums/nn102/csa_forever_2008/1049/Screenshot-UntitledWindow.png[/IMG]

---

### Post by ubudog on 2011-01-22
That's way better, lol.

Glad you got 2.0 installed good.  

You should try out some other planes too.  FG has some great ones.

---

### Post by Quadunit404 on 2011-01-23
I don't believe engine flames have been modeled into the Connie JUST yet. I still don't know how to enable the Turbochargers.

And, if you think that FlightGear 2.0 looks good, just wait until you see what will become FlightGear 2.2.0 at max :wink: (which I unfortunately have to rebuild the entire thing because something screwed up while compiling and FlightGear wouldn't start :|)

PS: If you want another good plane, look at the Tu-154B by [s]Project Tupolev[/s] Yurik Nikiforoff (aka yurik_nsk) or maybe [this Il-114]("http://translate.google.com/translate?hl=en&sl=auto&tl=en&u=http%3A%2F%2Fwww.flightgear.ru%2Fforum%2Fviewtopic.php%3Ff%3D9%26t%3D422%26start%3D0") when it's released. That cockpit makes me drool in awe...

---

### Post by Newbie2910 on 2011-01-23
This version seems more realistic flying, too.  For instance if I don't put the flaps down, it just isn't gonna take off, no matter what.

---

### Post by ubudog on 2011-01-23
Anyone know when FG 2.2 will come out?  Can't wait.  :p:p

---

### Post by Quadunit404 on 2011-01-23
I'm a member of the FlightGear forums and to be honest... we don't really know.

It's up to Curtis Olson (known as curt around the forums) when to release it because, well, he's the project lead :P

---

### Post by ubudog on 2011-01-23
> **Quadunit404 said:**
> I'm a member of the FlightGear forums and to be honest... we don't really know.

It's up to Curtis Olson (known as curt around the forums) when to release it because, well, he's the project lead :P

I'm a member too!

I suppose he will inform us...

---

### Post by Quadunit404 on 2011-01-24
Okay, I finally managed to get FlightGear rebuilt (turns out it was a change in the OpenSceneGraph API that the FlightGear developers have yet to embrace which led to compilation and installation errors regarding SimGear) and managed to grab a few screenshots around the KSFO-KOAK area (aka the San Francisco Bay.) Those water shaders are AMAZING compared to FlightGear 2.0!

If you want to see them, check the attached. The last one is someone I did not see on the Oakland runway and nearly collided with, even with reverse thrust on max :shock: fortunately he rotated before we hit each other.

---

### Post by mips on 2011-01-25
Quadunit404,

That looks really good ;)

---

### Post by ubudog on 2011-01-25
Kinda out of topic, I recommend installing FGrun, the FlightGear Launcher.  Since it is hard to install, I have made a script for people new to Linux.  

Hopefully this helps you.  (assuming you want to install fgrun)

[http://ubuntuforums.org/showthread.php?t=1672490](http://ubuntuforums.org/showthread.php?t=1672490)

---

### Post by Quadunit404 on 2011-01-26
Again off topic, but there's also [Fgo!]("http://sites.google.com/site/erobosprojects/flightgear/add-ons/fgo") (that's the actual name of the app!)

I like it better than fgrun as it's lighter on system resources and, therefore, higher frame rates in FlightGear :D

PS: mips, thank you :D

---

### Post by ubudog on 2011-01-27
> **Quadunit404 said:**
> Again off topic, but there's also [Fgo!]("http://sites.google.com/site/erobosprojects/flightgear/add-ons/fgo") (that's the actual name of the app!)

I like it better than fgrun as it's lighter on system resources and, therefore, higher frame rates in FlightGear :D

PS: mips, thank you :D

Cool.  I'll try to make an install script for that too... or do they already have one?

---

### Post by Quadunit404 on 2011-01-27
1. Install the dependencies (which are listed in the README in the Docs folder)
2. Mark the fgo file in the main directory as executable
3. Double click fgo and run it in a terminal, then let it create the .fgo directory (should be done automatically)
4. Done, no need for an installation script :wink:

---

### Post by Newbie2910 on 2011-01-27
Wow, I just loaded an alternate version of the Constellation.. what a huge difference.

---

### Post by ubudog on 2011-01-28
That's pretty sweet.  Where did you get it from?  I would like to try it out.  :P

---

### Post by Quadunit404 on 2011-01-28
I already linked to it.

---

### Post by alaukikyo on 2011-01-29
> **Quadunit404 said:**
> 1. Install the dependencies (which are listed in the README in the Docs folder)
2. Mark the fgo file in the main directory as executable
3. Double click fgo and run it in a terminal, then let it create the .fgo directory (should be done automatically)
4. Done, no need for an installation script :wink:

no need to run it in the terminal if its a gui app.

---

### Post by Quadunit404 on 2011-01-29
> **alaukikyo said:**
> no need to run it in the terminal if its a gui app.

It's because FlightGear does not natively have its own window for console output. Even on Windows it uses the Command Prompt for output.

---

### Post by Newbie2910 on 2011-01-29
What's funny is now I actually have to learn how to start the engines on this thing and other tasks before I can fly it.  The less-detailed aircraft you can just hit 9 to throttle up and they'll take off.  Not the 1049!  But that's ok I am eager to learn.

---

### Post by ubudog on 2011-01-29
> **Newbie2910 said:**
> What's funny is now I actually have to learn how to start the engines on this thing and other tasks before I can fly it.  The less-detailed aircraft you can just hit 9 to throttle up and they'll take off.  Not the 1049!  But that's ok I am eager to learn.

Yeah it's fun to learn.

---

### Post by Quadunit404 on 2011-01-29
How to start up the L-1049 Super Connie in 12 easy steps!

1. Right click twice so you can look around. Look up. Right click once and set all four of those things that say "MAGNETOS" to "BOTH"
2. Make sure you have the Flight Engineer view enabled (I forget how it's done in FlightGear 2.0, sorry :|) and switch over to it
3. Start the ship and cart batteries.
4. Flip up all the switches above that.
5. If they aren't already maxed out, set the mixture to max. This can be done with m/M (as in, m and Shift-M)
6. Look down at the dial with 1 2 3 4 around it.
7. Select one of those numbers and hit S
8. Repeat steps 6 and 7 until all four engines are started.
9. Shut down all the generators and ship batteries.
10. Release the brakes (Ctrl-B)
11. ???
12. PROFIT!

---

### Post by ubudog on 2011-01-31
Thanks!  That will be helpful.  :p

---

### Post by mips on 2011-02-24
> **Quadunit404 said:**
> Okay, I finally managed to get FlightGear rebuilt (turns out it was a change in the OpenSceneGraph API that the FlightGear developers have yet to embrace which led to compilation and installation errors regarding SimGear) and managed to grab a few screenshots around the KSFO-KOAK area (aka the San Francisco Bay.) Those water shaders are AMAZING compared to FlightGear 2.0!

If you want to see them, check the attached. The last one is someone I did not see on the Oakland runway and nearly collided with, even with reverse thrust on max :shock: fortunately he rotated before we hit each other.

Which version are you running?

PlayDeb has Version: 2.0.0-1~getdeb3

Is this version up to date with fixes or do I have to build my own?

Got a guide for what you did?

---

### Post by ubudog on 2011-02-25
> **mips said:**
> Which version are you running?

PlayDeb has Version: 2.0.0-1~getdeb3

Is this version up to date with fixes or do I have to build my own?

Got a guide for what you did?

I believe the PlayDeb version is the latest (stable) version.

---

