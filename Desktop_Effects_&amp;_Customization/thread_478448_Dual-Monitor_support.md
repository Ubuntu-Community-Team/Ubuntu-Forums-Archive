---
title: "Dual-Monitor support?"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by MichaelLerch on 2007-06-19
I've installed Ubuntu 7.04 [Feisty right?] and in order to do so I had to use a old 17" CRT monitor because my 20.1" BenQ LCD monitor wasn't displaying the screen [it has to be in a support resolution above 800x600].

My question is.. how do I get my BenQ LCD monitor that displays up to 1680x1050 to display my Ubuntu desktop, with full resolution [if possible]?

Thanks in advance,
Michael

---

### Post by dannyboy79 on 2007-06-19
you need to use propritary video drivers to get that high of  a res I am pretty sure. first post what the output is from entering this command into the terminal

lspci -v

then based on that, you'll need to install better graphics card drivers than what you're using. nvidia card are the easiest, then intel, then sis, then ati, this is just my opinion. otherwise, you could always try to add the resolution you want within your /etc/X11/xorg.conf file without even trying to install other gfx drivers BUT you won't get accelerated gfx for say beryl or compiz. sometimes even matching movies will be slow and stuttered.

first back it up with this command

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_b4_changes

then change it by editing it with root privlages

gksudo gedit /etc/X11/xorg.conf

then go down until you find a section like this:
    SubSection     "Display"
        Depth       24
        Modes      **"1600x1200"** "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

and just add in what res you want (my example was adding the 1600x1200), make sure you do it EXACTLY like the others, also in order,  and also that there is a space in between the existing entry and your new one. then make sure you save the file and exit.

then restart your xserver by hitting ctrl-alt-backspace (NOTE: this will shutdown anything you have running, so make sure nothing else is running)

now when you re login hopefully that new choice is there. if not, then it's most likely a gfx driver issue.

---

### Post by MichaelLerch on 2007-06-19
How will that get my second monitor working though?

---

### Post by dannyboy79 on 2007-06-19
> **MichaelLerch said:**
> How will that get my second monitor working though?

you didn't ask that, you asked to get your benq working which is what I am trying to do. I can't help you if you don't post the output of the command I asked so that I can tell which video card you have. I strongly suggest if some1 is trying to help you and they ask your to post the output from something, the easiest way to lose that person from helping you is to post back without any of the info they requested, and to also a different question.

If you'd like my help, then please provide info and do what I suggested and we'll go from there.

---

### Post by MichaelLerch on 2007-06-19
02:00.0 VGA compatible controller: ATI Technologies Inc R520 [Radeon X1800] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 0b12
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at d1000000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at 9000 [size=256]
        Expansion ROM at d0000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.1 Display controller: ATI Technologies Inc R520 [Radeon X1800] (Secondary)
        Subsystem: ATI Technologies Inc Unknown device 0b13
        Flags: fast devsel
        Memory at d1010000 (64-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <access denied>



Sorry, I'm new to all this still..



This is the HUGE section for the monitor(s?) that I found in the xorg.conf file you told me to edit


Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"BenQ FP202W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"BenQ FP202W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

---

### Post by dannyboy79 on 2007-06-19
ok, yeah, you won't get that high of a res using the vesa driver. You need to install the Proprietary ATI drivers. I have read the the Envy program here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
I have an Nvidia card so I can't help you specifically but this will at least get you the res you want, from their, you just need to use this guide for your dual display. [http://ubuntuforums.org/showthread.php?t=475189&highlight=ati+dual+head](http://ubuntuforums.org/showthread.php?t=475189&highlight=ati+dual+head)

good luck

---

### Post by MichaelLerch on 2007-06-19
> **dannyboy79 said:**
> ok, yeah, you won't get that high of a res using the vesa driver. You need to install the Proprietary ATI drivers. I have read the the Envy program here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
I have an Nvidia card so I can't help you specifically but this will at least get you the res you want, from their, you just need to use this guide for your dual display. [http://ubuntuforums.org/showthread.php?t=475189&highlight=ati+dual+head](http://ubuntuforums.org/showthread.php?t=475189&highlight=ati+dual+head)

good luck

Thank you so much!  

After using Envy it detected and installed the correct ATI driver, and then made modifications to the xorg.conf file for me. :)

The BenQ is displaying my desktop as I wanted, and its resolution is at 1680x1050 [60hz], just as I hoped.

I know I'm all so new to Ubuntu, but with your help, you just made me understanding of it a little easier. 

Sorry for having caused you troubles earlier!

Sincerely,
Michael

---

### Post by dannyboy79 on 2007-06-19
no problem, I am glad I could help! just try to keep in mind what I said regarding when people try to help you.

---

### Post by TheBuzzSaw on 2007-10-17
I am bumping this thread (instead of creating a new one) because I want to know how good the support is for dual monitors in Gutsy Gibbon. I am running the beta (sadly, I basically missed the RC period; I'm getting the final version tomorrow). Is the support improved between beta and RC/final? On my Darter Ultra laptop, the settings don't even detect that another monitor is plugged in. I cannot configure "screen 2" at all. Everything is grayed out (disabled). I am hoping that the final version will improve the situation. :(

---

