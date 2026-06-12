---
title: "Yikes, random hard freezes"
date: 2009-04-11
forum: General Help
---

### Post by dvfreelancer on 2009-04-11
After months of near flawless service my Ubuntu desktop has suddenly started freezing up hard at random intervals for no apparent reason.  

It will freeze, the current window will go gray and after a couple minutes all three of the lights on my keyboard will start flashing (num lock, caps lock...whatever the other one is).  It won't respond to anything but the reset button.  It may be related to either Ciro dock or FF, the only two apps running on the last freeze. 

I'm looking in the system logs but there's no HOLY CRAP entry I can find.  Just the seemingly normal start up messages.  

This behavior just started since the last update.  It's so seldom I have problems, how do you start diagnosing an issue like this?

I'm using Ubuntu 8.04 2.6.24-23-generic on an AMD system that has been a rock up to now.  There's 176 Gigs of free space on the drive and no recent hardware changes. 

So how do I figure which process is the guilty party?  This is frustrating because it's always been my trustworthy machine.  When all else fails, this one kept going.  

Tried starting FF apart from Ciro-dock and it's having real problems.  There's a message in the Xorg log that says Initialized AGP GART.  Does that mean anything?

---

### Post by tommcd on 2009-04-11
I'm not a hardware expert, but I know that random lockups like that can be due to bad RAM. Boot up the computer and run **memtest** from the grub menu. Or boot a Ubuntu live CD and run memtest. Let it run for a while and see if you get any errors. Also check /var/log/syslog and /var/log/messages for obvious errors.

It seems odd that an update in 8.04 would vause this since 8.04 is a LTS version and is geared toward stability. Do you remember what was in the recent update?

---

### Post by dvfreelancer on 2009-04-11
It says unrecognized command. 

But the whole display fragments every few seconds even in the grub menu.  It will scramble and if I hit the up or down arrow it will clear up for a few seconds, then go weird again. 

I checked the monitor connections, just to be sure it wasn't a cabling issue.

---

### Post by tommcd on 2009-04-11
> **dvfreelancer said:**
> It says unrecognized command. 

But the whole display fragments every few seconds even in the grub menu.  It will scramble and if I hit the up or down arrow it will clear up for a few seconds, then go weird again. 

I checked the monitor connections, just to be sure it wasn't a cabling issue.

Try booting up the Ubuntu 8.04 live CD. Or boot an Ubuntu 8.10 live CD if you have one. Run the live CD (either one will do) for a while. Surf the net, open and close directories, play some ogg videos or audio files. If the live CD runs ok, but only your installed Ubuntu has problems / lockups, then it is likely that your installed Ubuntu got screwed up somehow. If the live CD experiences the same problems / lockups, then I would think it was a hardware issue somewhere. You can also run memtest from the live CD.

---

### Post by dvfreelancer on 2009-04-11
Now it won't boot at all. The display is completely horked. I can't imagine Ubunu would fail in a serial fashion.  Where a problem gradually gets worse.  

Ironically, I'm using a Windows box to try and download the iso to rescue my Linux box.  The shame.  I've used Knoppix to resurrect non-booting Windows boxes and here I am depending on MS to save the day.  

While I'm waiting for the download I'm going to take everything apart, clean it and reseat the components.  Just in case something wiggled loose or got dirty.

update: It wasn't a loose component.  It's only got a single memory stick.  Odd for one to fail in such a gradual way.  I'll finish the download and try the rescue disk.

---

### Post by defaultusername on 2009-04-11
dvfreelancer,

Intrepid was giving me random crashes on a Thinkpad T60. The issue seems to be resolved after upgrading to Jaunty 9.04. Fortunately, it wasn't a hardware problem.

Unfortunately, the only thing you can do is replace components one-by-one until you find the culprit. Afterwards, it might not be a bad idea to do a complete torture test to ensure stability. Also, make sure your components aren't overheating -- poor cooling and overclocking can cause similar problems to what you're describing.

---

### Post by dvfreelancer on 2009-04-11
All good suggestions.  I'm having a hard time pinning this on Ubuntu as the screen image corrupts even in the BIOS menu.  There will be lines of random characters...ala The Matrix and when I hit the up/down arrow it clears up, then corrupts again.  

I've got a spare video card...never seen one go bad before, but there's always a first time.  

After that I'm just going to get a new dual core mobo.  I've got good backups so not really worried.  Copy the Desktop folder and I'm right back in business.  

Normally I suspect the power supply first.  Puters do some strange things when the PS is going bad.  But not like this. This is truly bizarre.

---

### Post by tommcd on 2009-04-11
> **dvfreelancer said:**
> All good suggestions.  I'm having a hard time pinning this on Ubuntu as the screen image corrupts even in the BIOS menu.  There will be lines of random characters...ala The Matrix and when I hit the up/down arrow it clears up, then corrupts again.  


If just booting into the BIOS causes the same, or similar, problems, then this pretty much rules out a software problem. I think you should consider this to be a hardware problem at this point. The video card is of course one possibility.

If you don't have an Ubuntu live CD you can just boot a Knoppix live CD or whatever you have to test the system. I think Knoppix has memtest also.

---

### Post by dvfreelancer on 2009-04-11
I downloaded the Ubuntu live CD.  Memtest is running as we speak.  So far, so good.  The screen is flickering during memtest.  It'll paint vertical strings of characters, then a second later the screen will reset.  

I'll try the live CD but I'm with you that it's probably hardware.  

Assuming the memory passes, I'll try swapping out the video cards and see what happens.

---

### Post by Sef on 2009-04-12
Let it run overnight for memtest.    Sometimes problems don't come up at first.

---

### Post by dvfreelancer on 2009-04-12
Pass complete, no errors, press Esc to exit.  

But the screen is still flash vertical rows of random characters spaced about 2 inches apart.  Sometimes it will be several seconds between the flashes, other times almost continuous.  

It will do it in the bios menu and cause freezes on the desktop, but it doesn't happen on the load menus. 

On to the live CD, then the video card. 

If neither one of those solve it then I'm getting a new dual proc mobo.

The live CD says it's running in low graphics mode because it can't detect my screen, graphics card or input device settings.

The live CD loads in low graphics mode. Slow, but it works.  When I take it out and try to boot back to the installed version It goes most of the way through the boot process, then fills the screen with complete garbage. Instead of a mouse pointer I have a giant square in the middle of a scrambled window of static.

---

### Post by dvfreelancer on 2009-04-12
Okay, I got this mostly resolved.  To recap, the nominees were:

- Recent kernel update

- Bad RAM 

- Bad video card

- Gremlins

The envelope please.  And the winner is (rattle-rattle-rattle)

**Video card!**  (insert crappy award show music)

Replaced the card with an old one in a different machine and that cleared it up.  Except now it's mind-numbingly slow.  Going to leave off the slick window effects until I can order a new mobo and graphics card.  Hey, if I'm going to crack the case again, might as well make it worthwhile.  

Thank you all for your assistance.  ):P

---

