---
title: "FlightGear  How do I load other planes?"
date: 2007-04-09
forum: Gaming &amp; Leisure
---

### Post by Dan_472 on 2007-04-09
Hello

I'm loving FlightGear, but so far I only see the Cessna available to fly.   In usr/share/games/FlightGear/Aircraft there are other aircraft,  how do I load them?

Thank You

---

### Post by PurplePenguin on 2007-04-09
I think you can do it via the command line... flightgear's got a good site with a lot of [documentation]("http://www.flightgear.org/docs.html"), you'll be able to find it there.

EDIT: Here are some command line options you can use.
    *  --aircraft=name of aircraft definition file  Example: --aircraft=c310. For possible choices check the directory /FlightGear/Aircraft. Do not include the extension &#8221;-set.xml&#8221;  into the aircraft name but use the remaining beginning of the respective file names for choosing an aircraft. This way flight model, panel etc&#551;re all loaded in a consistent way. For a full list, see Sec. 3.7 below.
    * --show-aircraft: Print a sorted list of the currently available aircraft types.

---

### Post by Eddison on 2010-10-24
Thanks for that guys- worked for me.
Just go to applications then accessories and open up 'terminal'
Then type in;
fgfs --aircraft=CitationX

Program will then load a citation for you. Be sure to use capital letters if you see them.
To see what other aircraft FlightGear has open the flightgear folder. click on computer then 'file system' then usr, then share then the folder games, then flightgear and finally-aircraft. Open the aircraft folder and you can see the different aircraft available. Type;
 fgfs --aircraft=
Then type the name of one of the folders there. For some reason, 777-200 did not work for me.

Eddison

---

### Post by Quadunit404 on 2010-10-24
There's also fgo. You can find it [here.]("http://www.flightgear.org/forums/viewtopic.php?f=6&t=6279&st=0&sk=t&sd=a&hilit=FGo") It's what I use for launching FlightGear. I think it was more or less designed for launching locally-installed copies of FlightGear (e.g. FlightGear Git compiles through download_and_compile.sh) though but I haven't tried that out.

---

### Post by Eddison on 2010-10-24
Nice- thanks for that.
Have you checked out OpenBVE? its a train sim, sounds dull and deadly boring but whats good about it is the level of detail in it- the sheer dedication that went into that sim is worth looking at.

eddison

---

