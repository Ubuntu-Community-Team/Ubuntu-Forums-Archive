---
title: "No Usplash and Monitor Turns Off While Booting? How do I fix this?"
date: 2008-03-17
forum: Desktop Environments
---

### Post by OzzyFrank on 2008-03-17
OK, while the loss of my cool Usplashes isn't that big a drama, I still need to figure out why it doesn't show, and why the monitor goes into standby mode till it gets to the GDM Login. This is because recently it wasn't going anywhere, and I couldn't see what was happening (or not happening), and I couldn't see any disk activity (via the led light), so I forced a reboot a couple of times (ie: hit the Reset button). After deciding to go into recovery mode, where I could see the verbose mode messages, I realised it has just been trying to do the fsck that gets automatically initiated after 35 or whatever boots.

Now, I have built a new Quad-core system, so this is a fresh reinstall of Ubuntu, but this time 64-bit (which is the only reason I would have bothered with a reinstall, rather than just dd everything to my new SATA drive). I can safely say it isn't an issue with my new 1Gb nVidia video card, since the Windows splash is fine, and the Ubuntu live CD shows me the Usplash (and doubt it has anything to do with my new LCD monitor, since it was the same on the CRT).

So what is doing this when Ubuntu boots? I noticed straight away that with the 64-bit version of Gutsy, some things were turned off by default, like even the Gnome (desktop) splash after login (?? I had to re-enable it with Ubuntu Tweak). So is there a way to force the Usplash and prevent my monitor getting no signal till the login? I'd rather prefer to know what is happening when it seems to stall (like with fsck doing its business). Thanks in advance.

---

### Post by chewearn on 2008-03-18
Take a look here:
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

---

### Post by OzzyFrank on 2008-03-18
Great guide, and I am sure it would help many, but it didn't work for me. Might have if I still have my CRT monitor attached, but not for my widescreen LCD.

I never even knew there was a **usplash.conf**, but did as instructed and replaced **1280x1024** with the more standard **1024x768**, then added the **vga=791** to **menu.lst**, and then **sudo update-initramfs -u -k `uname -r`**. The only difference after that was that instead of *Kernel alive* (and another line below that) appearing at the bottom of the screen before going blank, I saw a flash of *Loading stage...* at the top of the screen.

I then returned the usplash back to the default Ubuntu one, and tried the suggestion of **sudo update-usplash-theme usplash-theme-ubuntu**, but that was still the same.

I then went into Startup-Manager and, seeing the boot resolution as set to **640x480** at only **8 bits**, I changed that to **1024x768 **and **16 bits** (the value for **vga=791**). Still no go.

Now, the figures in the table below are the values for standard ratio screens:

Colours   640x400 640x480 800x600 1024x768 1152x864 1280x1024 1600x1200
--------+--------------------------------------------------------------
4 bits  |    ?       ?      770       ?        ?        ?         ?
8 bits  |   768     769     771      773      353      775       796
15 bits |    ?      784     787      790      354      793       797
16 bits |    ?      758     788      791      355      794       798
24 bits |    ?      786     789      792       ?       795       799
32 bits |    ?       ?       ?        ?       356       ?

... so I've gone looking for the values for widescreen, but can't find any. Does anyone know where to find a list? And will it make a difference? As I mentioned, this was happening on my CRT monitor (for the one day of rebuilding my PC, since the next day I decided to also upgrade my monitor to a 22" widescreen). And my mate with similar monitor gets the usplash, and it is at a low 4:3 resolution so the image is stretched, but he is running Ubuntu i386 (which is why I assumed it was something up with 64-bit Ubuntu). So I assume if I plugged in my old CRT I still wouldn't be seeing a usplash, even with these changes that apparently would suit it.

Any other ideas? As mentioned, the main things isn't so much the usplash, but not having the monitor turn off so if fsck or something needs my attention, I can see it. The only other thing I can think of is telling Startup-Manager to show text messages during boot.

---

### Post by Tomatz on 2008-03-18
Yeah most monitors do this when they are set to a resolution they dont support. Have you got a spare monitor so you can see if you can replicate the bug.  If you cant then it must be specific to your current monitor.

Probably the best place to start :)

Also below is a link to a table of widescreen monitor resolutions. Before using these google your monitors model number and find out what it is capable of (if you don't it could cause problems)

[http://www.prismo.ch/comparisons/](http://www.prismo.ch/comparisons/)

---

### Post by OzzyFrank on 2008-03-18
Of course I am not ruling anything out, but how come most people with widescreens have no problem with the default res for usplash (in 32-bit Ubuntu), with the only difference is that the image is of course stretched? I mean my mate has some Chinese no-name monitor, and I have a good current Asus. The difference between us he didn't go the 64-bit route.

Also, as mentioned, this happened on my 4:3 CRT screen, and also that the usplash shows up fine on a Live CD on this widescreen. And I can, for example, change the res now to a 4:3 one like 1024x768 and the only problem is that it looks crap (as one would expect, hehe). Got no problem with other distros, at least with the Live CDs, just like with Ubuntu's.

Thanks Tomatz for the link, but unfortunately the only "codes" it gives are like "WSXGA+" ("Wide Super Extended Graphics Array plus" - which is my monitor, or the top res of my monitor, being 1680x1050, and 16:10).

Does anyone know where I can find a list like that I supplied above, but for widescreens? Cheers

PS: Tried part 2 of that guide, once I found the link, and in **menu.lst** I found the suggested **# defoptions=splash quiet**, though mine looked like **defoptions=quiet splash vga=791**. I changed it to **defoptions=splash vga=791 quiet**, and when that didn't work tried again without the **quiet**. I of course generated a new boot image thingy with the command **sudo update-usplash-theme usplash-theme-ubuntu**. And I see from comments on that page in response to some saying this only affects old monitors that don't support 1280x1024 that plenty of people have monitors that do support that, but they're still haing the problem. And I assume they are talking about their 4:3 CRT monitors. But I'll try my CRT monitor again, since I haven't ruled out that this has fixed it for that (though I do doubt it).

---

### Post by OzzyFrank on 2008-03-18
OK, just had a look in xorg.conf, and there is none of the usual:

[COLOR="DarkRed"]Modes "1024x768" "800x600" "640x480"[/COLOR]

This is true of the current one (after enabling nVidia restricted drivers) and the original that was backed up! Could this have something to do with it? Could I add the section in myself, or is that not advised? I would assume I could, but then I've never seen my xorg.conf look like this in Ubuntu 32-bit (with my old P4).

I will just paste the few sections related to my display that are in there (never seen xorg.conf look so small either):

[COLOR="Indigo"]Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"[/COLOR]

That's it... all the rest is the mouse, keyboard, wacom, etc stuff. Hey, can someone with more knowledge tell me if it could be the **"NoLogo" "True"** bit? Or does that refer to something entirely different to the usplash?

---

### Post by Tomatz on 2008-03-18
I

---

### Post by OzzyFrank on 2008-03-18
Oh well, there goes that idea. Next!!

---

### Post by KingArthur10 on 2008-03-18
it's a common problem.  Try:

[http://ubuntuforums.org/showpost.php?p=4526658&postcount=5](http://ubuntuforums.org/showpost.php?p=4526658&postcount=5)

---

### Post by Tomatz on 2008-03-18
Maby try using envy ive seen reports that using updated graphics drivers fixed the problem.

**_Use this at your own risk_** 

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Just download and install envy then uninstall your current graphics drivers, reboot then run "envy".

After uninstalling your original drivers and rebooting if you cant start x dont worry just type "envy" at the command line :)

---

### Post by OzzyFrank on 2008-03-18
> **KingArthur10 said:**
> it's a common problem.  Try:

[http://ubuntuforums.org/showpost.php?p=4526658&postcount=5](http://ubuntuforums.org/showpost.php?p=4526658&postcount=5)

Thanks... but I think you somehow missed the fact it's already been tried, hehe.

As for [COLOR="Purple"]**Envy**[/COLOR], yeah I already used that to update my drivers. Got a cool control panel for my nVidia (god I'm glad to be rid of ATI!) but that never fixed the usplash issue. Thanks anyway! And others who don't know about Envy now do (I recommend it!). Cheers

---

### Post by Tomatz on 2008-03-18
My advice is just dont worry its not a real problem and it will probably be fixed when you next upgrade :)

Just turn your box on, run up the garden, come back and pretend all is cool!


:lolflag:

---

### Post by OzzyFrank on 2008-03-18
Hehe... my Quad-core is way too quick for that... I'm at the logon at about 10-15 secs! But as I said, when it doesn't get there after a few mins, I'd like to be able to see what the hell is going on. Let's hope it is rectified at some point (considering I am not the only one).

And the answer to your question: Because you make them read backwards! hehe

---

### Post by wildfox on 2008-03-19
Hi!
 Same problem here, nothing worked from the 'usual' methods. Is this a 8600GT issue?? I have the standard nv-driver, 8600GT, samsung tft (1280x1024 native).

---

### Post by OzzyFrank on 2008-05-05
This problem resolved itself after upgrading to Hardy. I now have my usplash... though would have gladly traded that for leaving alone the things that worked that now don't hehehe!! But I don't think that qualifies this to be marked as [SOLVED]!

---

