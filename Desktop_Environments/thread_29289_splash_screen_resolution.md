---
title: "splash screen resolution"
date: 2005-04-23
forum: Desktop Environments
---

### Post by dlanor78 on 2005-04-23
When I first installed kubuntu, everything looked okay but tiny.  So I changed my resolution from 1600x1200 to 1280x1024.

Now when I boot up kubuntu, the login screen is almost right, but the next screen that tells me the progress of kde starting up is way off.  In the lower rught all I can see is kub instead of kubuntu, and basically just looks too big for the screen.

I've tried fiddling with xorg.conf to fix this, but I can't seem to get it to make any difference.  Here's what my current resolution is once everything is loaded and running:  1280x1024.  And here's the relevent section from xorg.conf (after trying "sudo dpkg-reconfigure xserver-xorg"):

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"A90f"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

Any ideas on how to get the splash screen to display properly?  It's not really urgent, but it is annoying ;)

---

### Post by nad on 2005-04-23
Make a backup copy of this file then edit it to remove all the resolutions and depths that you will not be using. Do not alter the structure in any way (make sure you have an EndSection for every SubSection "Displpay"). You may  delete the Depth 1, 4, 8 and 15 sections completely. Are you ever going to require a mono, 16 color, 256 color and 15bit depth X display?

Now the 16bit and 24bit sections. If you are not going to use the 1600x1200 resolutions, delete them. You wish to keep the 1280x1024 resolution and by having this first in the list this is what the login screen will use. You may also get rid of any other resolutions you do not wish to use. If you wish to keep the ability to use the 1600x1200 resolution, put it at the end of the list. It will continue to show up in your resolution changer applet this way.

Dan M

---

### Post by jobertel on 2005-04-23
On a related note, using the Kubuntu live CD, I am having a tough time forcing KDE into 1024 x 768. It starts in 800 x 600. At the boot: prompt I have tried fb = 1024x768 but it still starts K in 800 x 600. Does anyone know the correct cheat code to force 1024 x 768?

Thanks,

John B.
Still a Linux Newb :confused:

---

### Post by nad on 2005-04-23
John,

I believe it is ' vga=794 '. But modifyiing your xorg.conf so that 1024x768 is the first resolution on the line at your default color depth should start X at that resolution.

Edit: My error. You did mention the live cd. The cheat code should work.

Dan M

---

### Post by dlanor78 on 2005-04-24
I removed all the irrelevant sections like described above, and put 1280x1024 at the beginning of the llist.  Still no change.  So I put 1600x1200 (default after fresh install) and it's exactly the same as before.

I'll keep playing with it later to see if I can find out what's going on here.  In the mean time, I'll just close my eyes or something  during bootup :-?

---

### Post by ludi on 2005-04-24
[QUOTE=dlanor78]I removed all the irrelevant sections like described above, and put 1280x1024 at the beginning of the llist.  Still no change.  So I put 1600x1200 (default after fresh install) and it's exactly the same as before.

I'll keep playing with it later to see if I can find out what's going on here.  In the mean time, I'll just close my eyes or something  during bootup :-?[/QUOTE]
 Try to change the greeting splash by another one in the control center.
I had this problem in ubuntu, putting the 1600x1280 option in the end of section solved my problem.
TIP: you can use Usplash for a "graphical boot". 
Take a look at [http://www.ubuntulinux.org/wiki/USplash/view](http://www.ubuntulinux.org/wiki/USplash/view)  :smile:

---

### Post by ludi on 2005-04-24
[QUOTE=jobertel]On a related note, using the Kubuntu live CD, I am having a tough time forcing KDE into 1024 x 768. It starts in 800 x 600. At the boot: prompt I have tried fb = 1024x768 but it still starts K in 800 x 600. Does anyone know the correct cheat code to force 1024 x 768?

Thanks,

John B.
Still a Linux Newb :confused:[/QUOTE]

Have you tried change the resolution setting in the Screen section of Desktop Settings?

---

### Post by jobertel on 2005-04-26
Dan & Ludi,

In desktop settings 640x480 is the only choice.

I did try "live vga=794" at the boot: prompt. It made all the text during the boot process very small, but KDE was still low resolution.

In /etc/X11/xorg.conf I removed all the resolutions except "1024x768" from all color depths, then restarted X with <Ctl><Alt><Backspace>, but still low res. At some point in the experimentation process I was able to cycle through various resolutions with <Ctl><Alt>+, but the high resolution display was small and in the upper left corner of the screen.

John B.

---

### Post by Darigaaz on 2005-08-28
[QUOTE=jobertel]Dan & Ludi,

In desktop settings 640x480 is the only choice.

I did try "live vga=794" at the boot: prompt. It made all the text during the boot process very small, but KDE was still low resolution.

In /etc/X11/xorg.conf I removed all the resolutions except "1024x768" from all color depths, then restarted X with <Ctl><Alt><Backspace>, but still low res. At some point in the experimentation process I was able to cycle through various resolutions with <Ctl><Alt>+, but the high resolution display was small and in the upper left corner of the screen.

John B.[/QUOTE]

I'm having a very similar problem - trying the vga=* cheat codes changes the text at the boot prompt, but in KDE it switches back to 640x480 regardless and won't let me change out of it. <Ctrl><Alt>+ does nothing for me. My xorg.conf file lists 1024x768 as the first resolution for all color depths.

Did you ever get this resolved, John? If so, how did you fix it?

---

