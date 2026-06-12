---
title: "Fixing overscan when TV cannot be adjusted (Ubuntu 16.04.3-desktop-amd)"
date: 2017-12-24
forum: Desktop Environments
---

### Post by kenok2 on 2017-12-24
Hi there better angels of the ubuntu community,

Complete newb here, got an intel computestick that came with no OS and decided to give ubuntu a go on it. 

It's connected to the living room TV via HDMI. The TV is pretty old and the aspect ratio cannot be changed to "Just scan". There are only two ratios possible, none of which help. The rest are grayed out ](*,), regardless of which HDMI port is used. The overscan must be fixed on the software side. 

On the previous win32 living room PC I just used the nvidia desktop resize setting to shrink the desktop down, but I haven't the slightest clue how to do that on kde or gnome or whatever graphical shell Ubuntu 16.04.3 comes with by default.

Googled around a bit and tried sudo xrandr with a plethora of switches and parameters. None of which managed to shrink the display at all. All I could do is move the desktop's position around instead of actually resizing it.

There's gotta be a way to just "shrink" the GUI without affecting resolution. The resolution is 1920x1080, of which only 1852x960 pixels are actually visible on the poor-excuse-for-a-tv 

Can anyone point me in the right direction? a hint towards a way around this?

Thanks!

---

### Post by Autodave on 2017-12-25
This has an Nvidia card in it? Have you installed a driver for that card yet?  If not, go to ADDITIONAL DRIVERS and let it search. For now, chose the recommended one.  After it installs, reboot to be on the safe side.

After reboot, go to SETTINGS and scroll through: you will find an Nvidia icon there. Open that and then you can chose the resolution you want/need.

---

### Post by kenok2 on 2017-12-25
Thanks Autodave!

The intel compute stick has some basic integrated intel graphics chip, no nvidia. Sorry I wasn't clear, the nvidia card was on the older living room PC, which I'm trying to replace with the compute stick.
It's not the resolution that I need to change, I need to keep the resolution as is but shrink down the desktop to less pixels than the actual resolution.

---

### Post by Autodave on 2017-12-25
Can you go into Settings -> Display and change it there?

---

### Post by kenok2 on 2017-12-25
There's no such setting there. Tried them all. The only settings there allow me to change the resolution or the DPI (make the interface elements larger or smaller). None of which fixes the overscan.
I need it to keep the resolution at 1920x1080 but shrink the visible output to less than that, about 1852x960.

This is kinda like how it looks like on the TV (an example I found on the web, not my actual TV), notice that about 5-10% of the image is missing off the sides:

[IMG]https://d1rktuf34l9h2g.cloudfront.net/7/72/7289e9c0_IMG_2891.jpeg[/IMG]

---

### Post by dga2 on 2018-01-01
The following worked for me using Kubuntu 16.04, KDE Plasma 5.5.5, an NVidia GK104 graphics card outputting to a fairly old Sony Bravia TV.

1. I didn't use the NVidia driver but instead used the X.Org Nouveau display driver (which is the default). I couldn't get it to work using the NVidia driver. I set this under the Software & Updates program, Additional Drivers tab.

2. I created a file called .xprofile in my home directory and put the following in it:
```

#!/bin/bash
xrandr --output HDMI-1 --set underscan on --set "underscan vborder" 30 --set "underscan hborder" 30 
 
``` 

The 'HDMI-1' in the command above may vary for you (it's more likely to be HDMI-0) but you can find out which by typing xrandr in a terminal and it will list your displays.

The 30s in the command above are the number of pixels it will underscan by and you can try different numbers to fit to your screen.

Best wishes.

---

### Post by kenok2 on 2018-05-09
Thank you so much for your advice, dga2.
Sorry for the incredibly late response, the compute stick in question was not in my possession for a few months but I got it back now.
Tried your solution, with the correct HDMI-(0/1..) parameter, but I keep get the error below, no matter if I run the command you suggested or save it in .xprofile in my home dir.

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  28
  Current serial number in output stream:  28

Any thoughts or tips would be much appreciated.
Thanks!

---

### Post by dga2 on 2018-05-09
What is the output from xrandr and what was the command you tried?

---

### Post by kenok2 on 2018-05-09
Wow, that was fast :)
The output was exactly as I quoted above:
[COLOR=#000000]
X Error of failed request: BadName (named color or font does not exist)[/COLOR]
[COLOR=#000000]Major opcode of failed request: 140 (RANDR)[/COLOR]
[COLOR=#000000]Minor opcode of failed request: 11 (RRQueryOutputProperty)[/COLOR]
[COLOR=#000000]Serial number of failed request: 28
[/COLOR]
Same output for when I run the command in a terminal or when it's in .xprofile on my home dir.

The command was:
xrandr --output HDMI-1 --set underscan on --set "underscan vborder" 30 --set "underscan hborder" 30
HDMI-1 is the correct one according to xrandr's output when I run it w/o any parameters.

---

### Post by dga2 on 2018-05-09
Hmm, in that case I don't know, sorry. I've got that error message before ([COLOR=#000000]BadName (named color or font does not exist)) but only where I've got the name of the output wrong. But if you say it is definitely using HDMI-1 then I don't know what else to suggest. Sorry not to be more help :-(.

You could try changing the driver under the 'Additional Drivers' section of 'Software and Updates' or changing the Compositor, Rendering backend from OpenGL to XRender or vice versa (this is under Display and Monitor settings in KDE, not sure about others). But I'm not very optimistic.[/COLOR]

---

### Post by jacksaw on 2018-05-26
I just found this thread and followed the xrandr instructions. I had to change to HDMI-0 and fiddle with the hborder and vborder values but other than that it worked perfectly!

Great advice dga2 thanks!

Also I am running Xubuntu 18.04 with a Radeon HD6850

---

