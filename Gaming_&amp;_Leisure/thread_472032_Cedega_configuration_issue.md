---
title: "Cedega configuration issue"
date: 2007-06-12
forum: Gaming &amp; Leisure
---

### Post by Kralizec on 2007-06-12
Hello,

I'm still relatively new to Linux, but I'm a fast learner. I've installed Cedega on my machine and when I start it up I (naturally) get the configuration screen. Therein lies the problem: I have a widescreen monitor and the bottom of the configuration screen where the buttons are is not visible.
So my question is, are there any ideas as to how I could resize my screen or the window (resize function on window is not available) to fit it or as to how I could configure Cedega from the terminal?

Another similar question is when I'm running Wine, Gecko installs fine but doesn't work when I'm running the game--in Counter-Strike I am unable to enter a game because Gecko doesn't render what it is supposed to render.

Any help that can be provided on either of these topics would be much appreciated. I'll be forthcoming with any more information you need. Thanks!

---

### Post by cogadh on 2007-06-12
Any reason for the double post?

Sounds like you need to fix your xorg.conf file to keep everything on the screen. What type of video card do you have and have you installed the current drivers for it? What screen resolution are you currently running at?

---

### Post by Kralizec on 2007-06-12
Sorry about the double-post. I got pulled away from what I was doing while I was composing the first time and when I got back it had logged me out and I didn't know whether or not the message had posted or not. 

My screen resolution is at max (1280x800) and I have an ATI Xpress card, using the most recent fglrx driver. What would I need to change in xorg.conf? If you need me to I'll post it in to the thread.

---

### Post by cogadh on 2007-06-12
Just post the "Monitor" and "Screen" sections, the rest of it is not necessary.

---

### Post by Kralizec on 2007-06-12
```
Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
   Identifier   "aticonfig-Monitor[1]"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
EndSection
```

```
Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
   Identifier "aticonfig-Screen[1]"
   Device     "aticonfig-Device[1]"
   Monitor    "aticonfig-Monitor[1]"
   DefaultDepth     24
   SubSection "Display"
      Depth   24
      Modes   "1024x768" "1600x1200"
      Viewport   0 0
   EndSubSection
EndSection
```

I just recently set it up so that I could have monitor cloning. The resolution/Cedega issue was occurring before I did that, however.

---

### Post by cogadh on 2007-06-12
Hmmm, it looks like you don't need to make any changes, that setup should be working. Do you run Beryl or Compiz on your system? They can sometimes do funny things to window sizes and locations.

---

### Post by Kralizec on 2007-06-12
Nope, no Beryl, no Compiz; I've tried getting Beryl working but no luck so I've given up for now. Do you know of a way I could rotate my screen so that the resolution could be like 800x1280? I know monitor rotation should be simple but in my resolution settings it is disabled.

---

### Post by cogadh on 2007-06-12
AFAIK you cannot reverse resolution since that is a function of the monitor hardware. Since you have a wide screen monitor, it maintains an aspect ratio of 16:9, meaning that any resolution set on the screen has to be equivalent to or a multiple of 16 x 9. In other words, you can't make the horizontal resolution shorter than the vertical and the only resolutions that should work properly are those that equal approximately 1.66 when divided (1280 / 800 = 1.6). Your monitor probably can do standard 4:3 resolutions as well (800 x 600, 1024 x 768, etc.), but I'd bet they don't look as good.

That does bring up an interesting idea; if you can, change to a standard 4:3 resolution and try running Cedega. I'd be interested to see if it is choking on the widescreen aspect ratio.

---

### Post by Kralizec on 2007-06-12
Trying it in 4:3 ratio didn't help. I'd actually tried that before seeking help here under the same notion that you suggested it. Alas... One other interesting thing about all this is that I had Cedega up and running shortly before this but had to reinstall it...it only started being a pain like this after that first reinstall. If you have any other ideas, I'm all ears, but if not, thanks for taking your time to help me out.

---

