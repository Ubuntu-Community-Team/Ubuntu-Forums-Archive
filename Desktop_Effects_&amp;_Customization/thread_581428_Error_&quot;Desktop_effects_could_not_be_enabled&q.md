---
title: "Error: &quot;Desktop effects could not be enabled&quot;"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by elreteipos on 2007-10-19
Just tried to enable desktop effects on Ubuntu 7.10 (upgraded from 7.04) and I got an error saying "Desktop effects could not be enabled". *compiz --replace* returned this output:> Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Windowmanager waarschuwing: "" in de configuratiedatabase is geen geldige waarde voor toetsbinding "toggle_shaded"
Windowmanager waarschuwing: "" in de configuratiedatabase is geen geldige waarde voor toetsbinding "panel_main_menu"My apologies for the Dutch error message. Here's a rough translation:> Window manager warning: "" in the configuration database is no valid value for key binding "toggle_shaded"I know that sounds a little non-English-ish, but I couldn't make out what the error message meant.

What could be wrong in my configuration? I'm using some cheap graphic card called Intel Extreme Graphics. I have managed to get Beryl running on my PC a few months ago, but I've had no luck with Gutsy's desktop effects yet.

---

### Post by coolen on 2007-10-19
Mine don't work either, although my error message is very different...
Perhaps if you create a key binding for toggle_shaded, it'll work?
Hit Alt+F2, and type in gconf-editor. From there, go to apps -> metacity -> window_keybindings, find the toggle_shaded option, and set it to something. Perhaps <Control>F4. Not sure if that conflicts with anything, but it's fairly simple.

---

### Post by Amaranth on 2007-10-19
I'm guessing you're using the 'vesa' driver instead of the 'intel' or 'i810' driver. Check out your xorg.conf and make sure you're using the right driver.

---

### Post by elreteipos on 2007-10-20
> **coolen said:**
> Mine don't work either, although my error message is very different...
Perhaps if you create a key binding for toggle_shaded, it'll work?
Hit Alt+F2, and type in gconf-editor. From there, go to apps -> metacity -> window_keybindings, find the toggle_shaded option, and set it to something. Perhaps <Control>F4. Not sure if that conflicts with anything, but it's fairly simple.Alright, tried that and now I get one error message of that kind instead of two:> Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Windowmanager waarschuwing: "" in de configuratiedatabase is geen geldige waarde voor toetsbinding "panel_main_menu"You could be right, although it looks more like an error that Metacity pooped out if you ask me. (Because starting Compiz returns "aborting and using fallback: /usr/bin/metacity".)> **Amaranth said:**
> I'm guessing you're using the 'vesa' driver instead of the 'intel' or 'i810' driver. Check out your xorg.conf and make sure you're using the right driver.I think I'm going to need some help with that. I'm not really familiar with X's config file. :)

**Update:** I got this from lshw:>         *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810
And my current xorg.conf entry for my graphics card:> Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic video card"
	Monitor		"MD32117PQ"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

### Post by exchequer598 on 2007-10-20
I recently did a fresh install of Gutsy and tried to enable the Desktop Effects when I got an error that desktop effects could not be enabled. Following the last post, I too typed in lshw in the Terminal window and got this :

>  *-display
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglr

AWN won't work as Compiz was not running. Please help!
Thanks

---

### Post by mhf on 2007-10-20
Finally after many hours of hard work, frustration and reading almost every thread I got it work.
I am new to linux. I just followed the the tuts on the following links and vola compiz works . Guys you cant measure mig pleasure. After 3 f... hair pulling days it works finally. hurra

Just follow these tuts.
its all about installing xgl and it will work

[http://linuxmint.com/forum/viewtopic.php?p=39204](http://linuxmint.com/forum/viewtopic.php?p=39204)

and then read this

[http://forlong.blogage.de/#blogentry_494](http://forlong.blogage.de/#blogentry_494)

---

### Post by mhf on 2007-10-20
I think I was over exited. It works but now I cannot run CompizConfig Setting Manager. Nothing happens when I click on it.
I logged off and changed the session to GNOME but I still have the 3D effects and still cannot run CompizConfig Setting Manager. I think the script has killed it. I am very tired. I will sleep for now, I will return back with the hope that you guys might have a solution. 
good luck

---

### Post by elreteipos on 2007-10-21
It's working! As Amarant said, it may not work if you're using the VESA driver. So I had to change> Section "Device"
	Identifier	"Generieke videokaart"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSectionto> Section "Device"
	Identifier	"Generieke videokaart"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSectionas I have a Intel Extreme Graphics video card. I had to install xserver-xorg-video-intel first though.

Maybe that's why it won't work. Open /etc/X11/xorg.conf and look for Section "Device". If Driver is set to "vesa", you may want to go look for a proper driver for your video card. What kind of video card do you have?

---

### Post by missingno on 2007-10-21
I'm using an ATI Radeon X1200 and it lets me turn on desktop effects, but I get an error message that says "The composite extension is not available" and it doesn't actually work. Even more bizarrely, clicking OK doesn't close the error message, only clicking the X does. Has anyone else seen this message? I'd really like to get that shiny pretty spinny workspace cube working.

---

### Post by jml75 on 2007-10-21
From what I discovered, for ATI cards, you need to install the "xserver-xgl" package to get desktop effects working.

So do :

sudo apt-get install xserver-xgl

or install it with Synactic

After the install, it warns you that xgl will start automatically after you restart X so just restart the computer and you should be good to enable the Desktop effects.

It did for me.

Cheers!

Jonathan

---

### Post by missingno on 2007-10-21
Thanks, it works great now! There's a minor bug that gives me the message about how xgl will start on the next boot every single time I boot up Ubuntu, but that's no big deal.

---

