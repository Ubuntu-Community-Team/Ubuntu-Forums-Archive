---
title: "Need to make Desktop smaller than screen (monitor)"
date: 2009-02-08
forum: Desktop Environments
---

### Post by crazysubguy on 2009-02-08
My wife surprised me by asking for a kitchen computer for recipes and other kitchen stuff.  I bought an LCD monitor and touch screen kit, but much to my dismay, the touch panel is about 1 cm too narrow.  The problem is the 15" screen I bought is actually 15.6 inches and the touch panel is for a 15" screen.  I can't return either one so I need to make do with what I have.

I need to create a black band on either side of the monitor and make the desktop fit into the touch area of the touchscreen, but when I specify a different resolution in xorg.conf, the monitor resizes and automatically adjusts the desktop to fit. 

The monitor's native resolution is 1366x768 and has only a VGA input.  What I think I need to do, is somehow send the monitor the 1366x768 signal, but have X render a smaller Desktop. In effect a desktop with black vertical bars on each side.

I have no idea how to do this.  Does anyone have any ideas?

---

### Post by warp99 on 2009-02-08
You can do this by settings a virtual desktop size smaller than your resolution settings as a manually add in your xorg.conf file. So you would do the following:

```
sudo gedit /etc/X11/xorg.conf
```

Scroll down to this section:

```
Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

```

and add the following:
```
Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
       [b]SubSection "Display"
		Virtual		1360 708
	EndSubSection[/b]
EndSection
```

That will decrease the size of the desktop by 60 points on the height and width. If you don't have a xorg.conf you can boot to recovery mode and use xfix to generate one to edit.

---

### Post by crazysubguy on 2009-02-08
Thanks for the quick response. I modified my xorg.conf file and it seems X automatically picks a  smaller mode than the virtual screen leaving me to scroll my way around the desktop.  For example, I first specified a virtual desktop of 1300 768, but instead of the native resolution - 1366x768, I logged into a desktop set at 1280x720.  I then set the virtual desktop to be 1120x720 and then X gave me  a 800x600 desktop. I've attachmed my xorg.conf

---

### Post by warp99 on 2009-02-09
Well i just learned that the virtual parameter is no longer honored starting with 8.04. Now you would use RandR to handle the desktop parameters. Here's a guide for beginners on using RandR that may be helpful:

[http://www.phoronix.com/scan.php?page=article&item=927&num=1](http://www.phoronix.com/scan.php?page=article&item=927&num=1)

I have little experience with RandR, but I looked at the man pages for xrandr and it looks like you can set the parameters to what you need. Just type "man xrandr" for more information. I would also search the forums for RandR and check out the help guides listed in my signature.

---

### Post by crazysubguy on 2009-02-11
It seems the virtual screen is for specifying the largest total area of the entire desktop. If I were to connect more than one display, all displays would need to fit within the virtual screen.  What that means for me is that the signal sent to the monitor will be less than the virtual screen which is the opposite of what I need to do.

xrandr either adjusts the mode sent to the monitor and the monitor then compensates by auto-adjusting, or it rescales the screen so that fewer pixels are scaled up to the monitor resolution.  At least that is what it seems to do for me.  Neither one accomplishes what I am trying to do. If I am missing something about xrandr please let me know.

I'm not giving up though, maybe there is a way to tell gnome-desktop that the desktop is limited to a smaller area than the total resolution available.

Thanks warp99 for the ideas so far.

---

### Post by psynautic on 2010-02-21
I'm searching for the same functionality. I have a Panasonic TC-L32X1 hooked up via hdmi with radeonhd drivers.  

Connecting with vga, I can manage to get the tv to display 1360x768 which is 6pixels from it's native resolution. But because of how I'd like my setup to work, and lack of a 15' vga cable I want to stick with HDMI. 

What happens with this particular tv, is that through hdmi it only allows for 480i, 480p, 720p, 1080i signals to display (for whatever reason that I'm not too worried about it only finds my preferred mode 1280x720). It then proceeds to overscan this resolution by about 3cm to the left and right and about 1cm to the top and bottom. The tv insists on processing and scaling the input, and in the manual it tells you that it assumes that hdmi is not a pc (short sighted indeed) so you don't have the options in the tv to force 1:1. 

Now I'm not totally clear as to why this happens from the 1280x720 being sent from a computer and not the 480p from my wii, or the hd content from my cable box.

I've heard that fglrx gives you access to some overscan/underscan tweaking if you use tv-out, but I've found that the 2d accelleration in fglrx is subpar, and would prefer if there was some way to tell the hdmi cable to output a 1280x720 signal to the tv, and tell X (specifically kde4) to only use something like 1240x654. After spending a ton of time searching I'm not sure there is anything out there to accomplish this.  At this point I would settle for a direction towards software that could be modified to do this. I'd be more than willing to lend a coding hand to adding something like this xrandr. It looks like there is a lot of frustration about this in the community.

psy.

---

