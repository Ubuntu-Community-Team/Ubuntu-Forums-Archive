---
title: "Dual Monitor setting question., Can I get clone option working w/nvidia driver?"
date: 2010-03-11
forum: Desktop Environments
---

### Post by wizarddrummer on 2010-03-11
Hi,
I have a nvidia 6600gt agp card.
 In Windows this card has three modes of operation
 [COLOR=DarkGreen]1) **clone**(same display on both monitors)[/COLOR]
 [COLOR=DarkGreen]2) **span**(extended desktop)[/COLOR]
 [COLOR=DarkGreen]3) **dual view**(treats each display as a separate device)[/COLOR]
 I apologize in advance. This is not a simple question; nothing in my life is simple.
 
 I installed the latest nvidia drivers after Ubuntu installation.
 
 [COLOR=DimGray]NVIDIA Driver Version 185.18.36
X Server Version: 11.0
Vendor Version: 1.6.4 (10604000)[/COLOR]
 
When I went to change the setting for the clone option the only settings I had were:
 [COLOR=DarkGreen]1) Disabled [off][/COLOR]
 [COLOR=DarkGreen]2) Separate X screen (requires X restart) [dual view in windows][/COLOR]
 [COLOR=DarkGreen]3) TwinView [span in windows][/COLOR]
 
I got Separate X to work (not what I wanted); then I wanted to try TwinView.
 
 It would not reset. I fiddled with it ; then had problems with can't write to xorg.conf and / or xorg.conf.backup; can't create this or that file, etc.  
 
I could not get the TwinView to work. I was stuck in Separate X.
 
through this process I made backups of the xorg.conf and was either removing and then touching the file so the nvidia app could write to it or pasting stuff with gedit.
 
*someone needs to address that debacle; (nvidia? Ubuntu developers?) The nvidia utility should never have a permissions problem (don't know where the blame for that goes; if it needs to do something in su mode then it should ask for a passwd.)*
 
 Then I issued several different commands for reconfiguring the xserver:
 sudo dpkg-reconfigure -phigh xserver-xorg  
 sudo dpkg-reconfigure xserver-xorg
 (neither of which did anything; xorg.conf remained the same)
 I tried: sudo nvidia-xconfig
 (that didn't work)
 
 Finally I removed the NVIDIA driver with the System Administration Hardware Drivers utility.
 
I checked to see what change it made to the xorg.conf file. xorg.conf and all of my backups were gone. OK, no problem, they have nvidia info in them and there's no driver.
 
I issued the xserver reconfig cmds; still no xorg.conf.
 
So I reboot.
 
When I am presented with the log in screen I notice both monitors are displaying the same info.
 
 Now I have cloning which is exactly what I want. But, I have cloning without any graphics acceleration.  
 
 This is useless because I want to give a demo for why Ubuntu is better than Windows to some people here in Mexico who are in the computing dark ages. The non accelerated graphics can keep up with word processing, and spreadsheets but that will get old pretty fast if that's all I can demo without going to a single monitor. It is much easier to look my computer screen while I am doing the demo that is displayed on a HDTV that is facing away from me.
 
 Can I have cloning and graphics acceleration with this nvidia graphics card in Ubuntu?
 
 Any help will be appreciated.

regards,

---

### Post by keforex on 2010-03-11
It would be nice if you could post the contents of your xorg.conf file that is located on \etc\X11.

I have two 30" monitors (not twin mode) and I travel with the mouse and move windows around both with ease.

My xorg.conf follows - compare with yours. My card is 8800 GTX but I believe the parameters should work for both.

"Composite" is an important option, I don't know if it is related to your issue, though.

In order to edit the xorg.conf file you need to have root access. Open terminal, sudo gedit and open it.

If you want to save xorg.conf using the nVidia utility you have to also load it up as root - open terminal, sudo nvidia-settings

BTW you won't have any acceleration if you uninstalled the driver. Re-install and sudo nvidia-settings with the parameters you need. Log out, log back in and see if it works. Always make a backup copy of xorg.conf before tweaking. Good luck!


```
Section "Monitor"
	Identifier     "monitor1"
	VendorName     "Hewlett-Packard"
	ModelName      "HP LP3065 Wide LCD Monitor"
	HorizSync       98.0 - 100.0
	VertRefresh     59.0 - 60.0
EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "HP LP3065 Wide LCD Monitor"
	ModelName      "HP LP3065"
	HorizSync       49.3 - 98.5
	VertRefresh     60.0
EndSection

Section "Screen"
	Identifier     "screen1"
	Device         "device1"
	Monitor        "monitor1"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Videocard0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "TwinView" "1"
	Option         "TwinViewXineramaInfoOrder" "DFP-0"
	Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +2560+0"
EndSection

Section "Module"
	Load           "dbe" # Double-Buffering Extension
	Load           "v4l" # Video for Linux
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load           "glx" # 3D layer
EndSection

Section "Extensions"
	Option         "Composite"
EndSection

Section "ServerLayout"
	Identifier     "layout1"
	Screen      0  "Screen0" 0 0
EndSection

Section "Device"
	Identifier     "device1"
	Driver         "nvidia"
	VendorName     "nVidia Corporation"
	BoardName      "NVIDIA GeForce FX to GeForce 8800"
	Option         "DPMS"
	Option         "TwinViewOrientation" "Clone"
	Option         "ModeValidation" "NoWidthAlignmentCheck, NoDFPNativeResolutionCheck"
	Option         "AddARGBGLXVisuals"
	Option         "ExactModeTimingsDVI"
	Option         "TwinView"
EndSection

Section "Device"
	Identifier     "Videocard0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 8800 GTX"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
	Option         "allowmouseopenfail"
	Option         "Xinerama" "0"
EndSection
```

---

### Post by wizarddrummer on 2010-03-11
Thanks for your reply.

8800 GTX's; sigh ... I have two of the 768MB 8800GTX's collecting dust because my main rig has gastraphogous flabostinificusticinated lesions. In other words it's dead and I don't know what's wrong with it ... huge story for a different time and place.

I installed the driver and rebooted.

As expected my CLONE (both monitors showing the same info) feature was gone. 

I opened the Nvidia X Server Settings (I have to admit this configuration utility is one really crappy program; nvidia must not be fond of the linux community with that piece of s**t)

In the utility I changed the monitor resolution; changed the secondary monitor resolution; selected the TwinView option and pressed the Save to X configuration file and promptly got "Failed to parse existing X config file '/etc/X11/xorg.conf'!"
Yay! Here we are again with the tedious stuff.

back soon

---

### Post by wizarddrummer on 2010-03-11
OK, here's my xorg.conf file
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony SDM-HS95P"
    HorizSync       28.0 - 65.0
    VertRefresh     57.0 - 63.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1280x1024 +0+0, DFP-1: 1920x1080 +1280+0; DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

There is the latest .conf file

---

### Post by wizarddrummer on 2010-03-11
I'm going to rant a little; actually alot!

This nvidia x server settings module is the worst most pitiful monitor setup program i have ever seen since i started using computers 34 years ago.

My gaming rig died before i switched to Ubuntu so i never had the pleasure of using this amalgamated piece of crap when I was using XP and my twin 8800GTX's.

The nvidia interface in XP was stellar.

**[COLOR=Blue]Why do I keep getting these messages?[/COLOR]**

[COLOR=Red]Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.[/COLOR]

I removed the xorg.conf.backup so there would not be anything it its way when it went to make the backup.

Not once have I been able to perform the operations and (SAVE) the changes using the utility. I've had to had edit the .conf files each time.

I can understand having to do that in Unix System III or V but here in Ubuntu? Not blaming Ubuntu mind you, it's the less than stellar nvidia application.

My configuration file has much less information than your (keforex's) file.

Your file has these important differences; this is what I do not have in my .conf file; the extra monitor, screen, and most importantly, the extra device information.

```

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Hewlett-Packard"
    ModelName      "HP LP3065 Wide LCD Monitor"
    HorizSync       98.0 - 100.0
    VertRefresh     59.0 - 60.0
EndSection

Section "Screen"
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection

Section "Module"
    Load           "v4l" # Video for Linux
EndSection

Section "Extensions"
    Option         "Composite"
EndSection


[COLOR=Blue]Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "nVidia Corporation"
    BoardName      "NVIDIA GeForce FX to GeForce 8800"
    Option         "DPMS"
    [COLOR=Red]Option         "TwinViewOrientation" "Clone"[/COLOR]
    Option         "ModeValidation" "NoWidthAlignmentCheck, NoDFPNativeResolutionCheck"
    Option         "AddARGBGLXVisuals"
    Option         "ExactModeTimingsDVI"
    Option         "TwinView"
EndSection[/COLOR]

Section "Device"
    Option    "NoLogo"    "True"
EndSection

Section "ServerFlags"
    Option         "allowmouseopenfail"
EndSection

```Can I use any of that without screwing it all up?

---

### Post by Jean85 on 2010-03-12
Let the nVidia tools rewrite the xorg.conf and restart from the begginning.

To rewrite it use

sudo nvidia-xconfig

You will have a fresh xconf that is perfectly compatible with nvidia-settings, with no parse errors.

---

### Post by wizarddrummer on 2010-03-12
> **Jean85 said:**
> Let the nVidia tools rewrite the xorg.conf and restart from the begginning.

To rewrite it use

sudo nvidia-xconfig

You will have a fresh xconf that is perfectly compatible with nvidia-settings, with no parse errors.

Thanks very much for your reply, 

This is probably the 15th time I've done this during the course of this ordeal. 

Folks, I know your time is valuable.

I try to do as much research as I can _before_ I ask for help the first time or any other time. 

I try to perform as many different combinations of things in my effort to make something work.

When I ask for help I am out of ideas; things are not working as advertised; or there's a legit issue I'm unaware of.

That being said, will someone please explain to me what is going on here. 

There is SOMETHING :confused: I don't know what; that is NOT working as it supposed to be working. 

Is is permissions? Is it a faulty Nvidia driver app? A faulty driver? Is it Ubuntu? Is it the X11 server? I don't have any idea. 

I was a Unix super geek/guru in the early 80's through the mid 90's (yes I had one of the first linux installations) NOW, I'm a NOOB again. Many things have changed. 

**Here is the exact sequence of events that I have experienced many times.**

**1)**[COLOR=DarkSlateGray] *I issued the command in a terminal window (a previous post shows I issued this and other resetting/restoring commands).*[/COLOR]
[COLOR=DarkGreen]**[COLOR=Blue]sudo nvidia-xconfig[/COLOR]**

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'[/COLOR]

**2)** [COLOR=DarkSlateGray]*I closed the programs and did a shut down.*
[/COLOR] 
**3)** [COLOR=DarkSlateGray]*When I logged back in I changed the monitor setting from the default 1024x768 to 1280x1024*[/COLOR]

**4a)** [COLOR=DarkSlateGray]*I pressed Apply*[/COLOR]
[COLOR=DarkGreen]The screen went blank for a few seconds; came back with the new resolution.

[COLOR=Black]**4b)**[/COLOR] [COLOR=DarkSlateGray]*I pressed OK to accept that new resolution.*[/COLOR][/COLOR]

**5) **[COLOR=DarkSlateGray]*I pressed the "***Save to X Configuration File***"*[/COLOR] [COLOR=DarkSlateGray]*button.*[/COLOR]

**6)** [COLOR=DarkSlateGray]*In the "***Save X Configuration Panel***" I pressed the "***Save***" *[/COLOR][COLOR=DarkSlateGray]* button*[/COLOR][COLOR=DarkSlateGray]*. *[/COLOR][COLOR=Sienna]**Note**[/COLOR][COLOR=DarkSlateGray]:* It does not matter if  [ ] "***Merge with existing file**[I]" is checked or unchecked.
I immediately got this error message:

[/I][/COLOR] **[COLOR=Red]"Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."[/COLOR]**

Screenshot is provided.

I'm at a loss here folks. That should NOT be happening. Correct?

This video setup process should not be like going to the dentist.

In almost a decade of using XP I have set up dual, triple and quad monitors; cloned, extended, separate etc., at least 1,000 times for myself and clients. And it took only about 30 seconds to perform this very simple operation. I didn't have to use a terminal window or a anything else to make it work. Yet, in Ubuntu,  [COLOR=Black]I've spent the better part of two whole days struggling with this; so I am about give up on my demo.[/COLOR]

[COLOR=Navy][COLOR=Black]Folks, all I have wanted to do from the get-go is have:[/COLOR] ** two monitors display the same information, at the same time, with the ability to use the graphics card's: higher resolution and graphics acceleration.**[/COLOR]

This video card will do what I want it to do in XP; the question is will it do this in Ubuntu? Maybe Nvidia's driver is not capable of doing this. IT WORKS when there is NO DRIVER present :); but I get crappy performance.

My final two questions; unless someone has an idea:
1)** [COLOR=Sienna]Is it possible to have two monitors display the same... (see bold text above) with my Geforce 6600gt agp video card in Ubuntu?[/COLOR]**

2) **[COLOR=Sienna]If this IS possible, is there anyone that knows the exact or almost exact sequence of events I need to perform to make it work?[/COLOR]**

Thanks again for all of your help.

---

### Post by wizarddrummer on 2010-03-13
Hoping someone had some ideas...

---

### Post by keforex on 2010-03-13
Check the permissions on the old conf files.

Open terminal

sudo nautilus

navigate to the folder \etc\X11

right click on file you want to check and choose properties

click on permissions tab

Now:

If you are running nvidia-config as root (meaning you run sudo nvidia-config in a terminal) and all the permissions on all those conf files are set to root **AND** they are set as Read and write, you shouldn't have a problem.

If you want, just delete the old xorg.conf files (keep backup copies on another folder just in case you need them later for reference) and then run the config tool again. (all this as root, via terminal typing in there sudo nautilus)

The nvidia-config tool in root mode will update the current xorg.conf file and save the original as a back up copy.

---

### Post by keforex on 2010-03-13
BTW I triple boot here, Ubuntu, Vista and Linux Mint. For all linux boots I use the EXACT SAME xorg.conf. 

Different from Windows, linux is a lot more secure OS that applies and enforces permissions to edit files that belong to the system. This way end users will not tamper with the system and create havoc. Same philosophy applies to apple computers.

By reading your long post above it seems like you are confused with the sequence of events. Assuming you are able to boot into ubuntu and you can see the desktop even if it is only in one of the two screens, the sequence is pretty simple. Keep in mind that just as a user you won't be able to save these crucial system files (that's the linux security). You need to be operating as the "boss" or as "root".

1) Boot up, and get to the desktop

2) Open a terminal window

3) Type sudo nautilus and press enter (this means you are operating the software nautilus as the "boss" or "root" via the command sudo)

4) Go to the folder \etc\X11

5) Select all the files that say xorg.XXXX - right click on them, copy and paste it somewhere safe like \Documents

6) Go back to \etc\X11 and delete de xorg.conf BACKUP COPIES. Do not delete the original xorg.conf.

7) Right click on xorg.conf -> properties -> permissions and make sure all are set to "root" and "Read and Write". If not, correct them using the drop down menus on that screen.

8 ) Close nautilus

9) On the terminal, load the nvidia tool by typing sudo nvidia-settings (this means you are operating the software nvidia-settings as the "boss" or "root" via the command sudo)

10) Configure the tool as you wish. Twinview, resolution, etc... keep in mind that with two monitors you need to choose settings on each one of them.

11) Only AFTER you are done configuring you will press "Save to X Configuration File". The new xorg.conf is saved and a backup copy is created in \etc\X11.

12) Once done, exit the tool, exit the terminal and reboot. (or just log out and log in again).

13) Now that you are logged in again, you are just a user. If you need to tamper with the tool again, you have to do so using the sudo command in the terminal as explained above.

14) Enjoy.

---

### Post by galdren on 2010-03-14
a lot of your problems seem to be caused by not being able to save the new xorg config file. The problem is that you need to boot the nvidia settings util as root since it won't ask for your password when it needs to do stuff as root (I have the same bug).

To do that just go to terminal and type sudo nvidia-settings. it worked out for me.

adressing the loss of the clone option: as long as you are still in seperate X configuration you won't be able to clone. first try to save the new xorg in twinview and reboot. When that's done you won't have any trouble cloning (if everything else is working)

---

