---
title: "What Am I doing Wrong?"
date: 2009-03-09
forum: General Help
---

### Post by Maxx730 on 2009-03-09
I installed the drivers for an ATI Radeon x1300. I put the new graphics card into my computer and this is what happens.

[http://www.Maxx730Designs.com/thenew/0002.ogg](http://www.Maxx730Designs.com/thenew/0002.ogg)

---

### Post by SuperSonic4 on 2009-03-09
No idea, can you summarise for anyone who's connection is not fast enough to load that video quickly?

---

### Post by Maxx730 on 2009-03-09
Basically, I have a eMachine with a
 1.6Ghz Processor
630mb of RAM

I had a 32mb graphics card in it originally, so I bought a new one to stop the lag and so I could use compiz. I download the .run file driver from the ATI site and ran it. It installed and two programs showed up on my main menu. 

ATI Catalyst Control Center
ATI Catalyst Control Center(Super User)

I tried putting the Card into the computer but nothing (not even the emachine turning on screen) shows up except for a bunch of Squigly lines all over the screen.

---

### Post by Neo_The_User on 2009-03-09
Dude..... TURN YOUR LCD OFF BEFORE IT BURNS! That's a really bad sign when that shows up. It will overheat and break. If you smell burning plastic, you're hosed.

---

### Post by Maxx730 on 2009-03-09
Do you know why its doing that?

---

### Post by Therion on 2009-03-09
Let me see if I follow all this correctly.

You had Ubuntu installed on your PC and were having problems with the video (this with the 32MB video card) so you replaced the video card with the ATI X1300, downloaded and installed the ATI driver, rebooted and... BAM:  Borkage.  

Correct?

---

### Post by Maxx730 on 2009-03-09
Exactly,

But if I put the 32mb Graphics card back in, it boots fine. It only boots like that when I have the 256mb in, I checked with the Geek Squad to see if it was that the graphics card wasnt getting enough power from my computer but they said it was fine and it should run.

---

### Post by kelvin spratt on 2009-03-09
was the new card an ATI  is it a PCi or VGA motherboard you are fitting it to.
Was the old card a built in card if it was you need to change the bios settings to use your new card.
Please post more details to get help

---

### Post by Therion on 2009-03-09
> **Maxx730 said:**
> Exactly,

But if I put the 32mb Graphics card back in, it boots fine. It only boots like that when I have the 256mb in, I checked with the Geek Squad to see if it was that the graphics card wasnt getting enough power from my computer but they said it was fine and it should run.
Roger that.  

Okay, so, first of all, the 32MB card you removed, it's a physical card then that occupied an AGP or PCI slot?  We're not discussing an integrated graphics chipset, correct?

And is this 32MB card also an ATI card?  

Methinks you have some serious video-driver vs. xorg.conf borkage going on here.

---

### Post by Maxx730 on 2009-03-09
The 32mb Card I removed is not built in.

The slot for the Video card and the ATI Radeon I got is an AGP slot.

---

### Post by joey-elijah on 2009-03-09
This does sound a bit like it's not getting enough power from the PSU tbh...

What is your PSU Wattage?

A 256MB card shouldn't be demanding the earth, but if the PSU is quite a low wattage there's just not enough draw to go around.

---

### Post by Maxx730 on 2009-03-09
Where should I look to find out how many watts the PC is putting out?

---

### Post by bailbath on 2009-03-09
What happens if you use the rescue option in your grub menu?
Have you tried Xfix from the rescue menu?
Ian

---

### Post by joey-elijah on 2009-03-09
Ahh.. that depends on how accessible your PSU is. It is normally written on a sticker on one of the sides. Somewhere there will be a code with something similar to XXDX500. The 500 means, in most cases, that's a 500W supply - & so forth. 

Otherwise there will be another sticker with heaps more detail which should give it. 

Just to check - did your new Graphics Card come with a box? Does it list a minimum PSU 'watt'? ARe there any connectors with the GFXC that need to be connected to the PSU? They tend to look like flat rectangles with three holes in.

From the software side, Have you tried booting with a liveCD?

I can imagine this is pretty dissapointing after getting a new card but, hopefully, it's a software issue (free to fix!). if not new PSU's can be picked up very cheaply online.

---

### Post by Therion on 2009-03-09
> **joey-elijah said:**
> Ahh.. that depends on how accessible your PSU is. It is normally written on a sticker on one of the sides. Somewhere there will be a code with something similar to XXDX500. The 500 means, in most cases, that's a 500W supply - & so forth.
It's an X1300 we're talking about here.  It's no 4870 and I assure you the AGP bus is putting out plenty of juice.

No, the issue here is the config.  You need to reconfigure X by running Xfix as directed above.  Or at least start there.

---

### Post by Maxx730 on 2009-03-09
I'll check when I get home about the watts.

I bought it off of ebay so it did not come with any stickers.  I checked with a computer specialist and he said there are not any plugs on it for extra power. 

And even if I cant get it fixed, thanks guys
I love Linux and this just makes it beter because I know the people who use linux are very helpfull.

---

### Post by Maxx730 on 2009-03-09
On the back of the computer it says 240v near the plug, im guessing that means 240 volts?

---

### Post by Maxx730 on 2009-03-09
.

---

### Post by Chemical Imbalance on 2009-03-09
> **Maxx730 said:**
> On the back of the computer it says 240v near the plug, im guessing that means 240 volts?

Usually you have to open your case and look at the side of the power supply to see the rating.  Look for ###W  (###being your wattage).

---

### Post by bailbath on 2009-03-10
I don't think has anything to do with power supply you are looking for a blind alley solution instead of doing the simple things first.
Ian

---

### Post by Maxx730 on 2009-03-10
I just need any answer to fix it :( I want this computer working

---

### Post by issih on 2009-03-10
From what you have said, you are not getting any boot at all, not even to the point of being able to enter bios, if that is correct, you need to pay more attention to the people talking about power issues than X based solutions. If your pc is not even posting then you have hardware problems not software.

(no offence meant to anyone here guys, but he does say that he doesn't even get to the emachines turn on screen, so I doubt this is anything to do with the OS)

One thought, although I am not that hopeful, is that a lot of modern graphics cards need a separate power connection direct to the card, rather than just drawing power over the bus.

You should take a look at your card's documentation, and indeed at the physical card itself to see if there is anywhere you could plug a spare molex connector in.

One other possibility is that you simply got unlucky and your new card is broken, is there another pc you could slot it into to test?

Hope that helps

edit..

seems at least some x1300's do need an extra molex connection to supply power:

[http://www.hardwarezone.com/news/view.php?cid=6&id=3883](http://www.hardwarezone.com/news/view.php?cid=6&id=3883)

you are looking for the little socket like in the middle small picture below the glamour shot of the box..

[http://www.hardwarezone.com/img/data/nnews/2006/3883/File/Power400.jpg](http://www.hardwarezone.com/img/data/nnews/2006/3883/File/Power400.jpg)

If you haven't already, you need to connect a molex power supply cable to that, hopefully you will have a spare one dangling about inside your case, if not you will need to find a molex splitter.

---

### Post by Therion on 2009-03-10
What will probably tell us if this is a hardware issue or a software issue is this:  Boot to an Ubuntu LiveCD.  

The LiveCD will use your installed graphics *card*, but will bypass any currently installed video *driver* in lieu of the generic vesa driver.  Then we'll have one of two scenarios to look at:

A) You DO get the same screen borkage with the LiveCD you're getting now.  This tells us you have issues with getting enough power to the video card.  

or

B) You do NOT get the same video problem you're getting now using the LiveCD.  This tells us you have a borked X configuration.

---

### Post by Maxx730 on 2009-03-10
Yes I tried using the live CD with the graphics card in and the same screen shows up. I think ubuntu is loading when I turn the computer on but its just the graphics are not being loaded properly

---

### Post by issih on 2009-03-10
Do you get any power on self test information (POST)(most noticeable feature will be where the computer site and cycles through the memory to check it)?

Can you enter bios?

Do you get to see grub?

Do you get ANY indication that the machine is functional? do the ubuntu drums play indicating it has made it to the login screen?

We need to clarify what you are actually seeing. From the moment you hit the power button, do you ever see anything legible as text?

From what you have said thus far I really do think you have a hardware issue, not a driver one.

---

### Post by Therion on 2009-03-10
If your PC boots straight to that garbled screen with the X1300 installed then, yes; you have a hardware problem.  Period.

---

### Post by Maxx730 on 2009-03-10
yes the computer boots strait to the screen, no GRUB, BIOS anything. If it is the hardware are you saying that I need to but a new graphics card?

---

### Post by kelvin spratt on 2009-03-10
With respect to everybody this post does not give any real specs for the machine or graphics card if it works with the old card then I would say its more related to the card even a low powered power supply should get post.
I think its the card that's at fault if its second hand you may need to bin it and learn.
If its new contact the tech department where you bought it and get it checked out

As somebody has suggested a couple of times Check if it needs a 2nd power supply
again just contact a supplier ask for there tech dept give them the details of the card over the phone and they will tell you if it does need a second power supply to the card if it does its no great deal you should have a spare connector if not you need a piggy back connector.

---

### Post by eeeek on 2009-03-10
I don't know enough to help you troubleshoot.

However, I read somewhere (on these forums, I think) that generally speaking, you'll have an easier time with a nvidia graphics card than an ATI one. 

I recently built my first computer and I had no problems with the nvidia card that I bought. 

I don't know whether or not you need a new video card. But if you do, I'd recommend getting a nvidia one and not an ATI chipset. 

Best of luck.

---

### Post by Therion on 2009-03-10
> **Maxx730 said:**
> ... are you saying that I need to but a new graphics card?
It's certainly beginning to look that way, yes.

You say you got this card off eBay?  Was it retail boxed or was it a used part?  That's kind of a moot point, really, but I'm hoping there's a chance of getting your money back.  

More to the point, if your PC is booting straight into that garbled screen then yeah, it's time to hit your local brick and mortar store and pick up a new, in-the-retail-box, video card.  

You don't need to spend a fortune for this.  Your problem, most likely, is going to be finding an AGP card at a brick and mortar location since most everything on the shelves these days is going to be PCI-e instead...

But, since you don't seem to mind buying online, you could look into something like one of the following:  [ATI X1650 Pro](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102781) ($65 on NewEgg and does require an additional connector, but the cable is included).  This is just one, cheap, option.  There are what I would call "better" options, but they cost more and I don't know what your budget for this is, assuming you even have one.

---

### Post by Maxx730 on 2009-03-10
Well, I am going to go out today and buy an nVidia card, hopefully 256mb becuase I dont need anything more.  Im guessing that all I need to do it get it, install the drivers and it should work?

---

### Post by Maxx730 on 2009-03-10
Also, the card came in a brown box with only bubble rap. So it probobly is the card...

---

### Post by Therion on 2009-03-10
> **Maxx730 said:**
> Well, I am going to go out today and buy an nVidia card, hopefully 256mb becuase I dont need anything more.  Im guessing that all I need to do it get it, install the drivers and it should work?
Be SURE the card you pick up today is for an **AGP** socket, or interface; nothing else.  PCI-e based cards will NOT fit in your PC.

Beyond that, 256MB of video memory is fine and the retail boxes don't go into detail about things like RAMDAC speeds, so I'm going to advise you to pick up something in the 6000 series (e.g. 6200, 6600) if you can.  

Be sure to check for additional power connectors besides the AGP bus and you should be good to go.  We'll deal with getting your Ubuntu install to use the correct restricted driver once the card is installed.

---

### Post by Maxx730 on 2009-03-10
Alright I'm gonna go in about an hour to Best Buy and I am guessing that if I ask they will know if the card is an AGP slot. If not ill post what kind it is on here since I've been on a Blackberry this whole time.

---

### Post by issih on 2009-03-10
Have you examined the misbehaving card to see if there is a molex connector on there yet? you really should do that before spending any more money, this is nothing at all to do with nvidia vs ati in terms of linux user friendliness, this is a straight hardware problem, the OS never gets a look in at all, the machine isn't even getting past POST.

Look at the links in my earlier post to see what you are looking for

Please work that bit out, because chances are if you don't you'll be back here in a few hours complaining that the replacement card is doing something similar, as most new cards take a secondary power supply.

---

### Post by Maxx730 on 2009-03-10
Alright, I got an nVidia GeForce 8400 recomended for linux from the geek squad and its running in my computer. Now aall I need are the drivers for it...

---

### Post by Therion on 2009-03-10
> **Maxx730 said:**
> Alright, I got an nVidia GeForce 8400 recomended for linux from the geek squad and its running in my computer. Now aall I need are the drivers for it...
Don't go downloading anything.

Go to System/Administration/Hardware and see if your video card is being recognized by Ubuntu.  You should see a couple of driver options listed for your nVidia card.  That menu will give you options for installing the restricted driver.  This is the preferred method for installing video drivers in Ubuntu unless you want to get into a manual install which really isn't necessary.  

Nice card by the way, anything from the the 8000 series should hold you over nicely.

---

### Post by Maxx730 on 2009-03-10
I went to System > Administration > Hardware Drivers and it said

NVIDIA Accelerated Graphics Driver 

So I clicked that and it asked me to install the stuff so I said ok.  It started to download the package or whatever and then it said this...

E: /var/cache/apt/archives/nvidia-glx-new_169.12+2.6.24.16-23.56_i386.deb: subprocess pre-installation script returned error exit status 2

(O and you guys were right, I went to the Geek Squad and they said that the Graphics card was just broken, guess I did a lot for something that wouldnt works haha...)

---

### Post by Therion on 2009-03-10
Okay you're doing the right thing, but the installer is balking.  I suspect broken packages and/or remnants of old drivers from your previous video card and/or previous attempts to install the X1300 you were working with earlier.

Unfortunately I don't feel qualified to tell you how to purge your system.

I suppose we could try using Synaptic to remove anything and everything ATI related.  That couldn't hurt.  Do you know how to use the Synaptic Package Manager?

---

### Post by Maxx730 on 2009-03-10
yeah i know how to use synaptic, should I just search for anything ATI related?

---

### Post by Therion on 2009-03-10
> **Maxx730 said:**
> yeah i know how to use synaptic, should I just search for anything ATI related?
Yeah, just put "ATI" in the box.  Just be careful and be sure you know what you're removing.

That and hope someone who REALLY knows how to fix this comes along soon because I'm not at all convinced this is going to solve the problem.

---

### Post by Maxx730 on 2009-03-10
Well I used EnvyNG to uninstall the ATI Drivers.  And now I go to run the .run file of the NVIDIA driver and it says that the 'X' Server is running and that needs to be shut down for the installation.

---

### Post by Therion on 2009-03-10
Well, you could use Envy to install your nVidia driver, BUT...  The first time you get a kernel update, your driver install is going to bork on you.

If you used Envy to remove the ATI driver-traces, I suggest you go BACK to the Restricted Driver Manager to try installing the nVidia driver for your 8400.

Why are you so intent on installing from source?

---

### Post by Maxx730 on 2009-03-10
ok, I reinstalled ubuntu, and I installed the driver.  Its working, except for when I use compiz, and open up firefox everything goes to hell.  I thought a 512mb graphics card would be able to handle compiz.

---

### Post by Therion on 2009-03-10
> **Maxx730 said:**
> ok, I reinstalled ubuntu, and I installed the driver.  Its working, except for when I use compiz, and open up firefox everything goes to hell.  I thought a 512mb graphics card would be able to handle compiz.
Can you be a little more specific?  Your card is fine and will have no trouble "handling" Firefox, Compiz or both.
Compiz, though, does have it's problems.  It's the window manager I love to hate.

---

### Post by Maxx730 on 2009-03-10
compiz seems to work fine with windows and other stuff, but when I have compiz on and firefox, when it is rendering websites all the sudden it will start to freak out and the wallpaper will appear in blocks where the website should be then all the menus start to disapear and then it just freezes

I push alt ctrl backspace and restart.

---

### Post by Therion on 2009-03-10
1.  Have you done your system-wide updates (System/Administration/Update Manager)?

2.  Open a terminal:```
sudo apt-get install ubuntu-restricted-extras
```

3.  In Synaptic install the **fusion-icon** package and the **compizconfig-settings-manager** package.

Ubuntu-restricted-extras will install codecs and Flash and Java to make sure your Firefox install is up to snuff.

The Fusion-Icon will add a package that will help determine if it's really compiz-fusion messing with Firefox.  I doubt it is, but it's possible.

The CCSM package will help you manage Compiz Fusion.  Post back when you're done.

---

### Post by Maxx730 on 2009-03-10
yeah its still crashing, would my cpu being only 1.6Ghz be a problem?

---

### Post by Maxx730 on 2009-03-10
Also, it is not crashing at all with anything else i open
only firefox crashes

---

### Post by Therion on 2009-03-10
Mmmkay, well we're in troubleshooting mode here so we're gonna take it one step at a time.
Go to System/Preferences/Appearance and click on the "Visual Effects" tab.
Set the option to "None".  This will shut off Compiz.  
Check to see if Firefox is still all crashy on you.  If it is, we know it's not a Firefox/Compiz conflict, but rather just Firefox being a b--ch.  
If the crashiness stops then yeah, you got a problem with Compiz not playing nice with Firefox.

By the way, did you install Ubuntu 8.10 or 8.04?  I'm betting 8.10, huh?

---

### Post by Maxx730 on 2009-03-10
i shut of visual effects and firefox does not crash...

and actually I only had ubuntu 8.04 on disk so i installed that.

---

### Post by Therion on 2009-03-10
Ah, 8.04 good.  Personally I've had better luck with 8.04 than I have with 8.10 but we'll have to see how things work out for you.  Unfortunately I'm not sure how, exactly, to resolve Firefox being crashy when you've got Compiz running.  I know it's not an UNcommon problem, though, so searching on the forums and/or making a new post focusing on that issue would be in order.

Are you running Firefox version 3.0.7?

Have you tried using the "Normal" setting in "Visual Effects" tab as well as "Extra"?  Maybe one would work better than another?

If you need to you can use the Compiz Fusion Icon (put the applet on one of your gnome panels) to quickly turn Compiz on and off.  Kind of a lousy work-around but it may be your only option.  

Sorry I can't be of more help with this specific problem.  Search the forums or make a new post if nothing here helps.

---

### Post by Maxx730 on 2009-03-10
Well I "fixed" it by trying Linux Mint. So far compiz is working great even when firefox is open

---

### Post by Maxx730 on 2009-03-10
also there was a problem and during the updates the computer got shut down. Now when I try to update it says I need to reconfigure something before I do. What should I do so that I can get updates?

---

### Post by Unikraken on 2009-03-10
So much delicious Dr. Pepper..

---

### Post by Chemical Imbalance on 2009-03-11
> **Maxx730 said:**
> also there was a problem and during the updates the computer got shut down. Now when I try to update it says I need to reconfigure something before I do. What should I do so that I can get updates?

```
sudo dpkg --reconfigure -a
```

then:

```
sudo apt-get install -f
```

That should help

---

### Post by Maxx730 on 2009-03-11
When I run,

sudo apt-get install -f

it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Chemical Imbalance on 2009-03-11
> **Maxx730 said:**
> When I run,

sudo apt-get install -f

it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

That's the first thing i mentioned in my post above.

After you run those commands in order then try restarting.  If that doesn't work, you'll have to find out which package it was that broke and manually remove it.

---

