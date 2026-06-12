---
title: "hi i'm a noob in need of help"
date: 2008-01-10
forum: Desktop Environments
---

### Post by origr15 on 2008-01-10
i've installed a 64bit ubuntu gusty gibbon and when i check my refresh rate its on 60 hrz but my screen (AOC 19 '' LCD) with my graphics card (Ge-Force 8600GT 512MG) can do 75 hrz so i checked and i need to install the nvidia display driver from the restricted driver manager but when i do that my scree goes even lower to 52 hrz ' what can i do, i have reinstalled my system cuz i'm afraid from the driver what should i do to get 75 hrz?  

why does my 64 bit ubuntu kinda look like its not finished ' i don't have an upslash and the entering the system sound comes before the screen changes from black...is tha a problem only with my pc?

my pc:
amd athelon64 X2 4600+ 
2 gig of ram
MSI k9n neo motherboard
250 gig of hard drive
Ge-Force 8600GT 512MB

Please Help ME! i came here because people told me that people here are nice , so please help me.

---

### Post by rune0077 on 2008-01-10
You should be able to set the refresh rate in System > Preferences > Screen Resolution.

If the desired rate is not there, you'll need to go to System > Administration > Screens & Graphics, and from here chose your screen model (or just chose standard plug n' play if the model isn't on the list), which should let you pick all resolutions and refresh rates for that model.

---

### Post by b0rka7a on 2008-01-10
Do you mean that when you install the driver, in Screen Resolution you see 52Hz, or the monitor says it's 52Hz ? Because my monitor works on 85Hz and in Screen Resolution I see 52Hz too :)
Run in terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
then add the line below under Section "Device":
```
	Option		"DynamicTwinView"	"false"
```.
Restart the X server and in Screen Resolution you should see the right frequency :) Hope it works.

Edit: Your Section "Device" in xorg.conf should look something like that:
```
Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"DynamicTwinView"	"false"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
```

---

### Post by PeterJS on 2008-01-10
Nothing 64 bit is very polished, it's getting better with every release but it's still the new kid on the block.

I've never messed with the refreshrate on my system, but have you looked at the nvidia config tool *nvidia-settings*, it seems to have settings for pretty much everything, including refesh rates, it might have the proper full range for your card.

---

### Post by origr15 on 2008-01-10
at the Screen Resolution  i have 51 hrz not even 52 i tried to install the driver usinfg envy but it did the same thing as the restricted thini did , so what do i need to do to have 75 hrz?

---

### Post by rune0077 on 2008-01-10
Okay, try this: Open compiz settings manager (advanced desktop effects), click General Options, go to display settings and set the refresh rate from there.

All of this is assuming that you have Compiz up and running.

---

### Post by origr15 on 2008-01-10
i have compiz and the advenced setting but i acnt seem to find what you described

---

### Post by lswest on 2008-01-10
um, the 51Hz that are listed there are actually on par with 75Hz, don't ask me why, but the number listed is lower than what the actual quality is.

---

### Post by origr15 on 2008-01-10
in my picture how can i get minimized windows go to the upper taskbar?
and how can i fix my refresh rate?

---

### Post by rune0077 on 2008-01-10
Refresh rate: go to advance desktop settings (if its not under System > Prefrences, install CCSM first). The very first item in the new window should be called General Options. In this, there's a tab called Display Setting where you can set the refresh rate (amongst other things).

The panel: right-click on the panel and select add to panel, then add the Windows List. Remember to remove it from the lower panel (right-click on it, select remove) so it don't end up in two places at once.

---

### Post by origr15 on 2008-01-10
i cant seem to find CCSM   or what it is...can give me link and a where to put it?

---

### Post by PeterJS on 2008-01-10
You can run ccsm straight from the terminal with the command:
```

ccsm

```
Or in the menu it should at
Sytem > Preferneces > Advanced Desktop Settings

---

### Post by rune0077 on 2008-01-10
CCSM is not preinstalled, though. So if you haven't installed it yet, open synaptic, search for CCSM and then install it first. Then do as above.

---

### Post by origr15 on 2008-01-10
Found it , i now have 75 hrz :
thank god and thank you all!

now i have 2 more question please:
in feisty that i saw once at a frriend house i saw a nice function - he put the mouse cruser on a mp3 song but without double clicking on it and the song kinda gave a preview aaa it kinda plaied the song but with no need of entering it , can you help me find it cuz i dont have it and i want it?

i have installed google toolbar on my firefox and when i press the bookmarks (of the toolbar) it says downloading bookmarks but it never ends , i never get my bookmark (and yes im on th signed in to it)
what can i do about this?

---

### Post by rune0077 on 2008-01-10
For the songs preview, open a Nautilus window. Then Edit > Preferences > Preview. Here you can set the sound preview (as well as others) to your liking. I haven't used it myself, but I think it's what you're looking for.

Can't help you with the other problem, sorry, never used Google toolbar.

---

### Post by origr15 on 2008-01-11
it didnt work

---

### Post by rune0077 on 2008-01-11
Rats! I wouldn't really know where to do it, then.

---

### Post by nanohead on 2008-01-11
I ran CCSM and did the prescribed procedure here, but not my screen is only showing the upper left quarter of the desktop.  The other 75% of my monitor are black and blank.

I cannot believe that screen configurations are still not fixed in Ubuntu and still require days of arcane surgery to solve.   Its getting depressing

---

