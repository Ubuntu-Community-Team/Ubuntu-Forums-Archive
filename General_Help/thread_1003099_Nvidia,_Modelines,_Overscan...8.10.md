---
title: "Nvidia, Modelines, Overscan...8.10"
date: 2008-12-05
forum: General Help
---

### Post by MCrittenden on 2008-12-05
Hey guys, I've looked around here quite a bit for a solution. I, like many others, have an overscan problem when using an nvidia (GForce 6200) chipset going to my Sony Trinitron 36" HDTV. I'm running DVI straight out of the card into the TV. I lose about 5% of the screen on all sides. I'm running Ibex and don't think it's a problem specific to Ubuntu since every other distro has given the same problem (it might not even be a computer problem, maybe it's my TV not handling the DVI signal well).

I'm running nvidia proprietary driver 177 and am on my TV's native resolution (which is a good start). It looks like the only solution involves making a custom modeline that will shrink the screen down to match up with what I can see. But I can't figure out how to make a modeline (google's not helping) and none of the generators make any sense to me. 

Can anybody help me out on making a modeline for this problem, or tell me if there's a better way? Will it even recognize my modeline changes while using the proprietary drivers? Some say it does, and some say it ignores them.

---

### Post by MCrittenden on 2008-12-08
Bump. In the meantime, I'm using empty panels to block off the screen space that I'm not using. Works pretty well.

---

### Post by MCrittenden on 2008-12-11
Last Bump. Anybody understand modelines?

---

### Post by tammer on 2008-12-26
I am experiencing this problem as well, although I'm outputting through s-video to a CRT SD TV. From what I've gathered, it seems that Nvidia has stopped supporting over/underscan through their drivers, but I'm not sure on this.

It also appears that modelines offer an alternative, manual overscan that bypasses the drivers, but there's nowhere that I can find a straightforward guide to using them.

Thanks for the empty panel idea, though, this is a pretty good work-around for the time being.

---

### Post by MCrittenden on 2009-01-07
Did you ever find an answer to the modelines?

---

### Post by hpadrick on 2009-01-08
Last night I finally got my HDTV perfect using an nVidia card, but the approach should be the same for all cards.  I will be working on the steps and post everything hopefully by tomorrow.  I know this seems like a worthless post, but hang in there.

---

### Post by FarJumper on 2009-01-08
> **hpadrick said:**
> Last night I finally got my HDTV perfect using an nVidia card, but the approach should be the same for all cards.  I will be working on the steps and post everything hopefully by tomorrow.  I know this seems like a worthless post, but hang in there.

Keeping my fingers crossed... I have the same problem with my Panasinic 42PY85 + nv6150

---

### Post by MCrittenden on 2009-01-08
Same here...eagerly waiting.

---

### Post by mwillams73 on 2009-01-09
I have the same vid card and in Xp ( windows) theres a seeting menu where you can fix that but there is none in Ubuntu ( intrepid) so I dont know if youll ever be able to fix it as long as Ubuntu stays years behind windows and mac

---

### Post by MCrittenden on 2009-01-09
> **mwillams73 said:**
> I have the same vid card and in Xp ( windows) theres a seeting menu where you can fix that but there is none in Ubuntu ( intrepid) so I dont know if youll ever be able to fix it as long as Ubuntu stays years behind windows and mac
Hey, smart comment for a smart guy! It's the fault of nvidia's proprietary drivers, not Ubuntu. Stop trolling.

---

### Post by hpadrick on 2009-01-10
I am pasting the instructions in here for searchs, but they will be hard to read.  I suggest downloading the attachment.  It's just an openoffice file gzipped.





Most of these instructions were gathered from [http://www.nvnews.net/vbulletin/showthread.php?t=118701](http://www.nvnews.net/vbulletin/showthread.php?t=118701)

After tons of research on the problem, everything was pointing to the TV giving bad information to X.  X will query a monitor for the available resolutions, refresh rates, and placement of the screen.  From the articles I read, most TV's use over-scanning on everything but a VGA input which is the reason for the picture getting cut off.

The only thing specific to the nvidia card are a couple of options needed in xorg.conf.  I am sure there are equivalent options for ATI and others, so if you know them please post them so we can have everything here.  

Here are the needed nvidia options and there placements, but do not use them yet.  Just write them down.

For the Monitor section:
        Option          "ExactModeTimingsDVI" "TRUE" 


For the Device section:
        Option          "UseEDID" "FALSE" 


We first have to start by using a command line tty and stopping gnome, so save everything that is open and hopefully you have a laptop to read the rest of this post off of.  If not print it out.

Hit ctl+alt+F2 to switch to tty2.  Log in and 

	sudo /etc/init.d/gdm stop

This will stop gnome and shutdown the GUI on tty7.

Next type
	
	X -verbose 6 > ~/xlog.txt 2>&1  

This will launch X and you will see a gray screen.  All output of X will be in the file xlog.txt located in your home(~) directory.  You will need information out of this file to continue, so get out of the gray screen and start gdm back up.

	ctl+atl+BACKSPACE  - will kill the gray screen
	
	sudo /etc/init.d/gdm start – will start gnome again  

Once you are back inside gnome open gedit and browse to your home directory to open xlog.txt

Within this file we will need the Horizontal Sync and Vertical refresh rates of your TV.  Find the section of the file that looks similar to :

(II) NVIDIA(0): Frequency information for Philips FTV (DFP-0): <-- of-course this will be your TV model
(II) NVIDIA(0):   HorizSync   : 15.000-50.000 kHz

(II) NVIDIA(0):   VertRefresh : 48.000-62.000 Hz

(II) NVIDIA(0):     (HorizSync from EDID)

(II) NVIDIA(0):     (VertRefresh from EDID)


Write down the HorizSync and  VertRefresh values.

Now we need to find some good working resolutions to create some modelines.

Locate the section that is similar to below.  Take note that this section states it is validating modes.

(II) NVIDIA(0): --- Building ModePool for Philips FTV (DFP-0) ---

(II) NVIDIA(0):   Validating Mode "1920x1080":

(II) NVIDIA(0):     1920 x 1080 @ 50 Hz

(II) NVIDIA(0):     For use as DFP backend.

(II) NVIDIA(0):     Mode Source: EDID

(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz

(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2448

(II) NVIDIA(0):       HSyncEnd, HTotal : 2492, 2640

(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084

(II) NVIDIA(0):       VSyncEnd, VTotal : 1094, 1124

(II) NVIDIA(0):       H/V Polarity     : +/+

(II) NVIDIA(0):       Extra            : Interlace

(II) NVIDIA(0):     Mode is valid.

(II) NVIDIA(0): 

(II) NVIDIA(0):   Validating Mode "1024x768":

(II) NVIDIA(0):     1024 x 768 @ 60 Hz

(II) NVIDIA(0):     For use as DFP backend.

(II) NVIDIA(0):     Mode Source: EDID

(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz

(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048

(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344

(II) NVIDIA(0):       VRes, VSyncStart :  768,  771

(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806

(II) NVIDIA(0):       H/V Polarity     : -/-

(II) NVIDIA(0):     Mode is valid.

(II) NVIDIA(0): 

(II) NVIDIA(0):   Validating Mode "1920x1080":

(II) NVIDIA(0):     1920 x 1080 @ 60 Hz

(II) NVIDIA(0):     For use as DFP backend.

(II) NVIDIA(0):     Mode Source: EDID

(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz

(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008

(II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200

(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084

(II) NVIDIA(0):       VSyncEnd, VTotal : 1094, 1124

(II) NVIDIA(0):       H/V Polarity     : +/+

(II) NVIDIA(0):       Extra            : Interlace

(II)NVIDIA(0):     Mode is valid.

Now we need to make some modelines, so grab a low resolution one like:

(II) NVIDIA(0):   Validating Mode "720x480":

(II) NVIDIA(0):     720 x 480 @ 60 Hz

(II) NVIDIA(0):     For use as DFP backend.

(II) NVIDIA(0):     Mode Source: EDID

(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz

(II) NVIDIA(0):       HRes, HSyncStart :  720,  736

(II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858

(II) NVIDIA(0):       VRes, VSyncStart :  480,  483

(II) NVIDIA(0):       VSyncEnd, VTotal :  489,  525

(II) NVIDIA(0):       H/V Polarity     : -/-

(II) NVIDIA(0):     Mode is valid.

Making sure it is marked as valid, and a high resolution one like:

(II) NVIDIA(0):   Validating Mode "1920x1080":

(II) NVIDIA(0):     1920 x 1080 @ 60 Hz

(II) NVIDIA(0):     For use as DFP backend.

(II) NVIDIA(0):     Mode Source: EDID

(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz

(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008

(II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200

(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084

(II) NVIDIA(0):       VSyncEnd, VTotal : 1094, 1124

(II) NVIDIA(0):       H/V Polarity     : +/+

(II) NVIDIA(0):       Extra            : Interlace

(II) NVIDIA(0):     Mode is valid.

My TV had a couple of different valid 1920 x 1080 modes.  I ended up choosing the one which will run at 60Hz.

Now to make the modelines just read down the mode from top to bottom starting at Pixel Clock.  In the parenthesis you can really put what you want. That will be the identifier used in your Screens sections, but for now just follow below.    

	modeline “720x480” 27.00 720 736 798 858 480 483 489 525 -hsync -vsync

	modeline “1920x1080” 74.25 1920 2008 2052 2200 1080 1084 1094 1124 +hsync +vsync Interlace

Notice the H/V polarity usage for hsync and vsync.

Now we have all the info we need to start messing with our xorg.conf file, but first make a backup of your current file.  In a terminal 

	sudo cp -v /etc/X11/xorg.conf /etc/X11/xorg.conf.BUP

So lets put together everything we have.  Open gedit with root permissions by pressing alt+F2 and typing 

	gksudo gedit /etc/X11/xorg.conf

Below is my very simple xorg.conf file with the added Options, HorizSync, VertRefresh, and modelines.

Section "Monitor"

	Identifier	"PhilipsHDTV"

	Option	 	"ExactModeTimingsDVI" "TRUE"
   # Added
	

	HorizSync	15-50
 # Added
	VertRefresh	48-62
 # Added


# Modelines we created earlier

	ModeLine "720x480" 27.00 720 736 798 858 480 483 489 525 -hsync -vsync


#KEY	Modeline   "MODENAME"     FF      H1    H2    H3    H4    V1    V2    V3    V4     FLAGS
 
	ModeLine "1920x1080"           74.25 1920 2008 2052 2200 1080 1084 1094 1124 +hsync +vsync Interlace


EndSection



Section "Screen"

	Identifier	"Default Screen"

	Monitor		"PhilipsHDTV"

	Device		"gForce8600GT"



	SubSection "Display"
 # Added subsection
		Depth 24

		Modes "720x480"
  # Identifier must match modeline name from above!!
	EndSubSection

EndSection



Section "Module"

	Load		"glx"

EndSection



Section "Device"

	Identifier	"gForce8600GT"

	Driver		"nvidia"

	Option 		"NoLogo"		"FALSE"

	Option		"UseEDID"		"FALSE"
 # Added
EndSection


In the Monitor section we added:
	Options	“ExactModeTimingsDVI” “True”

This forces X to read the timings from the modeline, not the TV.

	HorizSync	 with the numbers you wrote down from earlier. You do not need to include the 				kHz or Hz

	VertRefresh	again, numbers from earlier

	modelines	we created earlier. Be sure to copy the KEY above the “1920x1080” for later!  				Position the FF, H's, and V's like you see above.

In the Screen section we add the SubSection “Display” with Depth and the lowest modeline we created for Modes.  Remember that the Modes must match exactly what you have in your modeline as the MODENAME!!!

In the Device section we added:

	Option		“UseEDID” “FALSE”

This tells the video card not to pull any information from the TV allowing us to manipulate the resolution and position of X.

Save your new xorg.conf file.

Go to tty2 again and stop gdm

	ctl+alt+F2
	sudo /etc/init.d/gdm stop

Now hopefully you used the lowest modeline, so you will notice poor resolution for the gray X screen by issuing the most complicated *nix command ever written

	X

If you see an abnormally large X on the screen, or black bars on the side of the gray window that is a good sign.  This means you video card is 1. using the modeline you enter. 2. ignoring what your TV is telling it.

So Kill X

	ctl+alt+BACKSPACE

Stay in tty2 and lets change your resolution to the highest one using nano:

	sudo nano -w /etc/X11/xorg.conf

Be sure to use the -w here!!

Once you are in the editor find the modelines you created by using the down arrow or page down key.  Take note of what you named the highest valid resolution and continue to the Screen section.  Change the Modes option in the SubSection “Display”  to match the modeline “MODNAME” from above.  Mine was “1920x1080”.  Once that is changed:

	ctl+x
	answer yes to save
	X

This time you should be at the correct resolution with the over-scanned gray X screen.

It's time to correct the problem if you are still with me. Kill X and go back into nano

	ctl+alt+BACKSPACE
	sudo nano -w /etc/X11/xorg.conf

At this point, I made the resolution as whack as I could to get the screen positioned correctly, so on your high resolution modeline change the H1 and V1 values to something crazy like:

#orig 	ModeLine "1920x1080"           74.25 1920 2008 2052 2200 1080 1084 1094 1124 +hsync +vsync Interlace

#KEY	Modeline   "MODENAME"     FF      H1    H2    H3    H4    V1    V2    V3    V4     FLAGS
 
	ModeLine "1920x1080"           74.25 1800 2008 2052 2200 900 1084 1094 1124 +hsync +vsync Interlace

	

	ctl+x 
	answer yes to save
	X

Now you should see a shorter and very off center gray screen.  All that's left to do now is adjust the screen positioning and change the H1 and V1 to the highest values we can to fill the screen.

I am no longer going to tell you how to get in and out of nano or start and kill X so take notes if you need them.

To move the screen to the right, simply reduce the H2 and H3 values using the same amount for each.  For example, if you adjust H2 -50 make the same adjustment for H3:

#orig   	ModeLine "1920x1080"           74.25 1920 2008 2052 2200 1080 1084 1094 1124 +hsync +vsync Interlace

#KEY	Modeline   "MODENAME"     FF      H1    H2    H3    H4    V1    V2    V3    V4     FLAGS
 
	ModeLine "1920x1080"           74.25 1800 1958 2002 2200 900 1084 1094 1124 +hsync +vsync Interlace


Basically, just keep changing the numbers, saving the config, and starting and killing X until you like where the left edge of the screen is.

To move the screen down, do the same thing for the V2 and V3 settings.  Remember that a change to one means an equal change to the other.

#orig   	ModeLine "1920x1080"           74.25 1920 2008 2052 2200 1080 1084 1094 1124 +hsync +vsync Interlace

#KEY	Modeline   "MODENAME"     FF      H1    H2    H3    H4    V1    V2    V3    V4     FLAGS
 
	ModeLine "1920x1080"           74.25 1800 1958 2002 2200 900 1034 1044 1124 +hsync +vsync Interlace


Once the top and left edge are in place, adjust the H1 and V1 values to fit the rest of the screen.  My modeline ended up looking like this:

#orig   	ModeLine "1920x1080"           74.25 1920 2008 2052 2200 1080 1084 1094 1124 +hsync +vsync Interlace
	
	ModeLine "1920x1080_mod" 74.25 1820 1953 1997 2200 1000 1045 1055 1124 +hsync +vsync Interlace

So for my TV to display correctly, I lose 100 Horizontal pixels and 80 Vertical pixels.
 
After you are happy with everything:

	sudo /etc/init.d/gdm start

And you should be looking at the login screen and actually seeing the time on the bottom right!

---

### Post by hpadrick on 2009-01-10
Good Luck!!!!

It would be nice if xvidtune would work for us. I will be looking into that!

---

### Post by MCrittenden on 2009-01-10
Wow, I hope this works...can't wait to give it a shot. Thanks for all the effort you put into typing it up!

---

### Post by scottfmcleod on 2009-01-18
hpadrick -

Thanks for this post, it walked me through step by step and fixed my overscan issues!

Unfortunately now, my tv is connected via HDMI cable, and I learned: Option "UseEDID" "FALSE" 
disables HDMI audio.  

How can I go about maintaining these resolution settings and also keeping my hdmi audio?

Thanks!

---

### Post by scottfmcleod on 2009-01-18
Alright, I fixed my own issue by looking up various EDID commands.

To maintain custom timings and HDMI audio use the following:
Option "ModeValidation" "NoEdidModes"

instead of
Option "UseEDID" "FALSE"

---

### Post by VastOne on 2009-01-24
> **mwillams73 said:**
> I have the same vid card and in Xp ( windows) theres a seeting menu where you can fix that but there is none in Ubuntu ( intrepid) so I dont know if youll ever be able to fix it as long as Ubuntu stays years behind windows and mac

Further, In the shites I call Vista on  1/10th of a sliver of a partition, the same card with the Micro$oft drivers do the same dam thing and I cannot get even a edid.bin dump file because those same drivers cannot load anything but a generic vga when I try a straight vga connection....

Take your trolling back to the Windoze forums please...

---

### Post by VastOne on 2009-01-24
> **MCrittenden said:**
> Wow, I hope this works...can't wait to give it a shot. Thanks for all the effort you put into typing it up!

Well, did it work for you?

---

### Post by VastOne on 2009-01-24
> **hpadrick said:**
> Good Luck!!!!

It would be nice if xvidtune would work for us. I will be looking into that!

Rick, 

I really appreciate all the work you put into this and I am going to try your solution tomorrow....

I pulled this from my RCA 42 HD tv when I was in vga mode trying to get a edid.bin extracted...(did not work b/c nvidia X settings would not load b/c the xOrg vga drivers loaded)

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

If those are the correct HorixSync and VertRefresh, does it make finding the right modelines easier?

Again, thank you....

---

### Post by aeg1s on 2009-01-24
Thanks so much!  I found this post after finishing my HTPC build. Needless to say I was very upset at finding no way for my screen to be fully displayed.  While this took a little bit of time, your instructions were perfect.  Thanks!

---

### Post by hpadrick on 2009-01-26
> **VastOne said:**
> Rick, 

I really appreciate all the work you put into this and I am going to try your solution tomorrow....

I pulled this from my RCA 42 HD tv when I was in vga mode trying to get a edid.bin extracted...(did not work b/c nvidia X settings would not load b/c the xOrg vga drivers loaded)

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

If those are the correct HorixSync and VertRefresh, does it make finding the right modelines easier?

Again, thank you....
What video driver should be loading?  From what I understand, any TV with a VGA port should offer up the correct settings for PC use if the driver is correct for the card.  You will have to get the driver for your card up and running before you can pull the info you need.

The Hsync and Vsync in the section you posted have to do with your TV timings; not modelines.  In order to have a good place to start for a modeline, you will have to get the dump from X.  Let me know if I can help you any further

-Heath

---

### Post by VastOne on 2009-01-26
> **hpadrick said:**
> What video driver should be loading?  From what I understand, any TV with a VGA port should offer up the correct settings for PC use if the driver is correct for the card.  You will have to get the driver for your card up and running before you can pull the info you need.

The Hsync and Vsync in the section you posted have to do with your TV timings; not modelines.  In order to have a good place to start for a modeline, you will have to get the dump from X.  Let me know if I can help you any further

-Heath

Hi Heath,

When connected HDMI I can get nVidia X Server and drivers loaded no problem.  I am suffering from the overscan issue and believe that following the instructions of this thread, I should be able to solve it.....But! ;)

I believe that if I can get a good edid.bin capture from nVidia xServer in VGA mode, I could use that as a custom edid load (following the  success of yet another thread)  Problem is, when I connect vga cable and disable my geforce 8500 in bios (PCI load), nVidia drivers will not load and therefore xServer will not load run so I cannot capture the edid.bin in vga mode.

I did figure out the hsync and vsync values using read-edid version 2.0.0 (64 bit)

Now even in 1920 X 1080 (overscanned) I can tell you, I am not happy at all with the jittery tiny font picture I am seeing...So even if I get this loaded exactly, it may be a moot point.

I do appreciate your help and look forward to any insight you may have...

Thank you,

VastOne

---

### Post by hpadrick on 2009-01-27
@VastOne

If you get through the initial dump of the x.log you should have a couple of valid 1920x1080 modes.  Try them all to see if the jittery picture is resolved.  Everything is tiny at this resolution though, but I am running XBMC as the front end on the TV, so it looks great.  If you want to surf the net I suggest Opera; for some reason it handles scaling web pages better the Firefox.  Let us know how everything is working out for you.  Also, what is your Video card and Brand / Model of your TV?

-Heath

---

### Post by bbear1 on 2009-02-05
hpadrick,

I am new to this forum. I wanted to thank you for your amazing step-by-step instructions, I had great hopes that it would fix what for me has been a real headache this past couple of weeks, in fact it this problem has been driving me nuts!
Unfortunately X rejects my custom modeline and I cannot figure out what I am doing wrong.

Ubuntu is very new to me and I will do my best at providing all the necessary information:

OS: Ubuntu 8.10 32bit version
Computer Hardware: HTPC using a Asus M2NPV-VM motherboard with 6150 nvidia GPU
Nvidia driver: I installed nvidia 177.82 driver via Synaptic Package manager.
TV: Panasonic 42" plasma HDTV

Symptoms:
My system boots up fine and the resolution is at 1920x1080, but the gnome desktop does not fit the screen, due to the TV overscan issues. My TV does not have an option to disable overscan BTW

Next I create a custom modeline, but at this stage I don't attempt to change the parameters to try to fix the overscan. When X starts up it is unable to validate my modeline, rejects it and reverts to a default, 1024 768. In xlog.txt I see the messages:

(II) NVIDIA(0): Assigned Display Device: TV-0
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "1920x1080_30"
(WW) NVIDIA(0): No valid modes for "1920x1080_30"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".

As regards the modeline, I have created the custom modeline by the following three ways:

1. modeline extracted from infomration in the xlog.txt (as per your how-to guide)
2. Using 'Modeinfo' (from author of Powerstrip) I connected a laptop to my TV via DVI and had Modeinfo read the EDID information from my TV
3. used 'gtf 1920 1080 30" to build the modeline.

I tried the three modelines created above, but all fail to validate.

At this point I am at a complete loss as to what to try next. Do you (or anyone else reading this thread) have any idea?

I will attach my xorg.conf and the xlog.txt files,

thanks

---

### Post by bbear1 on 2009-02-06
Hi, I wanted to provide some more information, the following is a description of what I see happen on my system if I first start off with the original xorg.conf (from the original Ubuntu install) and then copy over my modified xorg.conf (the one in the zip file attached to my previous message). Maybe this will give some clues as to what might be going wrong:

Initially I boot system with original xorg.conf installed. My system comes up and I can see the gnome desktop on my TV and I make the following observations:

1. My plasma HDTV displays a blue colored desktop instead of the usual brown color scheme.
2. Under the 'Screen Resolution' tab (under system->preferences/admin (can't recall which one), I see that it is running at 1024x768. (and since my TV doesn't officially support this resolution then I assume this is why the colors are all messed up).
3. The gnome desktop fills my whole screen, so the dpi seems to have been adjusted automatically by the driver.
4. Under the nvidia settings (under System tab), I see a slider which enables me to adjust the overscan. This important to note, as it is this slider that magically disappears later on when I modify the xorg.conf.
5. Under 'Screen Resolution' and nvidia settings, the maximum resolution offered is 1024x768

Next I edit my xorg.conf to add a modeline to describe the 1920x1080 resolution (see xorg.conf included in the zip file attached to my previous message). I reboot my system and it comes up and I make the following observations:

1. The gnome desktop is the correct color
2. The desktop is in the center of the screen and takes up about half the screen (the driver must be using a dpi which is different to when I used the original xorg.conf)
3. Under the 'Screen Resolution' tab, the max resolution offered is still 1024x768 and I can see that this currently what it is running at.
4. Under the nvidia settings (under System tab), I see that more resolutions are now available, including 1920x1080, 1280x1024, 1280x720.
5. Under the nvidia settings, the overscan slider is no longer there !!
6. Under the nvidia settings I select 1920x1080 and hit 'apply'. My screen resizes to 1920x1080, however due to the overscan issue I cannot see the buttons at the top/bottom of my screen
7. Under 'Screen Resolution', I now see the other resolution settings available (1920x1080, 1280x1024, 1280x720)
8. Checking the Xlog I can see that the nvidia driver was unable to validate my custom modeleine and did the auto-select thing.

So, to summarize:

I am able to setup the driver to display at 1920x1080 but in doing so, the 'overscan' slider disappears from the nvidia setting panel. Even though my modified xorg.conf enables me to get a 1920x1080 desktop, the custom modeline is being rejected. This prevents me from adjusting the timing to fix the overscan. However, IF I could prevent the 'overscan' slider from disappearing from the nvidia settings panel in the first place, I would not need to describe custom timings in the modeline anyway.

If anyone has any ideas/suggestions please let me know.

thanks

---

### Post by gzusrawx on 2009-02-12
Have any of you noticed that you picture periodically shifts slightly? It makes it a pain to do this. I also found that my horizontal resolution (1280) is required to be divisible by 8 which also makes it difficult. Other than that it works, it's just every once in a while, my screen will shift and a blue line on the right will show, or a yellow line on the left. Any help would be greatly appreciated. Thanks,

Tim

---

### Post by bbear1 on 2009-02-12
Tim,

sorry but I can't comment on  your observations, as I am still struggling to fix the overscan issues on my system.

I have got nowhere with tweaking the xorg.conf to fix the overscan issue. I stumbled across a post to the nvidia forums by an Nvidia employee, he said that your can't use custom modelines when you are using the Component video output. If this is true then it must be my problem.

I don't have DVI or HDMI available on my HDTV so I have to use component input. I am currently looking into building a custom EDID .bin file then loading that via my xorg.conf file.

I can't believe it is so incredibly difficult to get video on Linux to be correct on my TV.

It still bothers me though that at one point I saw an 'overscan' slider in the nvidia-settings GUI but after loading my xorg.conf I never see that option again.

---

### Post by gzusrawx on 2009-02-22
Yah I came to the conclusion that it's the built-in pixel shifter (one of the anti-image retention features).

---

### Post by bbear1 on 2009-03-12
Hi,
I just thought that I better close the loop ..

finally I have managed to fix the overscan issue on my 8.10 system. I had to give up on the idea of using the component output from my computer as I came to the conclusion that you cannot use anything but the built-in defaults of the nvidia driver (HD1080i), HD720P, etc). It doesn't matter if you try to force the driver to use a custom EDID, it silently ignores it!

So, I went out and bought a DVI to HDMI cable and connected that between my 8.10 and my 42" Panasonic plasma HDTV. I read the edid from the TV (using nvidia-settings) and then proceded to create a custom EDID from that. In my xorg.conf that force the nvidia driver to use the custom EDID file.

I had some major issues figuring out what to put in the EDID, so I put together an Excel spreadsheet into which you type in by hand the hex values which are dumped from the original EDID. The spreadsheet then interprets this and prints out the various timing parameters and also the corresponding modeline equivalent.

Then, you just type in the modeline you desire and it converts it back to bytes (based on the Vesa EDID spec) and prints out the new EDID hex values. I then use a hex editor and create the new edid.bin file. This is then loaded as a custom edid by referencing it in the xorg.conf.

The spreadsheet is a bit clunky but it works and saved me hell of a lot of time. Also, at one point I used MonInfo (from the Powerstrip authors) and discovered that actually had a bug in it anyway and couldn't always be trusted. It is still a great free tool, but does have a bug with not correctly extracting the VSYNC Start timing from the EDID.

If anyone needs more info, or wants a copy of my spreadsheet then let me know.

BTW, although I didn't have a spare HDMI input on my TV, I decided to go the HDMI route and later I will buy a HDMI switch with IR remote. This way I can program my Harmony One remote to do the switching for me automatically when I switch between watching a DVD and using my Ubuntu box.

---

### Post by TheMono on 2009-03-14
> **hpadrick said:**
> I am pasting the instructions in here for searchs, but they will be hard to read.  I suggest downloading the attachment.  It's just an openoffice file gzipped.

(snip)



You sir are a god amongst men. You have my eternal gratitude. Thanks very much for taking the time to write that, I'm no longer stuck in Windows on my Bravia.

---

### Post by Gorthaur on 2009-03-21
Hello!

I've been following the instructions to set up the TV screen correctly and dealing with the overscan issue. I have a Panasonic Viera TC-32LX70L HD TV. When I change the values of "H2" and "H3" in order to move the screen to the right it doesn't work. Actually when I changed the vertical values "V2" and "V3" the screen was adjusted an it work, but not for the horizontal values. What should I do?

Thank you.

---

### Post by bbear1 on 2009-03-21
Are you just specifying the modeline in the xorg.conf or are you using custom EDID file? (not that it should make any difference)

Have you looked in the xlog to check that your modeline is being validated ok?

Only other thought is that older nvidia drivers (that's if you are using nvidia) needed the horizontal values to be evenly divisible by 8

If you want to provide your modeline I can try plugging into my spreadsheet and see what are the corresponding timing numbers it reports.

---

### Post by Gorthaur on 2009-03-21
> **bbear1 said:**
> Are you just specifying the modeline in the xorg.conf or are you using custom EDID file? (not that it should make any difference)

Have you looked in the xlog to check that your modeline is being validated ok?

Only other thought is that older nvidia drivers (that's if you are using nvidia) needed the horizontal values to be evenly divisible by 8

If you want to provide your modeline I can try plugging into my spreadsheet and see what are the corresponding timing numbers it reports.

BBear1 thank you for your fast response.

I'm talking about a modeline I made in the xorg.conf file. This is the file:

Section "Monitor"
	Identifier "PANASONIC-TV"
	Option "ExactModeTimingsDVI" "TRUE"
	HorizSync 15-45
	VertRefresh 59-61
	modeline "720x480" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync
# orig modeline "1280x720" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
	modeline "1280x720" 74.25 1150 1313 1353 1650 600 713 718 750 +hsync +vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"PANASONIC-TV"
	Device		"gForce8600MGS"

SubSection "Display"	
	Depth	24
	Modes "1280x720"
EndSubSection

EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"gForce8600MGS"
	Driver	"nvidia"
	Option	"NoLogo" "FALSE"
	Option "UseEDID" "FALSE"
EndSection

For the TV I'm using the "1280x720" modeline.

Even though I'm reducing the value of "H2" and "H3" there is no change in the TV. The overscan in the left is the same no matter how much I change the numbers. Is weird that I correct the vertical overscan with the same method but it doesn't work for the vertical.

This is my second day with ubuntu on my PC. I've never used it before, so there are many functions I don't know how to use yet,

In the xlog file this modeline was validated.

Thank you again for your help in this matter.

---

### Post by bbear1 on 2009-03-22
I cannot spot anything obvious. You are keeping the same HTotal value and the Hsync_width is still 40. Only thought is that perhaps you are violating some limit of the monitor itself and it is reverting to a default modeline, but if that was the case you would not see your modeline as validated on the Xlog.

I have read reports where the nvidia driver doesn’t always obey the users modeline, even if you add the switches like ‘ExactModeTimingsDVI’, which I see that you are already using. If that was the case then the way round it is to use a custom EDID, which is what I am doing.

One thing that might be worth trying is to dump the EDI from your monitor as sometimes the manufacturers EDID is bad. I did this by connecting my TV to my laptop (windows box) and running Moninfo (available from Powerstrip website):

[http://entechtaiwan.com/util/moninfo.shtm]("http://entechtaiwan.com/util/moninfo.shtm")

Alternatively you can use the nvidia-settings GUI and dump the EDID from there. You would still need to analyze the EDID (.bin/.raw) file in some program and I would still reconnect Moninfo. Note that Moninfo does have a bug with it not always reporting the vsync width correctly. But for the purposes of dumping the manufacturers data for timing limits, the program if just fine.

In the Xlog you can see the manufacturers data, or at least some of it so you may not need to use Moninfo but I found it quite a handy utility and the report is very easy to understand.

If you want to try the custom EDID method I can help you with that.

---

### Post by Gorthaur on 2009-03-22
Hello BBear1!

Even though I don't have the knowledge to do an EDID myself I would like to try it with your help. Please tell me what info is needed or has to be done in order to start.

I will try to search for EDID so at least I'm informed.

Thank you for your help.

---

### Post by bbear1 on 2009-03-22
The first step is to capture the EDID from your TV, you can do this from a windows box uisng Moninfo, or from your Ubuntu box as follows ..

System -> Administration -> Nvidia X Server Settings

Go to the GPU-0 tab, then the tab for your screen (in my case DFP-0). You should see an option Acquire EDID - select this and save to a file. This is the binary/raw EDID data from your TV.

Next, load this into Monifo and check the decoded values for the timing look ok. (you can also use parse-edid on your Ubunto box if you don't have access to a windows machine to run Monino. I can't remember how much detail parse-edid gives you however).

To customize the EDID you need to load the .bin/raw file into a hex editor. I use Hex Editor Neo from:

[http://www.hhdsoftware.com/]("http://www.hhdsoftware.com/")

There are also hex editors for Linux, hexedit is one that you should be able to download via the Synaptic Package manager.

Before you can change the hex bytes in your hex editor you need to figure out what the new values should be and calculate the new checksum bytes for each descriptor set. I wrote an Excel spreadsheet to do this, but you can also work it out manually. For the technical details do a search for 'VESA EDID' and you should find links to the standards documents for EDID. It is a bit tricky and if you make a mistake and send invalid timing parameters to your TV it can result in damage! (most new monitors I suspect protect against damage, but I add the disclaimer here anyway)

Once you have customised your EDID in your hex editor you need to save it back to a .bin file, then modify your xorg.conf to load your custom EDID, here is an extract from my xorg.conf as an example:

Section "Monitor"
	Identifier	"Configured Monitor"
	Option	"DPMS"	"false"
        Option  "ConnectedMonitor" "DFP"
        Option  "UseEDID" "TRUE"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        Option "AddARGBGLXVisuals" "true"
        Option "UseDisplayDevice" "DFP-0"
        Option "CustomEDID" "DFP-0:/etc/X11/custom_edid.bin"
	DefaultDepth	24
        SubSection "Display"
          Depth 24
          Modes "1840x1040"
        EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier "Configured Video Device"
        Option "UseEvents" "true"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

When you first load the custon EDID I suugest you enable verbose reporting for your Xlog, presumably you know how to do this? If not then I will dig out the instructions.

If you want to use my spreadsheet let me know, I can send it to you.

---

### Post by bbear1 on 2009-04-19
For those who are interested, I will attach my Excel spreadsheet. In addition it needs a 3rd party plug-in to be installed, this is called 'Morefunc' and is available as a free download. It provides additional HEX functions without which would have made the spreadsheet much harder to put together.

Morefunc can be downloaded from the following site:

[http://xcell05.free.fr/morefunc/english/index.htm]("http://xcell05.free.fr/morefunc/english/index.htm")

I wrote the spreadsheet for my personal use so there is no built-in documentation. Also, I have not built in any 'safety checks' so if you plug in some stupid numbers then it will give unexpected (but hopefully obvious) results.

The way I used is was to start my reading the EDID of my monitor using the nvidia-settings gui. Then I opened up the resulting .bin file using a binary viewer/editor. I used Hex Editor Neo on my PC, this is a great utility and is also free.

Hex Editor displays the binary data as hex bytes, and I then types these hex values into the spreadsheet. The spreadsheet then interprets the data and displays the timing values and the corresponding modeline.

In the bottom half of the spreadsheet there is a section where you can enter your own modeline, and as you type the modeline values the spreadsheet calculates the new timing values and fills in the new hex bytes and also calculates the new checksum byte which has to in the end of each descriptor block.

The spreadsheet only handles two descriptor blocks but could easily be expanded to more. The EDID for my HDTV only had two descriptor blocks in the EDID data, one for 720p and one for 1080i

After entering my custom modeline I then use Hex Editor to edit a copy of the original .bin file, I enter the new hex values calculated by the spreadsheet. After I have checked I entered the data correctly I save the .bin file and then as a sanity check I load it into Moninfo

Usually the modeline that Moninfo reports is correct but I have occasionally hit on some Vsync timing values which trigger a bug in the program. This is definitely a bug in the Moninfo program and not my spreadsheet. I confirmed this by manually checking my values against the VESA spec for EDID and also looked at the timing values as interpreted by X when it loaded my custom EDID .bin file.

Even though Moninfo has some quirks it is still a useful program to gather some data from the raw EDID (.bin) file. Monifno can be downloaded from the following location:

[http://entechtaiwan.com/util/moninfo.shtm]("http://entechtaiwan.com/util/moninfo.shtm")

(it is the program referred to as ‘Monitor Asset Manager’)

I will follow this post up later with some tips on how to use the spreadsheet.

---

### Post by David Valentine on 2009-04-27
Thanks for the great howto.  I found a way to circumvent the iterations needed to get the right screen size if you're running mythtv.  The following works for Mythbuntu 9.04.

1.  Follow the directions up through generating the new modelines in /etc/X11/xorg.conf.  You can probably skip the low resolution modeline as we won't use it.  
2.  Start MythTV.  From the top menu, navigate to Utilities/Setup, then Setup, then Screen Setup Wizards.  
3.  Use down and right arrows while watching the upper left corner of your screen.  A shaded right triangle will appear, with the right angle highlighted in white.  Use your arrows to position the point of the right angle at the upper left corner of your screen.  Hit enter, then do the same thing for the lower right corner of your screen.
4.  Write down the Size and Offset numbers.  
5.  Edit /etc/X11/xorg.conf.  The two Size numbers become your new H1 and V1 in your high resolution modeline.  Then subtract the first offset number from both H2 and H3 to get your new H2 and H3 values.  Finally, subtract the second offset number from both V2 and V3 to get your new V2 and V3 values.  Save xorg.conf.
6.  Restart X, and enjoy your right-sized screen.

---

### Post by NateMan on 2009-05-01
I too am having problems with nvida overscan issues. I've tried to fix my modelines and xorg.conf on my media center pc but to no avail. It appears that my xorg.conf file is not reading my modelines, since changing them seems to have no affect. Here is a copy of my xorg.conf.I would love to get this modeline problem fixed so that I can truly enjoy my newly setup ubuntu. 

Thank you in advance.

---

### Post by jt_04 on 2009-05-02
> **hpadrick said:**
> And you should be looking at the login screen and actually seeing the time on the bottom right!

I can't thank you enough.  I roughly followed your guide and was able to get 1920x1080 with no overscan on my Sony Bravia 40" (model KDL-40S4100).  I have been struggling with this for weeks.

I used your command:

```
X -verbose 6 > ~/xlog.txt 2>&1
```

to pull out the TV's modelines from the EDID info (i think I could have just looked at /var/log/Xorg.0.log too).   

somehow during this I found the Nvidia X-server gui was correctly detecting that I have a 1920x1080 mode.  I generated an xorg.conf file by hitting "Save to X Configuration File" in Nvidia X-Server Settings under "X Server Display Configuration".  the xorg.conf file it saved had the proper 1920x1080 modeline in it, because I verified it against the output from the command above.  the problem was that it was defaulting to 1024x768 because X didn't like the refresh rate of that modeline or something. 

at first, i was confused because I had two screens in my xorg.conf file and I could tell which one was being used.  then i read up on the xorg.conf file and figured out that the screen to be used is specified in the "ServerLayout" section.  I just had to point that screen line to the right screen.

then i had to add the options 

>     Option	   "ExactModeTimingsDVI" "TRUE"
    Option "ModeValidation" "NoEdidModes"

to stop the X server from validating the modes against the EDID info.  after that, it started in 1920x1080 just fine, with some overscan.

I knew from windows that I needed an 1824x1028 resolution to fit my TV.  I modified the 1920x1080 modeline to use this resolution, which worked perfect.  then I adjusted H2 H3 V2 V3 as you said to make the screen fit.

beautiful!  I've now got Ubuntu 9.04 (64-bit) running on my M3N78-EM motherboard with a Nvidia 9400GT card with a HDMI connection (with audio) to my Sony Bravia 40".  :):)

here is my xorg.conf if anyone cares:

> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Tue Mar 24 06:15:32 PST 2009

Section "ServerLayout"
    Identifier     "Default Layout"
#    Screen      0  "Screen0" 0 0
    Screen      0  "Sony Bravia KDL40S4100" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
    Option	   "DontZap" "no"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "KDL40W4100"
    HorizSync       15.0 - 70.0
    VertRefresh     58.0 - 62.0
    Modeline	   "1024x768" 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
#    ModeLine       "1920x1080" 148.50 1919 2030 2052 2201 1080 1084 1089 1125 +hsync +vsync
    ModeLine       "1920x1080" 148.50 1826 1982 2004 2201 1028 1058 1063 1125 +hsync +vsync
    Option         "DPMS" "FALSE"
    Option         "DPI" "100x100"
    Option	   "ExactModeTimingsDVI" "TRUE"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       15.0 - 70.0
    VertRefresh     58.0 - 62.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400 GT"
    Option "ModeValidation" "NoEdidModes"
EndSection

Section "Screen"
    Identifier     "Sony Bravia KDL40S4100"
    Device         "Device0"
    Monitor        "KDL40W4100"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1920x1080"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

### Post by feh on 2009-05-11
I just wanted to let the community know that the following options corrected overscan for my setup as well:

Option "ExactModeTimingsDVI" "TRUE"
Option "ModeValidation" "NoEdidModes"

I spent a week googling and trying everything under the sun to avoid the overscan on my HDTV connected to the HDMI output of an ASUS motherboard w/ a GeForce 8200 GPU on it. The above options (along with appropriate modelines) resulted in a perfectly sized screen.

Thanks!

---

### Post by orduek on 2009-05-15
thank you very much for this post.
I finally got my Nvidia working with DVI-->HDMI connection and not VGA.
Thanks again.

---

### Post by AiRAVATA on 2009-05-27
I have the following problem:

I have a laptop (nVidia) with hdmi out and I want to connect it to hdmi tv, not to be the principal monitor, but to be a clone (so I can watch movies). Now, I've done all the steps of the guide but I'm not sure how to modify my xorg.conf file in order for this to work.

Here is my xorg config:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: 1280x720 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Robotron3000 on 2009-06-11
ModeLine       "1920x1080" 148.50 1826 1982 2004 2201 1028 1058 1063 1125 +hsync +vsync

The above modeline that I grabbed from one of the previous posts worked like a charm on my Sony Bravia KDL 40W4000 under Ubuntu 9.04 Drunken Octopus (or whatever silly name this version has).

I am running an onboard nvidia 9400m on a Gigabyte E7AUM-DS2H with the closed source nvidia drivers.

Thanks to everybody who posted solutions in this thread.

(this post mostly made to thank people and get the KDL 40W4000 and correct modeline listed in a way that is findable by search engines).

/Robotron3000

---

### Post by NateMan on 2009-06-14
I've been working on this problem with my tv for some time now, and I'm finally close I believe to being able to fix my overscan, I have some confusion about using this method with twinview, despite the best try. I was able to get the factory modeline, as well as configure the display. When I tell it to not use edid, however, I can't get a picture onto my larger monitor. It acts like its not even getting a display. If I use the edid, of course I get no benefit. It seems like this guide would be perfect if it had some explanation of how to do this with a twinview setup since many media centers use dual monitors.

Here is my xorg.conf:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
   Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL P1130"
    HorizSync       30.0 - 130.0
    VertRefresh     48.0 - 170.0
    Option         "DPMS" "FALSE"
EndSection

Section "Monitor"
    Identifier     "PANASONIC-MMD"
    VendorName     "Unknown"
    ModelName      "PANASONIC-MMD"
    HorizSync      15.0 - 46.0
    VertRefresh    59.0 - 61.0
    ModeLine "1280x720" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
    #ModeLine "1280x720" 74.25 1180 1390 1430 1650 620 725 730 750 +hsync +vsync
    Option "ExactModeTimingsDVI" "TRUE"
    Option "DPMS" "FALSE"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    Option "ModeValidation" "NoEdidModes"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: 2048x1536_60 +1280+0, DFP: 1280x720_60 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "true"
    Option         "CursorShadow" "true"
    Option         "MigrationHeuristic" "greedy"
    Option         "TripleBuffer" "true"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT: 2048x1536_60 +1280+0, DFP: 1280x720_60 +0+171"
    SubSection     "Display"
        Depth       24
        Modes "1280x720"
    EndSubSection
EndSection
```

Also if it helps, here is the part of the xlog I used to generate the modeline. 

```
Panasonic 
HorizSync   : 15.000-46.000 kHz
VertRefresh : 59.000-61.000 Hz

(II) NVIDIA(0):   Validating Mode "1280x720":
(II) NVIDIA(0):     1280 x 720 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1390
(II) NVIDIA(0):       HSyncEnd, HTotal : 1430, 1650
(II) NVIDIA(0):       VRes, VSyncStart :  720,  725
(II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
```


Any help would be greatly appreciated since this problem has been driving me mad. Thanks in advance.

---

### Post by loomsen on 2009-06-14
oops, wrong forum :D

---

### Post by ffaker on 2009-06-15
Just wanted to mention this solution worked for me too, so thanks hpadrick!

I have a MythTV box connecting to a Toshiba LCD TV via HDMI. It was overscaned but now works and looks great.

---

### Post by jbol66 on 2009-07-02
I followed hpadrick's excellent method for editing the xorg.conf and have this problem - I get a good result with X but then when I start gdm I can see it starting (brown screen and pointer) but after a few seconds my tv blue screens on me (I guess it is rejecting the input).
I have a 42" Vizio on a zotac MB with nvidia running intrepid. Actually the 720x480 will display but 1280x720 and 1920x1080 won't. 
Several of my EDID entries have this note : 
(WW) NVIDIA(0): The EDID for VIZ GV42L HDTV (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "720x576" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid HorizSync range (31.000-70.000 kHz) would exclude
(WW) NVIDIA(0):     this mode's HorizSync (15.6 kHz); ignoring HorizSync check
(WW) NVIDIA(0):     for mode "720x576".
(II) NVIDIA(0):     Mode is valid.

Makes me wonder If I am getting some bogus frequency values

---

### Post by bsautner on 2009-07-08
hpadrick's fix worked great to repair the overscan problem with my 9800gtx on ubuntu 9.04 - DVI to HDMI Cable connecting to a AVR reciever which displayed on a sharp aquos 1080p

Best part was the wacked out settings turned out to be exactly what i needed. 

Thanks!

---

### Post by shaunburrows on 2009-07-12
Thanks for the great guide!

Worked after I figured out I needed multiples of 8 (thanks bbear1), and didn't make my numbers too whacked out.

As a tip take 5% off the resolution (the standard overscan amount I think), this gave almost the spot on res I needed.


For 9.04 users who want to be able to use ctrl-alt-backspace to restart x (dunno why they removed it), just add 

Section "ServerFlags"
Option "DontZap" "false"
EndSection

to xorg.conf

---

### Post by Bushwhacker on 2009-07-26
Hey everyone... that is if anyone is still checking out this thread. I needed to do this on my TV, but as I think someone mentioned earlier, the verbose output when using component output doesnt give any EDID info. Since I didn't even get passed that, I didn't want to tinker yet. All the modes listed are just created by Nvidia. Should I try using these?

Has anyone done any of this with component out? Even the S-video wouldn't give me EDIDs, but a DVI cable is like 70 bucks and it seems there is a way to make this work.

Thanks

---

### Post by B-Ionic on 2009-07-30
As alot before me has stated: Thanks hpadrick for a brilliant guide...

Still I have a problem that has given me alot of grey hair:

All works fine up to the point where I want to start X
> ...issuing the most complicated *nix command ever written: 
X

At this point I get a completely black screen and nothing seems to happen.

My workaround was to instead do a sudo /etc/init.d/gdm start

Voila, I get the login screen, and apparently it reads my modelines H1 and V1 parameters as the visible area gets smaller/larger according to my changes of theese modeline parameters.

This is where I am at a dead stop. The visible area gets decreased from the lower right corner. Hence I want to move the visible area to the right, according to the instruction I should decrease H2 and H3 with the same amount to move the visible area to the right. (or the same with V2 and V3 to move down)

Nothing happens when I change H2, H3 or V2, V3 ?!?!?

What am I doing wrong??

Basic setup:
Aspire Revo3600 with nVidia Ion
HDMI connected to..
LG Plasma 50PG6900

Unbuntu 9.04

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder57)  Thu Jul 23 05:55:42 PDT 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Thu Jul 23 05:53:56 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BSE LS_V20/30"
    HorizSync       14-68
    VertRefresh     48-62
    Option         "DPMS"
    Option         "ExactModeTimingsDVI" "TRUE"
    ModeLine       "720x480" 27.00 720 736 798 858 480 486 492 525 -hsync -vsync
    #KEY Modeline        "MODENAME"  FF    H1   H2   H3   H4   V1  V2  V3  V4 FLAGS
    # org ModeLine       "1280x720" 74.18 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
    ModeLine             "1280x720" 74.18 1240 1340 1380 1650 690 725 730 750 +hsync +vsync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION"
    Option         "ModeValidation" "NoEdidModes"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    # Option         "metamodes" "1280x720 +0+0"
    SubSection     "Display"
        Depth       24
        Modes "1280x720"
    EndSubSection
EndSection

```

---

### Post by roundhay on 2009-07-31
I am having problems getting the resolution correct. I have a 40" Sony KDL-40W4000 LCD and an Onkyo TX-SR605 receiver. I run an HDMI cable from my Nvidia Geforce 7600 GS card to the receiver and then to the TV.

The saved xorg.cong file (system > admin > NVIDIA X Server Settings then Save to X config file) is below:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ONK TX-SR605"
    HorizSync       14.0 - 70.0
    VertRefresh     48.0 - 62.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "UseEvents" "1"
    Option         "DPI" "100x100"
    Option         "NoLogo" "1"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The output from Xorg.0.log is:
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux htpc-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 31 19:59:44 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP: nvidia-auto-select +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.81
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     ONK TX-SR605 (DFP-1)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-1
(WW) NVIDIA(0): The EDID for ONK TX-SR605 (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(WW) NVIDIA(0): The EDID for ONK TX-SR605 (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "DFP:nvidia-auto-select+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Mouse? 1.0A
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Device: "/dev/input/event5"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Configuring as mouse
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse? 1.0A" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) set acceleration profile 0
```

From reading this thread I believe the correct Modelines for the Sony are:

Modeline "1024x768" 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
and
ModeLine "1920x1080" 148.50 1826 1982 2004 2201 1028 1058 1063 1125 +hsync +vsync

But I can't get system to work when I modify the xorg.conf I get errors and enter low res mode. I have tried several variants but get the same error.

Does anyone have any idea how I can modify my xorg.conf file to correct the resolution?

---

### Post by roundhay on 2009-08-01
Can anyone help?

---

### Post by jt_04 on 2009-08-02
> **roundhay said:**
> Can anyone help?

The [modeline database]("http://www.mythtv.org/wiki/Modeline_Database") has these lines for the 40W4000:

> Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    DisplaySize    884 495
    HorizSync      31.5 - 64.0
    VertRefresh    60.0 - 75.0
    Option         "DPMS"
    Option         "RenderAccel"
    ModeLine       "1920x1080" 148.50 1920 2448 2492 2640 1080 1084 1089 1125 +HSync +VSync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9400"
    Option         "ModeValidation" "NoMaxPClkCheck, AllowNon60HzDFPModes, NoVirtualSizeCheck, NoEdidMaxPClkCheck, NoMaxSizeCheck, NoHorizSynCheck, NoVertRefreshCheck, NoWidthAlignmentCheck, NoExtendedGpuCapabilitiesCheck, NoTotalSizeCheck"
    Option         "UseEDID" "False"
    Option         "NoBandWidthTest" "True"
EndSection


and don't forget to try putting these lines in your xorg "Monitor" section:
```
Option "ExactModeTimingsDVI" "TRUE"
```
and Device section:
```
Option "ModeValidation" "NoEdidModes" 
```

those options helped me get my Sony TV working.  You can also try to self-discover your modelines by reading Post #11 in this thread.

In general, what worked for me was to strip my xorg to the barebones (use the nvidia gui to generate a clean xorg).  then start adding in pieces bit by bit - nvidia card first, then monitor, etc.  then when it fails you know exactly what piece is the culprit.

---

### Post by roundhay on 2009-08-03
I have tried tweaking the xorg.conf file agin but I still can't get the resolution correct. I may be going about this incorrectly as the PC is connected to the Onkyo receiver not the Sony TV.

I ran X -verbose 6 > ~/xlog.txt 2>&1 and the complete output is below, I still trying to figure out how to use this data correctly and am not confident I understand what I need to do?
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux htpc-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug  3 18:24:06 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G70 [GeForce 7600 GS] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) NVIDIA X compatibility module for ABI 5.0 built from xorg-server-1.5.99.901
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP: nvidia-auto-select +0+0"
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(II) NVIDIA(0): GPU RAM Type: DDR2
(--) NVIDIA(0): VideoBIOS: 05.73.22.51.81
(--) NVIDIA(0): Found 2 CRTCs on board
(II) NVIDIA(0): Supported display device(s): CRT-0, DFP-0, DFP-1, TV-0
(II) NVIDIA(0): Bus detected as PCI Express
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): VPES : 5
(II) NVIDIA(0): SPS  : 12
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing constraints for  : GeForce 7600 GS
(II) NVIDIA(0): Maximum mode timing values   :
(II) NVIDIA(0):     Horizontal Visible Width : 8192
(II) NVIDIA(0):     Horizontal Blank Start   : 8192
(II) NVIDIA(0):     Horizontal Blank Width   : 4096
(II) NVIDIA(0):     Horizontal Sync Start    : 8184
(II) NVIDIA(0):     Horizontal Sync Width    : 504
(II) NVIDIA(0):     Horizontal Total Width   : 8224
(II) NVIDIA(0):     Vertical Visible Height  : 8192
(II) NVIDIA(0):     Vertical Blank Start     : 8192
(II) NVIDIA(0):     Vertical Blank Width     : 256
(II) NVIDIA(0):     Veritcal Sync Start      : 8191
(II) NVIDIA(0):     Vertical Sync Width      : 15
(II) NVIDIA(0):     Vertical Total Height    : 8193
(II) NVIDIA(0): 
(II) NVIDIA(0): Minimum mode timing values   :
(II) NVIDIA(0):     Horizontal Total Width   : 40
(II) NVIDIA(0):     Vertical Total Height    : 2
(II) NVIDIA(0): 
(II) NVIDIA(0): Mode timing alignment        :
(II) NVIDIA(0):     Horizontal Visible Width : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Start   : multiples of 8
(II) NVIDIA(0):     Horizontal Blank Width   : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Start    : multiples of 8
(II) NVIDIA(0):     Horizontal Sync Width    : multiples of 8
(II) NVIDIA(0):     Horizontal Total Width   : multiples of 8
(II) NVIDIA(0): 
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     ONK TX-SR605 (DFP-1)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): TV modes supported by this encoder:
(II) NVIDIA(0):   1920x1080; Standards: HD1080i
(II) NVIDIA(0):   1280x1024; Standards: HD1080i
(II) NVIDIA(0):   1280x720; Standards: HD720p, HD1080i
(II) NVIDIA(0):   1024x768; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI,
(II) NVIDIA(0):     PAL-N, PAL-NC, HD480i, HD720p, HD1080i, HD576i
(II) NVIDIA(0):   800x600; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC, HD480i, HD480p, HD720p, HD1080i, HD576i, HD576p
(II) NVIDIA(0):   720x576; Standards: PAL-BDGHI, PAL-N, PAL-NC, HD576i,
(II) NVIDIA(0):     HD576p
(II) NVIDIA(0):   720x480; Standards: NTSC-M, NTSC-J, PAL-M, HD480i, HD480p,
(II) NVIDIA(0):     HD720p, HD1080i
(II) NVIDIA(0):   640x480; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC, HD480i, HD480p, HD720p, HD1080i, HD576i, HD576p
(II) NVIDIA(0):   640x400; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC, HD480i, HD480p, HD720p, HD1080i, HD576i, HD576p
(II) NVIDIA(0):   400x300; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC, HD480i, HD480p, HD720p, HD1080i, HD576i, HD576p
(II) NVIDIA(0):   320x240; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC, HD480i, HD480p, HD720p, HD1080i, HD576i, HD576p
(II) NVIDIA(0):   320x200; Standards: NTSC-M, NTSC-J, PAL-M, PAL-BDGHI, PAL-N,
(II) NVIDIA(0):     PAL-NC, HD480i, HD480p, HD720p, HD1080i, HD576i, HD576p
(--) NVIDIA(0): ONK TX-SR605 (DFP-1): 165.0 MHz maximum pixel clock
(--) NVIDIA(0): ONK TX-SR605 (DFP-1): Internal Single Link TMDS
(--) NVIDIA(0): ONK TX-SR605 (DFP-1): Native FlatPanel Scaling is supported
(--) NVIDIA(0): ONK TX-SR605 (DFP-1): DFP modes are not limited to 60 Hz
(--) NVIDIA(0):     refresh rate
(--) NVIDIA(0): ONK TX-SR605 (DFP-1): DFP is not internal to notebook
(--) NVIDIA(0): 
(--) NVIDIA(0): --- EDID for ONK TX-SR605 (DFP-1) ---
(--) NVIDIA(0): EDID Version                 : 1.3
(--) NVIDIA(0): Manufacturer                 : ONK
(--) NVIDIA(0): Monitor Name                 : ONK TX-SR605
(--) NVIDIA(0): Product ID                   : 1889
(--) NVIDIA(0): 32-bit Serial Number         : 0
(--) NVIDIA(0): Serial Number String         : 
(--) NVIDIA(0): Manufacture Date             : 2007, week 0
(--) NVIDIA(0): DPMS Capabilities            :
(--) NVIDIA(0): Prefer first detailed timing : Yes
(--) NVIDIA(0): Supports GTF                 : No
(--) NVIDIA(0): Maximum Image Size           : 1600mm x 900mm
(--) NVIDIA(0): Valid HSync Range            : 14.0 kHz - 70.0 kHz
(--) NVIDIA(0): Valid VRefresh Range         : 48 Hz - 62 Hz
(--) NVIDIA(0): EDID maximum pixel clock     : 150.0 MHz
(--) NVIDIA(0): 
(--) NVIDIA(0): Established Timings:
(--) NVIDIA(0):   800  x 600  @ 60 Hz
(--) NVIDIA(0):   1024 x 768  @ 60 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Standard Timings:
(--) NVIDIA(0):   1280 x 1024 @ 60 Hz
(--) NVIDIA(0): 
(--) NVIDIA(0): Detailed Timings:
(--) NVIDIA(0):   1920 x 1080 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 148.50 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
(--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   1280 x 720  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1390
(--) NVIDIA(0):     HSyncEnd, HTotal : 1430, 1650
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   1920 x 1080 @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 148.50 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2448
(--) NVIDIA(0):     HSyncEnd, HTotal : 2492, 2640
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):   1280 x 720  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1720
(--) NVIDIA(0):     HSyncEnd, HTotal : 1760, 1980
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0): 
(--) NVIDIA(0): CEA-861B Timings:
(--) NVIDIA(0):   1920 x 1080 @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 148.50 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2448
(--) NVIDIA(0):     HSyncEnd, HTotal : 2492, 2640
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 31
(--) NVIDIA(0):   1920 x 1080 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 148.35 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
(--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 16
(--) NVIDIA(0):   1920 x 1080 @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2448
(--) NVIDIA(0):     HSyncEnd, HTotal : 2492, 2640
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1094, 1124
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 20
(--) NVIDIA(0):   1920 x 1080 @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.18 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
(--) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1094, 1124
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 5
(--) NVIDIA(0):   1280 x 720  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.25 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1720
(--) NVIDIA(0):     HSyncEnd, HTotal : 1760, 1980
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 19
(--) NVIDIA(0):   1280 x 720  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.18 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1280, 1390
(--) NVIDIA(0):     HSyncEnd, HTotal : 1430, 1650
(--) NVIDIA(0):     VRes, VSyncStart : 720, 725
(--) NVIDIA(0):     VSyncEnd, VTotal : 730, 750
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 4
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 732
(--) NVIDIA(0):     HSyncEnd, HTotal : 796, 864
(--) NVIDIA(0):     VRes, VSyncStart : 576, 581
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 625
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 18
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 732
(--) NVIDIA(0):     HSyncEnd, HTotal : 796, 864
(--) NVIDIA(0):     VRes, VSyncStart : 576, 581
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 625
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 17
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1464
(--) NVIDIA(0):     HSyncEnd, HTotal : 1590, 1728
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 22
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1464
(--) NVIDIA(0):     HSyncEnd, HTotal : 1590, 1728
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 21
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 736
(--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
(--) NVIDIA(0):     VRes, VSyncStart : 480, 489
(--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 3
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 720, 736
(--) NVIDIA(0):     HSyncEnd, HTotal : 798, 858
(--) NVIDIA(0):     VRes, VSyncStart : 480, 489
(--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 2
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1478
(--) NVIDIA(0):     HSyncEnd, HTotal : 1602, 1716
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 7
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 27.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1478
(--) NVIDIA(0):     HSyncEnd, HTotal : 1602, 1716
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 6
(--) NVIDIA(0):   640  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 25.17 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 640, 656
(--) NVIDIA(0):     HSyncEnd, HTotal : 752, 800
(--) NVIDIA(0):     VRes, VSyncStart : 480, 490
(--) NVIDIA(0):     VSyncEnd, VTotal : 492, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 1
(--) NVIDIA(0):   1920 x 1080 @ 24 Hz
(--) NVIDIA(0):     Pixel Clock      : 74.16 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1920, 2558
(--) NVIDIA(0):     HSyncEnd, HTotal : 2602, 2750
(--) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(--) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(--) NVIDIA(0):     H/V Polarity     : +/+
(--) NVIDIA(0):     CEA Format       : 32
(--) NVIDIA(0):   1440 x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1464
(--) NVIDIA(0):     HSyncEnd, HTotal : 1592, 1728
(--) NVIDIA(0):     VRes, VSyncStart : 576, 581
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 625
(--) NVIDIA(0):     H/V Polarity     : -/+
(--) NVIDIA(0):     CEA Format       : 30
(--) NVIDIA(0):   1440 x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1464
(--) NVIDIA(0):     HSyncEnd, HTotal : 1592, 1728
(--) NVIDIA(0):     VRes, VSyncStart : 576, 581
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 625
(--) NVIDIA(0):     H/V Polarity     : -/+
(--) NVIDIA(0):     CEA Format       : 29
(--) NVIDIA(0):   288  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 26
(--) NVIDIA(0):   360  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 26
(--) NVIDIA(0):   411  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 26
(--) NVIDIA(0):   576  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 26
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 26
(--) NVIDIA(0):   288  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 25
(--) NVIDIA(0):   360  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 25
(--) NVIDIA(0):   411  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 25
(--) NVIDIA(0):   576  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 25
(--) NVIDIA(0):   720  x 576  @ 50 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2928
(--) NVIDIA(0):     HSyncEnd, HTotal : 3180, 3456
(--) NVIDIA(0):     VRes, VSyncStart : 576, 580
(--) NVIDIA(0):     VSyncEnd, VTotal : 586, 624
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 25
(--) NVIDIA(0):   1440 x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1472
(--) NVIDIA(0):     HSyncEnd, HTotal : 1596, 1716
(--) NVIDIA(0):     VRes, VSyncStart : 480, 489
(--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 15
(--) NVIDIA(0):   1440 x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 1440, 1472
(--) NVIDIA(0):     HSyncEnd, HTotal : 1596, 1716
(--) NVIDIA(0):     VRes, VSyncStart : 480, 489
(--) NVIDIA(0):     VSyncEnd, VTotal : 495, 525
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     CEA Format       : 14
(--) NVIDIA(0):   288  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 11
(--) NVIDIA(0):   360  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 11
(--) NVIDIA(0):   411  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 11
(--) NVIDIA(0):   576  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 11
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 11
(--) NVIDIA(0):   288  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 10
(--) NVIDIA(0):   360  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 10
(--) NVIDIA(0):   411  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 10
(--) NVIDIA(0):   576  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 10
(--) NVIDIA(0):   720  x 480  @ 60 Hz
(--) NVIDIA(0):     Pixel Clock      : 54.00 MHz
(--) NVIDIA(0):     HRes, HSyncStart : 2880, 2956
(--) NVIDIA(0):     HSyncEnd, HTotal : 3204, 3432
(--) NVIDIA(0):     VRes, VSyncStart : 480, 488
(--) NVIDIA(0):     VSyncEnd, VTotal : 494, 524
(--) NVIDIA(0):     H/V Polarity     : -/-
(--) NVIDIA(0):     Extra            : Interlaced
(--) NVIDIA(0):     CEA Format       : 10
(--) NVIDIA(0): 
(--) NVIDIA(0): 
(--) NVIDIA(0): Raw EDID bytes:
(--) NVIDIA(0): 
(--) NVIDIA(0):   00 ff ff ff ff ff ff 00  3d cb 61 07 00 00 00 00
(--) NVIDIA(0):   00 11 01 03 80 a0 5a 78  0a 0d c9 a0 57 47 98 27
(--) NVIDIA(0):   12 48 4c 21 08 00 81 80  01 01 01 01 01 01 01 01
(--) NVIDIA(0):   01 01 01 01 01 01 02 3a  80 18 71 38 2d 40 58 2c
(--) NVIDIA(0):   45 00 40 84 63 00 00 1e  01 1d 00 72 51 d0 1e 20
(--) NVIDIA(0):   6e 28 55 00 40 84 63 00  00 1e 00 00 00 fc 00 54
(--) NVIDIA(0):   58 2d 53 52 36 30 35 0a  20 20 20 20 00 00 00 fd
(--) NVIDIA(0):   00 30 3e 0e 46 0f 00 0a  20 20 20 20 20 20 01 85
(--) NVIDIA(0):   02 03 45 70 5c 1f 10 14  05 13 04 12 11 16 15 03
(--) NVIDIA(0):   02 07 06 01 20 1e 1d 1a  19 0f 0e 0b 0a 26 25 24
(--) NVIDIA(0):   23 35 09 7f 07 0f 7f 07  17 07 50 3f 06 c0 57 06
(--) NVIDIA(0):   00 5f 7e 01 67 5e 00 83  4f 00 00 66 03 0c 00 11
(--) NVIDIA(0):   00 80 e2 00 39 02 3a 80  d0 72 38 2d 40 10 2c 45
(--) NVIDIA(0):   80 40 84 63 00 00 1e 01  1d 00 bc 52 d0 1e 20 b8
(--) NVIDIA(0):   28 55 40 40 84 63 00 00  1e 01 1d 80 18 71 1c 16
(--) NVIDIA(0):   20 58 2c 25 00 40 84 63  00 00 9e 00 00 00 00 55
(--) NVIDIA(0): 
(--) NVIDIA(0): --- End of EDID for ONK TX-SR605 (DFP-1) ---
(--) NVIDIA(0): 
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-1
(II) NVIDIA(0): Frequency information for ONK TX-SR605 (DFP-1):
(II) NVIDIA(0):   HorizSync   : 14.000-70.000 kHz
(II) NVIDIA(0):   VertRefresh : 48.000-62.000 Hz
(II) NVIDIA(0):     (HorizSync from EDID)
(II) NVIDIA(0):     (VertRefresh from EDID)
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Building ModePool for ONK TX-SR605 (DFP-1) ---
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
(II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x720":
(II) NVIDIA(0):     1280 x 720 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1390
(II) NVIDIA(0):       HSyncEnd, HTotal : 1430, 1650
(II) NVIDIA(0):       VRes, VSyncStart :  720,  725
(II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2448
(II) NVIDIA(0):       HSyncEnd, HTotal : 2492, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x720":
(II) NVIDIA(0):     1280 x 720 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1720
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1980
(II) NVIDIA(0):       VRes, VSyncStart :  720,  725
(II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2448
(II) NVIDIA(0):       HSyncEnd, HTotal : 2492, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 148.35 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
(II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2448
(II) NVIDIA(0):       HSyncEnd, HTotal : 2492, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1094, 1124
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
(II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1094, 1124
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x720":
(II) NVIDIA(0):     1280 x 720 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1720
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1980
(II) NVIDIA(0):       VRes, VSyncStart :  720,  725
(II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x720":
(II) NVIDIA(0):     1280 x 720 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1390
(II) NVIDIA(0):       HSyncEnd, HTotal : 1430, 1650
(II) NVIDIA(0):       VRes, VSyncStart :  720,  725
(II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     720 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  796,  864
(II) NVIDIA(0):       VRes, VSyncStart :  576,  581
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  625
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     720 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  796,  864
(II) NVIDIA(0):       VRes, VSyncStart :  576,  581
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  625
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     1440 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1590, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     1440 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1590, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     720 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  736
(II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     720 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  736
(II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     1440 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1478
(II) NVIDIA(0):       HSyncEnd, HTotal : 1602, 1716
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     1440 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1478
(II) NVIDIA(0):       HSyncEnd, HTotal : 1602, 1716
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 25.17 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 24 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.16 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2558
(II) NVIDIA(0):       HSyncEnd, HTotal : 2602, 2750
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0): The EDID for ONK TX-SR605 (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x576":
(II) NVIDIA(0):     1440 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1592, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  576,  581
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  625
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x576":
(II) NVIDIA(0):     1440 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1592, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  576,  581
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  625
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "288x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "411x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "288x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "411x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     2880 x 576 @ 50 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2928
(II) NVIDIA(0):       HSyncEnd, HTotal : 3180, 3456
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x480":
(II) NVIDIA(0):     1440 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1472
(II) NVIDIA(0):       HSyncEnd, HTotal : 1596, 1716
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x480":
(II) NVIDIA(0):     1440 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1472
(II) NVIDIA(0):       HSyncEnd, HTotal : 1596, 1716
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "288x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "411x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "288x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "411x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     2880 x 480 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2880, 2956
(II) NVIDIA(0):       HSyncEnd, HTotal : 3204, 3432
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     For use as DFP backend.
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): Native backend timings for ONK TX-SR605 (DFP-1):
(II) NVIDIA(0):   1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Pixel Clock      : 148.500 MHz
(II) NVIDIA(0):     HRes, HSyncStart : 1920, 2008
(II) NVIDIA(0):     HSyncEnd, HTotal : 2052, 2200
(II) NVIDIA(0):     VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):     VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):     H/V Polarity     : +/+
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
(II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x720":
(II) NVIDIA(0):     1280 x 720 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1390
(II) NVIDIA(0):       HSyncEnd, HTotal : 1430, 1650
(II) NVIDIA(0):       VRes, VSyncStart :  720,  725
(II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2448
(II) NVIDIA(0):       HSyncEnd, HTotal : 2492, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x720":
(II) NVIDIA(0):     1280 x 720 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1720
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1980
(II) NVIDIA(0):       VRes, VSyncStart :  720,  725
(II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2448
(II) NVIDIA(0):       HSyncEnd, HTotal : 2492, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 148.35 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
(II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2448
(II) NVIDIA(0):       HSyncEnd, HTotal : 2492, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1094, 1124
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2008
(II) NVIDIA(0):       HSyncEnd, HTotal : 2052, 2200
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1094, 1124
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x720":
(II) NVIDIA(0):     1280 x 720 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1720
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1980
(II) NVIDIA(0):       VRes, VSyncStart :  720,  725
(II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x720":
(II) NVIDIA(0):     1280 x 720 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1390
(II) NVIDIA(0):       HSyncEnd, HTotal : 1430, 1650
(II) NVIDIA(0):       VRes, VSyncStart :  720,  725
(II) NVIDIA(0):       VSyncEnd, VTotal :  730,  750
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     720 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  796,  864
(II) NVIDIA(0):       VRes, VSyncStart :  576,  581
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  625
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     720 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  796,  864
(II) NVIDIA(0):       VRes, VSyncStart :  576,  581
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  625
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     720 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 13.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  795,  864
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     720 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 13.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  795,  864
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     720 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  736
(II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     720 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 27.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  736
(II) NVIDIA(0):       HSyncEnd, HTotal :  798,  858
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     720 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 13.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  739
(II) NVIDIA(0):       HSyncEnd, HTotal :  801,  858
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     720 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 13.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  739
(II) NVIDIA(0):       HSyncEnd, HTotal :  801,  858
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 25.17 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 24 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 74.16 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2558
(II) NVIDIA(0):       HSyncEnd, HTotal : 2602, 2750
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1084
(II) NVIDIA(0):       VSyncEnd, VTotal : 1089, 1125
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0): The EDID for ONK TX-SR605 (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
(WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
(WW) NVIDIA(0):     check for mode "1920x1080".
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x576":
(II) NVIDIA(0):     1440 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1592, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  576,  581
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  625
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x576":
(II) NVIDIA(0):     1440 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1592, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  576,  581
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  625
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "288x576":
(II) NVIDIA(0):     288 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 5.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  288,  292
(II) NVIDIA(0):       HSyncEnd, HTotal :  317,  345
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x576":
(II) NVIDIA(0):     360 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 6.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  366
(II) NVIDIA(0):       HSyncEnd, HTotal :  397,  432
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "411x576":
(II) NVIDIA(0):     411 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 7.71 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  411,  417
(II) NVIDIA(0):       HSyncEnd, HTotal :  453,  493
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: Mode's width (411) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x576":
(II) NVIDIA(0):     576 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 10.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  585
(II) NVIDIA(0):       HSyncEnd, HTotal :  635,  691
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     720 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 13.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  795,  864
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "288x576":
(II) NVIDIA(0):     288 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 5.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  288,  292
(II) NVIDIA(0):       HSyncEnd, HTotal :  317,  345
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x576":
(II) NVIDIA(0):     360 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 6.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  366
(II) NVIDIA(0):       HSyncEnd, HTotal :  397,  432
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "411x576":
(II) NVIDIA(0):     411 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 7.71 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  411,  417
(II) NVIDIA(0):       HSyncEnd, HTotal :  453,  493
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: Mode's width (411) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x576":
(II) NVIDIA(0):     576 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 10.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  585
(II) NVIDIA(0):       HSyncEnd, HTotal :  635,  691
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x576":
(II) NVIDIA(0):     720 x 576 @ 50 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 13.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  795,  864
(II) NVIDIA(0):       VRes, VSyncStart :  576,  580
(II) NVIDIA(0):       VSyncEnd, VTotal :  586,  624
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x480":
(II) NVIDIA(0):     1440 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1472
(II) NVIDIA(0):       HSyncEnd, HTotal : 1596, 1716
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x480":
(II) NVIDIA(0):     1440 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1472
(II) NVIDIA(0):       HSyncEnd, HTotal : 1596, 1716
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  495,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "288x480":
(II) NVIDIA(0):     288 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 5.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  288,  295
(II) NVIDIA(0):       HSyncEnd, HTotal :  319,  343
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x480":
(II) NVIDIA(0):     360 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 6.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  369
(II) NVIDIA(0):       HSyncEnd, HTotal :  400,  429
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "411x480":
(II) NVIDIA(0):     411 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 7.71 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  411,  421
(II) NVIDIA(0):       HSyncEnd, HTotal :  456,  490
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: Mode's width (411) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x480":
(II) NVIDIA(0):     576 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 10.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  591
(II) NVIDIA(0):       HSyncEnd, HTotal :  640,  686
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     720 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 13.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  739
(II) NVIDIA(0):       HSyncEnd, HTotal :  801,  858
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "288x480":
(II) NVIDIA(0):     288 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 5.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  288,  295
(II) NVIDIA(0):       HSyncEnd, HTotal :  319,  343
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x480":
(II) NVIDIA(0):     360 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 6.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  369
(II) NVIDIA(0):       HSyncEnd, HTotal :  400,  429
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "411x480":
(II) NVIDIA(0):     411 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 7.71 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  411,  421
(II) NVIDIA(0):       HSyncEnd, HTotal :  456,  490
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: Mode's width (411) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x480":
(II) NVIDIA(0):     576 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 10.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  591
(II) NVIDIA(0):       HSyncEnd, HTotal :  640,  686
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x480":
(II) NVIDIA(0):     720 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 13.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  739
(II) NVIDIA(0):       HSyncEnd, HTotal :  801,  858
(II) NVIDIA(0):       VRes, VSyncStart :  480,  488
(II) NVIDIA(0):       VSyncEnd, VTotal :  494,  524
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : Interlace
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: EDID
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x175":
(II) NVIDIA(0):     320 x 175 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  175,  191
(II) NVIDIA(0):       VSyncEnd, VTotal :  192,  222
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x200":
(II) NVIDIA(0):     320 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  336
(II) NVIDIA(0):       HSyncEnd, HTotal :  368,  416
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  222
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "360x200":
(II) NVIDIA(0):     360 x 200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 17.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  360,  378
(II) NVIDIA(0):       HSyncEnd, HTotal :  414,  468
(II) NVIDIA(0):       VRes, VSyncStart :  200,  200
(II) NVIDIA(0):       VSyncEnd, VTotal :  202,  223
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 12.59 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  400
(II) NVIDIA(0):       VRes, VSyncStart :  240,  245
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  262
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "320x240": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.8 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 73 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  332
(II) NVIDIA(0):       HSyncEnd, HTotal :  352,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  244
(II) NVIDIA(0):       VSyncEnd, VTotal :  246,  260
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.8 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 15.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  328
(II) NVIDIA(0):       HSyncEnd, HTotal :  360,  420
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  250
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "320x240":
(II) NVIDIA(0):     320 x 240 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  320,  348
(II) NVIDIA(0):       HSyncEnd, HTotal :  376,  416
(II) NVIDIA(0):       VRes, VSyncStart :  240,  240
(II) NVIDIA(0):       VSyncEnd, VTotal :  242,  254
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.2 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 56 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 18.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  412
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  512
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  301,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 800x600
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 20.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  420
(II) NVIDIA(0):       HSyncEnd, HTotal :  484,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  314
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "400x300": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.2 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 72 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 25.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  428
(II) NVIDIA(0):       HSyncEnd, HTotal :  488,  520
(II) NVIDIA(0):       VRes, VSyncStart :  300,  318
(II) NVIDIA(0):       VSyncEnd, VTotal :  321,  333
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.2 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 24.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  408
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  528
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  312
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "400x300":
(II) NVIDIA(0):     400 x 300 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  400,  416
(II) NVIDIA(0):       HSyncEnd, HTotal :  448,  524
(II) NVIDIA(0):       VRes, VSyncStart :  300,  300
(II) NVIDIA(0):       VSyncEnd, VTotal :  302,  315
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.3 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 87 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 22.45 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  516
(II) NVIDIA(0):       HSyncEnd, HTotal :  604,  632
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  408
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "1024x768": 1024x768
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 32.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  672
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "512x384": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (70.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 37.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  524
(II) NVIDIA(0):       HSyncEnd, HTotal :  592,  664
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  388,  403
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (70.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 39.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  520
(II) NVIDIA(0):       HSyncEnd, HTotal :  568,  656
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  400
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "512x384":
(II) NVIDIA(0):     512 x 384 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 47.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  512,  536
(II) NVIDIA(0):       HSyncEnd, HTotal :  584,  688
(II) NVIDIA(0):       VRes, VSyncStart :  384,  384
(II) NVIDIA(0):       VSyncEnd, VTotal :  386,  404
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  800
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x960": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  688
(II) NVIDIA(0):       HSyncEnd, HTotal :  744,  900
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  500
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 74.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  480,  480
(II) NVIDIA(0):       VSyncEnd, VTotal :  482,  505
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x1024": 1280x1024
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 54.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "640x512": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (80.0 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 67.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  648
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  844
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  533
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (80.0 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (157.5 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 150.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x512":
(II) NVIDIA(0):     640 x 512 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  864
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  536
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.1 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (162.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 150.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (75.0 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (175.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 65 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.2 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (189.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (87.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (202.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 101.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (229.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 114.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1080
(II) NVIDIA(0):       VRes, VSyncStart :  600,  600
(II) NVIDIA(0):       VSyncEnd, VTotal :  602,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.2 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (204.8 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 102.40 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  960
(II) NVIDIA(0):       HSyncEnd, HTotal : 1060, 1224
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  697
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (83.7 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (261.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "896x672":
(II) NVIDIA(0):     896 x 672 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 130.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  896,  944
(II) NVIDIA(0):       HSyncEnd, HTotal : 1052, 1228
(II) NVIDIA(0):       VRes, VSyncStart :  672,  672
(II) NVIDIA(0):       VSyncEnd, VTotal :  674,  708
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (106.3 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (218.3 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 109.15 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  976
(II) NVIDIA(0):       HSyncEnd, HTotal : 1088, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  719
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (86.4 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (288.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "928x696":
(II) NVIDIA(0):     928 x 696 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 144.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  928,  992
(II) NVIDIA(0):       HSyncEnd, HTotal : 1104, 1280
(II) NVIDIA(0):       VRes, VSyncStart :  696,  696
(II) NVIDIA(0):       VSyncEnd, VTotal :  698,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (234.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 117.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1024
(II) NVIDIA(0):       HSyncEnd, HTotal : 1128, 1300
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (90.0 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (297.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1320
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  750
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (112.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "832x624":
(II) NVIDIA(0):     832 x 624 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 57.28 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  832,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  928, 1152
(II) NVIDIA(0):       VRes, VSyncStart :  624,  625
(II) NVIDIA(0):       VSyncEnd, VTotal :  628,  667
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (74.6 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "416x312":
(II) NVIDIA(0):     416 x 312 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 28.64 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  416,  432
(II) NVIDIA(0):       HSyncEnd, HTotal :  464,  576
(II) NVIDIA(0):       VRes, VSyncStart :  312,  312
(II) NVIDIA(0):       VSyncEnd, VTotal :  314,  333
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (74.7 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 81.62 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1336, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  895
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1152x864": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 40.81 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  668,  760
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  447
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "576x432": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 96.77 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1536
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (70.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 48.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  768
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  450
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (70.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 104.99 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  902
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 52.49 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  451
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.65 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1224
(II) NVIDIA(0):       HSyncEnd, HTotal : 1352, 1552
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  907
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (77.1 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.83 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  612
(II) NVIDIA(0):       HSyncEnd, HTotal :  676,  776
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  453
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (77.1 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 121.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  911
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: HorizSync (77.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 60.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  608
(II) NVIDIA(0):       HSyncEnd, HTotal :  672,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  455
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (77.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 143.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1232
(II) NVIDIA(0):       HSyncEnd, HTotal : 1360, 1568
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  915
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "576x432":
(II) NVIDIA(0):     576 x 432 @ 100 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 71.73 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  576,  616
(II) NVIDIA(0):       HSyncEnd, HTotal :  680,  784
(II) NVIDIA(0):       VRes, VSyncStart :  432,  432
(II) NVIDIA(0):       VSyncEnd, VTotal :  434,  457
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (91.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1408
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1520
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  790
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "1360x768": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  704
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  760
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  395
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "680x384": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1360x768":
(II) NVIDIA(0):     1360 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 84.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1360, 1432
(II) NVIDIA(0):       HSyncEnd, HTotal : 1568, 1776
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  781,  798
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1360x768": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "680x384":
(II) NVIDIA(0):     680 x 384 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 42.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  680,  716
(II) NVIDIA(0):       HSyncEnd, HTotal :  784,  888
(II) NVIDIA(0):       VRes, VSyncStart :  384,  385
(II) NVIDIA(0):       VSyncEnd, VTotal :  390,  399
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "680x384": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 122.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1488
(II) NVIDIA(0):       HSyncEnd, HTotal : 1640, 1880
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1082
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1400x1050": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 61.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  744
(II) NVIDIA(0):       HSyncEnd, HTotal :  820,  940
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  541
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: Mode's width (700) is not a multiple of
(WW) NVIDIA(0):     8.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 145.06 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1496
(II) NVIDIA(0):       HSyncEnd, HTotal : 1648, 1896
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1093
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (76.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 72.53 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  748
(II) NVIDIA(0):       HSyncEnd, HTotal :  824,  948
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  546
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (76.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 155.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1464
(II) NVIDIA(0):       HSyncEnd, HTotal : 1784, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1052
(II) NVIDIA(0):       VSyncEnd, VTotal : 1064, 1090
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (155.8 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 150.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  732
(II) NVIDIA(0):       HSyncEnd, HTotal :  892,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  532,  545
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (81.5 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1400x1050":
(II) NVIDIA(0):     1400 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 179.26 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1400, 1504
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1912
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1051
(II) NVIDIA(0):       VSyncEnd, VTotal : 1054, 1103
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (179.3 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "700x525":
(II) NVIDIA(0):     700 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 89.63 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  700,  752
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  956
(II) NVIDIA(0):       VRes, VSyncStart :  525,  525
(II) NVIDIA(0):       VSyncEnd, VTotal :  527,  551
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.8 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1440x900":
(II) NVIDIA(0):     1440 x 900 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 106.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1440, 1520
(II) NVIDIA(0):       HSyncEnd, HTotal : 1672, 1904
(II) NVIDIA(0):       VRes, VSyncStart :  900,  903
(II) NVIDIA(0):       VSyncEnd, VTotal :  909,  934
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1440x900": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x450":
(II) NVIDIA(0):     720 x 450 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 53.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  760
(II) NVIDIA(0):       HSyncEnd, HTotal :  836,  952
(II) NVIDIA(0):       VRes, VSyncStart :  450,  451
(II) NVIDIA(0):       VSyncEnd, VTotal :  454,  467
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "720x450": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1024":
(II) NVIDIA(0):     1600 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 103.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1600
(II) NVIDIA(0):       HSyncEnd, HTotal : 1656, 1664
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1024
(II) NVIDIA(0):       VSyncEnd, VTotal : 1029, 1030
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1600x1024": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x512":
(II) NVIDIA(0):     800 x 512 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 51.56 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  800
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  832
(II) NVIDIA(0):       VRes, VSyncStart :  512,  512
(II) NVIDIA(0):       VSyncEnd, VTotal :  514,  515
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "800x512": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 119.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1728
(II) NVIDIA(0):       HSyncEnd, HTotal : 1760, 1840
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1080
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "1680x1050": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 59.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  864
(II) NVIDIA(0):       HSyncEnd, HTotal :  880,  920
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  540
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "840x525": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 146.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1784
(II) NVIDIA(0):       HSyncEnd, HTotal : 1960, 2240
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1089
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):     BestFit Backend for "1680x1050": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 73.12 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  892
(II) NVIDIA(0):       HSyncEnd, HTotal :  980, 1120
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  544
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "840x525": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 174.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1096
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (174.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 70 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 87.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  548
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (76.6 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 187.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1800
(II) NVIDIA(0):       HSyncEnd, HTotal : 1976, 2272
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1099
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (187.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 93.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  900
(II) NVIDIA(0):       HSyncEnd, HTotal :  988, 1136
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  549
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (82.3 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1680x1050":
(II) NVIDIA(0):     1680 x 1050 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 214.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1680, 1808
(II) NVIDIA(0):       HSyncEnd, HTotal : 1984, 2288
(II) NVIDIA(0):       VRes, VSyncStart : 1050, 1053
(II) NVIDIA(0):       VSyncEnd, VTotal : 1059, 1105
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (214.8 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "840x525":
(II) NVIDIA(0):     840 x 525 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 107.38 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  840,  904
(II) NVIDIA(0):       HSyncEnd, HTotal :  992, 1144
(II) NVIDIA(0):       VRes, VSyncStart :  525,  526
(II) NVIDIA(0):       VSyncEnd, VTotal :  529,  552
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (93.9 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1080":
(II) NVIDIA(0):     1920 x 1080 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 138.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1080, 1083
(II) NVIDIA(0):       VSyncEnd, VTotal : 1088, 1111
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):     BestFit Backend for "1920x1080": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x540":
(II) NVIDIA(0):     960 x 540 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  540,  541
(II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     BestFit Backend for "960x540": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1200":
(II) NVIDIA(0):     1920 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 154.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 1968
(II) NVIDIA(0):       HSyncEnd, HTotal : 2000, 2080
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1203
(II) NVIDIA(0):       VSyncEnd, VTotal : 1209, 1235
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: PixelClock (154.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 150.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x600":
(II) NVIDIA(0):     960 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 77.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  617
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (74.0 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 341.35 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2072
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2656
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1512
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (341.4 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "960x720":
(II) NVIDIA(0):     960 x 720 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.68 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960, 1036
(II) NVIDIA(0):       HSyncEnd, HTotal : 1144, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  720,  720
(II) NVIDIA(0):       VSyncEnd, VTotal :  722,  756
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: PixelClock (170.7 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 266.95 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2200
(II) NVIDIA(0):       HSyncEnd, HTotal : 2424, 2800
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1589
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (266.9 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 133.47 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1100
(II) NVIDIA(0):       HSyncEnd, HTotal : 1212, 1400
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  794
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: HorizSync (95.3 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 340.48 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1603
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (340.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 170.24 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  801
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: PixelClock (170.2 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "2048x1536":
(II) NVIDIA(0):     2048 x 1536 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 388.04 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 2048, 2216
(II) NVIDIA(0):       HSyncEnd, HTotal : 2440, 2832
(II) NVIDIA(0):       VRes, VSyncStart : 1536, 1537
(II) NVIDIA(0):       VSyncEnd, VTotal : 1540, 1612
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (388.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 194.02 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1108
(II) NVIDIA(0):       HSyncEnd, HTotal : 1220, 1416
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  770,  806
(II) NVIDIA(0):       H/V Polarity     : -/+
(II) NVIDIA(0):       Extra            : DoubleScan
(WW) NVIDIA(0):     Mode is rejected: PixelClock (194.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x350":
(II) NVIDIA(0):     640 x 350 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  350,  382
(II) NVIDIA(0):       VSyncEnd, VTotal :  385,  445
(II) NVIDIA(0):       H/V Polarity     : +/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x400":
(II) NVIDIA(0):     640 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  672
(II) NVIDIA(0):       HSyncEnd, HTotal :  736,  832
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  445
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "720x400":
(II) NVIDIA(0):     720 x 400 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 35.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  720,  756
(II) NVIDIA(0):       HSyncEnd, HTotal :  828,  936
(II) NVIDIA(0):       VRes, VSyncStart :  400,  401
(II) NVIDIA(0):       VSyncEnd, VTotal :  404,  446
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 25.18 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  800
(II) NVIDIA(0):       VRes, VSyncStart :  480,  490
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  525
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "640x480": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 73 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  664
(II) NVIDIA(0):       HSyncEnd, HTotal :  704,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  489
(II) NVIDIA(0):       VSyncEnd, VTotal :  492,  520
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.8 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 31.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  656
(II) NVIDIA(0):       HSyncEnd, HTotal :  720,  840
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  500
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "640x480":
(II) NVIDIA(0):     640 x 480 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  640,  696
(II) NVIDIA(0):       HSyncEnd, HTotal :  752,  832
(II) NVIDIA(0):       VRes, VSyncStart :  480,  481
(II) NVIDIA(0):       VSyncEnd, VTotal :  484,  509
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 56 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 36.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  824
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1024
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  603,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 40.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  840
(II) NVIDIA(0):       HSyncEnd, HTotal :  968, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  605,  628
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "800x600": 800x600
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 72 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 50.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  856
(II) NVIDIA(0):       HSyncEnd, HTotal :  976, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  600,  637
(II) NVIDIA(0):       VSyncEnd, VTotal :  643,  666
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (72.2 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 49.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  816
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1056
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  625
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "800x600":
(II) NVIDIA(0):     800 x 600 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 56.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  800,  832
(II) NVIDIA(0):       HSyncEnd, HTotal :  896, 1048
(II) NVIDIA(0):       VRes, VSyncStart :  600,  601
(II) NVIDIA(0):       VSyncEnd, VTotal :  604,  631
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 87 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 44.90 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1032
(II) NVIDIA(0):       HSyncEnd, HTotal : 1208, 1264
(II) NVIDIA(0):       VRes, VSyncStart :  768,  768
(II) NVIDIA(0):       VSyncEnd, VTotal :  776,  817
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):       Extra            : Interlace
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (87.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 65.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1344
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(II) NVIDIA(0):     BestFit Backend for "1024x768": 1024x768
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 75.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1048
(II) NVIDIA(0):       HSyncEnd, HTotal : 1184, 1328
(II) NVIDIA(0):       VRes, VSyncStart :  768,  771
(II) NVIDIA(0):       VSyncEnd, VTotal :  777,  806
(II) NVIDIA(0):       H/V Polarity     : -/-
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (70.1 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 78.75 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1040
(II) NVIDIA(0):       HSyncEnd, HTotal : 1136, 1312
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  800
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1024x768":
(II) NVIDIA(0):     1024 x 768 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 94.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1024, 1072
(II) NVIDIA(0):       HSyncEnd, HTotal : 1168, 1376
(II) NVIDIA(0):       VRes, VSyncStart :  768,  769
(II) NVIDIA(0):       VSyncEnd, VTotal :  772,  808
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (85.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1152x864":
(II) NVIDIA(0):     1152 x 864 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1152, 1216
(II) NVIDIA(0):       HSyncEnd, HTotal : 1344, 1600
(II) NVIDIA(0):       VRes, VSyncStart :  864,  865
(II) NVIDIA(0):       VSyncEnd, VTotal :  868,  900
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: VertRefresh (75.0 Hz) out of range
(WW) NVIDIA(0):     (48.000-62.000 Hz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1376
(II) NVIDIA(0):       HSyncEnd, HTotal : 1488, 1800
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1000
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x960": 1920x1080
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x960":
(II) NVIDIA(0):     1280 x 960 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 148.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart :  960,  961
(II) NVIDIA(0):       VSyncEnd, VTotal :  964, 1011
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (85.9 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 108.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1328
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(II) NVIDIA(0):     BestFit Backend for "1280x1024": 1280x1024
(II) NVIDIA(0):     Mode is valid.
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 135.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1296
(II) NVIDIA(0):       HSyncEnd, HTotal : 1440, 1688
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1066
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: HorizSync (80.0 kHz) out of range
(WW) NVIDIA(0):     (14.000-70.000 kHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1280x1024":
(II) NVIDIA(0):     1280 x 1024 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 157.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1280, 1344
(II) NVIDIA(0):       HSyncEnd, HTotal : 1504, 1728
(II) NVIDIA(0):       VRes, VSyncStart : 1024, 1025
(II) NVIDIA(0):       VSyncEnd, VTotal : 1028, 1072
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (157.5 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 150.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 162.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (162.0 MHz) too high for EDID
(WW) NVIDIA(0):     (EDID Max: 150.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 65 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 175.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (175.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 70 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 189.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (189.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 202.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (202.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1600x1200":
(II) NVIDIA(0):     1600 x 1200 @ 85 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 229.50 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1600, 1664
(II) NVIDIA(0):       HSyncEnd, HTotal : 1856, 2160
(II) NVIDIA(0):       VRes, VSyncStart : 1200, 1201
(II) NVIDIA(0):       VSyncEnd, VTotal : 1204, 1250
(II) NVIDIA(0):       H/V Polarity     : +/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (229.5 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 204.80 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1920
(II) NVIDIA(0):       HSyncEnd, HTotal : 2120, 2448
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1394
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (204.8 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1792x1344":
(II) NVIDIA(0):     1792 x 1344 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 261.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1792, 1888
(II) NVIDIA(0):       HSyncEnd, HTotal : 2104, 2456
(II) NVIDIA(0):       VRes, VSyncStart : 1344, 1345
(II) NVIDIA(0):       VSyncEnd, VTotal : 1348, 1417
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (261.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 218.30 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1952
(II) NVIDIA(0):       HSyncEnd, HTotal : 2176, 2528
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1439
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (218.3 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1856x1392":
(II) NVIDIA(0):     1856 x 1392 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 288.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1856, 1984
(II) NVIDIA(0):       HSyncEnd, HTotal : 2208, 2560
(II) NVIDIA(0):       VRes, VSyncStart : 1392, 1393
(II) NVIDIA(0):       VSyncEnd, VTotal : 1396, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (288.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 60 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 234.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2048
(II) NVIDIA(0):       HSyncEnd, HTotal : 2256, 2600
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (234.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0):   Validating Mode "1920x1440":
(II) NVIDIA(0):     1920 x 1440 @ 75 Hz
(II) NVIDIA(0):     Mode Source: VESA
(II) NVIDIA(0):       Pixel Clock      : 297.00 MHz
(II) NVIDIA(0):       HRes, HSyncStart : 1920, 2064
(II) NVIDIA(0):       HSyncEnd, HTotal : 2288, 2640
(II) NVIDIA(0):       VRes, VSyncStart : 1440, 1441
(II) NVIDIA(0):       VSyncEnd, VTotal : 1444, 1500
(II) NVIDIA(0):       H/V Polarity     : -/+
(WW) NVIDIA(0):     Mode is rejected: PixelClock (297.0 MHz) too high for
(WW) NVIDIA(0):     Display Device (Max: 165.0 MHz).
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Done building ModePool for ONK TX-SR605 (DFP-1) ---
(II) NVIDIA(0): 
(II) NVIDIA(0): 
(II) NVIDIA(0): --- Modes in ModePool for ONK TX-SR605 (DFP-1) ---
(II) NVIDIA(0): "nvidia-auto-select" : 1920 x 1080 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1920x1080"          : 1920 x 1080 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1920x1080_60"       : 1920 x 1080 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1920x1080_60_0"     : 1920 x 1080 @ 59.94/60 Hz (CEA-861B Format 16) (from: EDID)
(II) NVIDIA(0): "1920x1080_60_1"     : 1920 x 1080 @  59.9 Hz  (from: X Server)
(II) NVIDIA(0): "1920x1080_50"       : 1920 x 1080 @  50.0 Hz  (from: EDID)
(II) NVIDIA(0): "1920x1080_24"       : 1920 x 1080 @ 23.97/24 Hz (CEA-861B Format 32) (from: EDID)
(II) NVIDIA(0): "1920x1080_60i"      : 1920 x 1080 @ 59.94/60 Hz (CEA-861B Format 5) (from: EDID)
(II) NVIDIA(0): "1920x1080_50i"      : 1920 x 1080 @ 50 Hz Interlace (CEA-861B Format 20) (from: EDID)
(II) NVIDIA(0): "1680x1050"          : 1680 x 1050 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1680x1050_60"       : 1680 x 1050 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1680x1050_60_0"     : 1680 x 1050 @  59.9 Hz  (from: X Server)
(II) NVIDIA(0): "1600x1024"          : 1600 x 1024 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1600x1024_60"       : 1600 x 1024 @  60.2 Hz  (from: X Server)
(II) NVIDIA(0): "1440x900"           : 1440 x  900 @  59.9 Hz  (from: X Server)
(II) NVIDIA(0): "1440x900_60"        : 1440 x  900 @  59.9 Hz  (from: X Server)
(II) NVIDIA(0): "1440x576"           : 1440 x  576 @ 50 Hz (CEA-861B Format 30) (from: EDID)
(II) NVIDIA(0): "1440x576_50"        : 1440 x  576 @ 50 Hz (CEA-861B Format 30) (from: EDID)
(II) NVIDIA(0): "1440x480"           : 1440 x  480 @ 59.94/60 Hz (CEA-861B Format 15) (from: EDID)
(II) NVIDIA(0): "1440x480_60"        : 1440 x  480 @ 59.94/60 Hz (CEA-861B Format 15) (from: EDID)
(II) NVIDIA(0): "1400x1050"          : 1400 x 1050 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1400x1050_60"       : 1400 x 1050 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1360x768"           : 1360 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1360x768_60"        : 1360 x  768 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1360x768_60_0"      : 1360 x  768 @  59.8 Hz  (from: X Server)
(II) NVIDIA(0): "1280x1024"          : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x1024_60"       : 1280 x 1024 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1280x960"           : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x960_60"        : 1280 x  960 @  60.0 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "1280x720"           : 1280 x  720 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1280x720_60"        : 1280 x  720 @  60.0 Hz  (from: EDID)
(II) NVIDIA(0): "1280x720_60_0"      : 1280 x  720 @ 59.94/60 Hz (CEA-861B Format 4) (from: EDID)
(II) NVIDIA(0): "1280x720_50"        : 1280 x  720 @  50.0 Hz  (from: EDID)
(II) NVIDIA(0): "1152x864"           : 1152 x  864 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1152x864_60"        : 1152 x  864 @  60.0 Hz  (from: X Server)
(II) NVIDIA(0): "1024x768"           : 1024 x  768 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "1024x768_60"        : 1024 x  768 @  60.0 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "960x540"            :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x540d60"         :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525"            :  840 x  525 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d60"         :  840 x  525 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "840x525d60_0"       :  840 x  525 @  59.9 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x600"            :  800 x  600 @  60.3 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_60"         :  800 x  600 @  60.3 Hz  (from: X Server, VESA, EDID)
(II) NVIDIA(0): "800x600_56"         :  800 x  600 @  56.2 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "800x512"            :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "800x512d60"         :  800 x  512 @  60.2 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x576"            :  720 x  576 @ 50 Hz (CEA-861B Format 18) (from: EDID)
(II) NVIDIA(0): "720x576_50"         :  720 x  576 @ 50 Hz (CEA-861B Format 18) (from: EDID)
(II) NVIDIA(0): "720x576_50i"        : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26) (from: EDID)
(II) NVIDIA(0): "720x576_50i_0"      : (1440)x 576 @ 50 Hz Interlace (CEA-861B Format 22) (from: EDID)
(II) NVIDIA(0): "720x480"            :  720 x  480 @ 59.94/60 Hz (CEA-861B Format 3) (from: EDID)
(II) NVIDIA(0): "720x480_60"         :  720 x  480 @ 59.94/60 Hz (CEA-861B Format 3) (from: EDID)
(II) NVIDIA(0): "720x480_60i"        : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11) (from: EDID)
(II) NVIDIA(0): "720x480_60i_0"      : (1440)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 7) (from: EDID)
(II) NVIDIA(0): "720x450"            :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "720x450d60"         :  720 x  450 @  59.9 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "680x384"            :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "680x384d60"         :  680 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "680x384d60_0"       :  680 x  384 @  59.8 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512"            :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x512d60"         :  640 x  512 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480"            :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480d60"         :  640 x  480 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "640x480_60"         :  640 x  480 @  59.9 Hz  (from: X Server, VESA)
(II) NVIDIA(0): "640x480_60_0"       :  640 x  480 @ 59.94/60 Hz Interlace (CEA-861B Format 1) (from: EDID)
(II) NVIDIA(0): "576x576"            : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26) (from: EDID)
(II) NVIDIA(0): "576x576_50i"        : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26) (from: EDID)
(II) NVIDIA(0): "576x480"            : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11) (from: EDID)
(II) NVIDIA(0): "576x480_60i"        : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11) (from: EDID)
(II) NVIDIA(0): "576x432"            :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "576x432d60"         :  576 x  432 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384"            :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "512x384d60"         :  512 x  384 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300"            :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d60"         :  400 x  300 @  60.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "400x300d56"         :  400 x  300 @  56.3 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "360x576"            : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26) (from: EDID)
(II) NVIDIA(0): "360x576_50i"        : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26) (from: EDID)
(II) NVIDIA(0): "360x480"            : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11) (from: EDID)
(II) NVIDIA(0): "360x480_60i"        : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11) (from: EDID)
(II) NVIDIA(0): "320x240"            :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "320x240d60"         :  320 x  240 @  60.1 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "288x576"            : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26) (from: EDID)
(II) NVIDIA(0): "288x576_50i"        : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26) (from: EDID)
(II) NVIDIA(0): "288x480"            : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11) (from: EDID)
(II) NVIDIA(0): "288x480_60i"        : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11) (from: EDID)
(II) NVIDIA(0): --- End of ModePool for ONK TX-SR605 (DFP-1): ---
(II) NVIDIA(0): 
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Using MetaMode string: "DFP: nvidia-auto-select +0+0"
(II) NVIDIA(0): Requested modes:
(II) NVIDIA(0):     "DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0): MetaMode "DFP:nvidia-auto-select+0+0":
(II) NVIDIA(0):     Bounding Box: [0, 0, 1920, 1080]
(II) NVIDIA(0):     ONK TX-SR605 (DFP-1): "nvidia-auto-select"
(II) NVIDIA(0):         Size          : 1920 x 1080
(II) NVIDIA(0):         Offset        : +0 +0
(II) NVIDIA(0):         Panning Domain: @ 1920 x 1080
(II) NVIDIA(0):         Position      : [0, 0, 1920, 1080]
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(II) NVIDIA(0): 
(II) NVIDIA(0): Implicitly adding the following modes to X Screen 0 (these
(II) NVIDIA(0):     will be available via XRandR and XF86VidMode):
(II) NVIDIA(0): 
(II) NVIDIA(0): "1920x1080_60_0" : 1920 x 1080 @ 59.94/60 Hz (CEA-861B Format 16)
(II) NVIDIA(0): "1920x1080_60_1" : 1920 x 1080 @  59.9 Hz 
(II) NVIDIA(0): "1920x1080_50"   : 1920 x 1080 @  50.0 Hz 
(II) NVIDIA(0): "1920x1080_24"   : 1920 x 1080 @ 23.97/24 Hz (CEA-861B Format 32)
(II) NVIDIA(0): "1920x1080_60i"  : 1920 x 1080 @ 59.94/60 Hz (CEA-861B Format 5)
(II) NVIDIA(0): "1920x1080_50i"  : 1920 x 1080 @ 50 Hz Interlace (CEA-861B Format 20)
(II) NVIDIA(0): "1680x1050"      : 1680 x 1050 @  60.0 Hz 
(II) NVIDIA(0): "1680x1050_60_0" : 1680 x 1050 @  59.9 Hz 
(II) NVIDIA(0): "1600x1024"      : 1600 x 1024 @  60.2 Hz 
(II) NVIDIA(0): "1440x900"       : 1440 x  900 @  59.9 Hz 
(II) NVIDIA(0): "1440x576"       : 1440 x  576 @ 50 Hz (CEA-861B Format 30)
(II) NVIDIA(0): "1440x480"       : 1440 x  480 @ 59.94/60 Hz (CEA-861B Format 15)
(II) NVIDIA(0): "1400x1050"      : 1400 x 1050 @  60.0 Hz 
(II) NVIDIA(0): "1360x768"       : 1360 x  768 @  60.0 Hz 
(II) NVIDIA(0): "1360x768_60_0"  : 1360 x  768 @  59.8 Hz 
(II) NVIDIA(0): "1280x1024"      : 1280 x 1024 @  60.0 Hz 
(II) NVIDIA(0): "1280x960"       : 1280 x  960 @  60.0 Hz 
(II) NVIDIA(0): "1280x720"       : 1280 x  720 @  60.0 Hz 
(II) NVIDIA(0): "1280x720_60_0"  : 1280 x  720 @ 59.94/60 Hz (CEA-861B Format 4)
(II) NVIDIA(0): "1280x720_50"    : 1280 x  720 @  50.0 Hz 
(II) NVIDIA(0): "1152x864"       : 1152 x  864 @  60.0 Hz 
(II) NVIDIA(0): "1024x768"       : 1024 x  768 @  60.0 Hz 
(II) NVIDIA(0): "960x540"        :  960 x  540 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "840x525"        :  840 x  525 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "840x525d60_0"   :  840 x  525 @  59.9 Hz DoubleScan 
(II) NVIDIA(0): "800x600"        :  800 x  600 @  60.3 Hz 
(II) NVIDIA(0): "800x600_56"     :  800 x  600 @  56.2 Hz 
(II) NVIDIA(0): "800x512"        :  800 x  512 @  60.2 Hz DoubleScan 
(II) NVIDIA(0): "720x576"        :  720 x  576 @ 50 Hz (CEA-861B Format 18)
(II) NVIDIA(0): "720x576_50i"    : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26)
(II) NVIDIA(0): "720x576_50i_0"  : (1440)x 576 @ 50 Hz Interlace (CEA-861B Format 22)
(II) NVIDIA(0): "720x480"        :  720 x  480 @ 59.94/60 Hz (CEA-861B Format 3)
(II) NVIDIA(0): "720x480_60i"    : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11)
(II) NVIDIA(0): "720x480_60i_0"  : (1440)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 7)
(II) NVIDIA(0): "720x450"        :  720 x  450 @  59.9 Hz DoubleScan 
(II) NVIDIA(0): "680x384"        :  680 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "680x384d60_0"   :  680 x  384 @  59.8 Hz DoubleScan 
(II) NVIDIA(0): "640x512"        :  640 x  512 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "640x480"        :  640 x  480 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "640x480_60"     :  640 x  480 @  59.9 Hz 
(II) NVIDIA(0): "640x480_60_0"   :  640 x  480 @ 59.94/60 Hz Interlace (CEA-861B Format 1)
(II) NVIDIA(0): "576x576"        : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26)
(II) NVIDIA(0): "576x480"        : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11)
(II) NVIDIA(0): "576x432"        :  576 x  432 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "512x384"        :  512 x  384 @  60.0 Hz DoubleScan 
(II) NVIDIA(0): "400x300"        :  400 x  300 @  60.3 Hz DoubleScan 
(II) NVIDIA(0): "400x300d56"     :  400 x  300 @  56.3 Hz DoubleScan 
(II) NVIDIA(0): "360x576"        : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26)
(II) NVIDIA(0): "360x480"        : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11)
(II) NVIDIA(0): "320x240"        :  320 x  240 @  60.1 Hz DoubleScan 
(II) NVIDIA(0): "288x576"        : (2880)x 576 @ 50 Hz Interlace (CEA-861B Format 26)
(II) NVIDIA(0): "288x480"        : (2880)x 480 @ 59.94/60 Hz Interlace (CEA-861B Format 11)
(II) NVIDIA(0): 
(II) NVIDIA(0): Computing DPI using physical size from ONK TX-SR605 (DFP-1)'s
(II) NVIDIA(0):     EDID and first mode to be programmed on ONK TX-SR605
(II) NVIDIA(0):     (DFP-1):
(II) NVIDIA(0):   width  : 1920 pixels  1600 mm (DPI: 30)
(II) NVIDIA(0):   height : 1080 pixels  900  mm (DPI: 30)
(--) NVIDIA(0): DPI set to (30, 30); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): GPU initialized
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0): First mode initialized
(II) NVIDIA(0): Using built-in logo image.
(II) NVIDIA(0): Logo is 744x537 with depth 24.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(II) NVIDIA(0): Composite wrapper disabled.
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Mouse? 1.0A
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Device: "/dev/input/event5"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Configuring as mouse
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse? 1.0A" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) set acceleration profile 0
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) APM registered successfully
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): kernel module enabled successfully
(II) NVIDIA(0): GPU initialized
(II) NVIDIA(0): Interrupts enabled
(II) NVIDIA(0): Setting mode "DFP:nvidia-auto-select+0+0"
(II) NVIDIA(0): First mode initialized
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Visuals set up
(II) NVIDIA(0): Pixmap depths set up
(II) NVIDIA(0): GLX visuals set up
(II) NVIDIA(0): Framebuffer set up
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(II) NVIDIA(0): Composite wrapper disabled.
(II) NVIDIA(0): Default colormap initialized.
(II) NVIDIA(0): Palette loaded
(II) NVIDIA(0): DPMS enabled
(II) NVIDIA(0): Screen initialization complete
(==) RandR enabled
(II) Initializing extension GLX
(EE) XKB: No components provided for device Virtual core keyboard
(WW) Couldn't load XKB keymap, falling back to pre-XKB keymap
[config/dbus] couldn't register object path
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "gb"
(**) AT Translated Set 2 keyboard: xkb_layout: "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Mouse? 1.0A
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: always reports core events
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Device: "/dev/input/event5"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Configuring as mouse
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Wireless Optical Mouse? 1.0A: (accel) set acceleration profile 0
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Microsoft Microsoft Wireless Optical Mouse? 1.0A: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

---

### Post by jt_04 on 2009-08-05
that output is supposed to tell you what modelines are supported by your TV. But, in your case, the output is not giving you the modelines supported by your TV, it's giving you the modelines that your _receiver_ can support (which may not be the same as the TV's modelines).

try connecting the PC directly to the TV and get it working.  try using the modelines from the modeline database, or the modelines that I used for my TV in my earlier post.  If that doesn't work, then run that command again and look at the output to find the right modelines for your TV, following the instructions in post 11.

when i was figuring out my TV, it helped to read up on what a modeline was and the format.  here is a [link to the xorg man page]("http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html")

---

### Post by ricankevo on 2009-08-09
After updating the xorg.conf and restarting X all i get is a black screen on my Panasonic Plasma? But no errors in Xorg.0.log file. Any suggestions?

After playing around some more I can alter the 1080 down to whatever needed(eg. 1050, 1060 etc...) but when I alter 1920 to anything lower then 1910 it results in a black screen when I restart gdm. any help is appreciated. 

Panasonic S1 50in Plasma 1080p
Nvidia 9400gt dvi to hdmi

---

### Post by sumi15sim on 2009-10-19
Thank U sooo much been looking for this :D

---

### Post by mehturt on 2009-12-28
Thanks for this info, I was able to remove much of the overscan by the info from this thread.  Note that I was not able to remove all of it, about 10 to 20 pixels on the left are still hidden.
I am using Nvidia 8200 on Samsung LE32.

---

### Post by smiggs on 2009-12-30
I've been trying to get a Geforce 7600GS to display 1920x1080 on a LG M227WDP without shifting the picture slightly up and to the left.

I've spent all evening on this and I've come to the conclusion that I have the [modelines ignored bug]("https://bugs.edge.launchpad.net/ubuntu/+source/xorg-server/+bug/280894"). 

However with these settings in my xorg.conf file

```
Option "ExactModeTimingsDVI" "TRUE"
```

in the specific monitor

and

```
Option "UseEDID" "FALSE"
```

under the device the monitor is using so monitor0 uses device0.

The NVIDIA X Server settings defaulted to 1920x1200 which fitted in the screen but I was able to change the NVIDIA X Server settings to 1920x1080 still within the correct parameters and it has held the pose with a complete reboot.

The NVIDIA X Server put this into the xorg.conf:

```
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT: 1920x1080_60.00 +0+0, DFP: 1280x1024 +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
```

I have attached my full xorg.conf for info. I'm utterly baffled as to how or why it works but it does. Such is my bewilderment that I've left in the last modeline I tried because I don't really want to touch anything in case I'm wrong.

---

### Post by ogbk on 2010-01-05
Hello,

Did anyone manage to fix the problem that changing H2/H3 V2/V3 fields doesn't seem to have any effect? I see a couple of people seem to have had a similar problem, but no-one seems to have resolved it yet.

I can get the X config working, but no matter what I change these values to, it still won't move the desktop from the top left corner?

I'm running an asrock 330 (with Nvidia ion) connected to a Samsung le32r41bx TV.

---

### Post by bbear1 on 2010-01-05
Sorry to be late to catch up on this thread but for some reason I rarely get the notification emails when someone updates this thread.

I am able to adjust the size and position of the display on my Panasonic 42" plasma, but I was got nowhere with it until I switched from using component cables to DVI/HDMI.

I forget where I read it (nvidia forums probably) but I recall that there was a problem when using component as the timing settings in the xorg.conf get ignored. From what I can remember you just have basic settings available in xorg.conf for NTSC, PAL, etc. I don't know what cable you are using however.

I am now using a DVI to HDMI cables and the nvidia driver respects the settings in my xorg.conf. I don't force the timings in my xorg.conf however, instead it just points to a custom EDID  bin file which I created using a Excel spreadsheet which I put together some time ago.

Messing around with the EDID data is tricky (and potentially dangerous), that is what I put together a spreadsheet to help me work out the correct EDID bytes.

---

### Post by ogbk on 2010-01-06
The connection is HDMI>HDMI so it should work really. I'll take a look at the custom eDID thing then as that looks like the best hope.

thanks

---

### Post by bbear1 on 2010-01-06
ogbk,
ok, hdmi connection rules out the component problem I mentioned, however it is always possible that the EDID being read from your TV is bad (it happens with some screens apparently)

If you look at your xorg log file does it say that your modeline has been successfully validated?

---

### Post by Gorthaur on 2010-02-17
I know this thread has been here for a long time and I it's been a while since I posted in this thread but if you can download the latest NVIDIA driver, right now I'm using version 190.53, it is possible to adjust overscan compensation going into NVIDIA X server settings. Look for the option Overscan Compensation. Hope it helps somehow.

---

### Post by wurzel21 on 2010-03-02
as a noobie was hoping the overscan option in 190.53 driver would be my saviour:confused:
But I can not find it any where on the NVIDIA x server settings app.

any ideas please :)

---

### Post by Bullwinkle_Moose on 2010-03-07
The problem is that only one version of the NVIDIA driver apparently had the overscan compensation slider, and there are reports it doesn't work on some systems.  For those still having issues, see [http://www.nvnews.net/vbulletin/showthread.php?t=148662](http://www.nvnews.net/vbulletin/showthread.php?t=148662)

---

### Post by przemeklach on 2010-03-19
> **Gorthaur said:**
> I know this thread has been here for a long time and I it's been a while since I posted in this thread but if you can download the latest NVIDIA driver, right now I'm using version 190.53, it is possible to adjust overscan compensation going into NVIDIA X server settings. Look for the option Overscan Compensation. Hope it helps somehow.

Hi,

So yes I confirm that the above mentioned works; however, the setting for adjusting for the overscan disappears when I change my resolution to 1920x1080: the option is only available when I have 720 selected. I don't understand why this happens. Has anyone come across this problem and fixed it?

I'm running an Acer AR1600 hooked up to a Sharp Aquos 42 inch tv using HDMI.

Thanks in advance.

---

### Post by samuelkarush on 2010-04-12
im using this guide in karmic 9.10, its gotten me a almost there, but the custom modeline i created isnt being validated, as shown in xorg.log.
 My Xorg.conf file didnt have a monitor section, so I added that. I commented out the options in the device section so i could get back to a usable resolution. heres the xorg file:

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24

SubSection "Display"
Modes "1280x720"
EndSubSection

EndSection

Section "Monitor"
        Identifier "SANYO LCD"
        Option "ExactModeTimingsDVI" "TRUE"
        HorizSync 15-46
        VertRefresh 59-61
        Modeline "1280x720" 74.25 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
        Modeline "720x480" 27.00 720 736 798 858 480 489 495 525 -hsync -vsync
Endsection


Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        ##Option "UseEDID"        "False"
        ##Option "ModeValidation" "NoEdidModes"
EndSection



One thing i noticed, which may mean nothing, is that with this xorg.conf file, the xorg.log shows that the display device is a sanyo lcd. If i uncomment the above lines, the display device is just dfp-0.
 the modelines are exactly the values i got from running: X -verbose 6 > ~/xlog.txt 2>&1 

 any ideas why this modeline wouldnt be validated?

ok, i figured out why it wasnt validated, i had to add this to the screen section : 
 Monitor  "SANYO LCD"
 this matches the identifier in the monitor section.

 ok, so now i can edit the h1 values with multiples of 8, x will start and display, but display looks no different. if i edit v1, i get no display, regardless of multiples i use.


ok, heres where im at. ive tried a ton of xorg options i read about, none have an effect on my use of modeline. i can get a very small change in the h1 value to have an effect,  but any changes to v1,2,3 will leave me with a blank screen when i start x. I do however see a difference in where the login information is placed on the screen when i stop x. It is further down the screen than normal.
 so i read about creating a custom modeline earlier in this thread. sounds great, but i dont use windows, so i found this:[http://sathyasays.com/2008/10/26/how-to-tackle-screen-resolution-problems-in-linux/#comment-39052](http://sathyasays.com/2008/10/26/how-to-tackle-screen-resolution-problems-in-linux/#comment-39052),  which was simple enough to edit the edid.bin i pulled from my tv. I put the file in X11 and put the right options in xorg.conf and pointed it to the new edid. and.... it is ignored. i tried putting it in the device, screen and monitor sections and have tried everything i have seen using google the last couple days, but nvidia-auto-select takes over. i could put a dear john letter in there for all it cares. it seems like i could at least get some kind of error reported? I am using this command every time i start x to see what is going on:  sudo X -verbose 6 > ~/xlog1.txt 2>&1 
 im not done trying, but i have to wonder, is there some characteristic of my tv that is holding me back? I did notice that when i got the new edid.bin file built, when i used parse-edid to read it the hsync and vsync values where out of range of what info i got from the the tv. maybe this is the problem?

---

### Post by SpiffWilkie on 2010-04-28
I am trying to follow instructions as written starting in post 35 but am having issues getting morefunc to behave on my system.  Is there anyone that could possible pop my edid data into the spreadsheet and give me the results?  This is my edid.bin data as given by Monitor Asset Manager.  I am going bonkers trying to get this thing sorted out in Ubuntu on an Acer Revo.  The overscan is killing me.  Thanks.
```

Monitor
  Model name............... LC-47SB57UT
  Manufacturer............. Sharp
  Plug and Play ID......... SHP4757
  Serial number............ n/a
  Manufacture date......... 2009, ISO week 0
  -------------------------
  EDID revision............ 1.3
  Input signal type........ Digital
  Color bit depth.......... Undefined
  Display type............. RGB color
  Screen size.............. 1040 x 580 mm (46.9 in)
  Power management......... Not supported
  Extension blocs.......... 1 (CEA-EXT)
  -------------------------
  DDC/CI................... n/a

Color characteristics
  Default color space...... Non-sRGB
  Display gamma............ 2.20
  Red chromaticity......... Rx 0.643 - Ry 0.332
  Green chromaticity....... Gx 0.272 - Gy 0.599
  Blue chromaticity........ Bx 0.152 - By 0.067
  White point (default).... Wx 0.285 - Wy 0.293
  Additional descriptors... None

Timing characteristics
  Horizontal scan range.... 15-76kHz
  Vertical scan range...... 55-71Hz
  Video bandwidth.......... 150MHz
  CVT standard............. Not supported
  GTF standard............. Not supported
  Additional descriptors... None
  Preferred timing......... Yes
  Native/preferred timing.. 1920x1080p at 60Hz (16:9)
    Modeline............... "1920x1080" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
  Detailed timing #1....... 1280x768p at 60Hz (16:9)
    Modeline............... "1280x768" 68.250 1280 1328 1360 1440 768 771 778 790 +hsync -vsync

Standard timings supported
     720 x  400p at  70Hz - IBM VGA
     640 x  480p at  60Hz - IBM VGA
     800 x  600p at  60Hz - VESA
    1024 x  768p at  60Hz - VESA
    1280 x  720p at  60Hz - VESA STD
    1280 x 1024p at  60Hz - VESA STD
    1440 x  900p at  60Hz - VESA STD
    1680 x 1050p at  60Hz - VESA STD

EIA/CEA-861 Information
  Revision number.......... 3
  DTV underscan............ Not supported
  Basic audio.............. Supported
  YCbCr 4:4:4.............. Supported
  YCbCr 4:2:2.............. Supported
  Native formats........... 1
  Detailed timing #1....... 1280x720p at 60Hz (16:9)
    Modeline............... "1280x720" 74.250 1280 1390 1430 1650 720 725 730 750 +hsync +vsync
  Detailed timing #2....... 720x480p at 60Hz (16:9)
    Modeline............... "720x480" 27.000 720 736 798 858 480 489 495 525 -hsync -vsync
  Detailed timing #3....... 1920x1080i at 60Hz (16:9)
    Modeline............... "1920x1080" 74.250 1920 2008 2052 2200 1080 1084 1094 1124 interlace +hsync +vsync
  Detailed timing #4....... 1440x480i at 60Hz (16:9)
    Modeline............... "1440x480" 27.000 1440 1478 1602 1716 480 488 494 524 interlace -hsync -vsync

CE video data (timings supported)
    1920 x 1080i at  60Hz - HDTV (16:9, 1:1)
    1280 x  720p at  60Hz - HDTV (16:9, 1:1)
     720 x  480p at  60Hz - EDTV (16:9, 32:27)
     720 x  480p at  60Hz - EDTV (4:3, 8:9)
     640 x  480p at  60Hz - Default (4:3, 1:1)
    1920 x 1080p at  60Hz - HDTV (16:9, 1:1) [Native]
     720 x  480i at  60Hz - Doublescan (16:9, 32:27)
     720 x  480i at  60Hz - Doublescan (4:3, 8:9)
    1920 x 1080p at  24Hz - HDTV (16:9, 1:1)
    NB: NTSC refresh rate = (Hz*1000)/1001

CE audio data (formats supported)
  LPCM    2-channel, 16/20/24 bit depths at 32/44/48 kHz

CE vendor specific data (VSDB)
  IEEE registration number. 0x000C03
  CEC physical address..... 0.3.0.0
  Supports AI (ACP, ISRC).. Yes
  Supports 48bpp........... No
  Supports 36bpp........... Yes
  Supports 30bpp........... Yes
  Supports YCbCr 4:4:4..... No
  Supports dual-link DVI... No
  Maximum TMDS clock....... 150MHz

Report information
  Date generated........... 4/28/2010
  Software revision........ 2.50.0.849
  Operating system......... 5.1.2600.2.Service Pack 2

Raw data
  00,FF,FF,FF,FF,FF,FF,00,4D,10,57,47,01,01,01,01,00,13,01,03,80,68,3A,78,0A,8D,10,A4,55,45,99,27,
  11,49,4B,A1,08,00,81,C0,81,80,95,00,B3,00,01,01,01,01,01,01,01,01,02,3A,80,18,71,38,2D,40,58,2C,
  45,00,0F,48,42,00,00,1E,A9,1A,00,A0,50,00,16,30,30,20,37,00,0F,48,42,00,00,1A,00,00,00,FC,00,4C,
  43,2D,34,37,53,42,35,37,55,54,0A,20,00,00,00,FD,00,37,47,0F,4C,0F,00,0A,20,20,20,20,20,20,01,8D,
  02,03,21,71,49,05,04,03,02,01,90,07,06,20,23,09,07,07,67,03,0C,00,30,00,B0,1E,E3,05,03,01,E2,00,
  0F,01,1D,00,72,51,D0,1E,20,6E,28,55,00,0F,48,42,00,00,1E,8C,0A,D0,8A,20,E0,2D,10,10,3E,96,00,0F,
  48,42,00,00,18,01,1D,80,18,71,1C,16,20,58,2C,25,00,0F,48,42,00,00,9E,8C,0A,A0,14,51,F0,16,00,26,
  7C,43,00,0F,48,42,00,00,98,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,00,66

```

---

### Post by bbear1 on 2010-04-28
SpiffWilkie,
I am the author of that spreadsheet and post #35.

You mention that you have popped the info from the EDID dump but that morefunc is not behaving for you. What version of Excel are you running?
Morefunc has been around for a while, I don't know if it is compatible with later versions of Excel.

I still have morefunc installed and also have an older version of Excel so hopefully it will still work for me.

Later versions of Excel may well support the hex functions provided by morefunc, I have not had a chance to check. I will have a go at entering your EDID info into my template of that spreadsheet and get back to you soon.

---

### Post by SpiffWilkie on 2010-04-29
> **bbear1 said:**
> SpiffWilkie,
I am the author of that spreadsheet and post #35.

You mention that you have popped the info from the EDID dump but that morefunc is not behaving for you. What version of Excel are you running?
Morefunc has been around for a while, I don't know if it is compatible with later versions of Excel.

I still have morefunc installed and also have an older version of Excel so hopefully it will still work for me.

Later versions of Excel may well support the hex functions provided by morefunc, I have not had a chance to check. I will have a go at entering your EDID info into my template of that spreadsheet and get back to you soon.

I am using Excel 2003 and I believe morefunc 5.06.  I have installed it and have the morefunc menu in Excel.  I have verified that it's checked on the add-in page, but I get the #name? error whenever I enter in new information and the cells recalculate.  I appreciate the help!

Thanks!
Steve

---

### Post by bbear1 on 2010-04-29
I am using the same version of Excel (2003). I am not sure how to query the Morefunc version and I installed it some time ago and I can't recall which version I downloaded at that time.

Under Tool/Add-In's in Excel, you do have Morefunc ticked?

I also have 'Analysis toolpack' ticked, I am not sure where that came from. Anyway, I just turned off that add-in and my spreadsheet looks ok.

I have transferred the values from your EDID dump from the Monitor Asset Manager and entered into my spreadsheet. My spreadsheet calculates the modeline to be exactly what is in the Asset Manager report, also the checksums match. So this confirms that I have entered all the info correctly, so we can start to tweak the timing parameters and generate the modified EDID.

Before we try a modified EDID however, can you confirm that you have set up your xorg.conf to load a custom EDID, and that it is able to load the original one ok? (check the xorg0.log to make sure it is not rejecting the EDID and defaulting to some other setting)

---

### Post by bbear1 on 2010-04-29
My spreadsheet populated with data from your Monitor Asset Manager report is attached.

---

### Post by SpiffWilkie on 2010-05-02
Thanks so much for helping out.  I edited edid.bin but haven't been successful in loading it.  This is the text from a fresh xorg.conf file that I just dumped

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sharp LC-47SB57UT"
    HorizSync       15.0 - 76.0
    VertRefresh     55.0 - 71.0
    Option         "DPMS" "false"
    Option         "ConnectedMonitor" "DFP"
    Option         "UseEDID" "TRUE"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "ION LE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseDisplayDevice" "DFP-0"
    Option         "CustomEDID" "DFP-0:/etc/X11/new_edid.bin"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I am a complete noob with linux so any help is greatly appreciated.

Thanks!

---

### Post by bbear1 on 2010-05-02
SpiffWilkie,
before you try loading a modified edid.bin, have you checked that your can load the original one?

Just change that CustomEDID line in your xorg.conf to point to the original edid which you read from your monitor/tv.

This is the first step, before trying to load any modified one.

---

### Post by bbear1 on 2010-05-03
SpiffWilkie,,
can you please post your xorg0.log?

(in /var/log)

I checked your xorg.conf to the one which I am using and there are some differences but the only ones which are possibly  relevant are that in my xorg.conf I have the following:

Section "Screen"
   ..
   ..
        Option "AddARGBGLXVisuals" "true"

        SubSection "Display"
          Depth 24
          Modes "1920x1080"
        EndSubSection
    ..
    ..
EndSection

I don't know if it matters that you have metamodes defined in your xorg.conf or not.

Anyway, if you can provide your xorg0.log then it might give some clues.

Also, I really think that you ought to make sure you can load the original EDID first before you go creating custom versions of it.

Do this in "baby steps" as much as possible.

---

### Post by foxruns on 2010-08-11
this is a giant thread..i read a lot of the begining of it however i couldnt find one thing..
im using twin view with a 22-ish or something monitor (which works fine) and a hannspree 25 inch which is having the same overscan issure..so i was wondering if anyone could tell me if hpadricks guide would work for this?

---

### Post by Brian96 on 2011-01-30
So, is hpadrick's fix still the recommended course for 10.04 and 10.10?  I'm kind of surprised nvidia hasn't put an overscan correction back into the nvidia-settings GUI, particularly since there is such an adjustment in the Windoze version.

---

### Post by spacey42 on 2011-03-11
Another thanks to hpadrick, years (and versions) later and still fixed me right up!  

For future reference, I have a Sony WEGA KV30HS420 TV.  While capable of 1080i, I find the 720p resolution easier on the eyes.  I left just a touch of overscan around the edges, and here's the modeline I settled on:

ModeLine       "1280x720" 74.180 1144 1324 1364 1650 666 708 713 750 +hsync +vsync

---

### Post by shubes on 2011-04-04
I have a Zotac Zbox (nvidia GT218) running Ubuntu 10.10, using HDMI output to a Mitsubishi WD-52527, and had the overscan problem. In the nvidia settings under GPU0 - (ION) -> DFP-n (Mitsubishi MEUSPTUS), there's a slider control for Overscan Compensation that solves this problem nicely. I needed to go to 144 to get a nice fit. The horiz-vert ratio isn't perfect, but it's close enough.

Kudos to everyone involved with making this work to begin with, and more recently making it simple to adjust.

I have an NVidia Quadro FC 570M in my deskbook computer running Ubuntu 10.4 with NVidia drivers, and it has an Overscan Compensation slider as well, although I haven't used it. I expect it works the same as in 10.10.

So to answer Brian's question, I think that hpadrick's method has become the 2nd choice, first choice being to find and use the Overscan Compensation sliders that are now included in the GUI.

---

### Post by GROwen on 2011-07-18
Finding this thread was such a relief.

A big thanks to hpadrick, I'd thought I'd run out of options until I found this. Which unfortunately took soooo much time, can't believe it doesn't rank better in searches.

Unfortunately my Nvidia card doesn't support the 'overscan compensation slider' which is a bugger but I can now mess about with ModeLines to my hearts content.

One catch with hpadrick's solution for me is that I don't see an X or a grey screen when I run the command 'X'. I can work around that by restarting the X-server checking res, going back to stop it etc but I'd like to know if this is a symptom of a bigger problem that I should be concerned about?

I don't have my xlog.txt log available at the moment but if useful I can post.

Thanks in advance for any help with this.

---

### Post by ausairman on 2011-07-22
Unfortunately, hpadrick's instructions didn't work for me. When I type

```
sudo /etc/init.d/gdm stop
```

I receive this message:

```
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop
```

So then I try typing

```
service gdm stop
```

and it says

```
stop: unknown instance:
```

I tried typing just "sudo gdm stop" which produced this:

```
WARNING**: Could not acquire name; bailing out
```

Anyway so I tried to continue (the first message was a bit vague as to whether it actually failed or was just recommending a different solution). When I typed this

```
X -verbose 6 > ~/xlog.txt 2>&1
```

I briefly saw half a NVIDIA logo and then the screen went black. Ctrl+alt+backspace had no effect and I just had to turn off the computer manually.

I am running ubuntu 11.04 on a Dell M1530 (core duo with GT8600M). The reason I'm trying to do this is because I want to run the laptop on my TV through a HDMI cable, and the screen runs off the edge of the TV. 

I would really appreciate some help as I have very little experience with ubuntu, EDID, etc.

Thanks in advance!

---

