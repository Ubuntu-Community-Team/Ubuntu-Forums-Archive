---
title: "[SOLVED] No Flash: HELP!!!!!"
date: 2007-08-07
forum: Desktop Effects &amp; Customization
---

### Post by upthelum on 2007-08-07
Hopefully someone can help me with this problem. I've been trying unsuccessfully for about a week to install Flash Player and plugins to let my kid watch wwe video's from the wwe website. It's all that's stopping him from ditching windows, he's ten. I have tried all sorts of methods to install from the Adobe way recommended on their website, to ways i found on lots of threads here. None seem to work properly although i am a little closer to achieving my goal. Until today i had managed to get Flash installed but when i viewed a video it asked for an mplayer plugin, which i promptly installed too. 

The stage i'm at now is: Flash is installed and "seems" to be working but now the video begins and starts transferring the data, and that's about as far as it gets. You can see from the pics i attached that it's trying to play the clips but doesn't. 

Any help would be appreciated thanks.

---

### Post by nichipet on 2007-08-07
When I get home I'll try the same videos to see if they work for me. I have Flash working and I think MPlayer's Firefox plugin is installed as well.

---

### Post by upthelum on 2007-08-07
Thanks, i use an athlon 64 though so i think that's an issue too but i'm making some progress.

---

### Post by nichipet on 2007-08-07
My laptop is 64 bit Intel Core 2 Duo, 2 GB RAM, UbuntuStudio 7.04. I think I used apt-get to install flash and mplayer from medibuntu.

---

### Post by Krydahl on 2007-08-07
> **upthelum said:**
> Thanks, i use an athlon 64 though so i think that's an issue too but i'm making some progress.

Did you install the 64 bit version of ubuntu? If so, see here: [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

---

### Post by upthelum on 2007-08-07
> **Krydahl said:**
> Did you install the 64 bit version of ubuntu? If so, see here: [http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

I'm not entirely sure, how can i find out from my os?

---

### Post by FuturePilot on 2007-08-07
That looks like an issue with Mplayer, not Flash. Make sure you have the necessary codecs installed. That's most likely the problem. 
[Look here]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Krydahl on 2007-08-07
As you can probably tell from my number of posts, I'm no expert. However, if you type:

>  ls / 

at a terminal do you see a directory called lib64? I'm guessing that if you do you're running 64bit and if you don't you aren't.

Having said that, checking the mplayer codecs sounds like a better bet.

---

### Post by SynapseR on 2007-08-07
Have you tried 

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by mgmiller on 2007-08-07
I just tried going to the wwe site.  They are streaming a windows media format, not flash.  My flash player works great everywhere.  I have the mediaplayer connectivity plugin for Firefox and tried playing their stream with totem-gstreamer, gmplayer, helix (realplayer) and vlc with no joy.  I finally changed the command in mediaplayer connectivity to mplayer instead of gmplayer and it worked.  So my suggestion would be to make sure you have mplayer and vlc and whatever other players you want installed from synaptic first.  

Then get the mediaplayer connectivity plugin from Firefox.  (look in Tools > Addons) and look on the extensions tab.  On the bottom right is get extensions link.  Once you're on the page, search for mediaplayer connectivity and install that.  

After a restart of Firefox, a wizard should start up to configure it.  For Windows media, select mplayer as the player.  If you need to tweak it later, once on a web site, click Tools > Mediaplayer Connectivity and configure.  Put a tick in the expert mode box.  Next to the Windows Media entry put checks in all the boxes and the path should be     /usr/bin/mplayer  (**_not_** /usr/bin/gmplayer)  the argument should be    %f  Then click apply and OK.  

Try going back to the site and see what happens.  It worked for me.

---

### Post by nichipet on 2007-08-07
I don't think it's your browser, but rather their website. I tried it and it just sat there "Waiting for video.wwe.com"

---

### Post by upthelum on 2007-08-07
Thanks for all your response. I've got as far as downloading the codecs but i dont have a lib64 directory (can i upgrade to 64 without a re-install or is that a silly question) and the codecs wont install, im getting a dependency error, see attachment. After i installed the mediaplayer connectivity plugin, it started to look a bit promising, but now i get a blank screen opening, see 2nd attachment. I'm off to bed so will take it back up in the morning, thanks again...

---

### Post by mgmiller on 2007-08-08
It looks like you are close.  The libdvdcss2 you are trying to install is only for playing DVD movies and won't help your current problem.  To try fixing the black screen in mplayer, go to your Applications menu and under Sound and Video, run the mplayer movie player.  Right click the player and select preferences.  Go to the Video tab and select the xv driver.  Click ok and exit the player.  Then try going back to your wwe website and see what happens.

---

### Post by mgmiller on 2007-08-08
> can i upgrade to 64 without a re-install or is that a silly question

Not a silly question.

That being said, since the 64 bit is a different architecture than the 32 bit, you can't just upgrade to it.  You would need to do a full re-install.  

My understanding is that the multimedia parts of the 64 bit Ubuntu are still a bit of a pain to get going.  I don't think there is a native 64 bit flash yet, although there are supposed to be workarounds for that as well as most other problems.

I have an AMD 64 bit cpu that happily runs the 32 bit version of Ubuntu.  Since you are having problems in 32 bit, I don't think you want to add more complexity by changing to 64.

As an experiment, you could try running the 64 bit Live CD and see if you get any luck at getting it to play the videos on the wwe web site.  You can attempt to install all the players and codecs and even try for flash without having to reboot or installing to your hard drive, so you don't risk anything beyond some time.

---

### Post by mgmiller on 2007-08-08
One final thought on your libdvdcss2-dev problem.
This package is the development files package used to compile applications that use libdvdcss2.

It depends on the libdvdcss2 package being installed first.  Your error message clearly states it is not installed yet.

You just need to install the packages in the right order.  libdvdcss2 first, then the -dev package.

---

### Post by upthelum on 2007-08-08
> **mgmiller said:**
> It looks like you are close.  The libdvdcss2 you are trying to install is only for playing DVD movies and won't help your current problem.  To try fixing the black screen in mplayer, go to your Applications menu and under Sound and Video, run the mplayer movie player.  Right click the player and select preferences.  Go to the Video tab and select the xv driver.  Click ok and exit the player.  Then try going back to your wwe website and see what happens.

Ok i did that but no cigar yet. I went for the codecs again from Medibuntu. I did [_this_]("https://help.ubuntu.com/community/RestrictedFormats/NonNativeCodecs?highlight=%28codecs%29") for 7.0.4.
And got this error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

I found some lists of codecs but was unsure of which ones to take, last night i tried 3 but still no cigar. I got an architecture error with the 64 bit codec so i think it's safe to say that's a problem. I also tried a 32 bit version of Firefox, which didn't work.
I've tried a few different browsers too, can anyone recommend a browser that may work with windows media streams? Not sure what to try next!!! :roll:

---

### Post by mgmiller on 2007-08-08
The GPG key error is not critical, just click ok and it will go through.  
To install the key so you don't get the error anymore, open a terminal and past the following into it:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Hit enter and it should download and install the key for you.

Try installing the ubuntu-restricted-extras package.  This is a meta package that installs a lot of extra codecs and keeps them up to date.

One other thing to try is to go back into the mplayer preferences menu and go to the codecs and demuxer tab.  In mine, I have nothing checked and both video codec family and audio codec family say "none".  You could try changing to these settings or experimenting with other video codec settings (there are 2 that are w32 codecs), and see what happens.  Remember, you must close mplayer each time you make the change for it to become effective.

Other than that, I'm not sure why you are having problems.  Usually mplayer has a bunch of codecs that it installs for itself and is all you need.  It works on my system on your wwe web site.  This has to be a codec issue of some sort.

---

### Post by mgmiller on 2007-08-08
> I got an architecture error with the 64 bit codec so i think it's safe to say that's a problem

No, it isn't.  You do not have 64 bit Kubuntu installed, so you can't use the 64 bit codecs.

> I also tried a 32 bit version of Firefox, which didn't work.

Where did you get this version from?  You should try to only use the version that is in the Ubuntu repositories.  Since you installed mediaplayer connectivity, you must have been using a Firefox from somewhere.  It is important that Firefox be installed before adding any plugins, or they may not be correctly picked up by the browser.

---

### Post by upthelum on 2007-08-08
> **mgmiller said:**
> The GPG key error is not critical, just click ok and it will go through.  
To install the key so you don't get the error anymore, open a terminal and past the following into it:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

Hit enter and it should download and install the key for you.

Try installing the ubuntu-restricted-extras package.  This is a meta package that installs a lot of extra codecs and keeps them up to date.

One other thing to try is to go back into the mplayer preferences menu and go to the codecs and demuxer tab.  In mine, I have nothing checked and both video codec family and audio codec family say "none".  You could try changing to these settings or experimenting with other video codec settings and see what happens.  Remember, you must close mplayer each time you make the change for it to become effective.

Other than that, I'm not sure why you are having problems.  Usually mplayer has a bunch of codecs that it installs for itself and is all you need.  It works on my system on your wwe web site.  This has to be a codec issue of some sort.

Thanks again for the info, i did install the unrestricted ubuntu packages and i'll try what you recommend as soon as i get back to linux. I have another _[thread]("http://ubuntuforums.org/showthread.php?t=520797")_ going about installing adobe photoshop in linux which is why i'm in winblows (most unfortunately), this time it's so i can get my better half over too, you wouldn't have any ideas about that would you? I fully intend to make the switch altogether to linux as long as i get all the proggy's i need to run (sorry for getting side-tracked). This is just the beginning, i go to uni next month so i'm not entirely sure what other software i will need except ms access. The 32 bit version came from another thread, it runs from terminal with "firefox32 &", but isn't in kmenu and like i mentioned i tried a few codecs which didn't work (was that a blunder?), as it recommended that you can use 32 bit firefox on 64 bit, before i realised i didn't have 64 bit installed, is this just a codec issue for sure and not related to the architecture?

---

### Post by mgmiller on 2007-08-08
> is this just a codec issue for sure and not related to the architecture?

I am confident that it is not an architecture issue.  All these things should work fine in 32 bit.  You are more likely to have problems with a 64 bit install, so for the time being, stick with 32.  The only other big difference between our systems is that yours is Kubuntu (kde) and mine is Ubuntu (gnome).  This may have some influence, but since I have no real experience with kde, all the help I am giving you is from my knowledge of gnome.  I am able to view the wwe videos even with my compiz desktop effects turned on.

Just curious, why photoshop instead of gimp?  For about 90% of stuff, it's just as good, although I understand there are some things it doesn't do.  Most users only use about 25% of the features in either application, so I guess what I'm asking is, what does she need to do that gimp can't?

---

### Post by upthelum on 2007-08-08
Ok what if i were to change sessions and set up everything in a gnome session, can i do that? I cant get compiz to work either i've got frustrated trying to, it's installed but just loads for 20 seconds and stops. It's not a case of what the gimp cant do, she found out she will be using photoshop in college as of next week so it's essential really.

 Like i asked earlier, if adobe files can be opened and changed in the gimp and vice versa that would be good. The thing is she isn't familiar with windows never mind linux in the slightest and isn't too great with computers in general so i don't want to complicate things any more than necessary.

---

### Post by upthelum on 2007-08-08
I actually downloaded the 64 bit version of feisty tonight in case i decided to re-install but i'll  try it on vmware first.

---

### Post by mgmiller on 2007-08-08
> Ok what if i were to change sessions and set up everything in a gnome session, can i do that? 

Yes, most people have no problems switching back and forth between the 2.  You would use your package manager to install ubuntu-dekstop.  This should create a gnome environment and install all the ubuntu apps.  To access it, log off.  On the log on screen there should be a sessions button somewhere.  If you click that you will see the option to log into a gnome session.

The reason I say most people, is that I have read a few posts (not many) where installing gnome from kde or vice-versa has caused some problems.

I would suggest backing up any important data before attempting this.

> Like i asked earlier, if adobe files can be opened and changed in the gimp and vice versa that would be good. 

Yes, gimp can both read and write .psd files.  So she can open a *.psd, work on it and save it again in the same format.  Photoshop should then also be able to open and further modify it.

That being said, her university may insist on Photoshop.  I don't know.  You can check with the crossover office people   [http://www.codeweavers.com/]("http://www.codeweavers.com/")to see if the support photoshop.  If they do, the cost is not terrible.

---

### Post by mgmiller on 2007-08-08
> I cant get compiz to work either

I just noticed this.  What video card do you have and what driver are you using?  This can have an impact on displaying all sorts of things.

---

### Post by upthelum on 2007-08-08
Good news about gnome then but does the apps i have installed in kde, affect what i can/cannot install in gnome? 

It's below on my signature, asus board uses K8M890 vga chipset which i have using 256mb. The driver i'm not sure of i just installed ubuntu and meddled with system settings and things seem to look decent enough, i'm still a noob in a lot of respects.

---

### Post by mgmiller on 2007-08-08
> Good news about gnome then but does the apps i have installed in kde, affect what i can/cannot install in gnome? 

Nope.  Gnome can happily run kde apps and vice versa as far as I know.  I am running a few kde apps in my Ubuntu desktop.  They "work a treat".

I am researching your mobo, hold on a bit and I will have some video info for you.

---

### Post by mgmiller on 2007-08-08
From what I can see, your integrated video is via unichrome/S3.  This is very low performance and you are almost certainly using the "vesa" driver.  You can do a quick check by running:

```
gedit /etc/X11/xorg.conf
```

Then scroll down till you see the part about section "device" after the monitor bit.  Mine looks like this:

```
Section "Monitor"
    Identifier     "VX2235wm"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
```

In my case, the system is calling my card a "Generic Video Card".  It's really an Nvidia, notice the next line for Driver reads  'nvidia".

I would be willing to bet you driver line says "vesa".

This is the compatibility driver and cannot do accelerated graphics.  So you can't get compiz to work.  Different video chip sets will also use parts of the video driver in different ways, so one card that can display this kind of video with vesa and another won't.  There may be a "via" driver, but I am not familiar with it.  

Is there a "Restricted Drivers Manager" in Kubuntu?  If there is, see if it offers a better driver for you.  Failing that, you may never get accelerated video with this integrated video card.  

Your easiest solution might be to get a modestly priced US$ 50-100 nvidia video card.  Since your mobo is socket 939, I assume it uses AGP and not pci-express for video.  
EDIT:  I just discovered you are pci-express, not AGP.  There should be lots of modestly priced video cards out there for you, as this is the latest bus.

There are mobos out there that have integrated nvidia cards that would work, as long as you stick with socket 939, you can reuse your cpu, ram, etc.  

The cost of the mobo would be about the same as the cost of the separate card, but the video performance would not be as good.  I would suggest you stay away from ati, as many of them can create a lot of problems.  That being said, I have had good experiences with ati 9600 based cards, and they should be very cheap.  In fact, the 9600 series runs compiz with the standard ati driver.  However, this is again, not an accelerated driver, so other video things may suffer.  If you install the ati accelerated driver, called "fglrx", video speeds up, but you lose the ability to run compiz.  Like i said, ati=problems.

With nvidia, you have to install the accelerated driver to get compiz to work, so you get the best of both worlds.  Before buying the card, make sure it's Linux friendly, check these forums for problems.  The vast majority of nvidia cards work great, but there are a few clunkers out there.  I would think pretty much any geforce 7xxx AGP card should work well, but check to make sure.  If you get a card that is too slow, it will "stutter" when trying to display compiz effects.  It just wouldn't be right to have your wobbly windows appear jerky.

Post your xorg.conf file here and I can see if there is anything else of interest to suggest.

---

### Post by mgmiller on 2007-08-08
EDIT: I just discovered you are pci-express, not AGP. There should be lots of modestly priced video cards out there for you, as this is the latest bus.

Most of the newer video cards use dvi for connection to the monitor.  Since your current monitor is using a vga connector, if you have no other choice, make sure the new video card also has a vga connector or ships with a dvi to vga adapter.  If your monitor is dvi capable, you may want to spring for a dvi cable also.  You usually get noticeably better display with dvi than analog vga.  These cables can be gotten reasonably on line.

---

### Post by upthelum on 2007-08-08
Yes it says vesa. Here's the output:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Philips 190X"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Philips 190X"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Also the spec from the mobo:

2Xddr400, dual-ch, 1xpcieX1, 2xPCI, 2xsata(1.5Gb/s), raid support, EZ Flash and Crachfree bios2.

I remember looking up asus for linux drivers but there didn't appear to be one released. Synaptic says i have restricted driver installed but i cant find it, do i run it from terminal?

I was going to get an Nvidia card at some point anyway but i may consider changing the board too now. It was only 40 quid anyway and i can always keep it for another build project. My last board (i recently upgraded) was a gigabyte which i put into a machine for my kid (as usual it's not finished yet but will be soon, i need 2 dvd writers also). 

But hey it wont put me off linux, only more determined to get an even better spec machine.

---

### Post by mgmiller on 2007-08-08
> Synaptic says i have restricted driver installed but i cant find it, do i run it from terminal?

If you have the restricted driver manager installed, then you run it by going to (Don't know kde, gnome instructions follow):

System > Administration > Restricted Drivers Manager

Just run it and see what it says.

From what I can see, your monitor is vga only.  So, my comment about the vga port/dvi-vga adapter is important in the selection of a new video card.

If you are considering a new mobo, be aware that pretty much all of them don't give stellar 3d performance.  The best of the bunch at the moment use an integrated nvidia 7025 or 7050 video chip that does not have a driver in the Ubuntu repos yet.  It should be there by October when 7.10 ships.  It is possible to install the driver directly from nvidia, but you will have problems every time there is a kernel upgrade.  As a noob, I would like to see you have the smoothest possible ubuntu experience.  You may be better off just buying a new nvidia video card and putting it in your current mobo.

---

### Post by upthelum on 2007-08-08
Hey another development, when i ran "gedit /etc/X11/xorg.conf", i had to install it first. So i did and then ran apt-get update, which i noticed, installed the codecs i needed. So i went back to wwe and ran a video, wadda y'know, it works.

Hey presto, just like that. It opened and closed after displaying 2 seconds of footage, but re-opened a moment later and played the video, sound working too. This is great man, suppose i will just get the kid to watch his clips and let me know if any more problems arise. 
Just tried Youtube but that's not happening and i dont use it anyway but that's a result, and is what i enjoy about the forums, getting results.

As yet i cant find the restricted drivers app but attached a dump of info from device manager. I'll do my homework on nvidia cards too, my last one was agp and it's going into the kids new box. Thanks for all your help it's appreciated, i might as well mark this as Solved and encourage you to look at any un-solved threads i have whenever your not too busy (and as long as you dont mind).

---

### Post by mgmiller on 2007-08-08
My current suggestion would be nvidia 7600 or 7800 series cards.  Decent performance and reasonable price (under US$100).  It all depends on your budget.  Be careful with nvidia 8500/8600 and the newest cards.  I don't think there is any Linux support for them yet.

---

### Post by upthelum on 2007-08-08
Sorry wrong image.

---

### Post by mgmiller on 2007-08-08
Great news...:lolflag:

Looks like you can get by with your current card as long as you don't want to run compiz.
I'll chalk this up to one of those kde/gnome differences things.

> Just tried Youtube but that's not happening 

Now this really is a flash issue.

In gnome, using System > Administration > Synaptic Package Manager try uninstalling and reinstalling the ubuntu-restricted-extras package. This should remove and reinstall flash.  Hopefully it will see the Firefox on your gnome side and fix it.

---

### Post by upthelum on 2007-08-08
Before i got video working in wwe, it would start in Youtube and then just play about 1 second of video and freeze. 

If synaptic un-installs and re-installs will i have to get the codecs again?

---

### Post by upthelum on 2007-08-08
Aye the description in synaptic says it's for gnome so is it ok to try this in kde?

---

### Post by upthelum on 2007-08-08
I just got a quad-shot of ubuntu, that was strong!!!!!
Oops no i didn't i'm getting tired lol.

---

### Post by mgmiller on 2007-08-08
oh, wait... I just realized you got this working in kde.  I believe the editor in kde is kate, so when you tried to use gedit, which is the editor in gnome, you had to install it.  

After all this time, it's possible all you needed to do was run your package manager and tell it to update and then install all the updates.](*,)

As far as flash is concerned, look in your kde package manager and try uninstalling and reinstalling flashplugin-nonfree.

---

### Post by upthelum on 2007-08-08
Ok thanks i'll get on top of it after a kip... :cool:

---

### Post by mgmiller on 2007-08-08
Also, after doing this, make sure you close all instances of Firefox and then rerun Firefox to test it.  In the address bar, you can type:
```
about:plugins
```

Scroll down a bit and look for the shockwave flash entry.  Mine looks like this:

```
Shockwave Flash
    File name: libflashplayer.so
    Shockwave Flash 9.0 r48
```

Once that's in, flash should work.

---

### Post by mgmiller on 2007-08-08
> Ok thanks i'll get on top of it after a kip... 

:lolflag:
We are separated by a common language.  I had to google the phrase to see what it meant.  
I guess it's getting rather late in Glasgow.  

Any way, have a good kip.  (Is that correct?)  

):P

---

### Post by upthelum on 2007-08-10
Hey i did that and it seems to be fine so far although it's not too quick at opening, but i can live with that. I'll work on compiz next after i put suse on vmware, then next week or so i should look for an nvidia card, a friend who is very knowledgable about hardware recommended staying away from ati too so thanks again for the help.

---

### Post by mgmiller on 2007-08-11
You're welcome.

---

