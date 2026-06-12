---
title: "Problems with X, nVidia, compiz, &amp; beryl"
date: 2007-08-22
forum: Desktop Environments
---

### Post by philandstuff on 2007-08-22
Hello all,

I installed ubuntu last week and since then X has not been working reliably. I have had a number of problems:

1. My laptop's maximum resolution is 1600x1200 but I cannot get this resolution with the nvidia driver at all. System->Preferences->Screen Resolution only gave me the options of 640x480, 800x600 or 1024x768; nvidia-settings allowed me to get as high as 1400x1050. The default depth in my xorg.conf is 1600x1200. I can cope with 1400x1050, it's just vexing that I can't get the full range which I know is possible.

I tried playing around with beryl and compiz. However this was fraught with many problems.

2. In compiz, I enabled the desktop cube with 4 viewports:
 a. Often, the window manager would fail completely. Windows would have no titlebars and be rendered unmovable.
 b. Often, but not very predictably, new windows would not be updated - they would only appear as black rectangles. The contents could be interacted with: the mouse cursor turns into an I-beam over text boxes, for example. This is very irritating because currently it is happening to the compiz settings dialog!
 c. When running but not doing anything, a process called compiz.real would consume more than its fair share of CPU cycles - between 10 and 40%. I mean, how does it spend so much effort doing nothing? This happened even with the following disabled: wobbly windows, fading windows, metacity theme transparency, desktop cube ("Classic" Effect instead), zoom, water, annotate, screenshot, clone. What is it spending 30% of CPU time doing?

3. In beryl, I enabled the cube desktop with transparent workspaces and skydome image:
 a. Sometimes the menubar and taskbar on the desktop were not drawn properly - they just appeared as black rectangles. The objects which I knew to be on them were still there - I could still access the beryl manager menu, for example, and hover over the taskbar to get thumbnails of windows.
 b. Similarly to compiz, sometimes titlebars would disappear. However this was not universal - some windows could still have titlebars while others lost theirs.
 c. Similarly to compiz, sometimes windows would display as black rectangles. Again, they could be interacted with tooltips appear when you hover over the appropriate part. Playing around with the advanced options (Binding, Rendering, Rendering Platform etc) in beryl manager seemed to change which windows were affected. Checking "Disable GL Yield Setting" didn't fix this problem.

4. A problem shared by both beryl and compiz was that if I switched away to a text console, then when I returned to the X desktop everything was black except the mouse cursor. At this point I could switch back to the text console and kill the X server; however, if I tried to click on anything nothing would respond and I would no longer be able to switch to a text console. sshing in to kill the X server still worked; however, this was not always an option and I have simply had to poweroff to get out of this state, several times.

Hardware details:
This is an old laptop, a Toshiba Satellite Pro 6100.
Mobile Pentium 4 M, 2GHz (with hardware support for speed step down to 1.2GHz)
256Mb RAM (tiny, yes I know, but it runs XP fine)
1 Gb linux swap partition
Graphics card: nVidia NV17 GeForce4 420 Go

Software details:
Ubuntu: 7.04, Feisty
Kernel: 2.6.13.4-x86_01doc [1]
xorg.conf: [http://www.doc.ic.ac.uk/~pgp/myxorg.conf](http://www.doc.ic.ac.uk/~pgp/myxorg.conf)

Don't know what other details I need to provide, hope this is enough!

Phil

---

### Post by el.motar on 2007-08-22
Hi I have the same laptop with it seems the same NVDIA card, my seems to be,
 grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)

Rev a3, but I am having the same problems with the NVDIA drivers, if I enable NVDIA in xorg.conf instead of the nv driver all I get is a black screen.
Although it seems that the system is running OK.
Because if I type my username and password the systems seems to be logging me in, although it does not show the desktop just a black screen.
I have installed the drivers via the restricted modules applet, which I think installs the lates version.
Which version have you install and could you post a copy of your xorg.conf, it would be very helpful to me.
Sorry that I can not help you solving those issues.
My system runs very estable with the NV driver though.
I am a wally, did not see the link to your xorg.conf.
Will let you know if I have better luck with my 6100.

Thanks
ATB

---

### Post by philandstuff on 2007-08-23
Hi there,

Yes I originally had a similar problem to you - i had not a black screen, but a broken screen showing the ubuntu login screen but with cloudy patches of white which got brighter until the whole screen was white. I fixed this by putting the line

Option "UseDisplayDevice" "DFP"

in the video card section of my xorg.conf; though my current xorg doesn't have this and it still works. Have you tried using nvidia-settings to generate an xorg.conf?

---

