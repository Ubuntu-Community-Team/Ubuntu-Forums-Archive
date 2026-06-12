---
title: "Tips for Gutsy Xrandr compiz radeon driver dual screen"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by BungaMan on 2007-10-19
This stuff is not for beginners.  If you don't know much about this then don't try it.  If you do then it's up to your own responsibility if your system gets broken so you are warned in advance !

This is entirely written for my situation which is:  Try to use dual screen with AIGLX, open source radeon driver and compiz.  My setup is a laptop with radeon mobility 9600 and an external connected CRT screen.

1. If you upgraded from Feisty to Gutsy, chances are you also have the Xgl package (xserver-xgl) installed.  You better remove this for better performance.  It degraded the graphical UI and you don't need it anyway because we will use aixgl.

2. Auto setup of dual screen doesn't work to good for me and the "Screens and graphics" ain't much worth for me either so diving back into xorg.conf.  The updated radeon driver doesn't support mergedfb or xinerama anymore so we'll prep xorg.conf for xrandr.

Start with a simple Device section, leave  the tweaking for later on
```
Section "Device"
	Identifier	"MobRad9600"
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Vendorname	"ATI"
EndSection
```

Now add a Monitor section for each monitor you have attached
```
Section "Monitor" 
	Identifier	"Laptop"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"CRTThuis"
	Vendorname	"LG"
	Modelname	"CRT 1280x1024"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
	Modeline  "1280x1024" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
EndSection
```

If you don't know the horizonsync and vertrefresh then you can start without them and hope for decent detection.  The modeline in the second monitor isn't necessary either but I'll explain that later.  If you absolutely want to add the modeline then run the following command in a terminal.
```
more /var/log/Xorg.0.log | grep "Modeline \"1280x1024\" "
```
Replace the resolution with the one you are looking for.  Note that a monitor can have multiple modelines, each will give you a different refresh rate.  More so, with 2 monitors supporting the same resolution you will have the modelines of each so be careful here.  To be sure, open up Xorg.0.log in gedit and look for the lines.  See for which monitor they are generated.  You will need the right modeline afterwards for xrandr.

Now setup the Screen section
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"MobRad9600"
	Defaultdepth	24
	Monitor		"Laptop"
	SubSection "Display"
		Depth	24
		Viewport	1280 0
		Virtual		2560 1024
		Modes		"1280x1024" "1280x800"
	EndSubSection
EndSection
```
Only one screen section and we set it up with the default monitor.  In my case thats the LVDS of my laptop.  Virtual is important, it defines the total horizontal and vertical size of what you are going to look at.  I have a CRT at 1280x1024 and a laptop lcd at 1280x800.  The crt left of the laptop so that makes 1280+1280=2560 for the horizontal size and 1024 vertically.  Not 1824 vertically because the screens are next to each other, not below each other.  Viewport will define the position of my default screen in this virtual size.  My crt will take up the first 1280 horizontally so the horizontal starting point of my lcd is 1280.  0 for the vertical position because I let both screens align at the top.  Modes contains all the resolutions that I will use.  Probably isn't needed with xrandr, but this is untested.

Now we still need a serverlayout
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"AIGLX"		"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"		"Enable"
EndSection
```

Make sure that the AIGLX is there and set to true.  I don't kow if the DRI section is necessary but it works when it is there, same for Composite :)

My xorg.conf is attached for reference.

3. That should do it for xorg.conf but it doesn't make dual screen work yet.  So let's see how we can get xrandr to do its job properly.

Let's query for some info in a console
```
xrandr -q
```

It will show you the detected resolutions for each connector (VGA-0 and LVDS in my case).  For my CRT, the 1280x1024 resolution was not detected but my monitor sure can handle it so I instruct xrandr to add this "mode".  This is where the detected Modelines are needed from Xorg.0.log.  The example will make it clear.
```
 xrandr --output VGA-0 --newmode "1280x1024" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
```
As you can see, I'm telling xrandr to add a new mode to connector VGA-0.  I'm giving the mode the name "1280x1024" but you can call it "monkeyres" for example :)  The rest of the parameters are taken from the Modeline as you know by now.

This is not enough, newmode is for adding a supported resolution.  Now we have to tell to actually use that resolution.
```
xrandr --addmode VGA-0 "1280x1024"
```
The example is pretty much self explainatory now.

Now we are ready to activate dual screen properly compared to the clone mode you may have right now.
```
xrandr --output VGA-0 --left-of LVDS --mode 1280x1024
```
This is also easy to understand.  Tell xrandr that I want to have VGA-0 positioned left of LVDS (my laptop lcd) and use mode name 1280x1024 for VGA-0.

Because xrandr is all about dynamic setup, your setup ain't going to last after a reboot so I made a little script that detects if my desired mode is added and executes the above commands if necessary.  Then added the script to my session and each time I log on I have a dual screen started.

This is the content of the script
```
#!/bin/sh

if ! xrandr -q | grep -q "VGA-0 connected 1280x1024" ; then
        xrandr --output VGA-0 --newmode "1280x1024" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
fi

xrandr --addmode VGA-0 "1280x1024"
xrandr --output VGA-0 --left-of LVDS --mode 1280x1024

```

Now lets get compiz started.  Try running the following command in a terminal.
```
compiz --replace &
```
It is possible that due to the dual screen setup, you now have a screen that is too large for the maximum texture size.

4. To solve the maximum texture size problem, first of all add support for large textures in DRI.  Install driconf and then check in your home dir for the file ".drirc".  If it doesn't exist then you may need to run driconf once.  In the file add a node for allow_large_textures.
```
<driconf>
    <device screen="0" driver="r300">
        <application name="Default">
            ...other options...
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>
```

Good, now this won't run compiz.  Compiz checks for the opengl parameters.  In my case the maximum supported texture size is 2048x2048.  As you know my virtual area is 2560x1024 so that's a bit out of range.  For some background info... compiz makes textures of everything, programs, task bars at the top, your wallpaper, etc.

5. Let's make compiz not check for the texture size.  DO THIS ON YOUR OWN RISK.  The effect for me is that texturizing my background fails so I have a white are for the supported texture size and for the desktop area that is out of range, I get a funky disfunctional area that I can live with :)  If you stretch a program across your dual screen, you'll notice that at one point it will be blank until you resize it back within your maximum texture size.

So... edit /usr/bin/compiz and comment out "return 1;" in the following function.  Should be at line 231.
```
# Check if the max texture size is large enough compared to the resolution
check_texture_size()
{
	TEXTURE_LIMIT=$(glxinfo -l | grep GL_MAX_TEXTURE_SIZE | sed 's/.*=[^0-9]//g')
	RESOLUTION=$(xdpyinfo  | grep -i dimensions: | sed 's/[^0-9]*pixels.*(.*).*//' | sed 's/[^0-9x]*//')
	VRES=$(echo $RESOLUTION | sed 's/.*x//')
	HRES=$(echo $RESOLUTION | sed 's/x.*//')
	verbose "Comparing resolution ($RESOLUTION) to maximum 3D texture size ($TEXTURE_LIMIT): ";
	if [ $VRES -gt $TEXTURE_LIMIT ] || [ $HRES -gt $TEXTURE_LIMIT ]; then
		verbose "Failed.\n"
#		return 1;
	fi
	verbose "Passed.\n"
	return 0
}
```
Commenting it out will keep everything OK except that it will not return a failure but just continue.  This is a bit dirty but for now the easiest.

Save the file and try again to run "compiz --replace &" in a terminal.

I hope that works for you or at least give you a clue on where to look.

[edit]updated some info

---

### Post by justmehere on 2007-10-20
Thank you. After several days of trauma these tips helped me get my screens working properly again. I've got a radeon X700 and 2 Samsung SyncMaster 225bws (DVI-0 and VGA-0). Following these tips and setting the virtual size to 3360x1050 I've now got them working in a similar way  to Xinerama. Having followed the tips I did

xrandr --q
xrandr --auto
xrandr --output VGA-0 --pos 1680x0
xrandr --output VGA-0 --mode 1680x1050

and it all works.

:¬}

---

### Post by cygnis1 on 2007-10-20
How do I  remove xserver-xgl ?
Cygnis1

---

### Post by BungaMan on 2007-10-21
I'm using a dutch version so this is translated out of my head.  It could be a bit different.

system -> Management -> **Synaptic** package management

Search for xserver-xgl and remove it.

---

### Post by BungaMan on 2007-10-23
In the attachment you have my updated xorg.conf

It contains modification so that X starts up with dual head from the start.  The trick is to define the monitors for the connectors in the driver section.

---

### Post by pdelgado on 2007-10-24
Thank you so much for your tips.. I finally got both monitors working... 

the only problem I've got now is that the wallpaper isn't displayed and my right monitor shows a black block (rectangle) yet I CAN place windows in that area.

I'm assuming the problem is with the texture size... any ideas how to fix that?

---

### Post by BungaMan on 2007-10-24
yes that is because it fails to generate a texture for your desktop area.  For the maximum size you'll get the white area and the right most becomes an area that is never cleared in memory.  Hence the effect you notice when moving stuff around in that area.

---

### Post by gtducati on 2007-10-25
For anyone interested, this is the cleanest working xorg.conf file I have finally assembled to handle the dual monitor issue with Gutsy using the ATI driver. The order of the device, monitor and screen sections apparently is important (after much wasted time struggling to figure it all out). I'm posting links below as they helped me arrive at a solution.  

[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)

My configuration is as follows:
Dell Precision Workstation 320 w/
Two Dell 20" Flat Panels (max. combined res: 3200x1200)

Details can be seen in the attached file.

---

### Post by BungaMan on 2007-10-25
The order of the sections is not important.  What would have been the issue if the order was not correct?

---

### Post by userid on 2007-10-25
Radeon 9700

Thanks for your clean xorg.conf.. have had a nightmare so far, only occurred to me v late that mergedfb is deprecated. No luck with proprietary AMD drivers either.

Now I got it working on randr, dual head WITH direct rendering; only problem are full-screen applications that "crash" randr and re-set it to clone mode.

As randr appears to be rather new, I havent found any appropriate guides on this subject..

---

### Post by gtducati on 2007-10-25
Remember that there are limitations on the max virtual resolution.  For my particular configuration, I am only able to get the dual monitor feature to work at 3200x1200. In other words, I don't have direct rendering.

---

### Post by BungaMan on 2007-10-26
It differs depending on your card.  For reference.. mine is a ATI mobility 9600 with a virtual that can support 3 monitors.  I have the virtual size set at 3360 1024 (1280x1024 - 1280x800 - 800x600).  Haven't tried anything bigger.

---

### Post by c0mp13371331337 on 2007-10-26
I've been an Ubuntu user for a wee-bit over a year now, and I thought this issue to be worthy enough of my first post on the forums.

First off, I want to thank BungaMan for the intel on getting dual monitors working on Gutsy.  I probably never would have figured out that the new radeon driver doesn't support MergedFB anymore, and since I copied my xorg file from the previous Fiesty install which worked fine, I would have been sitting there in front of two cloned screens, looking at xorg.conf opened in Nano at the terminal, wondering what changed.

That having been said, I'm left wondering why MergedFB support was dropped in the first place.  Once I found out about it, it was easy to get up and running, didn't have any weird glitchiness watching full-screen movies or full-screen games, started dual-screens at gdm startup, rather than waiting til you're logged in and having to run a script to start dual, etc.

Xrandr is okay, I suppose it does get the job done, but just barely and with many downfalls.  On top of all the issues mentioned above, my primary monitor (DVI-0) has some strange 'pink-ish orange-ish' hues to the right of anything white, almost like a shadow.  Plus text doesn't look all that great on that monitor.  I'm not sure if this is a setting that I need to adjust or what.  I've already disabled all of Compiz from running.  Love the eye-candy, but until the open-source DRI implementation is a bit more sophisticated than the current 2048x2048 limitation, I'd rather have 3200x1200 running.  Haven't really played around with it too much, as I'd like to roll back my radeon driver, if possible.  

Does anyone know how to do this?  I wouldn't really even know where to begin.  Any assistance or nudges in the right direction that may assist me in downgrading my radeon driver would be greatly appreciated.  The radeon driver that came with Fiesty worked wonderfully.  This new version (mostly because MergedFB support has been dropped) doesn't seem as solid.  BTW, for anyone interested, here's my setup:

Dell Dimension 4500 (Frankensteined with better mobo & GPU)
Pentium Celeron 2.0 ghz processor
768MB RAM
256MB ATI Radeon 9200SE (RV280) GPU
Dual Dell M781p CRT Monitors (Combined resolution 3200x1200)

---

### Post by BungaMan on 2007-10-26
I'm not that familiar with it but afaik the radeon driver wasn't changed much except for supporting xrandr. That 2048 limitation has always been there because it is the maximum texture size your card can handle.  Different video card -> different limitation.  As far as your DVI problems I can't help.

If you really want to use the previous driver I guess you could try to enable the feisty repository.  Then force xserver-xorg-video-ati from the feisty repo.  I'd be interested to see how your primary monitor looks like.  Perhaps a screenshot or digital picture?

---

### Post by c0mp13371331337 on 2007-10-26
Thanks for the prompt reply, BungaMan.  Forgive my ignorance regarding the max texture size.  I was under the impression that the limitation lied within the radeon driver, not the graphics card itself, so thanks for the update there!

I've taken a few pics of some windows open on the primary, then moved them over to the secondary and took a few more for reference.  While the pictures don't really do justice to what I'm seeing on this end, they're the best I could come up with.  Screenshots don't work at all, unfortunately. If I take a screenshot and open the picture on the primary monitor, all the 'shadows' are there.  But when I move the picture over to my secondary monitor, they disappear and the screenshot looks perfectly normal, so you'd call me a mad-man if I were to send a screenshot. :-)

First image is of the primary (sorry for the scan-line across the center!) and the other is the secondary monitor.  Also tied in with the screenshot problem, when I VNC into my home system from work, the entire display looks just fine.  Which makes sense, VNC being not much more than a glorified screenshot-taker-and-photo-transferer.

Just reaching in the dark here, but gamma settings?  Something to that effect?  I'm not sure what else would affect the display looking at the symptoms that I'm having.

---

### Post by BungaMan on 2007-10-27
Are your monitors close to eachother?  It are CRT's so they are very sensitive to magnetic tearing.  Try using only the primary one and have the power disconnected from the second one.  The left one might have a more protective case.  To do the test, switch the connection while keeping the monitors in the same order.  If that moves the problem to the other minitor, you know it is related to the video card.

Screenshots are done by taking what is in memory and transferring that into an image file.  So if nothing shows on the screenshot then rendering the screen image is fine.

---

### Post by saucerful on 2007-10-29
Hey,

Great thread.  Before I go through another couple of hours trying to get this to work, I want to confirm that it "should" work on the configuration I am attempting:

Thinkpad T43 w/ ATI X300
the laptop screen has resolution 1400x1050
the external lcd uses VGA and has resolution 1280x1024

I have the driver working on one screen currently (with AIGLX, Compiz), and actually when i login it shows GDM on both screens (clone), but then immediately after logging in it turns off the external display.

Has anyone been successful with a similar configuration, or forsee any problems for me? What exactly was the issue that appeared earlier about a maximum texture size?

Thanks,
Eric

---

### Post by c0mp13371331337 on 2007-10-31
For those of you following along at home (and for anyone else who happens to care) I've resolved all previously stated issues.  May not have been the cleanest fix, or the best, but it works for me and is exactly what I set out to do originally.

Basically, I just rolled back the xserver-xorg-video-ati driver to the one from Feisty.  Not the easiest task, but the good news is that I managed to do it all through repos, without having to manually compile a thing.

In doing so, I'm now able to use MergedFB as opposed to Xrandr to get dual displays working.  So now my screens work EXACTLY the way they did back in Feisty, and I was able to keep my current Gutsy install.

I'll leave it at that for now, but if anyone else is in the same boat as myself and would rather have Feisty's OSS ati/radeon drivers, I urge your to express your interest here and I will gladly go into detailed instructions on exactly how I did this.

NOTE: This is in no way meant to demean or diminish the hard work and effort that BungaMan put into the Xrandr HowTo.  I still want to stress that his work is much appreciated, not only by myself but also by others who benefited from his original and subsequent posts.  That having been said, Xrandr is not for everyone (yet) and I would just like to show people that if Xrandr doesn't work for them, there is the option to go back to the way dual screens worked in Feisty with MergedFB.

---

### Post by NcScZ on 2007-11-01
> **c0mp13371331337 said:**
> ...

I'll leave it at that for now, but if anyone else is in the same boat as myself and would rather have Feisty's OSS ati/radeon drivers, I urge your to express your interest here and I will gladly go into detailed instructions on exactly how I did this.
...


Yes I would like to see the instruction set for this. 
Thanks.

---

### Post by cporter71 on 2007-11-01
+1 on the how to roll back to feisty display.  I use a T42p through a port replicator and 2 different locations (4 different monitors).  Had this all working in feisty and have not been able to get even one monitor (DVI-0) working properly with xrandr (although the query show all attached monitors).  

Thank you to all.  This post has been helpful.

---

### Post by madsporkmurderer on 2007-11-01
> **c0mp13371331337 said:**
> 
I'll leave it at that for now, but if anyone else is in the same boat as myself and would rather have Feisty's OSS ati/radeon drivers, I urge your to express your interest here and I will gladly go into detailed instructions on exactly how I did this.



Would be much appreciated, thanks

---

### Post by c0mp13371331337 on 2007-11-01
Okay, by popular demand, here it is:

[CENTER][SIZE="5"]Rolling Back The Gutsy xserver-xorg-video-ati To Feisty Version[/SIZE][/CENTER]

Like much of the software we've all come to know, love and cherish, this how-to is provided with no warranty of any kind.  It worked for me, no gaurantees it will work for you.  Hopefully you all still have the previously working copy of xorg.conf from Feisty.  If not, you'll probably have to re-build it to specification.

First of all, add the following to your /etc/apt/sources.list document:

```
# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
```

I'm positive not all of those are needed, but that's what I had.  Comment out any and all other lines (Using a # at the beginning) referring to the Gutsy repos and any others, just to be safe.  Save that file (obviously requiring you to have opened the file as root).

Next, reboot the computer and hit Esc when GRUB tells you to so that you can choose between startup options.  Select the safe mode for the most recent kernel you've got so that once booted, you're at the root shell, NO graphics should have loaded whatsoever.  This will also mean you have no network connection to install the new version, but we'll cross that bridge when we come to it.

First thing to do at the root prompt, run:

```
apt-get remove xserver-xorg-video-ati
```

This will more than likely tell you it's uninstalling both xserver-xorg-video-ati and xserver-xorg-video-all.  This is fine, hit yes and let it do its thing.

Next, because your xorg.conf is still probably using the radeon or ati drivers, we'll have to tell it to use another one.  So at the root prompt, type:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

to backup your existing file, for posterity, then:

```
nano /etc/X11/xorg.conf
```

to edit the existing one.  In the device section, change the driver to "vesa".  No other change should be necessary, as this will probably break the xserver anyway.  Save the file and exit.  Then type 'reboot' at the root prompt to restart the system.

Let it get as far as it can, eventually it will try to start up the graphical system, then X will kick the bucket because you broke xorg.conf.  Good going.  But with Gutsy, it should be able to fix itself enough to give you cloned displays running 800x600, which is good enough to re-install the drivers, now that we have a network connection.

Once you're all logged into your profile and whatnot, open a terminal and run: 

```
sudo apt-get update
```

for good measure, then:

```
sudo apt-get install xserver-xorg-video-ati
```

That should go without a hitch and you should now have your Feisty drivers back.  Replace the current fallback xorg.conf with your old one from Feisty:

```
sudo cp /path/to/your/old/xorg.conf /etc/X11/xorg.conf
```

Now reboot your computer.  I found that my monitors were still cloned, so I had to change the resolution in System > Preferences > Screen Resolution from 1600x1200 to 3200x1200 once I was all logged in.  That will depend upon your own personal setup and xorg.conf though.  You may or may not have to do that.  And I'm sure anyone who's read this post this far will know this already, but compiz-fuzion will obviously not work if x OR y resolution is greater than 2048.  This is obviously the case in my setup, so I've disabled compiz altogether.

Be sure to delete those temporary Feisty repos from sources.list and un-comment all the lines to your other repos.

I'm sure this is not the easiest or most efficient means of rolling back the driver, but this is how *I* did it, so this is what I know, and it worked for me.  Let me know if anything needs clarification or if anyone runs into any hitches.  I'll try my best to help.

---

### Post by madsporkmurderer on 2007-11-03
Thanks for that, it has got me from being stuck in 800x600 to being able to use xorg to set things up properly with one problem- Xinerama isnt working; whichever of my two screens I list first in the server layout gets cloned to both displays

---

### Post by c0mp13371331337 on 2007-11-03
Not familar with Xinerama, unfortunately.  I've been using MergedFB for my dual-monitor needs.  Nvidia card, I take it?

---

### Post by madsporkmurderer on 2007-11-04
ATI, I dont really know why i used Xinerama when I set it up but I dont remember there being any major reason why MergedFB couldnt bbe used- Ill give it a go and see what happens

---

### Post by madsporkmurderer on 2007-11-04
Got mergedfb to work, theres only one slight problem that due to one of my 21"monitors breaking I am currently using a 17" as my secondary to the right of my primary. The 1600X1200 added to the 1280x1024 has been merged to 2880x1200 meaning that the 17¨ has to scroll up and down.

I imagine this is just the way it works and I´ll have to put up with it until I find another 21¨

Thanks for all the help it is loads better than when I started

---

### Post by c0mp13371331337 on 2007-11-04
Kudos, madsporkmurderer, glad to see that's all working out for you.  As far as the scrolling viewport, I think that's just an unfortunate consequence of having two different resolutions.  It may or may not be possible to crank out two different resolutions, basically having a polygon-shaped framebuffer as opposed to a regular rectangle.  Haven't personally had the need to research this at all.  I mean, you could sacrifice a bit of resolution on the good monitor, bump it down to whatever the largest size the smaller one can support, if the scrolling viewport is really bothersome.  Or, as you said, wait til you get another 21".  (Wanna get me one too, while you're at it? ;)  )

---

### Post by BungaMan on 2007-11-05
c0mp13371331337 thanks for your kind words a few posts earlier :)

if you use mergedfb then you can stop the scrolling with MergedNonRectangular set to true.  

Here's a post with my older xorg.conf layed out for mergedframebuffer.
[http://ubuntuforums.org/showpost.php?p=2329182&postcount=13](http://ubuntuforums.org/showpost.php?p=2329182&postcount=13)

---

### Post by cleonII on 2007-11-06
> **BungaMan said:**
> yes that is because it fails to generate a texture for your desktop area.  For the maximum size you'll get the white area and the right most becomes an area that is never cleared in memory.  Hence the effect you notice when moving stuff around in that area.

BungaMan, the tutorial absolutely rocks.
But I'm getting that error too. Do you know a solution for that?
I have an ati radeon 7500.

Thanks!

---

### Post by BungaMan on 2007-11-06
It's all in the first post!

---

### Post by Kevin on 2007-11-13
Just a little suggestion, I can't verify it 100% cause my r300 just hard crashes whenever i xrandr anything to it...

But to get around the 2048x2048 limitation on *some* configurations you can simply arrange them above and below each other.  For example, two 1280x1024 screens could be arranged above each other, creating a 1280x2048 canvass.  This obviously doesn't work for everyone, but it would work for a laptop with 1280x800 and an external monitor of 1280x1024 for example, or even up to 1920x1200 really! (1920x2000)

---

### Post by ethanhunt on 2007-11-26
I tried all the steps for with my intel 915GM card. IT does not work. Any possible workarounds 

Here is my config
Dell 610 / Intel 915Gm chipset
Two external monitors connected.
xrandr works perfectly on my Gutsy so i have dual display.

---

### Post by airtonix on 2007-11-27
reason why xinerama is used on ati is so you can move applications between displays.

hi...i jus reinstalled feisty. and am looking at getting big desktop going again.

i've had it before on feisty, and i know it was with xinerama. i forget the rest.

I can supply all details if required.

---

### Post by bleaked on 2007-11-30
First off, thank you again BungaMan.. your tutorial has gotten me much further than that debian wiki everyone always points me to..

Second, I'm so very close to getting this to work, but just need a few additional tips.

I have two CRTs, the 17" (1024x768 @ 85) in a VGA port and the other 19" (1280x1024 @ 75) in the DVI port.  The 17" is on the left and 19" on the right.

Following your instructions, everything seems to load properly, except the 19" monitor is running at 1024x768, when I believe I have it setup to run at 1280x1024.  Either way, I can drag windows over, and I could even live with it.. However, if I maximize a window on the 19", then move my mouse away, then back, the system completely freezes.  This happens every time.

Now, I'm not sure what I might be doing wrong, so here are my questions:

With a desired setup such as this, what would you set the Viewport and Virtual fields in the xorg.conf?

And, would it make more sense to make the larger or the smaller monitor the default?

Here is my relevant xorg.conf for reference:

```

Section "Device"
	Identifier	"Radeon 9600"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option 		"Monitor-DVI" "986FS"
	Option		"Monitor-VGA" "KDS XF-7b"
EndSection

Section "Monitor"
	Identifier	"986FS"
	Option		"DPMS"
	HorizSync 	30-86
	VertRefresh 	50-160
	Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
EndSection

Section "Monitor"
	Identifier	"KDS XF-7b"
	Option		"DPMS"
	Option		"LeftOf" "986FS"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Facade"
	Device		"Radeon 9600"
	DefaultDepth	24
	SubSection "Display"
		Depth 24
		Viewport	1280 0
		Virtual 	2560 1024
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Facade"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"AIGLX"		"true"

EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option 	"Composite" 	"Enable"
EndSection

```



Thank you,

excitatory

---

### Post by BungaMan on 2007-12-03
You have an issue with the freeze and the resolution.  Resolution is covered below but the freezing I can't help you with.  It could be due to the max resolution work around but I can't tell for sure.

Try leaving out the Modes in the Display subsection.  You don't need it and you can set a preferred mode in your monitor section now.

If it still gives you resolution issues then check in a terminal with "xrandr -q" to see if your DVI connector has a 1280x1024 mode defined.  If it isn't then probably that modeline in your xorg.conf is wrong.

The viewport defines the position of your primary display in the virtual.  because your 19" is on the right at 1280 0 in your virtual, it means that your 19" is seen as the primary.  If you want to be sure of this you can set the monitor option in the screen section.  Can't see any technical reason why you would want to have one or the other set as primary.  It's a personal choice I guess :)

---

### Post by Jense on 2007-12-12
Thanks so much, this works just perfect. For the first time I got two screens and compiz working on my t41, even with an ati 7500.
This is Great!!!!!

:):):):):):):)

---

### Post by tekknokrat on 2007-12-27
I have tested the initial tips and configuration and I can now adjust all the modes via xrandr which is fine and I am thankful for the origin poster figuring this out and the others offering example configs.

What still bothers me is that rotation leads to a crash of the whole system ( oss ati driver )
and that I can't store the settings I want persistently.

I have an 19" and 15" monitor and tried to adjust config to get the 19" running initial with 1280x1024 and the 15" with 1024x768.

I tried several approaches with Option PreferredMode, Modeline in both Monitorsections but I can't force Xorg to use the defined resolution on start.

Afterwards this is no problem:
```

lila@gentoo:~$ xrandr --output DVI-0 --mode 1280x1024
lila@gentoo:~$ xrandr --output VGA-0 --pos 1280x0

```

Does someone some has some tips in which way I could change my config?
```


Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
    	Option "monitor-DVI-0"	"monitor1"
    	Option "monitor-VGA-0" 	"monitor2"

EndSection

Section "Monitor"
	Identifier	"monitor1"
        Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 
1028 1060  -HSync +Vsync
#        Option "PreferredMode" "1280x1024_60.00"
EndSection

Section "Monitor"
	Identifier "monitor2"
	Option "RightOf" "monitor1"
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"monitor1"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	2304 1024
		Modes "1280x1024-1024x768" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 		"Main Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout"	"Default Layout"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by dziadgba on 2007-12-27
I nearly got dual screen: two monitors working -> I can go with the mouse from on to the other monitor.
unfortunately the resolution of the second LCD monitor (the first is a Laptop monitor) is not working properly.
It shows a black block at the right which is jumped-over by the mouse, it seams that the system fails to enlarge the screen properly to the horizontal size of the monitor, vertical size is ok.
Somebody knows what I am doing wrong?

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection



Section "Device"
        Identifier      "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
        Driver          "ati"
        BusID           "PCI:1:0:0"

        Option          "monitor-Laptop" "laptop"
        Option          "monitor-LG" "lg"

EndSection


Section "Monitor"
        Identifier      "laptop"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
        Option "PreferredMode"  "1280x800"
EndSection


Section "Monitor"
        Identifier      "lg"
        Option "RightOf" "laptop"
        Option          "DPMS"
        HorizSync       30-83
        VertRefresh     56-75
 Modeline "1440x900"  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
        Monitor         "laptop"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Viewport        1280 0
                Virtual         2720 900

                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"

        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
Option          "AIGLX"         "true"



# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection


Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite"             "Enable"
EndSection


```

then I am doing simply:

```

$ xrandr -q
Screen 0: minimum 320 x 200, current 2720 x 900, maximum 2720 x 900
VGA-0 connected 1440x900+1280+0 (normal left inverted right) 408mm x 255mm
   1440x900       59.9*+
   800x600        56.2  
   640x480        60.0  
LVDS connected 1280x800+0+0 (normal left inverted right) 0mm x 0mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)
$ 

```

and finally

```

xrandr --output VGA-0 --right-of LVDS --mode 1440x900

```

hope someone can help me!

---

### Post by tekknokrat on 2007-12-30
@dziadgba

sorry if i missunderstand but do you mean you have initially the correct resolution for both of your monitors?
Or is it only shown "correct" in xrandr?
When your "virtual" size in xorg.conf is heigher then you ould indeed get graphical fragments - which i think your black block is one.

For me both monitors are started with 1024x768 my config is in the post above. But indeed xrandr shows the resolutions correct:

VGA-0:   1024x768@60    60.0*+
DVI-0 :    1024x768       75.1     70.1     60.0*

---

### Post by dziadgba on 2007-12-30
@ tekknocrat
thanks for the replay

xrand shows it correct - I think I indeed go out of limits so I get fragmented monitor.
I stopped trying though and returned to the Feisty Version for the graphical output- everything now work fine again.

---

### Post by DavidTruesdale on 2008-01-11
First, thanks for the post, I just bought two new LCD displays and thought I might have to move back to Windows to get them to work. I have experienced two problems previously mentioned by others. My computer has a tendency to freeze when the cursor gets within a critical distance of the border between the two monitors. It doesn't always, but if I do it enough, it will crash eventually. So bad, in fact, that only a hard restart will bring it back. As you can imagine, this has prevented me from doing any serious work while running both displays. The second problem is that my secondary display is much brighter than my primary display. It is washing itself out. I assume that it is a problem with the gamma setting, but I have been unable to locate a solution anywhere. If there is anyone that has had a similar problem and managed to fix it, please help.

---

### Post by tekknokrat on 2008-01-14
Is someone here who has also the problem that different resolutions aren't working on start with xrandf-1.2 / ati / intel ?

Theres a bug open on xorg.freedesktop.org about this issue.

[https://bugs.freedesktop.org/show_bug.cgi?id=12869](https://bugs.freedesktop.org/show_bug.cgi?id=12869)

If you have problems with setting resolution in xorg.conf it would be helpful if you'd post your config/logfile there.

---

### Post by snowglyder on 2008-01-30
Thanks for the guide, I finally have 2 screens working! I am having an issue with compiz now. When I commented out the return: 1 line in the compiz file and did compiz --replace, my screens would start flashing and it would fail. I figured that this was because my resolution was set too high (1280x1024), so I went to 1024x768 so that my virtual resolution is within the 2048 2048. Now when I run the compiz --replace it will work for a minute or so, but the system freezes to where I can't even restart X. It keeps playing my music in the background, but the display is locked. The only way to get out of it is to hard shutdown the pc. I've also tried going to 16-bit depth, but it does the same thing. Any suggestions on how to troubleshoot getting compiz to work? Here's my xorg.conf:

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Driver		"ati"
	BusID		"PCI:5:4:0"
	Option "monitor-VGA-0" 	"monitor2"
    	Option "monitor-DVI-0"	"monitor1"
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"monitor2"
	Option		"DPMS"
	Option "LeftOf" "monitor1"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
	Monitor		"monitor1"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual 2560	1024
		Modes		"1280x1024" "1024x768"  
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Option		"AIGLX"		"true"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "ServerFlags"
	Option		"DefaultServerLayout"	"Default Layout"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by BungaMan on 2008-02-02
I'm afraid your card will be too old to handle this.  Guessing here but maybe your texture support is limited to 512x512?  You can find this out when running compiz --replace in a terminal without commenting the return 1.  That means the resolution of a single screen doesn't even fit in 1 texture for your card.  So you cannot make the size of a program more than 512x512 or weird things start to happen.

---

