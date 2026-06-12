---
title: "HOWTO: Beryl with latest nvidia drivers and FEISTY's built in AIGLX (no XGL)"
date: 2007-02-09
forum: Desktop Effects &amp; Customization
---

### Post by PriceChild on 2007-02-09
[LEFT][SIZE=5][COLOR=black][SIZE=6][COLOR=Red][SIZE=2][COLOR=black]Original thread here: [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)
To install Compiz on Nvidia, please follow [http://ubuntuforums.org/showthread.php?t=359367](http://ubuntuforums.org/showthread.php?t=359367)
[/COLOR] 
[/SIZE][/COLOR]**[COLOR=Red]Beryl is beta software and unstable. Be prepared for breakage![/COLOR]**[/SIZE][/COLOR][/SIZE]
[/LEFT]
  
[CENTER][SIZE=5][COLOR=black]_Have a look [here]("http://ubuntuforums.org/showthread.php?t=272104") for other howtos on Beryl & Official Compiz_[/COLOR][/SIZE][/CENTER]
 
[CENTER][COLOR=black][SIZE=1][SIZE=4]Go to #ubuntu-effects on irc.freenode.net for support.[/SIZE][/SIZE][/COLOR][/CENTER]

[LEFT]Nvidia have released their 9xxx series drivers. In laymans terms, this allows compiz/beryl to now run directly on an x server (xorg7.1) without separate aiglx or xgl.[/LEFT]

 As far as i understand, you MUST remove all existing xgl/aiglx from your system for this method.
 
[SIZE=6]STEP 1: Install nvidia drivers[/SIZE]
 Go to System > administration > restricted drivers manager and enable the nvidia driver.
[SIZE=6]STEP 2: Install Beryl[/SIZE]
 ```
sudo apt-get install beryl beryl-manager emerald-themes
```[SIZE=6]
[/SIZE][SIZE=6]STEP 3: Lets Go![/SIZE]
 Type beryl-manager into alt+f2 or a terminal and all should work.
 
I hope this has worked :) If it doesn't then preferably try and get help in the IRC channel first: #ubuntu-effects on irc.freenode.net If your problem gets fixed, then post it below and i'll add it to this main post if important :)

---

### Post by ~LoKe on 2007-02-09
Question:  The thread title implies that you need AIGLX, but you mention removing/not needing XGL and AIGLX.  Are you saying that it's not required, but since it's built in, it might as well (must) be there anyways?

---

### Post by PriceChild on 2007-02-09
AIGLX functions are part of the nvidia drivers and xorg7.1 (I've never decided which ;) )

---

### Post by leech on 2007-02-09
After reading all the things on XGL, AIGLX, Beryl, Compiz, etc you tend to get confused and an overall headache.

From what I've gathered (granted this could be wrong) is that AIGLX is built-in for Xorg 7.1, but that means only Xorg 7.1 drivers utilize it.  So any drivers the X team itself makes that support 3D (mostly the Radeon for older ATI cards and Intel cards) support AIGLX.  

nVidia uses their own implementation that is still considered AIGLX.  So it works with having 3D acceleration and is quite stable and fast.

ATI's fglrx drivers don't support the proper extension, so to use the desktop-effects you have to use XGL, which is a layer on top of Xorg, so no 3D acceleration for other applications as XGL will take it over.

So technically the title of the post is correct, it's just not Xorg's built-in AIGLX, but Feisty's (w/ nvidia's driver) that makes it built-in.

Leech

---

### Post by PriceChild on 2007-02-10
I'm happy with that leech :)

---

### Post by higi on 2007-02-10
That's not AIGLX.

Nvidia BETA drivers have their own implementation of accelerated indirect rendering (GLX_EXT_TEXTURE_FROM_BITMAP extension)

---

### Post by Marquis_de_Carabas on 2007-02-12
Thanks PriceChild, it's working great! 

Did you forget the ctrl-alt-backspace step though? It wouldn't work for me without that. 

Beryl seems much more polished than it did when I used it on Edgy though; great stuff.

---

### Post by leech on 2007-02-12
> **higi said:**
> That's not AIGLX.

Nvidia BETA drivers have their own implementation of accelerated indirect rendering (GLX_EXT_TEXTURE_FROM_BITMAP extension)

Isn't that pretty much what I said?  :D  

In essence AIGLX requires the extension of GLX_EXT_TEXTURE_FROM_BITMAP which the nVidia supports.  It is NOT beta anymore, there have been several releases since the initial beta which was version 9425 if I recall, then came 9426 which was the first non-beta driver with it, and now we have 9631 in Feisty and 9746 is the latest driver that supports the Geforce 8 series.

Everyone keeps referring it to a beta driver, which it no longer is.  ATI doesn't even have a driver out that supports this at all, but then again ATI has always been a "Linux, oh yeah... well maybe we should try to support it a little bit since so many are whining."  

Leech

---

### Post by PriceChild on 2007-02-13
> **Marquis_de_Carabas said:**
> Thanks PriceChild, it's working great! 

Did you forget the ctrl-alt-backspace step though? It wouldn't work for me without that. Good to hear and added that crucial step thanks :)

---

### Post by loopjeremyloop on 2007-02-13
Okay, so.... suppose, for a minute, that I already have Beryl working on my NVidia system (latitude d820 w/ quadro 120m) but the framerates pretty much suck (I average around 25-30)-

Would reinstalling with this built-in AIGLX work better?  How do I determine, first, what rendering method I actually AM using? 

If it would make sense to go with this built-in AIGLX, what would I need to remove and how would I go about it?  


/thanks for the handholding in advance.  I'm usually smarter than this.  :)  all these acronyms might have hit my saturation point...

---

### Post by PriceChild on 2007-02-13
Well what system are you currently using?

I'm always pretty scared about helping people who're asking about Beryl... ESPECIALLY when its in the Feisty subforum...

---

### Post by loopjeremyloop on 2007-02-13
> **PriceChild said:**
> Well what system are you currently using?

I'm always pretty scared about helping people who're asking about Beryl... ESPECIALLY when its in the Feisty subforum...


i used the method listed first at this wiki-
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method)


don't be nervous - this is not a critical laptop, and breaking it is totally okay.  :)  i use 2 systems for work, this laptop and a desktop still on edgy - so even if something dies on the lappy, I'm still fine.  let's have some fun, darnit!  

:D

---

### Post by PriceChild on 2007-02-13
I'm afraid that howto does basically the same as mine so I can't really help you further.

---

### Post by loopjeremyloop on 2007-02-13
> **PriceChild said:**
> I'm afraid that howto does basically the same as mine so I can't really help you further.

gotcha, totally fine.  thank you PriceChild.

---

### Post by hotani on 2007-02-15
Just to be different, I tried installing Beryl without opening a Terminal window. And... it actually worked! :)

I added the repository via synaptic (although I couldn't figure out a non-CLI way to add the key...), then installed beryl-manager. After that, I added a custom application launcher to the panel with "beryl-manager". When I clicked it, lo and behold, beryl took over. 

This is really nice to see, and hopefully we are not too far from the "click to enable desktop effects" button in the control center.

---

### Post by leech on 2007-02-15
To do it 100% graphically, what you need to do after adding the repository in Synaptic, you download the Key by going to [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) then you can save the file.  Under Synaptic you simply go under the Repositories, then there is a "Authentication" tab.  Click on that, then click on Import key.  Show it where the key file is (in this case it saves it as [email]root@lupine.me.uk.gpg[/email]).  

Then just click reload and your repository should be authenticated.  

Leech

---

### Post by naseem on 2007-02-15
hi, just installed feisty, with the 2.6.20-8-generic kernel, I followed the how to for beryl and latest nvidia but on restart xserver crash, is it a kernel bug or what happened?

---

### Post by Medieval_Creations on 2007-02-17
I was able to get everything installed on a new Feisty (AMD64) Install.  Plugged in my resolution and away I went with the installation of Beryl & nVidia-glx.  Everything installed fine and I got everything up and running, save for my Refresh Rate.  My monitors native resolution is 1440x900 with a Refresh rate of 60.  With the new nVidia drivers I have 2 choices 50 & 56.  This is a minor issue really because the only time I really even notice is when watching a Video/DVD.

Any thoughts as to what I'm over looking?

Here's my xorg.conf```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:55:59 PST 2006

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "LCM-19w4"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44 [GeForce 6200 TurboCache(TM)]"
    Monitor        "LCM-19w4"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"stylus" "SendCoreEvents"
	InputDevice	"cursor" "SendCoreEvents"
	InputDevice	"eraser" "SendCoreEvents"
EndSection

Section "Extensions"
	Option         "Composite" "Enable"
EndSection

Section "DRI"
	Mode 0666
EndSection

```

---

### Post by PriceChild on 2007-02-17
Go to the nvidia settings manager or type```
sudo nvidia-settings
```Into a terminal and edit the resolutions there then save it to the X configuration.... or do it manually, your choice ;)

---

### Post by mid_night gypsy on 2007-02-17
Midevil,
I was able to fix 50-56hz problem by adding in xorg (device) under nvidia this line.
Option         "DynamicTwinView" "FALSE" .You will need to restart x.
hope this helps,gypsy

---

### Post by merlyn on 2007-02-20
Thanks heaps for the howto, it worked flawlessly for me.

One question I have though and that is how to change the shadows.

I would prefer the 'stronger' shading to be on the bottom and to the right of the window, rather than on the top and to the right.

I've browsed through the beryl settings manager options, and for the life of me cannot find where to change this.

Perhaps I'm going blind, humour me.

---

### Post by Tichondrius on 2007-02-20
Worked great on my new Dell E1705 laptop with 17" WXGA (1440x900) display,  Nvidia 7900GS, Core2Duo T7200 2.0GHz (4MB L2), 2GB DDR2-667, 80GB HD. I'm running Feisty 64-bit and I already previously installed the nvidia-glx drivers but I still needed to run the nvidia-xconfig command in this howto to set the special attributes for AIGLX.

Beryl is very nice, seems more impressive than Compiz which I used previously (on a different machine).

One important question - how do you get the focus to follow the mouse ? couldn't find the setting for it, and I cant live without it (even in windows using powertoys/xmouse. btw, vista still doesnt support it).

---

### Post by PriceChild on 2007-02-20
> **merlyn said:**
> Thanks heaps for the howto, it worked flawlessly for me.

One question I have though and that is how to change the shadows.

I would prefer the 'stronger' shading to be on the bottom and to the right of the window, rather than on the top and to the right.

I've browsed through the beryl settings manager options, and for the life of me cannot find where to change this.

Perhaps I'm going blind, humour me.You'll need to edit the theme in emerald's theme manager.

---

### Post by mundano on 2007-02-20
Hi... 

I have followed every step in the howto, but I always have this error when I try to start X..

[[IMG]http://img399.imageshack.us/img399/3272/nvao2.th.jpg[/IMG]](http://img399.imageshack.us/my.php?image=nvao2.jpg)

Can anyone help me?


Ia have an GeForce 440MX, and except the beryl repo I don't have any unofficial repositories..


EDIT: case solved... I have tried everything but the nvidia drivers from the repositories don't work for me... I don't know why... 

I instaled the oficial nvidia driver and now everything works fine...

---

### Post by goldenatom on 2007-02-20
Worked out just fine for me. I was sort of shocked at how easy it was compared to Edgy...

---

### Post by merlyn on 2007-02-21
> **PriceChild said:**
> You'll need to edit the theme in emerald's theme manager.

Cool, thanks for the tip, and thanks once again for the howto.

Cheers

---

### Post by blitze on 2007-02-21
Been running Beryl for a few few weeks now and it has proved to be very stable and usable.  Even after updates which has had Compiz breaking.

Kudos to the Beryl team for getting things more ironed out.  Now if we could only stop the bitching between them (more one sided but still it exists). :KS 
(Not that I use KDE either but I like the smiley star).  :lol:

---

### Post by TheMono on 2007-02-21
> **mundano said:**
> Hi... 

I have followed every step in the howto, but I always have this error when I try to start X..

[[IMG]http://img399.imageshack.us/img399/3272/nvao2.th.jpg[/IMG]](http://img399.imageshack.us/my.php?image=nvao2.jpg)

Can anyone help me?


Ia have an GeForce 440MX, and except the beryl repo I don't have any unofficial repositories..


EDIT: case solved... I have tried everything but the nvidia drivers from the repositories don't work for me... I don't know why... 

I instaled the oficial nvidia driver and now everything works fine...


You did have linux-restricted-modules installed, right?

---

### Post by Milamber_Cubed on 2007-02-23
Hi Guys,

Just did a fresh install of Herd 4 and then followed this guide straight through.

Initiailly things looked good - no error messages, Nvidia logo appeared on screen (screen seemed a bit blurrier, but anyway). Got to installing Beryl/Emerald and after starting them up, all windows/panels/menus etc became unresponsive.

I can move windows that are open, but not interact with their contents in any way and can't open any new windows - system/applications menus don't pop up. I can, however roate the cube with either keyboard or mouse shortcuts, which is really odd. The only way I can break out of this is to switch to tty1 and "killall beryl". After switching back, metacity is in full force and everything is working again.

I would love for there to be a solution to this.... Any ideas?

Nvidia 6600GT APG 128MB, btw. Athlon 64 3500+ running in 32-bit mode with 1GB RAM - should be able to handle this really :D

---

### Post by PWill on 2007-02-23
> **Milamber_Cubed said:**
> Hi Guys,

Just did a fresh install of Herd 4 and then followed this guide straight through.

Initiailly things looked good - no error messages, Nvidia logo appeared on screen (screen seemed a bit blurrier, but anyway). Got to installing Beryl/Emerald and after starting them up, all windows/panels/menus etc became unresponsive.

I can move windows that are open, but not interact with their contents in any way and can't open any new windows - system/applications menus don't pop up. I can, however roate the cube with either keyboard or mouse shortcuts, which is really odd. The only way I can break out of this is to switch to tty1 and "killall beryl". After switching back, metacity is in full force and everything is working again.

I would love for there to be a solution to this.... Any ideas?

Nvidia 6600GT APG 128MB, btw. Athlon 64 3500+ running in 32-bit mode with 1GB RAM - should be able to handle this really :D
Same here. They are moving to X.Org 7.2. Wait for it...

---

### Post by Milamber_Cubed on 2007-02-23
> **xiamcitizen said:**
> Same here. They are moving to X.Org 7.2. Wait for it...

OMG... I knew i should have gone with edgy. :lolflag:   I just thought that Feisty was so close that there was little point. Everything else is working fine so far though, so I can't complain too much :) 


I really want to try out some of the latest effects that I saw in some videos. My laptop is running dapper so is unable to keep up. Ah well. i guess that by April most of this stuff should be sorted out.

I guess I will just have to be patient. :-k

---

### Post by TheMono on 2007-02-23
It better be sorted by April lol!

---

### Post by PriceChild on 2007-02-23
> **Milamber_Cubed said:**
> Hi Guys,

Just did a fresh install of Herd 4 and then followed this guide straight through.

Initiailly things looked good - no error messages, Nvidia logo appeared on screen (screen seemed a bit blurrier, but anyway). Got to installing Beryl/Emerald and after starting them up, all windows/panels/menus etc became unresponsive.

I can move windows that are open, but not interact with their contents in any way and can't open any new windows - system/applications menus don't pop up. I can, however roate the cube with either keyboard or mouse shortcuts, which is really odd. The only way I can break out of this is to switch to tty1 and "killall beryl". After switching back, metacity is in full force and everything is working again.

I would love for there to be a solution to this.... Any ideas?

Nvidia 6600GT APG 128MB, btw. Athlon 64 3500+ running in 32-bit mode with 1GB RAM - should be able to handle this really :D

> **xiamcitizen said:**
> Same here. They are moving to X.Org 7.2. Wait for it...There's a bit problem with amd64 feisty with beryl atm... We think its to do with the xorg7.2 transfer... be patient :)

---

### Post by Milamber_Cubed on 2007-02-23
> **PriceChild said:**
> There's a bit problem with amd64 feisty with beryl atm... We think its to do with the xorg7.2 transfer... be patient :)

I am not running the 64-bit kernel though :( Any ideas?

EDIT: I guess you could mean it's a CPU specific bug rather than a kernel one. Oh well... I will twiddle my thumbs and wait.

Or go for Edgy :D

---

### Post by FyreBrand on 2007-02-28
A little feedback update.  This is working perfectly for me with the latest update.  The install is very seamless and smooth now.

---

### Post by cow_racer on 2007-03-01
How come my title bars disappear?

---

### Post by feld on 2007-03-01
> **cow_racer said:**
> How come my title bars disappear?

Because you didnt set the rendering mode in Beryl to Copy. The nvidia driver requires this.

---

### Post by Matrik on 2007-03-02
Since the dist-upgrade to herd5 and the new desktop-effects/Compiz, beryl just stopped working.
If I try to launch beryl-manager, X crashes with the error: 
```

Mar  2 11:06:01 Matrik gdm[4822]: gdm_cleanup_children: child 15405 crashed of signal 6
Mar  2 11:06:01 Matrik gdm[4822]: gdm_cleanup_children: Slave crashed, killing its children

```

Same error if I try to enable compiz with the desktop-effects

It was working just fine with the  trevino svn version on xorg7.2

Has anyone an idea of what is going wrong?

---

### Post by ronacc on 2007-03-02
I am running the x86_64 version of ubuntu beryl had been working , except for occasional breakages during updates , until the update to 2.6.20-9 and xorg7.2 . I use the Nvidia - NVIDIA driver (9746) and after reinstalling the driver after the update to 2.6.20-9  starting beryl manager or selecting opengl/glx information in nvidia settings kills x instantly and dumps me back to the login screen. from my xlog it looks like the nvidia glx module is not being loaded but the nv-glx is. I have tried to reinstall the driver but cntrl-alt-bkspc just dumps me back at the login the same thing happens when I cntrl-alt-f1 and kill Xorg . how do I get x to stay dead long enough to reinstall the nvidia driver ? or would some other solution be better ? Note ! I saw the above about 7.2 and amd64 has that been resolved ? or is this it and I should just wait awhile longer?

---

### Post by ntetreau on 2007-03-02
I'm having crashing issues as well.  Everything was working fine up to a few days ago, even with xorg 7.2 installed.  Now, X crashes as soon as gnome starts is beryl-manager is enabled.  Tried with svn packages as well but made not difference.

Nic

---

### Post by DeeZiD on 2007-03-02
You have to reinstall the nvidia driver ;)
(sudo apt-get install nvidia-glx --reinstall)

regards Dennis

---

### Post by ronacc on 2007-03-02
deeZiD if that was pointed at me  I am NOT using nvidia-glx I am using NVIDIA-Linux-x86_64-1.0-9746-pkg2.run  . I need to reinstall that to see if reinstalling cures my problem . I cannot reinstall it because it must be run from console without x running and nomater how I kill x it just restarts and dumps me back at the login window.

---

### Post by FyreBrand on 2007-03-02
Did you try just shutting down and then starting at the tty?

If it won't let you shutdown then you can issue from the terminal:
```
sudo shutdown -h now
```

Just write all the steps you need to do for reinstalling the driver so you won't be stuck trying to remember the exact commands.

Also do you follow the nvidia site instructions to install or do you use [**tseliot's guide here**]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy").  It's for Edgy but I think the manual install instructions might still apply to Feisty.  Either way check his guide.  It might give you an idea of what to do or something you might have overlooked.

---

### Post by ronacc on 2007-03-02
I use the nvidia site instructions to install the driver , I think that the problem arose after the last update to 2.6.20-9 , at the time I installed the driver some of the kernal modules were heldback and the driver may have compiled the glx module incorrectly.  sudo shutdown -h now  halts the system as in power off . thanks for the try. I also tried changing the driver in my xorg.conf file to vesa but that just restarts the system with the vesa driver , mabye I'll try "nv" since I dont have the ubuntu nvidia driver installed mabye that will cause x to barf its cookies.

---

### Post by DeeZiD on 2007-03-02
My personal howto:

Switch to Console (ALT+CTRL+F1)
Log in
Use the following command to stop gdm and X (sudo /etc/init.d/gdm stop)
Then start the nvidia-installer (sudo sh NVIDIA<tab>)


regards Dennis

---

### Post by ronacc on 2007-03-02
Thanks DeeZiD that got it  , when installed the driver after the 20-9 update it must have compiled the modules against the 20-8 sources , I didnt realise I had to stop gdm independently , before I had just used ctrl-alt-backspace and then ctrl-alt-F1 , also neat trick that NVIDIA<tab> , saves a bunch of typing ;) beryl is back up and running now , next question where do I change the render mode to copy so I can get my title bars back ? I looked in beryl-settings but didnt see that .

---

### Post by DeeZiD on 2007-03-02
Open a terminal:```
sudo nvidia-xconfig --add-argb-glx-visuals
```

restart X

---

### Post by ronacc on 2007-03-02
thanks again

---

### Post by DeeZiD on 2007-03-02
Copy is much slower than Texture From Pixmap. 
Argb-glx-visuals fix the problem which the nvidia driver has.
Copy would only be necessary if your card did not have enough memory.


regards Dennis

---

### Post by VuDu on 2007-03-02
Hi there everyone!

Thanks for the HowTo's, I finally managed to make my X start :) I reinstall the restricted-modules and nvidia-glx but it didn't work, so I tried installing the drivers from the nvidia page and it WORKED!!! :D
Now everything is working almost flawlessly... almost because I found that Xorg still "eats" a lot of processor time when I'm running on AC power. When I change to the battery power, when I'm idle the processor stays below 5%, when I scroll Firefox's pages it stays below 50%. 
As soon as I plug the cable, the idle % jumps to 30%, scrolling makes it go to 100% and I even feel some lag when typing on a terminal and on GkrellM I can see that most of processor % is system time, not user time and top claims it's Xorg that's devouring it.

Does anyone have any clue on what may be the problem and how to fix it?

---

### Post by FyreBrand on 2007-03-02
> **DeeZiD said:**
> Copy is much slower than Texture From Pixmap. 
Argb-glx-visuals fix the problem which the nvidia driver has.
Copy would only be necessary if your card did not have enough memory.


regards DennisThanks DeeZiD.  I never knew what adding argb-glx-visuals did only that it is needed.

---

### Post by maniacmusician on 2007-03-03
> **FyreBrand said:**
> Thanks DeeZiD.  I never knew what adding argb-glx-visuals did only that it is needed.
When I used edgy, I used Trevino's repos for Beryl. After moving to feisty, I've noticed that this version does not have as many plugins, even when using beryl-plugins-unsupported.

Is this because it's not an SVN snapshot? Are there even any existing SVN snapshot repos for Feisty?

---

### Post by hanzomon4 on 2007-03-03
I use the edgy svn repos in feisty....

---

### Post by maniacmusician on 2007-03-03
> **hanzomon4 said:**
> I use the edgy svn repos in feisty....
...you can do that? Trevino's edgy repos, on Feisty?

No package conflicts or big screw ups? If someone else can confirm this, I'll definitely be a little happier.

---

### Post by PriceChild on 2007-03-04
> **maniacmusician said:**
> ...you can do that? Trevino's edgy repos, on Feisty?

No package conflicts or big screw ups? If someone else can confirm this, I'll definitely be a little happier.I really REALLY don't recommend using packages for edgy in feisty or vica verca... They're called "edgy" packages for a reason :)

If you really want to, then uninstall all debs, svn the beryl source and build it yourself :) Its not very hard once you have all the dependencies installed which can be automated with apt.

Pricey

---

### Post by Eddie Hung on 2007-03-04
> **maniacmusician said:**
> ...you can do that? Trevino's edgy repos, on Feisty?

No package conflicts or big screw ups? If someone else can confirm this, I'll definitely be a little happier.

I'm doing exactly that, and it works fine for me!

(Except maybe heliodor, the gnome window decorator - but you can use Emerald instead)

Eddie

---

### Post by RandomJoe on 2007-03-04
Oh my...  What a fun way to kill a Sunday morning! :)  I just got Feisty up and running on another machine, then Beryl.  The HOWTO works nicely!  Then I just sat there playing with effects for a few hours... :rolleyes:

It's also fun to see the 3GHz CPU scaled down to a mere 750 MHz even while playing around with all those effects! :cool:

The only note I might make, that may be causing some people grief, is that loading the nvidia driver caused apt to pull in the 386 kernel, which of course meant I lost SMP.  After some digging around in Synaptic, I found the linux-generic package was NOT selected.  Selecting that brought in all the modules needed to make it work with the 'generic' kernel.  I would have thought that package should already be installed, since that's the default kernel?

I did have one major frustration that I haven't resolved - I originally tried to use one of my Dell laptops that has an nVidia GPU in it.  It has been a solid performer with previous versions of the nVidia driver, but as soon as I loaded the driver this time, nothing.  At the point X starts, the display just turns off completely - no backlight, nothing.  I can Ctrl-Alt-Fx to get to a console login, and if I switch back to X the backlight goes off again.  I even commented out the new/unusual lines in xorg.conf so it's just like the config I usually use on that machine, same effect.

I'm hoping this isn't what I suspect - has nVidia dropped a bunch of "older" cards from the latest driver again?  It'd be fun to load Beryl up and show it off to friends and coworkers...

---

### Post by PriceChild on 2007-03-04
> **RandomJoe said:**
> I'm hoping this isn't what I suspect - has nVidia dropped a bunch of "older" cards from the latest driver again?  It'd be fun to load Beryl up and show it off to friends and coworkers...Yes many cards were dropped.

Try installing the 9631 driver from nvidia.com instead.

---

### Post by FyreBrand on 2007-03-04
> **PriceChild said:**
> Yes many cards were dropped.

Try installing the 9631 driver from nvidia.com instead.9631 is what is in the restricted repository right now.  Is it different than the 9631 that's on the nvidia site?

And just a bit of feedback after trying a clean install from herd 5 (kubuntu).  The guide still works great in that beryl gets up and running just fine.  The only problem I had was with default settings in xorg.conf.  I had to do a little manual wrangling to get it to default to the right resolution and refresh rate.

---

### Post by PriceChild on 2007-03-04
The 9*** driver should work with the same cards as 8***... I'm confused :)

Sorry I forgot which guide I was posting in (the edgy guide installs 9746 which dropped cards)

---

### Post by Mr_J_ on 2007-03-04
I can't seem to install beryl.
Up to that it's all fine.

Just states a few dependencies and warns they won't be installed...

---

### Post by FyreBrand on 2007-03-04
> **PriceChild said:**
> The 9*** driver should work with the same cards as 8***... I'm confused :)

Sorry I forgot which guide I was posting in (the edgy guide installs 9746 which dropped cards)Haha.  That's okay.  I'm just enough of a newbie that I wanted to make sure I wasn't confused.

Mr-J:  Post your errors and make sure you followed the guide in the first post very carefully.  Common problems with dependencies could have to do with not having the proper repositories enabled.  You need to post more specific information though or no one can help you.

---

### Post by Nirro on 2007-03-20
If I have the defaulted compiz already up and running, and I want to replace to beryl, 
do I need to uninstall compiz first ? 
otherwise how to switch between them ?

Thanks.

---

### Post by rsambuca on 2007-03-20
> **Nirro said:**
> If I have the defaulted compiz already up and running, and I want to replace to beryl, 
do I need to uninstall compiz first ? 
otherwise how to switch between them ?

Thanks.

In the Beryl Manager, you can just select between Beryl, Metacity, and Compiz.

---

### Post by Nirro on 2007-03-20
> **rsambuca said:**
> In the Beryl Manager, you can just select between Beryl, Metacity, and Compiz.
Thanks.

I think that this should be stated in the guide as well (first post).

---

### Post by m.musashi on 2007-03-26
Thanks again for doing a how to PriceChild. It seems to be working except that I don't have any window decorations. I can open the emerald theme manager but I just don't have any window borders. I also don't have the gem in the notification area so I can't actually check or try to reload emerald. Any suggestions?

---

### Post by FyreBrand on 2007-03-26
> **m.musashi said:**
> Thanks again for doing a how to PriceChild. It seems to be working except that I don't have any window decorations. I can open the emerald theme manager but I just don't have any window borders. I also don't have the gem in the notification area so I can't actually check or try to reload emerald. Any suggestions?What kind of video card do you use m.musashi? I know nvidia but what model version?  Also when you switch emerald themes does anything happen?  The green emerald doesn't show in the task manager, but the red emerald should.  How are you starting beryl?  Also is this Gnome or KDE?

---

### Post by m.musashi on 2007-03-27
I am running gnome. The card is a 7600 gs. If I switch emerald themes nothing happens. In edgy, I had the red emerald in the task manager but nothing shows up in feisty. I tried to launch it by typing "beryl-manager" in a run box (alt-f2) but I got an error about it not being installed. If instead I just type "beryl" in the run box it loads. I can spin the cube and such and my windows are wobbly but no emerald.

I tried using different methods to install the nvidia driver thinking maybe that was the problem but now I just have a broken X. I thought it was odd that "beryl-manager" didn't cause beryl to load but thought maybe it was a chance since "beryl" worked. If I try to reinstall it just says that it's the newest version.

Thanks. If you have any suggestions I'll try. I still have edgy on this box so I'm not too worried about messing things up.

---

### Post by PRGUY85 on 2007-03-27
Im having the usual problem where the Nvidia driver doesn't match with the kernel.  I can start the computer fine with the regular"nv" driver but not with the "nvidia" one.  Also, I don't know if I have the official Nvidia drivers installed on my laptop.  Could that be the problem: the old nvidia official 9631 drivers interferring with the most recent nvidia-glx drivers on the repos?

---

### Post by merlyn on 2007-03-27
Hi all,

I've recently taken the plunge and dist-upgraded my stable desktop to fiesty, (which I've been running fiesty on a 'test' partition for some time now).

The oddest thing occurred when installing Beryl, I followed the install steps provided by Price Child and it didn't want to play.

This is despite the fact that the process worked perfectly on my 'test' install a number of weeks back, go figure.

If anybody else finds themselves in a similar situation [this]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia#The_123_NoFile_Automatic_Installation_Method") install guide on the Beryl site may help, it did me.

---

### Post by pylorns on 2007-03-27
holy crap, it worked - after 2 reinstalls since I hosed my nvidia drivers, simply installing the restricted instead of the ones from nvidia's website and following this - but you left out the install of beryl-manager - at least if it was a dependency it didn't auto download...

sudo apt-get install beryl-manager

---

### Post by FyreBrand on 2007-03-28
> **m.musashi said:**
> I am running gnome. The card is a 7600 gs. If I switch emerald themes nothing happens. In edgy, I had the red emerald in the task manager but nothing shows up in feisty. I tried to launch it by typing "beryl-manager" in a run box (alt-f2) but I got an error about it not being installed. If instead I just type "beryl" in the run box it loads. I can spin the cube and such and my windows are wobbly but no emerald.

I tried using different methods to install the nvidia driver thinking maybe that was the problem but now I just have a broken X. I thought it was odd that "beryl-manager" didn't cause beryl to load but thought maybe it was a chance since "beryl" worked. If I try to reinstall it just says that it's the newest version.

Thanks. If you have any suggestions I'll try. I still have edgy on this box so I'm not too worried about messing things up.Make sure your default color depth is 24.  That's kind of obvious I know, but it's always good to recheck the little things.

When you installed and configured the restricted nvidia driver did you use the --add-arg-glx-visuals switch as follows:
```
sudo nvidia-xconfig --composite --add-arg-glx-visuals
```
or you can add this to the "Device" section in your xorg.conf file
```
Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 GT]"
    Driver         "nvidia"
    Option "AddARGBGLXVisuals" "True"
EndSection
```

There are a few other things that could be set in xorg.conf like triple buffering and the no root clipping switch, but I'm not too sure when those are applicable.  There are several threads on this problem here in the beryl forums: [**Beryl Forums**]("http://forum.beryl-project.org/").

---

### Post by PriceChild on 2007-03-28
> **pylorns said:**
> holy crap, it worked - after 2 reinstalls since I hosed my nvidia drivers, simply installing the restricted instead of the ones from nvidia's website and following this - but you left out the install of beryl-manager - at least if it was a dependency it didn't auto download...

sudo apt-get install beryl-managerWhoops will fix that :)

> **FyreBrand said:**
> There are a few other things that could be set in xorg.conf like triple buffering and the no root clipping switch, but I'm not too sure when those are applicable.  There are several threads on this problem here in the beryl forums: [**Beryl Forums**]("http://forum.beryl-project.org/").Tripple buffering isn't good and will cause adverse performance.

---

### Post by m.musashi on 2007-03-28
> **FyreBrand said:**
> Make sure your default color depth is 24.  That's kind of obvious I know, but it's always good to recheck the little things.

When you installed and configured the restricted nvidia driver did you use the --add-arg-glx-visuals switch as follows:
```
sudo nvidia-xconfig --composite --add-arg-glx-visuals
```
or you can add this to the "Device" section in your xorg.conf file
```
Section "Device"
    Identifier     "nVidia Corporation NV40 [GeForce 6800 GT]"
    Driver         "nvidia"
    Option "AddARGBGLXVisuals" "True"
EndSection
```
Thanks for the help.

Yes, default depth is 24.

I ran the code as is on the first page. I looks a tad different. Also the added option shows up in the screen section and not the device section. I can manually edit that if it's wrong. However, could that cause beryl-manager to not load? It does seem to be working (spinny cube and all) but no emerald and no gem on the panel.

---

### Post by FyreBrand on 2007-03-28
> **PriceChild said:**
> Whoops will fix that :)

**Tripple buffering isn't good** and will cause adverse performance.Thanks for clarifying that.  I I should have checked that option out better before recommending it.  Sorry.  I won't recommend it again in the future.

> **m.musashi said:**
> Thanks for the help.

Yes, default depth is 24.

I ran the code as is on the first page. I looks a tad different. Also the added option shows up in the screen section and not the device section. I can manually edit that if it's wrong. However, could that cause beryl-manager to not load? It does seem to be working (spinny cube and all) but no emerald and no gem on the panel.I'm not sure if it matters if the add-argb-glx-visuals is in screen or device.  I've always had it and seen it in device, but I use KDE and maybe it's different for that.  I'm not knowledgeable enough to know for sure.  It shouldn't hurt to check it out and see if it does make a difference.  Just comment it out in the screen section and copy it into the device section and see

Beryl doesn't pull in beryl-manager so check and make sure that is installed and not just beryl.

---

### Post by PriceChild on 2007-03-29
> **FyreBrand said:**
> I'm not sure if it matters if the add-argb-glx-visuals is in screen or device.  I've always had it and seen it in device, but I use KDE and maybe it's different for that.  I'm not knowledgeable enough to know for sure.  It shouldn't hurt to check it out and see if it does make a difference.  Just comment it out in the screen section and copy it into the device section and seeargb glx visuals is a valid option in both device and screen :)

---

### Post by FyreBrand on 2007-03-31
> **PriceChild said:**
> argb glx visuals is a valid option in both device and screen :)
Thanks again.  You are the mod!  The beryl-mod even :)

---

### Post by PriceChild on 2007-03-31
> **FyreBrand said:**
> Thanks again.  You are the mod!  The beryl-mod even :)Wooo go team!

---

### Post by sgtkwol on 2007-03-31
Ok, after plenty of  ](*,) I finally have it.  I upgraded from edgy to feisty.  Installed the restricted drivers from the easy menu.  Then, I made about every change I could to my xorg.conf.  I will post the the sections that I changed and see if it helps anybody.  I got these changes from too many sources to name.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
        Option         "AIGLX" "true"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "dri"
    Load           "vbe"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Driver         "nvidia"
    Option "XAANoOffscreenPixmaps"
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Monitor        "SVA 9005B"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
"note this is right before all the color and resolution options"

Section "Extensions"
    Option         "Composite" "enable"
    Option         "RENDER" "Enable"
EndSection

Section "DRI"
Mode 0666
EndSection

Hope this helps somebody!!!    Now I gotta back this up in email just in case. :biggrin:

---

### Post by rsambuca on 2007-03-31
> **sgtkwol said:**
> Ok, after plenty of  ](*,) I finally have it.  I upgraded from edgy to feisty.  Installed the restricted drivers from the easy menu.  Then, I made about every change I could to my xorg.conf.  I will post the the sections that I changed and see if it helps anybody.  I got these changes from too many sources to name.

To be honest, I am surprised that xorg layout actually works, but hey, if it does, great!

---

### Post by dgrafix on 2007-04-02
Looks good, got a virgin fiesty install, gonna try it :)

Will this work with GEforce4MMX 8xAGP? (it still has a way to go before added to legacy, i checked @nv)

Also, how do i do this
  "As far as i understand, you MUST remove all existing xgl/aiglx from your system for this method."

Because this is a virgin install, it will be a nice testbed. I gave up trying beryl on my dented & deranged (by me :)) dapper drake installation (he was getting old and the feathers were starting to fall out)

---

### Post by PriceChild on 2007-04-03
> **dgrafix said:**
> Will this work with GEforce4MMX 8xAGP? (it still has a way to go before added to legacy, i checked @nv)Yes.
> **dgrafix said:**
> 
Also, how do i do this
  "As far as i understand, you MUST remove all existing xgl/aiglx from your system for this method."If you haven't installed any yourself (due to it being a fresh install) just ignore that and follow instructions :)

---

### Post by packjamNL on 2007-04-06
[QUOTE= I hope this has worked :) If it doesn't then preferably try and get help in the IRC channel first: #ubuntu-effects on irc.freenode.net If your problem gets fixed, then post it below and i'll add it to this main post if important :)[/QUOTE]

Worked *fine* for me on my FFawn x86_64 version, only I had to choose a "window manager" ofcourse, wich is beryl for me
I want to "s-vhs" my nVidia 7600-GS to my TV wich has a s-vhs option too, the nVidia driver from the nVidia.com site has the settings to config a TV to the card as 0-1.
With the script I used is it still possible to have those settings because I can't find an nVidia icon in the menu.

---

### Post by slayerboy on 2007-04-09
PriceChild,  THANK YOU for this!

I decided to be stupid and try Fiesty today.  So far, everything seems to work fine for me.  Then I decided to be even more of a dolt and try to get Beryl running.  After about 4 hours of almost reinstalling a 2nd time, I came across sheer genius on my part that kinda wipes out the stupidity and then kinda makes it 100% even more stupid.

Here's what I did.

I installed the restricted-modules stuff for my Nvidia Geforce4 MX4000.  (NOTE:  to anyone with this model, NONE of the drivers in restricted-modules like this card it seems)  First I couldn't get my resolution above 800x600, even when it was manually edited in xorg.conf that I wanted 1280x960 (my LCD's native).  I tried uninstalling and reinstalling the restricted modules for a couple of hours with no luck, most of the time only being able to get X going with the NV driver.  Once I finally got the Nvidia drivers to work and tried installing Beryl, the commands in the OP didn't work with the legacy driver.  Obviously, the nvidia-glx driver didn't work at all, but at least with the nvidia-glx-legacy I could get it to start with the nvidia driver.  And of course the code in the OP to set the options didn't work!:lolflag:

So I decide to get the driver directly from NVidia, going for the 96xx version because I know this works on my card.  I installed it, it configured everything, ran the instructions according to what was in the OP.  After several times of discovering what headers and dev libraries I needed and installing them, I finally got it to install.

Then, of course, I got created with the mismatched driver version in the kernel error that prevented x from starting.  I made sure I removed the nvidia-glx-legacy drivers so that wasn't a problem.  I remembered that in order to prevent breakage in kernel updates, linux-restricted-modules needed to stay installed.  As  a last ditch effort, I removed this, and whaddya know?  I got into X with the 96xx Nvidia driver!  I then continued on with the rest of the instructions in the OP.

Needless to say, I've never been more impressed with Beryl.  I love the Flame effect!  Explode was nice when the windows closed but it took too much time.:KS

Ok, so now that I got that all going and let everyone know what I did to get this working, I'm assuming that when there's a kernel update, I just need to rerun the Nvidia installer script that I downloaded, but not allow it to modify my xorg.conf, correct?

Also, I'm noticing that for the most part speed isn't all that much affected except when I'm playing music in XMMS.  When I'm in firefox, the music skips a lot until a page stops loading then it's fine.  I have 1GB RAM and 2GB swap.  I haven't had the chance to see if this does the same thing in another media player or with movies.

Other than the minor issue of skipping music, and the driver issues, Fiesty is awesome!

Again, thanks PriceChild!

---

### Post by MoLE on 2007-04-11
> **slayerboy said:**
> 
Ok, so now that I got that all going and let everyone know what I did to get this working, I'm assuming that when there's a kernel update, I just need to rerun the Nvidia installer script that I downloaded, but not allow it to modify my xorg.conf, correct?


You might find tseliot's [envy script]("http://albertomilone.com/") very useful for automating the process, once he has updated it for feisty.

I noticed the latest kernel update from today split out 3 versions of the nvidia restricted driver, rather than the two previously available.

HTHs

---

### Post by FyreBrand on 2007-04-11
> **MoLE said:**
> You might find tseliot's [envy script]("http://albertomilone.com/") very useful for automating the process, once he has updated it for feisty.

I noticed the latest kernel update from today split out 3 versions of the nvidia restricted driver, rather than the two previously available.

HTHsHmm, that's interesting and a bit confusing.  The driver description using 'aptitude show' indicates that nvidia-glx-config should be used to enable the drivers, but it has no man page.  The nvidia-xconfig still has the man page.

I'm curious to try it out.  Here it goes.

By the way nvidia-glx is ver. 9631, nvidia-glx-new is 9755.

---

### Post by slayerboy on 2007-04-11
> **FyreBrand said:**
> Hmm, that's interesting and a bit confusing.  The driver description using 'aptitude show' indicates that nvidia-glx-config should be used to enable the drivers, but it has no man page.  The nvidia-xconfig still has the man page.

I'm curious to try it out.  Here it goes.

By the way nvidia-glx is ver. 9631, nvidia-glx-new is 9755.

Ok, so now the nvidia-glx is scaled back to the 9631?  alrighty then.  Once Fiesty gets released I try it with the nvidia-glx, right now things are working great.  When the LiveCD comes out , I'll make a fresh install just for fun.  Heck it doesn't take that long anyways..lol.

---

### Post by FyreBrand on 2007-04-11
I installed the nvidia-glx-new package and it works fine.  I had to twiddle with the xorg.conf file a bit, but nothing crazy.

---

### Post by Applegeek on 2007-04-16
I got Feisty to install flawlessly on my Gigabyte M61PM-S2 Mobo (AMD64, 4200), it found the integrated sound card and NIC without any problem at all (this was a problem for this Mobo with Edgy) and everything seems stable and flawless.  I ran all updates and everything still fine.

Then I installed the 9755 (AMD64) driver for nVidia (I'm using a 7100 card).  Great, everything still working.

Then I installed Beryl/beryl-manager/emerald-themes 0.2.1....  OK, the eye candy is now working, the cube is rotating nicely and the pages burn up.  Cool!

I've got cube, animations turned on.  Blur is turned OFF.

The only issue I'm having is if I go to a console (Ctrl-Alt-Fx) and then try to jump back to the gui, all I get is black screen - the cursor is there and alive, just nothing behind it.  If I try to jump back to a console, system crashes hard.  I can't ctrl-alt-BS, or anything.  Reset button time.

Any clues??

---

### Post by slayerboy on 2007-04-17
> **Applegeek said:**
> I got Feisty to install flawlessly on my Gigabyte M61PM-S2 Mobo (AMD64, 4200), it found the integrated sound card and NIC without any problem at all (this was a problem for this Mobo with Edgy) and everything seems stable and flawless.  I ran all updates and everything still fine.

Then I installed the 9755 (AMD64) driver for nVidia (I'm using a 7100 card).  Great, everything still working.

Then I installed Beryl/beryl-manager/emerald-themes 0.2.1....  OK, the eye candy is now working, the cube is rotating nicely and the pages burn up.  Cool!

I've got cube, animations turned on.  Blur is turned OFF.

The only issue I'm having is if I go to a console (Ctrl-Alt-Fx) and then try to jump back to the gui, all I get is black screen - the cursor is there and alive, just nothing behind it.  If I try to jump back to a console, system crashes hard.  I can't ctrl-alt-BS, or anything.  Reset button time.

Any clues??

same issue here.  I have decided to keep beryl turned off since I've upgraded to a newer video card and can play World of Warcraft again! (w00t!!!!) and Beryl doesnt play nicely with WoW sometimes.

Being that Beryl is still very early in development and still in the testing phases, it is remarkably stable for the most part.

---

### Post by PriceChild on 2007-04-22
*moved to desktop effects & customisation*

---

### Post by jbeiter on 2007-04-23
I upgraded to feisty from edgy over the weekend and installed beryl. I'm using a Dell 820 laptop and I loaded NVIDIA-Linux-x86-1.0-9746-pkg1.run.

Everything seems to be working fine, except for one annoying item. On every cube face, except for the "main" desktop, windows and menus leave a tracking phantom mess. If you move a window/term/app around on the screen, it leaves a mess of tracks behind that don't go away unless you flip the cube.

I'm a first time Beryl user but I'm assuming this is not working as designed. Any ideas or at least assurance this is not normal?

---

### Post by slayerboy on 2007-04-23
> **jbeiter said:**
> I upgraded to feisty from edgy over the weekend and installed beryl. I'm using a Dell 820 laptop and I loaded NVIDIA-Linux-x86-1.0-9746-pkg1.run.

Everything seems to be working fine, except for one annoying item. On every cube face, except for the "main" desktop, windows and menus leave a tracking phantom mess. If you move a window/term/app around on the screen, it leaves a mess of tracks behind that don't go away unless you flip the cube.

I'm a first time Beryl user but I'm assuming this is not working as designed. Any ideas or at least assurance this is not normal?

how much memory is dedicated to the graphics card, and how much total memory is installed?  Also, what's the model of the card?

---

### Post by Unoone on 2007-04-24
I'm getting decapitated window edges when I enable beryl or compiz. I'm running the latest Nvidia drivers.

Ouch! I made a mistake and selected the XGL composite manager in the settings. Now every time I start up Beryl Manager the screen freezes. Can someone tell me how to change the composite manager outside of the Beryl Manager? Thanks.

---

### Post by jbeiter on 2007-04-24
> **slayerboy said:**
> how much memory is dedicated to the graphics card, and how much total memory is installed?  Also, what's the model of the card?

I have a Quadro NVS 110M with 128MB. The system has 2GB of memory installed.

---

### Post by jbeiter on 2007-04-24
I unchecked "Desktop Manager support viewports" in the general settings for beryl-manager.. problem fixed.

---

### Post by klato on 2007-04-27
> **Unoone said:**
> I'm getting decapitated window edges when I enable beryl or compiz. I'm running the latest Nvidia drivers.

Ouch! I made a mistake and selected the XGL composite manager in the settings. Now every time I start up Beryl Manager the screen freezes. Can someone tell me how to change the composite manager outside of the Beryl Manager? Thanks.

Try editing the beryl settings file...I think it's in ~/.beryl/settings or maybe just .beryl is the file...

---

### Post by Unoone on 2007-04-27
> **klato said:**
> Try editing the beryl settings file...I think it's in ~/.beryl/settings or maybe just .beryl is the file...

I went out on the web and searched the Linux community and found the solution. First, a fresh update/install  of Ubuntu and Beryl. Following the tips in this thread, Nvidia users have to install the latest drivers. Then add the add-arg-glx-visuals to your xorg.conf -

```
sudo nvidia-xconfig --composite --add-arg-glx-visuals
```

To get things rolling or for any blunders while messing with the Beryl settings do -

```
beryl --force-aiglx
```

That's it!:popcorn:

---

### Post by dgrafix on 2007-04-28
do you mean you started compiz as the 'window manager?'
I did that too and it froze. What i did was log into a non X term and did:

(I think this location is correct do a locate first!)
sudo mv /usr/bin/compiz /usr/bin/compiz.backup

This seems to force beryl back to metacity and it all works again and you can reselect beryl (and removes the option from the menu :).

Dunno if it helps.

---

### Post by jack888 on 2007-04-29
for older nvidia cards, nvidia installer fails . From various posts I have seen 
older nvidia cards do compile under feisty.

You have to patch nvidia 8776 to get it to work. I followed  the  instructions on the following link.
[http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/](http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/)

But It was still trying to load the kernel module from /lib/modules/2.6.20-15-386/volatile

the one I compiled was put in /lib/modules/2.6.20-15-386/kernel/drivers/video/nvidia.ko
I did insmod /lib/modules/2.6.20-15-386/kernel/drivers/video/nvidia.ko

Now X and beryl both work.

Cheers :-)

---

### Post by PriceChild on 2007-04-30
> **Unoone said:**
> I went out on the web and searched the Linux community and found the solution. First, a fresh update/install  of Ubuntu and Beryl. Following the tips in this thread, Nvidia users have to install the latest drivers. Then add the add-arg-glx-visuals to your xorg.conf -

```
sudo nvidia-xconfig --composite --add-arg-glx-visuals
```To get things rolling or for any blunders while messing with the Beryl settings do -

```
beryl --force-aiglx
```That's it!:popcorn:This is NOT necessary.

Please use the restricted-manager which will handle the addition of the argbglxvisuals line.

---

### Post by marlinnhag on 2007-05-02
Well I guess to start this post off I am pretty much a newbie I have been using Linux for a few months but I was using SUSE and after I destroyed that computer (could have been me could have  just been that it was  a old computer) I just went and bought another computer. It is a 2.2GHz there is 1 GB of ram and it has a Nvidia Card with 128GB of Ram (not sure of the model. I decided to go with Ubuntu after the hell I experienced with SUSE.

SO I have ubuntu up and running (Fiesty newest version) I have been etremely happy with it and it has been very user friendly. SO I heard about this Beryl thing and decided that I had to have it (mainly for the water effect thing.)

After searching around on how to install it I kinda took a bunch of stuff from multiple sources on how to do it and went from there.  I believe I have the right Nvidia stuff installed I do have the restricted drivers installed but not sure if they are the right ones. 

I have the beryl manager installed and selected all the things I want but nothing has changed on the desktop or in the windows. Sometimes when I select something in the manager it just flashes the windows a bit and nothing changes.

I came to this last post and saw the code:
sudo nvidia-xconfig --composite --add-arg-glx-visuals

When I put that in this is the response I get...

nvidia-xconfig: unrecognized option: "--add-arg-glx-visuals"

SO I am assuming something is wrong... ANy help would be greatly appreciated...

---

### Post by C-King on 2007-05-02
It's --add-arg**b**-glx-visuals ;)

---

### Post by marlinnhag on 2007-05-02
Ok I put that in and it told me that it has wrote that to my xconf... Yet still when I click on the baryl desktop icon and select the window manager to baryl the screen flashes a bit and does a little dance and then nothing... when I go back to the window manager again it beryl still isnt selected.

If I go under preferences and select desktop effects I get this:

The composite extension is not available...

---

### Post by marlinnhag on 2007-05-03
Yeah so Im retarded... I got it to work... I guess restarting X would help huh?

---

### Post by falfool on 2007-05-03
I've just had a fresh install of Feisty Fawn, I'm running Intel Pentium 4 2.6 GHz, 512 DDR2, nVidia GeForce 5500 FX, and an 80 GB SATA.

Well, I followed your Howto, and everything has gone ever so smooth so far, I'm really amazed! When I run beryl-manager, everything looks just as anticipated, smooth, fast, and eye-candy. However, for some confusing reason, in a certain amount of time after running beryl, the system freezes in a weird manner. The mouse pointer could still be moved, but nothing else is responding, tried Ctrl-Alt-Backspace, tried tty1, turning off/on capslock or numlock keys, everything dead. And to top it off, XMMS is still playing music in the background, and I even waited for the next track to come, and it continued normally, while the system is .. frozen or something. 

I tried loading an older version of the kernel, nothing changed. I also doubt it is something with my nvidia drivers, since everything is working perfectly. The crash or freeze is mainly concerned with Beryl, I believe, anyone experienced something like this? Any ideas?

Thanks,
Ahmad

---

### Post by scottpledger on 2007-05-05
I can get neither Compiz nor Beryl running.  When I try using desktop-effects, i get
```
nvidia restricted driver is already enabled
/usr/bin/compiz.real: No RandR extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 333 error_code 180 request_code 156 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

And i get the same error with Beryl (RenderBadPicture)... any ideas?  I have a GeForce 7900 GS and a dual-head display with Xinerama.  I think that Xinerama might be what is messing it up, but I don't know for sure.

---

### Post by ShadowVlican on 2007-05-06
[COLOR="Red"]PriceChild[/COLOR], simple guide works great thanks!

also thanks to the developers who have worked on this to make it *ultra* easy to install! much improved from 6.10!

---

### Post by shanike on 2007-05-07
1) i have installed beryl but appearently i have no startup script (since beryl doesn't auto-load on login, i have to run beryl-manager manually).

2) when running beryl, is it possible to remove that ruby beryl icon from tray? or is it inevitable?

PS: beryl itself works great. what an amazing piece of work!

---

### Post by strumluff on 2007-05-08
> **shanike said:**
> 1) i have installed beryl but appearently i have no startup script (since beryl doesn't auto-load on login, i have to run beryl-manager manually).

2) when running beryl, is it possible to remove that ruby beryl icon from tray? or is it inevitable?

PS: beryl itself works great. what an amazing piece of work!

Yeah no probs sorting this one out.

If you go to System -> Preferences -> Sessions

Then add a New startup program. Give it a name i.e. "Beryl" and use 'beryl' as the command without the quotes. If your borders dont load when just beryl is executed then create another new startup program name it Emerald and the command 'emerald --replace' again without quotes. 

That sorts your starting up beryl without the ruby in the panel all in one go.

---

### Post by dj.spot on 2007-05-08
Hi
New here! New to ubuntu!
got a question... are there any known issues on installing beryl on 7.04?
i have 6.06 installed ... and i tried to install beryl....but cant install beacause dependencies :( 
will i have the same problem if i'll update to 7.04
can anybody help me out?
or at least is there any way to make it work on 6.06

---

### Post by shanike on 2007-05-08
thanks a lot, i added beryl-manager to my sessions, i just wasn't sure of the command at the time i was writing my post... meanwhile, i got used to the ruby icon ;)

---

### Post by DarkDancer on 2007-05-08
Nevermind.

---

### Post by PriceChild on 2007-05-10
dj.spot tell me what card you have (lspci | grep VGA) and I'll tell you what guide to follow :)

---

### Post by jogege on 2007-05-13
was able to get Beryl running on my FX 5200 card without any problems. After installing the Nvidia restricted drivers, I installed beryl-manager and it was all working smoothly. I had thought maybe the water effects and snow effects would not work, but they are all running without issues

---

### Post by homerj742 on 2007-05-15
Here is my story

1) I installed Beryl before enabling Nvidia restricted drivers, duh! I booted into a white screen. so from the terminal, I ran sudo apt-get remove beryl (yeah I know now), but it allowed me to boot into the desktop.

2) I enabled the restricted drivers.

3) Loaded up Synaptic Package manager, did a search for beryl, and removed any traces of beryl I could find.

My goal is to do a fresh install. My question is: am I doing this properly? Should I be checking into anything else? Please advise! any help would be appreciated!

---

### Post by sefs on 2007-05-17
These setups do not mention tweaking xorg.conf to make it work.  Is this an unnecessary step now?

---

### Post by PriceChild on 2007-05-17
> **sefs said:**
> These setups do not mention tweaking xorg.conf to make it work.  Is this an unnecessary step now?It is unnecessary, Feisty should do it itself :)

---

### Post by PriceChild on 2007-05-17
> **homerj742 said:**
> My goal is to do a fresh install. My question is: am I doing this properly? Should I be checking into anything else? Please advise! any help would be appreciated!Just install the restricted drivers and then apt-get beryl. :) Simple.

---

### Post by sefs on 2007-05-17
I've been using an old xorg.conf since breezy on a new install.  can you print your xorg.conf here so i can see.

And do you mean i can have a plain old vanilla xorg.con enabled for nvidia restricted drivers and that should work.

for instance i have a line in the bottome that disables composite.  Can i remove things like that from the conf file since it was not present in the vanilla version of it?

Thanks for the fast response.

actually let me post mine as well and someone can tell me what i can remove to simplyfy my xorg.conf as much as possible.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	# Load 	"GLcore"
	Load 	"ic2"
	Load	"bitmap"
	Load	"ddc"
	# Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	# Option	"UseFBDev"		"true"
        # set RenderAccel to true when vulnaribility is fixed after 10-18-2006
        Option          "RenderAccel"  		"false"  
     	Option          "TripleBuffer" 		"true"
	Option		"UseEDID" 		"false"
EndSection

Section "Monitor"
        Identifier      "AOpen F2707"
    	HorizSync       24.0-80.0
    	VertRefresh     49.0-75.0
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Monitor         "AOpen F2707"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes         	"1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes         	"1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes         	"1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes         	"1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes         	"1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes         	"1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
  Option "Composite" "Disable"
EndSection

```

> **PriceChild said:**
> It is unnecessary, Feisty should do it itself :)

---

### Post by sefs on 2007-05-17
btw now that beryl is remerging with compiz.  is this the end of the bling as we know it? :)

---

### Post by tckrockz on 2007-05-27
can we use Beryl with nvidia geforce 6200

---

### Post by PriceChild on 2007-05-27
yes

---

### Post by RockTonic3 on 2007-06-07
when I start beryl up, it takes away the title bar on all of my windows and i can't move them...  has anybody else had this problem?

---

### Post by PriceChild on 2007-06-07
Please make sure you start beryl with beryl-manager not beryl. pastebin your xorg.conf and an output of glxinfo & lspci please.

---

### Post by RockTonic3 on 2007-06-11
I have been starting it with beryl-manager.  Here's my xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation GE Force Go 7800 GTX"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation GE Force Go 7800 GTX"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```


output of glxinfo...

```
christopher@chris-voltaire:/etc/X11$ sudo glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 7800 GTX/PCI/SSE2
OpenGL version string: 2.1.0 NVIDIA 97.55
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x22 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x23 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x24 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x25 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x26 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x27 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x28 16 tc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x29 16 tc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x2a 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x2b 16 tc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x2c 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x2d 16 tc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x2e 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x2f 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x30 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x31 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x32 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x33 16 tc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x34 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x35 16 tc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x36 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 None
0x37 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x38 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 None
0x39 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3a 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 None
0x3b 16 dc  0 16  0 r  y  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3c 16 dc  0 16  0 r  .  .  5  6  5  0  4  0  0 16 16 16 16  0 0 None
0x3d 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x3e 16 dc  0 16  0 r  y  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x3f 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x40 16 dc  0 16  0 r  .  .  5  6  5  0  4 16  0 16 16 16 16  0 0 Ncon
0x41 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x42 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x43 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x44 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  0 16 16 16 16  0 0 Ncon
0x45 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x46 16 dc  0 16  0 r  y  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x47 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x48 16 dc  0 16  0 r  .  .  5  6  5  0  4 24  8 16 16 16 16  0 0 Ncon
0x10c 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


```


```
and output of lspci...

christopher@chris-voltaire:/etc/X11$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GE Force Go 7800 GTX (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

```

---

### Post by PriceChild on 2007-06-12
Please do```
gksudo gedit /etc/X11/xorg.conf
```and add the following line to section Device, or section Screen:
```
    Option         "AddARGBGLXVisuals" "True"
```Restart your X server and all should be good.

---

### Post by RockTonic3 on 2007-06-12
still doesn't work...  here's my xorg.conf again:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation GE Force Go 7800 GTX"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation GE Force Go 7800 GTX"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200"
    EndSubSection
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I tried adding it to the sections one at a time because i wasn't sure what you meant by or...  neither worked so i put it in both sections and it still didn't work.

---

### Post by RockTonic3 on 2007-06-12
ah got it to work.  This did the trick:

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

I found it here...  should have looked harder in the first place.  Thanks for the help anyway, apparently all i had to do was have the line you told me to add in a different place.

[https://help.ubuntu.com/community/BerylOnFeisty](https://help.ubuntu.com/community/BerylOnFeisty)

---

### Post by dgrafix on 2007-06-13
Has anyone else had a problem with beryl removal and missing desktop icons (you cannot even right click :( ) and my background picture is also missing but that comes back if i click on prefs>desktop background. but goes away again on next reboot 

cant get the icons back tho, ive tried configuration editor and everything i can think of.

---

### Post by c_martini on 2007-06-17
I followed the guide to install Beryl and Nvidia driver back in the guide for Edgy posting by PriceChild. This was a great guide but since then have upgraded to Kubuntu Feisty about a month back. I was able to get Beryl running without too much hassle but am a bit frustrated having to reinstall the Nvidia kernel mode driver everytime I update the Linux kernel. It has got to the point that I just skip updating the kernel because I don't want to go through the process of reinstalling the Nvidia driver at the console outside of KDE.

I only discovered this version of the guide for Feisty recently and I wasn't aware I could now use the nvidia-glx driver instead of the propietary one.

What I would like to know is: **What is the easiest way to get rid of the current way the Nvidia driver is installed for my system and then go to using the nvidia-glx driver. I really hate reinstalling the driver everytime I update the kernel. There must be an easier way to do this and still have 3d and functional Beryl...**

:confused:

---

### Post by C-King on 2007-06-18
The NVidia-installer has an uninstall option, just execute the installer with the '--help'-option to check.

---

### Post by c_martini on 2007-06-18
> **C-King said:**
> The NVidia-installer has an uninstall option, just execute the installer with the '--help'-option to check.

Thanks for the tip.. Almost plainly obvious :oops:
Had a look and the **--uninstall** switch does the deed...

Thanks again.

---

### Post by paulerickson on 2007-06-27
Okay, so I've done walkthroughs to get Beryl running on my Radeon All-in-Wonder card - great; and I've done walkthroughs to get Beryl running on my onboard Nvidia GeForce 6100 - dandy.  But I can't for the life of me get Beryl running on both screens!

If I use the "nv" driver, I can run on the Radeon screen fine, but I get nothing but a white screen and errors on the Nvidia screen.  Am I right that this is to be expected; that Beryl can't run on the "nv" driver?

Anyway, I installed the "nvidia" driver (by selecting "nvidia-glx" in Synaptic), and I get
```
paul@paul-desktop:~$ beryl --screen 1
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Root visual is not a GL visual
2 screens detected.
Currently we cannot guarantee that Beryl will work correctly with multiple X screens.
Using the --no-context-share command line option can help.
Please report any success to the beryl developer mailing list. The list can be found at lists.beryl-project.org

```
screen 1 is Nvidia, but it's the same with 0 - nothing happens.  If I run with --skip-tests, It'll run on the Nvidia screen, but just kill Metacity on the Radeon screen if I try running it.  Because the xserver is NVIDIA?  Can I do the nvidia driver and AIGLX?

How can I get both to cooperate?

---

### Post by Genecks on 2007-07-02
> **c_martini said:**
> Thanks for the tip.. Almost plainly obvious :oops:
Had a look and the **--uninstall** switch does the deed...

Thanks again.

I don't get it. What's the command for this? I'm using the old, glx form. I guess I'll have to use the beta, right?
How do I uninstall?

---

