---
title: "HDMI with ATI!"
date: 2009-04-17
forum: General Help
---

### Post by coskierken on 2009-04-17
Please, no ATI bashing, I just have a question and problem.  Does ATI 4650 HDMI work in Intrepid?  I have not had problems with the drivers at all with one monitor.  Got them all loaded, as I have been working with ATI X1650 on my laptop for a couple of years and learned how to get them to load.  I have found out, through much hair pulling, when I have the an LCD PC monitor hooked up to the VGA and HDMI hooked up to the TV, U will start and once it loads to start screen, it goes blank.  Nothing ever shows up on the TV via HDMI either. The 4650 has to be seeing the connection via HDMI.  If I unhook HDMI and restart, it comes up fine. SHould I have set the resolution the PC monitor to the same as the HDTV/HDMI of 1366x768?  I have tested the HDMI on the TV via an HDMI output from an HDMI DVD player and the picture is great.   

Now, if I hook up the PC monitor via DVI and TV via VGA, no problems. I can have dual monitors in various setups.      

The new machine is a desktop with specs below:
MSI G45M Digital MB
Intel Q9550 2.83G
8G PC1066 (32 bit so only see 3G)
Biostar ATI 4650HD 512MB Native HDMI/DVI/VGA 
WD 500G/Hitachi1TB HDDs
Sharp LC32SB23U HDTV
Dual Boot Intrepid 8.10/XP 32bit (Hate to say it, but if I want to use all my ram, may have to buy(beating myself up over this) Vista 64bit.   

I will move up to Jaunty 64bit when released out of beta.  Same question for it as above.  Mostly, I will use 64bit to rip mp3 and mp4s.  Any help, no ati bashing, will be appreciated. Thanks

---

### Post by danwood76 on 2009-04-17
I'm asuming you are using the restricted drivers? (from ATI also called fglrx)

Have you tried starting the PC with just the TV hooked up to the HDMI?
It could be an issue with X's virtual monitor size, though I havent used fglrx in a while as my ATI is supported by the open source drivers.

---

### Post by ushills on 2009-04-17
i know my ati card wont let me use hdmi with another output vga or dvi.

also why not use 64bit 9.04?

---

### Post by coskierken on 2009-04-17
Thanks for the tip.  I got it working with just hdmi or vga, but not both.  They are suppose to do this.  I know vga and dvi will work together as have did it in xp and intrepid.  Next is a dvi to hdmi adapter.  We will see.  This is not what I paid for.  Probably will return it.

---

### Post by dariusp686 on 2009-04-17
I have a new Dell Studio 15 which has an ATI Mobility Radeon HD 4570.  There are VGA and HDMI connectors.

Under Ubuntu 9.04 beta with the open source drivers connecting with HDMI just shows a blank screen.  It is able to detect the external monitor and is configured to use it, xrandr shows it is present and I can moved stuff onto it (of course I can't see it but I can see it move off the laptop screen).

Using the ATI/AMD proprietary FGLRX driver however works and HDMI shows the screen.

---

### Post by danwood76 on 2009-04-17
> **coskierken said:**
> Thanks for the tip.  I got it working with just hdmi or vga, but not both.  They are suppose to do this.  I know vga and dvi will work together as have did it in xp and intrepid.  Next is a dvi to hdmi adapter.  We will see.  This is not what I paid for.  Probably will return it.

I would expect that the HDMI and VGA are connected to one output and the DVI to the other (the card only has 2 main outputs).
The most common configuration would be HDMI plus DVI, I would expect the DVI to HDMI will sort you out!

---

### Post by coskierken on 2009-04-18
Well, everything I have read about VGA/DVI/HDMI is that VGA must be run with DVI or HDMI and DVI and HDMI cannot be run at the same time.  Well, just to test it out, I finally put the DVI and HDMI on at the same time and rebooted.  It works great now and I did a big DUH and kick myself in the butt for not trying it earlier.  I have it going now in XP (I know....) with the main on the 19" LCD monitor via DVI (downloading 64 bit Jaunty Beta, webpages up, and skin for the movie player) and the movie playing on the Sharp 32" LCD.  I am sure it will work in U once I reboot.  
     Thanks for all the help.  I was about to order another video card, so I don't have to spend the money.  Instead, a new case and power supply will be coming next week.  :biggrin:

---

### Post by coskierken on 2009-04-18
Update... Rebooted with DVI/HDMI in Intrepid and it works great.  There a few little quirks I have to work out, but output is great.  Finished the  
download of 9.04 x64 and will install today.  Probably see me in the x64 thread.  

Oh, my system specs:

Q9550 2.83 OCed only to 3G (for now:D)
8G Gskill 1066
MSI G45M Digital (easy board to configure and OC)
ATI 4650 512MB (quick enough for light gaming and inexpensive) 
500G WD / 1TB Hitachi

---

