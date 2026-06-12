---
title: "Supporting virtual screen resolutions"
date: 2009-03-24
forum: Desktop Environments
---

### Post by jrosler on 2009-03-24
Hi All,

I've got Ubuntu 8.04 with Gnome on a new Dell Inspiron mini netbook. The only problem I have is that the resolution on this device is only 1024x600 and I'd like to have a larger virtual resolution that would hopefully allow me to have a larger base desktop.

Any thoughts on how I can do this?

Thanks for any and all feedback. I'm new to ubuntu and Linux.

---

### Post by bigbencg on 2009-03-25
The screen in your netbook is a digital display, meaning it will only support certain resolutions.  There is a way to force new resolutions other then the ones detected and listed in the display settings but there is no gaurentee they will work.  I know what you are asking, I have seen some windows computers that have a desktop larger than the screen and moving the mouse on the edges of the screen will move the desktop around.  That is a functon of the graphics adapter and drivers.  

Gnome does offer, if you look in the lower right corner of your screen, multiple desktops.  You will see a little box with a one and two, those are multiple desktops.  You can click on either one to switch a desktop, or if you move your mouse onto a clear section of the desktop scrolling the wheel will also change desktops.  You should also be able to right click the desktop selector and enable more desktops, I am running KDE (kubuntu) and I can set up to 20 desktops.

Using the multiple desktop feature is your best and easiest solution, and will provide you with more desktop real-estate!

---

### Post by zeealpal on 2009-03-25
Yeah, i have a netbook with 1024 x 600, i use gnome and you can set up to 32 x 32 virtual desktops. I have tried to increase the resolution, but i couldn't set it above the native

---

### Post by bigbencg on 2009-03-25
> I have tried to increase the resolution, but i couldn't set it above the native

Correct, since it is a digital display and has a set resolution, you are bound to that resolution.

---

### Post by zhocchao on 2009-03-25
I don't know for sure, but I think that xrandr can do this. 
I DID NOT TEST IT (some day I will (maybe))

---

### Post by jrosler on 2009-03-25
Thanks for the response, bigben. This is exactly what I'd like. The gnome desktop switcher doesn't give me enough screen real estate if I want to do something where there isn't enough space.

I installed eclipse to do some java development and decided I'd like to play around with the Google Web Toolkit (GWT). I downloaded the GWT Designer from instantiations (eclipse plugin for GWT graphical design) and noticed that their dialog in eclipse to request a license was taller then 600 pixels and I couldn't get to the controls on the dialog to request a license :-(. They hadn't used scrollbars in their dialog to handle smaller screen resolutions. This would also be a problem if I try and use visual editors to try and design dialogs or web pages that are larger then my display. I was hoping there was an easy way around all of this.

I tried running xrandr as was suggested by someone else, but it just replied that larger resolutions aren't supported on the display.

If anyone else has any other thoughts I'd love to hear them.

Thanks, again.

---

### Post by zhocchao on 2009-03-25
I read that you have to insert something like this in xorg.conf:

Section "Screen"
        ...
        SubSection "Display"
                Virtual 3200    1200
        EndSubSection
EndSection

if you had this error:

xrandr: screen cannot be larger than 1920x1200 (desired size 3200x1200)

---

### Post by bigbencg on 2009-03-25
If you want to try it, I have been trying to help someone force a resolution on a Television connected to their computer.  I wrote a lengthy post on creating a new mode and setting the mode.  I do not know how well your display would handle a larger resolution, but you can try.  The nice thing about xrandr is it is not permanent, and restarting the computer will undo any changes made.

[http://ubuntuforums.org/showthread.php?t=1101829]("http://ubuntuforums.org/showthread.php?t=1101829")

The last post on the first page is the procedure if you dare to try.

---

### Post by bigbencg on 2009-03-25
I have never tried setting a virtual resolution in xorg.cong before, I will have to play with that.

---

### Post by jrosler on 2009-03-25
I backed up xorg.conf (in /etc/X11) and changed the screen to this

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual 1280 1024
	EndSubSection
EndSection


I then ran "xrandr -s 1280x1024"  and it came back with the following error -

Size 1280x1024 not found in available modes

I thought that perhaps I had to restart the X server or something after changning the xorg.conf file, so I just restarted my machine and tried again and got the same problem.

Any thoughts?

---

### Post by bigbencg on 2009-03-25
xrandr will only allow you to switch to modes that are listed in the output of ```
xrandr -q
```  Plus it does not seem to me that the entry into xorg.conf was correct, all resolutions in xorg.conf have an x in them.  ie: 1280x1024

I will experiment with the virtual resolution when I get a change, which will be tomorrow since I haven't slept in over two days and I have class tonight.  I will share my findings.

---

### Post by zhocchao on 2009-03-25
I think xorg.conf is OK.Screen 0 displays the maximum value, but I had no luck in changing the desktop size. The good news are: panning is implemented in xrandr 1.3  which comes with Jaunty. And it works just fine. It could be you have to change virtual size in xorg.conf. My notebook worked 1280x1280 without changing

xrandr --output LVDS --panning 1280x1280

---

### Post by jrosler on 2009-03-25
jaunty is still in alpha, though, although I guess a stable release is supposed to be out soon (April 23rd is current target). Are you suggesting I use that then, or is there a way to get the X updates sooner? xrandr -v comes back as 1.2 and panning isn't in the list of supported params.

I made the change bigben mentioned since I fat fingered the xorg.conf file and didn't put in the "x" in the resolution (1280x1024), but after doing that and rebooting Gnome (e.g. I guess the X server) came back in low resolution mode and wasn
t happy, so I removed my xorg.conf changes.

---

### Post by zhocchao on 2009-03-25
I thought about replacing xrandr in ibex, but I wont do it. Somehow it could be possible (I really don't know). I have a triple Boot system with Jaunty and by now I use it only for testing (some things don't work, but right now I am using it). It will replace ibex within 2 months. Panning is nice, but I can wait.
If you need a fully reliable system i wouldn't recommend  Jaunty by now. If not, you could give it a try.
If your HD is big enough you can make dual boot, or try a liveCD (liveUSB? Netbook?)

ps the "x" is not needed

---

