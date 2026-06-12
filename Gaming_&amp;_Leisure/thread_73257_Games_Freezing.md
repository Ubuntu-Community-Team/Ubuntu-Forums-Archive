---
title: "Games Freezing?"
date: 2005-10-08
forum: Gaming &amp; Leisure
---

### Post by arcanistherogue on 2005-10-08
Hey.  I run all my games through a Failsafe terminal, and I am using Ubuntu 5.04 with kubuntu-desktop (though I don't think it matters with a failsafe terminal).  I like using the failsafe terminal as it usually fixes all my sound errors and whatnot :) 

Anyway, so my computer is as follows:

-AMD Athlon 64 3000+
-A-Open 256 MB nVidia 6600 (AGP 8x)
-512 MB RAM
-500 W PSU

I don't think anything else matters, ask if you need anymore info.  I am running most of these games without CD's (UT2004 with latest patch, steam games). 

So, I run my games.  Games like Quake 2 run fine with occaisonal freezing if I play for about 1-3 hours, and Quake 3 Demo (ran through cedega, couldn't figure out how to install Linux native demo) sometimes freezes after about 20 minutes of play.  CS:S  freezes anyware past 10 minutes of playing, sometimes I can get a good hour in before it does.  UT2004 freezes after anwhere from 10 minutes onward, but usually later on (20 imnutes in).  The oddest part is that the Doom III demo doesn't crash at all.  I run it at 800 x 600 with Medium Detail and it hasn't crashed once.  Most other games I run in 1280 x 1024 (UT2004, some steam gaems) or 800 x 600 with 2x AA (source games).

now, when it crashes, it just freezes.  The sound stutters for about 1 second, and when I hit NumLock or CapsLock the lights don't go on or off on my keyboard.  I can't move my mouse or do Ctrl-Alt-Backspace.  I have the latest drivers installed, and I average about 4000 FPS in GLXGears, which I have already been told by many people is odd for my card.

Now, people from GameFAQs who have tried to help me think it is just bad parts.  People on linux IRC channels think it is overheating.  The problem doesn't happen as frequently on Windows, but it still happens nonetheless.  However, I put a fan on an old nic card and used a dremel tool to cut a hole in it and remove the pins, and put that near my video card.  It doesn't freeze as quickly as it did months before because of this, but as i said earlier it still freezes enough to make games not enjoyable. 

I am thinking about investing in one of those spiffy Zalman heatsinks with the big flower thing and the copper fins.  Before I dish out 30 bucks for this, is this definantly heating, and will this help my computer at all?  Here is a picture of my current card with heatsink:  [http://www.newegg.com/Product/Product.asp?Item=N82E16814135164](http://www.newegg.com/Product/Product.asp?Item=N82E16814135164)

Does anyone think there are any other things that could be contributing to the freezing?

---

### Post by Dennis Laumen on 2005-10-08
If it happens in Windows as well you can bet it's a hardware problem.

The reason it probably happens a little less in Windows is probably because the games need more resources because of the emulation. This is just a wild guess though.

If you built the computer yourself you should think of a better cooling solution. The Zalmans are great I have one of those flowery thingies on my processor and my video card (and a Zalman heatsink on my northbridge ;)), the only problem with them is, is that they are a little pricey. If you can spare the money you should really buy them (it not only cools your card but will also silence it!).

If the system is prebuilt you should return to the vendor because they apparently built a case with terrible cooling which is something they should have tested.

Anyway, good luck with it and let us know what you will do.

---

### Post by duan on 2005-10-08
Man Its no use if the video card and cpu is freezing cold but the voltage regulatros and the bits without fans are dying. 

I have an asus mobo that acted up like this recently, but at my previous job we had epox mobos blow after only 6 months duty by the dozens. Bad parts on the voltage regulators used on the board and just plain cheap hardware. One friend of mine there started replacing blown caps and regulator ICs on the boards and they are working great again!

I rebuilt my whole pc in another box with the chassis fan and the PSU fan blowing over the mobo and all out one big hole on the back(works great and I play this vegastrike game for hours ....) I could adjust the psu fan speed and boosted it a bit until all air coming out is fairly cool. The box is posted in the gallery of this forums under misc linux art (the barbarian pc). It was also done with a dremel tool so maybe it is a recommended accesory for linux?

This is just the sorry state with cheap mobos with NO design going into cooling the system as a whole. 

good luck

---

### Post by arcanistherogue on 2005-10-08
Interesting.  I have an Asus K8N-e mobo, and I built the computer myself in March.  It has been running fine Until I reformatted in July to make more room for linux and less for windows.  Up until then I had 65 GB windows and 15 GB linux, but I made it 40 GB and 40 GB.  Now I have a seperate 40 GB for windows and an 80 GB for linux.

The games work nicely on windows, but they still freeze.  However, 3 things I do that make the freezing less frequent make me think Its a cooling problem.  

1)  I moved the pc up a bit.  The back used to be about 4 inches from a wall, now it is about 8 inches.  There are 3 fan ports on the back. 

2) I have my air conditioner on.

3) I added that fan card I mentioned in my first post.

This would make it seem like it is just overheating, right?  I have both stock coolers on my CPU and my Video card.

Here are some pictures of my computer, taken in June: 
[http://photobucket.com/albums/y196/arcanistherogue/?action=view&current=HPIM2081.jpg](http://photobucket.com/albums/y196/arcanistherogue/?action=view&current=HPIM2081.jpg)

As you see, there is only one hard drive in there at the time.  Now I have 3 (1 older 17 GB for backing up stuff).  I have that fan right over my graphics card, and I added a fan card right underneath it.  About 1 week ago I rerouted all of the cables to try to make airflow better, and I removed my LED cathode tube (the blue thing hanging vertically in the case).  I moved all the books and crap to the left of the case somewhere else too, and The computer has been moved up from its position (hard to see in this picture, you cant see the depth of the wall).  Also, that paper looking thing in the bottom of my case is just a decal with a diagram of my mobo on it I put in.

Yeah, as you can see I only have stock coolers.  It will probably solve my problems if I get the Zalmans, no?  And should I get a northbridge  cooler?  I have the one that comes with the K8N-e, its just a blue heatsink with an ASUS logo.

---

### Post by duan on 2005-10-08
My pc was also a big box like that until it became this[http://ubuntuforums.org/gallery/showimage.php?i=1044&c=4]("http://ubuntuforums.org/gallery/showimage.php?i=1044&c=4")

I did buy a noiseless fan kit which was basically just better fans(PSU with controllable fan, copper heatsink for CPU and big chassis fan) the chassis fan can now be monitored like the cpu fan. I think the new fans work better. 

But it was not an expensive rig. I placed all the drives in the bottom of the box with a piece of mdf board in between them and the top part where the mobo is - that isolates the heat from the drives so it doesn't bother the mbo so much. Now the cpu fan, the chassis fan and psu fan all draw air from the top (lid of my cheap plastic box) and blows it out the hole in the back where the motherboard sticks out because the mobo is bigger than the box, so the draft is over the board, but i have no expansion cards so the board is flat and easier to cool (but my graphics are poor....)

There is nothing blowing air onto the middle of you board and thats where the regulators sit (these IC's are the ones contolling ALL the current going to your CPU and supporting chips what 70 amps nowadays!, and they have NO heatsinks)

I still think my pc is uglier. :-)

---

