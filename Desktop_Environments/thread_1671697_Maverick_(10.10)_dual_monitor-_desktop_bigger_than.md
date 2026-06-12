---
title: "Maverick (10.10) dual monitor- desktop bigger than screen..."
date: 2011-01-20
forum: Desktop Environments
---

### Post by verdomde on 2011-01-20
Hi, I have had a look around, there are plenty of dual monitor threads- most of them are old), but none of them seem to have my particular question.

Im running a wee Aspire One, 1024*600 with an external monitor 1024*768 (maverick desktop edition- 10.10)

I have them set up independently, the external is to the right, and above my aspire. I have set this up in the monitors options. But it seems the desktop environment (although not the backgrounds) extend off to the right of my aspire (under the external) and to the left of my external- (above my aspire).

I know that it may be nit-picking, but it is a right pain when I 'loose' stuff on this phantom desktop space.

For example- when i move my cursor into one of these spaces- and have to wiggle it about till it pops onto one of the screens.

Any help?

Also- i'd like my screensaver to pop up on both screens, and span them both- not just be repeated on both...
Thanks.
Paul

---

### Post by Krytarik on 2011-01-21
Check "System -> Preferences -> CompizConfig Settings Manger -> General Options -> Display Settings -> Outputs".

There seems to be no real solution for the duplicate screensaver thing, only did a short web search.

---

### Post by verdomde on 2011-01-21
> **Krytarik said:**
> Check "System -> Preferences -> CompizConfig Settings Manger -> General Options -> Display Settings -> Outputs".

There seems to be no real solution for the duplicate screensaver thing, only did a short web search.

Hey, cheers for the speedy reply- i had a look, certainly interesting to play around with. Doesn't stop my cursor going off screen though (that i can understand. Aint a big problem anyway.) Bt, since trying that, my screensaver is on both monitors. Thats a step up. Although spanning them would be cooler.
Thanks again.
While i'm here- would there be a benefit to enabling compiz to draw the wallpaper? I don't get it..

:)

---

### Post by Krytarik on 2011-01-21
Try setting up the config via xorg.conf:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
> **verdomde said:**
> 
Bt, since trying that, my screensaver is on both monitors. Thats a step up. Although spanning them would be cooler.
Isn't that exact the same behaviour as described in your initial post?
> **verdomde said:**
> 
While i'm here- would there be a benefit to enabling compiz to draw the wallpaper? I don't get it..

Do you mean the "Wallpaper" plugin of Compiz?:
[http://wiki.compiz.org/Plugins/Wallpaper](http://wiki.compiz.org/Plugins/Wallpaper)

With it you could possibly have different wallpapers at your workspaces, but it apparently requires a patch of Nautilus (which handles the desktop) to work.

---

### Post by verdomde on 2011-01-22
> **Krytarik said:**
> Try setting up the config via xorg.conf:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Isn't that exact the same behaviour as described in your initial post?

The screensaver was only displaying on one monitor- not both. I guess i neglected to mention that properly. It's on both now, but as 2 independent screensavers. I can live with that. Spanning is probably impossible given the different dimensions of the monitors.

Regarding the wallpaper thing- thanks again also. I guess I could have googled that myself eh- but I'm not really just lazy. I didn't think i'd find out if there were benefits to using it. Although there seems like there isn't any at present, as the nautilus patch doesn't currently work for different wallpapers on each desktop.
On top of that, I kinda like my wallpaper enough at the moment, that seeing it twice is a pleasure :). Using xplanetfx for a couple weeks now, and still in love with it.
Thank you again for your speedy reply.
Paul
(would mark as solved, but it isn't really, just too petty a problem to worry about for too long - someone else may care)  :)

---

### Post by verdomde on 2011-01-22
> **Krytarik said:**
> Try setting up the config via xorg.conf:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)



sorry, just spotted this bit, am still half asleep, trying it now.

---

### Post by verdomde on 2011-01-22
Ok, I had a look at these posts. Both are excellent, and I think I'll be able to do as I please :) I will post the result when I figure things out (am going to take my time-I don't want to start changing things on this level without a little background study). The main reason I didn't find this stuff is that I thought 10.10 didn't use xorg configuration- because I couldn't find xorg.conf. It seems though, that the configuration files are now in /usr/share/X11/xorg.conf.d, and you make a new one for the displays- am reading up on that now.
Thanks mightily for your time. Will follow up when apropriate.

---

### Post by verdomde on 2011-01-22
OK,
Having read up a bit, on the links you provided- thanks-, I think i can explain the position better. I used randr to add a mode to my external monitor, making it the same dimensions as my laptop(1024x600). This means I no longer lose things off-screen. The problem is, my external (vga1) is _above_ and to the right of my laptop. BUt not all the way above. If I alter the position in the monitors settings in ubuntu then it leaves space above the laptop display, and below the vga1 display. This, I have come to understand, is the framebuffer?... This is the space where i lose my mouse (very annoying when trying to activate cairo dock, which sits at the top of my laptop screen.).

So I guess what I'm trying to say, is that I either need to change the shape of the framebuffer, so it wraps around the screens, or use two framebuffers that the mouse can move across, and drag windows across. This second is probably impossible. The first, probably very very complicated.
Thats my guess anyway.

For the moment I am sticking to having them both set to 1024x600 and pretending they are just sitting next to each other.

It's not the end of the world- eh
:)
Thanks again
Paul

---

### Post by Krytarik on 2011-01-22
The "framebuffer" has nothing to do with the positioning of the desktop areas, although one could draw it from the word:
[https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer)

If I got it right, the bottom edge of your external screen is a bit higher than the top edge of your laptop screen. Thus it's imo impossible to adapt the desktop positions exactly to their real positions, you could just pretend they are sitting corner on corner.

As of the "xorg.conf.d" directory, it has a slightly different path, but thanks for the hint, I didn't know that location before:
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

### Post by verdomde on 2011-01-22
Yeah, I checked out the framebuffer thing after posting, the term i was looking for is virtual desktop (I think.)
It's the dead-space in the virtual desktop that is the problem. But living with the monitors side-by-side (virtualy), even though one is higher, isn't the worst thing in the world.
Thanks again.

Paul

---

### Post by Krytarik on 2011-01-22
How about setting up the diagonal positions, as I described, in xorg.conf like this:
```
Section "ServerLayout"
    Identifier     "DualSreen"
    Screen       0 "Screen0"
    Screen       1 "Screen1" Relative "Screen0" 1024 -600
    Option         "Xinerama" "1"
EndSection

```
Excerpt of the xorg.conf man page:
[http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html)> 
**Screen  ***screen-num*** "screen-id" ***position-information* One of these entries must be given for each screen being used in a session.  The *screen-id* field is mandatory, and specifies the **Screen** section being referenced.  The *screen-num* field is optional, and may be used to specify the screen number in multi-head configurations.  When this field is omitted, the screens will be numbered in the order that they are listed in. The numbering starts from 0, and must be consecutive.  The *position-information* field describes the way multiple screens are positioned.  There are a number of different ways that this information can be provided: [INDENT]  *x y*  
 **Absolute  ***x y*  These both specify that the upper left corner's coordinates are (*x*,*y*). The **Absolute** keyword is optional.  Some older versions of Xorg (4.2 and earlier) don't recognise the **Absolute** keyword, so it's safest to just specify the coordinates without it.   **RightOf   "***screen-id***"**  
 **LeftOf    "***screen-id***"**  
 **Above     "***screen-id***"**  
 **Below     "***screen-id***"**  
 **Relative  "***screen-id***"*** x y*  These give the screen's location relative to another screen.  The first four position the screen immediately to the right, left, above or below the other screen.  When positioning to the right or left, the top edges are aligned.  When positioning above or below, the left edges are aligned. The **Relative** form specifies the offset of the screen's origin (upper left corner) relative to the origin of another screen. [/INDENT]

---

### Post by verdomde on 2011-01-22
> **Krytarik said:**
> How about setting up the diagonal positions, as I described, in xorg.conf

Hmm,it may well work. But it wouldn't be in xorg.conf, but in 10-monitors.conf, and the problem (for me)is that If i create that conf file, I have to include the config of the two screens, the device for both screens, the server layout (as you have written) and for both monitors.
It probably isn't that hard, but it does seem to be beyond me- for most of today I have been trying to get a working config, but it always stops loading before x starts. I think I aint good enough, or rather, I need to study it more. I even copied and pasted from another aspire one owner online, and added the dual monitor stuff from the other post. No luck. That's why I gave up on the xorg method and tried xrandr.
In truth my aspire is running really well as is, and I'm worried that running from an x config might nullify some of the features that are keeping it sweet. 10.10 Is 'so-far' the best distro i've installed, I don't want to end up taking a step back by accidentally disabling something... This glitch ain't really worth it.
In saying that, I will probably give it a go tomorrow. I know I can at least undo whatever I implement by deleting the 10-monitor.conf file. I wouldn't want your administrations to go to waste :)
I appreciate the help
Paul

---

### Post by Krytarik on 2011-01-22
Don't change the mentioned 10-monitors.conf, all you have to care about is xorg.conf.
Back it up before, and it's not risky at all. The worst what could happen is that end up at the console login and have to restore the backup by a simple copy command.

Offers Randr such an option, to position the screens diagonally? Then you can just do it that way, to achieve at least a near-perfect positioning.

---

### Post by verdomde on 2011-01-23
> **Krytarik said:**
> Don't change the mentioned 10-monitors.conf, all you have to care about is xorg.conf.
Back it up before, and it's not risky at all. The worst what could happen is that end up at the console login and have to restore the backup by a simple copy command.


I believe this is where there may be some confusion. As I understand it maverick10.10
doesn't have a xorg.conf. sudo Xorg -configure. It uses the latest version of xorg, which creates the .conf files in usr/share/X11/xorg.conf.d. These files are "snippets" of the old xorg.conf... i think. I did a search for xorg.conf and didn't find one.

I tried creating one with sudo Xorg -configure last night, this was created in my home folder- I wouldn't know where to copy it to to make it work- as there is now no etc/X11 folder.

But i should be able to copy the relevant monitor/device/screen section from it, and use it to create a 10-monitor.conf, along with your suggested server layout- will try now...
Just found this- which explains;
[http://askubuntu.com/questions/5314/where-is-etc-x11-xorg-conf](http://askubuntu.com/questions/5314/where-is-etc-x11-xorg-conf)
It also explains I can put that new xorg.conf i created into usr/share/xorg.conf.d and it'll work as normal...

> **Krytarik said:**
> 
Offers Randr such an option, to position the screens diagonally? Then you can just do it that way, to achieve at least a near-perfect positioning.

RandR does this, as does the monitors settings panel, but the cursor still leaves the screen
thanks again, trying new xorg.conf now

---

### Post by verdomde on 2011-01-23
I tried combining configs, as above. This config doesn't break anything, it all boots up. But i've no idea if it does anything at all.

Section "ServerLayout"
    Identifier     "DualSreen"
	Screen	0 "Screen0" Absolute 0 0
	Screen   1 "Screen1" Relative "screen0" 1024 768
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option "Xinerama" "1"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "dri"
	Load  "dbe"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Option		"Enable" "true"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	Screen		0
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
       Identifier  "Card1"
        Driver      "intel"
        Screen          1
        BusID       "PCI:0:2:0"
EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
		Modes	"1024x600" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
		Modes     "1024x600" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"  
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
		Modes     "1024x600" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"  
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
		Modes     "1024x600" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"  
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes     "1024x600" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"  
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes     "1024x600" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"  
	EndSubSection
EndSection

Section "Screen"
	Identifier  "Screen1"
	Monitor		"Monitor1"
 DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes      "1024x600_75.00"
    EndSubSection
	Device		"Card1"	
EndSection

Section "Monitor"
	Identifier "Monitor1"
	Modeline "1024x600@75" 85.52 1024 1056 1376 1408 768 782 792 807
	Option "Enable" "true"

EndSection

It has no effect on the cursor leaving the desktop areas, and I can't get the vga (monitor 1) to display 1024x600 this way. Xrandr works for that though.

---

### Post by Krytarik on 2011-01-23
I naturally can't check the file structure of 10.10, as I have only 10.04. Did you also read the wiki [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config) , which has been linked in the article, and which I also posted earlier. I know that the xorg.conf is outphased, it is mandatory anymore, you may not have one at all and it is not created by default. In 10.04 there is still the directory /etc/X11 where you can place a xorg.conf with custom options, the wiki mentions /etc , I don't know if that is true for 10.10. I personally wouldn't put my custom config in those files in xorg.conf.d, as it isn't mentioned or recommended anywhere.

As for your "config":
```
Section "ServerLayout"
    Identifier     "DualSreen"
    Screen    0 "Screen0" Absolute 0 0
    [COLOR=Red]Screen   1 "Screen1" Relative "screen0" 1024 768
# should be: [/COLOR][COLOR=Red]Screen   1 "Screen1" Relative "Screen0" 1024 -600[/COLOR]
InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option "Xinerama" "1"
EndSection
```Besides this, the config seems to be ok.

---

### Post by verdomde on 2011-01-23
> **Krytarik said:**
>  In 10.04 there is still the directory /etc/X11 where you can place a xorg.conf with custom options, the wiki mentions /etc , I don't know if that is true for 10.10. I personally wouldn't put my custom config in those files in xorg.conf.d, as it isn't mentioned or recommended anywhere

Hey, i did see somewhere, in one of the links you supplied (i think) that in the xorg.conf.d was the place to put it with 10.10. there is an etc/X11 though, ill shift it there, see if it still works.

In the server layout section- when I keep the '-' in the position cordinates (1024 -600) I get an error on that line, invalid screen or something, and x doesn't start.

I still believe that this won't solve the problem, I found this bug though [https://bugs.launchpad.net/ubuntu/+source/libxrandr/+bug/373367](https://bugs.launchpad.net/ubuntu/+source/libxrandr/+bug/373367)
about the cursor being lost off-screen.
Halfway down there is a programme someone has written to draw 'windows' into the void areas I mentioned, when the cursor tries to go into these windows it is bounced back onto the visible screen, sounds like that-d work well- but I can't get it to work yet. 
It's called XCreateMouseVoid. the file ends in cc, the instructions are to use "g++ XCreateMouseVoid.cc -lX11 -o XCreateMouseVoid" to install it, but when I try to run it it says xcreatemousevoid is an unknown command.
Nothing is ever easy eh-
I'll figure it out

---

### Post by verdomde on 2011-01-23
Got that wee programme running, just had to ./ xcreatemousevoid, it is perfectly effective. I have two windows where the mouse will not go, and I've positioned them in the 'phantom' screen areas. So now the cursor just jumps back onto the screen. Still trying to work out how to get my dock to work, but that should'nt  take long. So, I think that's enough for me to mark this solved. It doesn't look like anyone from the bugs is interested in providing an actual fix, so the xcreatemousvoid workaround will have to do.
Thank you again for all your help
Paul

---

### Post by Krytarik on 2011-01-23
I was afraid that the "-" thing doesn't work, but if you put it the other way around, you also just make a "-". You can specify "absolute" positions for both, like that:
```
Section "ServerLayout"
    Identifier     "DualSreen"
    Screen         0 "Screen0" Absolute 0 600
    Screen         1 "Screen1" Absolute 1024 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option "Xinerama" "1"
EndSection
```
Doesn't make the mentioned workaround the things even worse?
Now you not only have a area which you can't see, but you also can't reach it with the mouse?

---

### Post by verdomde on 2011-01-23
> **Krytarik said:**
> 
Doesn't make the mentioned workaround the things even worse?
Now you not only have a area which you can't see, but you also can't reach it with the mouse?

Haha, that is a unique way of thinking about it, yes. But- as I can't see the area- the mouse is useless there anyway, and if anything gets lost in that area I usually maximise it by the taskbar or use keyboard shortcuts to bring it back. (occasionaly I do go 'fishing' with the mouse and the 'alt' button though)

If I lose anything (which mainly happens when I am switching from one monitor to multi-monitor) i can just killall xcreatemousevoid and go fishing as usual.

I will try xconf again though, with the serverlayout you've just posted, see if it changes everyting, but im sure those desktop voids would still be there...

---

### Post by Krytarik on 2011-01-23
Fishing time, LOL!!:p
> **verdomde said:**
> 
I will try xconf again though, with the serverlayout you've just posted, see if it changes everyting, but im sure those desktop voids would still be there...
Shouldn't be, but the screen positions wouldn't represent their real positions, as mentioned earlier. But that would be better than fishing, unless you like it of course. LOL;)

---

