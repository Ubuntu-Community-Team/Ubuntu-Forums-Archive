---
title: "[SOLVED] Please Help With Visual Effects!!!!"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by philidox on 2008-02-18
THIS DRIVING ME NUTS! Every time in enable visual effect other than "None" my whole gnome enviroment turns to complete dodo.  My mouse disappears, the borders on my windows dissappear, the graphics on my computer start looking like old school nintendo.  Please someone, anyone help me fix this problem!!!

---

### Post by chavanak on 2008-02-18
Which graphics card you are using? Type in" lspci | grep VGA" without quotes into a terminal window and give the output. Also  type in compiz in the terminal give the output!!!

---

### Post by philidox on 2008-02-18
Thank You!!! Here it is
user@user-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Unknown device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
05:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
user@user-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0295 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/home/user/.themes/c2/gtk-2.0/gtkrc:54: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop

If you want exact specifications of my video card please follow this link:
[http://www.newegg.com/product/product.aspx?Item=N82E16814143090](http://www.newegg.com/product/product.aspx?Item=N82E16814143090)

Just click on the specifications tab.  If you need anything else please let me know I get the responses to the forums as a text message on my phone so i'll know almost instantly and will responsed just as fast

---

### Post by chavanak on 2008-02-18
Are you able to use the other compiz options i mean extra or normal in appearence--> visual effects tab???

Which plugins are enabled in your ccsm

---

### Post by philidox on 2008-02-18
> **chavanak said:**
> Are you able to use the other compiz options i mean extra or normal in appearence--> visual effects tab???

Which plugins are enabled in your ccsm

Yes I have tried that along with GLDesktop and Advance Desktop Effect Setting(ccsm).  After being really frustrated I just started uninstalling stuff hoping I would resolve the issue hit me up with any possible solutions.  Thanx once again

---

### Post by chavanak on 2008-02-18
Glad i waas of some help!!!

---

### Post by philidox on 2008-02-18
NO NO NO, my issue has not been solved I just said what I was doing to try and fix it but it has not worked I need help please!!!

---

### Post by Kivech on 2008-02-18
Did you install xserver-xgl?

If you haven't, try that one, reboot and see how it goes.

You can install it with the synaptic package manager: System>Administration>Synaptic Package Manager

This is what fixed it for me, and it seems to me that in your case it's missing.

Good luck!

Kivech

---

### Post by chavanak on 2008-02-18
I guess you can try removing compiz and installing it again

---

### Post by erginemr on 2008-02-18
1. Did you install the binary driver for your NVidia card? You can check it from under:
System -> Administration -> Restricted Drivers Manager

2. What is the outcome of "glxinfo | grep direct"?

---

### Post by chavanak on 2008-02-18
Try envy. it will install nvidia drivers and also configure your system perfectly

---

### Post by snow_56767 on 2008-02-18
Have you installed the nvidia-legacy driver?
and do you have the kernel source installed?
 Driver ```
sudo apt-get install nvidia-glx-legacy
```
 Kernel Source ```
sudo apt-get install nvidia-legacy-kernel-source
```

---

### Post by philidox on 2008-02-19
Wow thats alot I'll try all of these ideas hopefully it will work

---

### Post by philidox on 2008-02-19
> **erginemr said:**
> 1. Did you install the binary driver for your NVidia card? You can check it from under:
System -> Administration -> Restricted Drivers Manager

2. What is the outcome of "glxinfo | grep direct"?

1. Yes I went to check it and it says in use, it reconizes the nvidia driver

2.user@user-desktop:~$ glxinfo | grep direct
direct rendering: Yes

Kivech:  I tried install the xserver-xgl and it made my gnome enviroment act wierd again but thx for the suggestion

---

### Post by philidox on 2008-02-19
> **chavanak said:**
> Try envy. it will install nvidia drivers and also configure your system perfectly

Installed Envy and every time I start the program it does nothing.  I tried using alt+f2, and I went thru Applications>>>Sound & Video>>Envy 24 Control.  Man what a drag

---

### Post by erginemr on 2008-02-19
> **philidox said:**
> 1. Yes I went to check it and it says in use, it reconizes the nvidia driver

2.user@user-desktop:~$ glxinfo | grep direct
direct rendering: Yes

Kivech:  I tried install the xserver-xgl and it made my gnome enviroment act wierd again but thx for the suggestion

Your above reply clearly indicates that the binary NVidia driver has been installed and your 3D (glx) extensions are in effect. There is no need for you any more to install it again via NVidia web site, Envy, etc.

At this stage, we can try two things:

1. Post your /etc/X11/xorg.conf here, so that I will check yous with mine and add missing lines if any for Compiz to work. You can use the following command to list the contents of this file, and then copy from it to your next post:
```
gedit /etc/X11/xorg.conf
```

2. I remember that there has been an update of Gutsy Compiz packages in the past couple of weeks. Perhaps the version you are using does not like your hardware and going through an update will resolve your problems. But for it to work, you have to enable **backports** repository. 
From Main Menu -> Admin. -> Synaptic -> Settings -> Repositories 
make sure that all options are as given in the attached screnshots. Then press **reload** from the Synaptic main toolbar to get the latest Compiz version.

---

### Post by philidox on 2008-02-20
Man I missed up big time.  I installed the nvidia driver suggest by snow and I forgot to backup my xorg.conf file and now I can't even load ubuntu.  The video is completely shot.  I had this problem when I first installed the nvidia 7950GT but I can remember where I got the fix for it.  It something I installed after the Section "DRI".  ARRGGHHH I just cant remember how to fix it.  It should be common amongst the linux community.  If you can help me get the xorg.conf for my graphics card after that i'll post my xorg.conf so I pick up where I last left off.  Just so you know everything looks fine until i get to the log in screen.  The grub screen, usplash all look like normal. The login screen is completely blank but I still hear the sound even after i log in so i know ubuntu running fine just the video card is not configured good. Thanx for the help.

---

### Post by bothebobo on 2008-02-20
Hey philidox
I feel for you. I was in the same situation before i gave up and now im detemined again. But i do have a smart code that resets your xorg to default which all graphix cards can handle. It saved my *** more than once
```

bo@VoltronCrew:~$ sudo dpkg-reconfigure -phigh xserver-xorg

```
I dont know what all those options do and i really dont care, but its true and tried. Write it down on a piece of paper and leave it in your desk, it comes in handy in stupid situations.

So you run it by getting to the terminal line before the loging screen. and how do you do that, well when you start ubuntu you should be able to select recovery terminal mode. i cant remember what button you push, but youll figure it out.
good luck, and im waiting to see how you solve the graphics thing, since i have the same exact prob, just with a geforce 5200
peace

---

### Post by erginemr on 2008-02-20
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
as suggested by bothebobo is a valuable advice, but you should have the correct NVidia driver installed. You seem to have installed nvidia-glx-legacy & nvidia-legacy-kernel-source, but your card is listed here:
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

under the new drivers section. So, if your card is a new generation card (namely GeForce 7950 GT) as reported by lspci, when you boot into the recovery mode, try the above command and enter "startx" to start the graphical mode. If unsuccessful, then edit xorg.conf file and replace "nvidia" with "nv", the open source NVidia driver for the time being.

As soon as you load into Gnome, you should remove these:
```
sudo aptitude remove nvidia-glx-legacy nvidia-legacy-kernel-source
```
and install
```
sudo aptitude install nvidia-glx-new nvidia-new-kernel-source nvidia-kernel-common
```
Finally,
```
sudo nvidia-xconfig
```
to put the binary driver back into effect. (It basically replaces "nv" with "nvidia" in xorg.conf file.)

---

### Post by philidox on 2008-02-20
> **bothebobo said:**
> Hey philidox
I feel for you. I was in the same situation before i gave up and now im detemined again. But i do have a smart code that resets your xorg to default which all graphix cards can handle. It saved my *** more than once
```

bo@VoltronCrew:~$ sudo dpkg-reconfigure -phigh xserver-xorg

```
I dont know what all those options do and i really dont care, but its true and tried. Write it down on a piece of paper and leave it in your desk, it comes in handy in stupid situations.

So you run it by getting to the terminal line before the loging screen. and how do you do that, well when you start ubuntu you should be able to select recovery terminal mode. i cant remember what button you push, but youll figure it out.
good luck, and im waiting to see how you solve the graphics thing, since i have the same exact prob, just with a geforce 5200
peace

Well I tried the command funny thing is its in the xorg.conf file itself, thx but unfortunately it did not work.  I know exactly what I did to fix the nvidia graphics card display but I just cant remember what I type in to the "DRI" section.  Man I should have emailed that to myself or something.  Keep the resolutions coming.

---

### Post by philidox on 2008-02-20
erginemr I LOVE YOU MAN!!!  After hours of googling I finally just listened to what you said it BLAM problem fix.  I know where to get good advice from next time.  Now that i'm thru fix my blank screen issue tell me how to get this ADES working. ONCE AGAIN THX

---

### Post by erginemr on 2008-02-20
This is great! :popcorn:
Glad that your desktop is back, but what is this ADES? If you mean your initial problem with Compiz effects, did enabling backports to get the latest Compiz version in my post below:
[http://ubuntuforums.org/showpost.php?p=4364190&postcount=16](http://ubuntuforums.org/showpost.php?p=4364190&postcount=16)
make any difference? 

By the same token, you might need to add a line to your xorg.conf file, so can you please post it here?

---

### Post by philidox on 2008-02-21
Sorry it took so long to get back with the xorg.conf file my internet was down.  Ok its up let me know what to do.  I appears that I have won the battle but not the war.  My mouse appears as a big pixelated square and whenever I start a video my computer freezes up.  Please help, and as always thx for the fast responses,  I'll response immediately from here on out now that my internet is up and running.

---

### Post by erginemr on 2008-02-22
To begin with, here is mine. I will compare my config with yours, and will share my findings with you...

Meanwhile, please tell us about your monitor type and size, and its natural resolution.

---

### Post by erginemr on 2008-02-22
Well, this X server issues sometimes drive me nuts too; it is as if computer is playing tricks against us to test our patience. Anyway, before I lose my sanity ;), lets go back to your problem...

Comparing the two files, I'd like to point out the differences and put forward my suggestions. I suggest you to divide the problem into pieces: That is, comment out parts of xorg.conf piece by piece, try it out by restarting the graphical server (Ctrl+Alt+BackSpace) and if it doesn't work, uncomment or revert back that part and proceed with the next one. Here we go:

First things first, you should back up your current config file, to be used in case we mess it up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
```

PART 1:
----------
Regarding Section "ServerLayout", if you don't have a wacom tablet ([http://en.wikipedia.org/wiki/Wacom](http://en.wikipedia.org/wiki/Wacom)), you should comment (#) the following lines:

```
Section "ServerLayout"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
  	..........
EndSection
```

This has probably nothing to do with your problem, but I have read posts of people having strange problems when these are active without a connected actual wacom hardware.

PART 2:
----------
Regarding Section "Files", I had configured my X server before with the command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and my config file has no reference to the X11 font directories whatsoever. Yet, I have googled and fond many config files on the net with exactly the same lines as yours. So, this part is OK. Here is the one I have:

```
Section "Files"
EndSection
```

PART 3:
----------
Regarding Section "Module", again dpkg-reconfigure has left only one line "glx" in this section. I don't know what the other modules are good for, and couldn't find any satisfactory information on the net among a myriad of xorg.conf postings. But you should at least thy commenting all others and leaving the "glx" module only and restart the X server with Ctrl+Alt+BackSpace to see if it makes any difference.

```
Section "Module"
    Load           "glx"
EndSection
```


PART 4:
----------
Regarding Section "Monitor", You should consult to your monitor's manual or technical sheets on the net, to make sure that its horizontal and vertical refresh rates match with the  information inside your config file.

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 204.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection
```

PART 5:
----------
Well, this is the heart of it, most probable contender for the origin of the problem. Let me begin with the given screen sizes. I don't think that "4095x4095" is the natural resolution of your monitor. You should find it out and replace this strange setting with that value. 

Generally speaking, for a regular CRT or 17" LCD monitor with 4/3 screen ratio; 1280x1024 or 1024x768 is OK. For a wide-screen LCD/TFT monitor, 1680x1050 or 1280x800 is a good candidate if it is 17", and 1900x1440 if 19".

```
Section "Screen"
   ..........
   SubSection     "Display"
        Depth       24
        Modes      [COLOR="Red"]**"4095x4095"**[/COLOR] "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

Regarding Section "Screen" again, you should try adding the following two lines to your config file before the "Display" subsection, which somehow affects the performance of Compiz:

```
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
```
    
Well, that is all there to it. You should restart your server each time to check if your problem is gone, if not, thy the next item in queue. I cannot guarantee 100% success, as the same setting on one hardware can have quite different effects on another one. So, may good luck be with you!...

---

### Post by erginemr on 2008-02-22
On a final note:

1. You can keep an eye on the errors issued during the X server startup with:
```
cat /var/log/Xorg.0.log | grep "(EE)"
```

2. You were looking for one Section "DRI", that was used in fixing your former configuration. I have come across a few xorg config files that involved loading a "dri" module and a "DRI" section dedicated to it, but all of them belonged to an ATI card. You may want to try it anyway:
 
```
Section "Module"
	........
	Load  	"dri"
	........
EndSection
```
and at the end of the file:
```
Section "DRI"
	Mode 	0666
EndSection
```

---

### Post by philidox on 2008-02-22
Well sorry to say but Mission Failed.  Mouse still invisible and computer freezes whenever I play a video. The only thing I got left is the error I got from inserting the command you gave me earlier

the command:cat /var/log/Xorg.0.log | grep "(EE)"

result: (WW) warning, (EE) error, (NI) not implemented,  (??) unknown.

Sorry it took me long to respond but I was trying out all the solutions you gave me.  I'll be right here at my computer waiting.

---

### Post by erginemr on 2008-02-22
Your mission, Jim, should you decide to accept it, is to disable Compiz (from preferences -> appearance -> visual effects) in an effort to isolate the source of the problem and restart the session to check whether mouse cursor is shown and video playback works flawlessly without any desktop effects. 

This post will self-destruct in five seconds. :)

---

### Post by philidox on 2008-02-22
> **erginemr said:**
> Your mission, Jim, should you decide to accept it, is to disable Compiz (from preferences -> appearance -> visual effects) in an effort to isolate the source of the problem and restart the session to check whether mouse cursor is shown and video playback works flawlessly without any desktop effects. 

This post will self-destruct in five seconds. :)

YESSSSS, I'VE DONE IT!!!! I got it all working,  I mean everything working flawlessly.  I just had to do a clean install of ubuntu.  I've been upgrading seen Edgy.  Ubuntu has gotten alot better at its own game since then but man it is freakin awesome.  YES YES YES.  Now its own baby.  Thx Erginemr and thanx snow if it wasnt for you I would have never done a clean install of ubuntu even though it did mess up my system.  The war is over, victory at last

---

### Post by erginemr on 2008-02-23
This is great news philidox! Seeing [SOLVED] beside you post made my day! I believe successive upgrading may have broken something on your system. Anyway, take care and enjoy your new fresh shiny Gutsy, then!

[I]"We make war that we may live in peace." - Aristotle

"Peace is not the absence of war; it is a virtue; a state of mind; a disposition for benevolence; confidence; and justice." - Spinoza[/I]

I know I am a prick. Just can't help it ;)

---

### Post by CarnivorouZ on 2008-02-26
I have read pages upon digital pages of Ubuntu forums looking for a cure to the visual effects problem I have.  Unlike Philidox, I do not get anything after installing the restricted drivers.  After the ubuntu load screen it goes to black screen and that's all she wrote.
Up to this point I have enabled Compiz and fglrx as well as updating and upgrading everything I can in the repositories and no luck.

code:
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

The video card is a ATI Radeon x1650.
Let me know if there is any other info I can provide to help me solve this issue.  I would really like to utilize Ubuntu's visual effects.

---

### Post by erginemr on 2008-02-26
> **CarnivorouZ said:**
> I have read pages upon digital pages of Ubuntu forums looking for a cure to the visual effects problem I have.  Unlike Philidox, I do not get anything after installing the restricted drivers.  After the ubuntu load screen it goes to black screen and that's all she wrote.
Up to this point I have enabled Compiz and fglrx as well as updating and upgrading everything I can in the repositories and no luck.

code:
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

The video card is a ATI Radeon x1650.
Let me know if there is any other info I can provide to help me solve this issue.  I would really like to utilize Ubuntu's visual effects.

I suggest you to start a new thread to your problem with a proper name. If you continue this old thread, which has been marked as [SOLVED], the chance of someone noticing your problem will be very low. 

So, please start a new thread and give its link here, so that I can also follow. 

Besides, I couldn't understand this: *"After the ubuntu load screen it goes to black screen and that's all she wrote."* Does this mean that you cannot have the Gnome desktop at all? Please explain the current state of your computer better in your new thread.

---

