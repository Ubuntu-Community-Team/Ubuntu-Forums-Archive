---
title: "Script for install Beryl/ATI/AIGLX on Ubuntu Edgy"
date: 2007-01-14
forum: Desktop Environments
---

### Post by Waappu on 2007-01-14
Hi

I created script and guide for installing Beryl for ATI cards using AIGLX. 
I hope you can read this [small guide and test script]("http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html"). Please comment and give feedback.

Script is copy from [nvidia script]("http://ubuntuforums.org/showthread.php?t=335034") and modified for ATI and AIGLX.

Edit:
If you have tested this script please post 
- did Beryl work
- modifications to script
- modifications to your /etc/X11/xorg.conf
- Upgraded to Xorg 7.2 Yes/No
- output of ```
lspci | grep 'ATI'
```


Edit:
This might help if Beryl is running slow and also other problems.
Xorg 7.2 has ehnannced AiGLX support and better 3D performance.
[http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087)

---

### Post by cypr3ss on 2007-01-18
Hi Waappu,

First of all, thanks for the script!!  I did have one issue when running the script, which i've described below.  

I have just installed Ubuntu 6.10 on my Thinkpad t43 (from the alternate install CD), which (according to /etc/X11/xorg.conf) uses an ATI Technologies, Inc. M22 [Radeon Mobility M300].

I experienced a slight problem with your script, where it checks for an ATI display controller, it was reporting there wasn't one.

When I run "lspci |grep  -i 'Display controller: ATI'" it finds nothing, however if I run "lspci |  grep 'ATI'" it returns :

01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]

So, my work around was to comment out this check in the script, and then it ran through without error, and after the reboot I was able to start beryl-manager and everything works!! :D  Very happy.  But I thought this may be of interest to you, or someone else trying to use your script.

Regards,

Cypr3ss.

---

### Post by Waappu on 2007-01-18
Hi

Thanks =) That was useful information . I will correct that to script

---

### Post by jeyaganesh on 2007-01-20
hi waapu, thank you very much for easy-to-follow instructions. i reached lot to install beryl, at last i saw your instructions and intalled it in few seconds. now i am playing with beryl themes and windows:guitar: . Thanks to you:D :D

---

### Post by Waappu on 2007-01-21
Hi

Thanks =). Could please post some information about your system and output of```
lspci | grep 'ATI'
```
it will help also other users.

---

### Post by peralta on 2007-01-24
The script perfectly worked with me. I installed ubuntu 6.10 just to test beryl and i'm very happy with the result. 

I have only two little problems:
- Videos do not play well when using beryl. It kind of shines, or play only sound.
- When I close beryl (mostly to watch videos, because of the above problem), the windows do not show the top bar where you see the name, close, minimize and maximize buttons and move the window.

Any help with that?

Thanks a lot for the script.

---

### Post by acejones on 2007-01-24
Your script worked for me in 6.10 Kubuntu.  i had tried 3 or 4 other ones that hadn't, and 1 had worked in Ubuntu 6.10

mike@mike-kubuntu:~$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

Installed on a Dell C640 with 512mb RAM

---

### Post by CowzRule on 2007-01-25
> **peralta said:**
> The script perfectly worked with me. I installed ubuntu 6.10 just to test beryl and i'm very happy with the result. 

I have only two little problems:
- Videos do not play well when using beryl. It kind of shines, or play only sound.
- When I close beryl (mostly to watch videos, because of the above problem), the windows do not show the top bar where you see the name, close, minimize and maximize buttons and move the window.

Any help with that?

Thanks a lot for the script.

You need to right click the Beryl emerald icon in your notification area and click "Select Window Manager - Metacity".

---

### Post by peralta on 2007-01-25
> **CowzRule said:**
> You need to right click the Beryl emerald icon in your notification area and click "Select Window Manager - Metacity".

I know that... but if i do that i turn off beryl. Did you get me?

---

### Post by Waappu on 2007-01-25
> **peralta said:**
> I have only two little problems:
- Videos do not play well when using beryl. It kind of shines, or play only sound.
- When I close beryl (mostly to watch videos, because of the above problem), the windows do not show the top bar where you see the name, close, minimize and maximize buttons and move the window

Hi

I can't figure out now why windows title bar not showing when you change to metacity.
When you disable Beryl you can try right click notification area gem and select Reload Window decorator or Reload Window Manager.

You can try this to your video problem with Beryl:
Type in terminal```
gstreamer-properties
``` Go to video tab and select to output X Window system (No XV)

---

### Post by Waappu on 2007-01-25
> **peralta said:**
> - Videos do not play well when using beryl. It kind of shines, or play only sound.
- When I close beryl (mostly to watch videos, because of the above problem), the windows do not show the top bar where you see the name, close, minimize and maximize buttons and move the window

Hi

I don't know does this make difference but you can try this Beryl shutdown script.
[http://ubuntuforums.org/showthread.php?t=338873](http://ubuntuforums.org/showthread.php?t=338873)

---

### Post by x64Jimbo on 2007-01-25
AWESOME! This is really cool! Very nice.

---

### Post by peralta on 2007-01-25
> **Waappu said:**
> Hi

I can't figure out now why windows title bar not showing when you change to metacity.
When you disable Beryl you can try right click notification area gem and select Reload Window decorator or Reload Window Manager.

You can try this to your video problem with Beryl:
Type in terminal```
gstreamer-properties
``` Go to video tab and select to output X Window system (No XV)

About the title bar i notice that sometimes it doesn't show, sometimes yes. But this is not a big problem.

The video thing is what get me nervous. I tried gstreamer-proprieties as you said. But the problem persists. The script to shut it down don't help much, i want to play videos using beryl, as we can see in every video demonstrating beryl.

In your computer videos play well with beryl on?

Thank you for helping.

---

### Post by Waappu on 2007-01-26
> **peralta said:**
> About the title bar i notice that sometimes it doesn't show, sometimes yes. But this is not a big problem.

The video thing is what get me nervous. I tried gstreamer-proprieties as you said. But the problem persists. The script to shut it down don't help much, i want to play videos using beryl, as we can see in every video demonstrating beryl.

In your computer videos play well with beryl on?

Thank you for helping.

Hi

Videos playing ok in my system. Could you please post output ```
lspci | grep 'ATI'
``` and your /etc/X11/xorg.conf file ?

---

### Post by anonymous666 on 2007-01-26
Hi.

I successfully installed and had beryl running fine using your script. Then I edited my monitor resolution in /etc/X11/xorg.conf.  After restarting, beryl did not function anymore. I tried to change the resolution again but beryl still didnt want to function. I can open the beryl-manager but no effects whatsoever. How could I revert back to the state when beryl was not installed yet? I am planning to revert back and then reinstalling using your script. Any ideas? 

Thanks in advance

edited: Never mind. Somehow Metacity is selected as default on "Select window manager" option. Problem solved.

---

### Post by Patrick-Ruff on 2007-01-30
I bet half of you are experiencing most of these issues because of the bad 3d accel support on the newish-old cards.  the xXXXX series cards don't even work at all without FGLRX (or so I hear.)

I assume video's don't play well because the expiremental 3d acceleration is using your CPU to do half the rendering. probably more then half.  

we should get some coders together and code a better open source driver . . .

---

### Post by warbread on 2007-01-31
Despite the fact that I'm pretty sure my card wouldn't work with AIGLX, I tried the script out for want of not using XGL (which keeps crashing...)  It didn't work.  When I turned on Beryl, X restarted.  

I've got an HP Pavilion 
Radeon 200M 128mb
512mb ram

grok@potofgold:~$ lspci | grep 'ATI'
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

Awesome work, though, Waappu.  Let me know if I can help further.

---

### Post by Waappu on 2007-01-31
> **warbread said:**
> Despite the fact that I'm pretty sure my card wouldn't work with AIGLX, I tried the script out for want of not using XGL (which keeps crashing...)  It didn't work.  When I turned on Beryl, X restarted
Hi

I'm sorry that didn't work.
But see if this post could help you
[http://ubuntuforums.org/showthread.php?t=341149](http://ubuntuforums.org/showthread.php?t=341149)

---

### Post by FastZ on 2007-01-31
Well, your script works on my Dell Inspiron 9300 with an ATI Mobility Radeon M300 integrated video.  However, it is glitchy as all hell.  Maybe this is just how Beryl is for ATI?  Beryl runs perfectly without a hitch on my desktop computer that uses an nVidia card (GeForce4 MX 440 AGP 8X), and that uses AIGLX too.

Here are a few things.

Did beryl work?
- Yes, beryl works, but is very glitchy and is not very smooth-operating and locks up my computer every so often.  beryl splash screen does not show up when running beryl-manager from command line.

output of lspci | grep "ati"
```

matt@matt-laptop:~$ lspci | grep "ati"
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
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
matt@matt-laptop:~$
```Output from what shows up when I type "beryl-manager" at the command line:

```

matt@matt-laptop:~$ beryl-manager
matt@matt-laptop:~$ libGL warning: 3D driver claims to not support visual 0x4b
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x4b
Reloading options
```

Can someone explain " libGL warning: 3D driver claims to not support visual 0x4b" to me?  What does that mean?

---

### Post by Waappu on 2007-01-31
> **FastZ said:**
> Can someone explain " libGL warning: 3D driver claims to not support visual 0x4b" to me?  What does that mean?
Hi

Your card can't show some textures. E.g. water plug in not work on that card.
If you disable e.g. blur and trailfocus plugin does it help anything?

---

### Post by fiveryanfrenzy on 2007-02-01
THANK YOU!

You made that so nice and simple I had been toying with it (and failing) for some time now I can get some sleep!

Thinkpad T43 with ATI M300

this is sweet!

Someone sticky this for ATI users!!!

---

### Post by araz on 2007-02-02
> **Waappu said:**
> 
- did Beryl work  It woked 75%(no totem, to slow(still finding solutions))

> - modifications to script No modifications
> - modifications to your /etc/X11/xorg.conf  No modifications
> - output of ```
lspci | grep 'ATI'
```
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

thanks Waappu :D

---

### Post by l0k1_ on 2007-02-06
Beryl working like a charm except for some weird message in terminal about the driver saying it doesn't run 3D. Rain effects don't work, can't tell if others work/don't work. 

No Modifications to  script

I had to make the modifications for the radeon open source wiki and the beryl wiki: adding the extensions and enabling AIGLX mostly

Output:
loki@loki-desktop:~$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)

Just a comment - the script itself didn't let me run beryl - i had to actually go and install it using the beryl wiki then everything worked. THANKS a BUNCH!

---

### Post by Waappu on 2007-02-06
> **l0k1_ said:**
> Beryl working like a charm except for some weird message in terminal about the driver saying it doesn't run 3D. Rain effects don't work, can't tell if others work/don't work
That is common problem with ATI cards. Beryl water plugin not working. All others should be fine. I try to find good link where it is explained

> **l0k1_ said:**
> Just a comment - the script itself didn't let me run beryl - i had to actually go and install it using the beryl wiki then everything worked.
Sorry, but I don't understand what you mean. Could you please post steps that do to get Beryl working. It might help others and I can change script if needed.

---

### Post by Waappu on 2007-02-06
> **l0k1_ said:**
> Beryl working like a charm except for some weird message in terminal about the driver saying it doesn't run 3D. Rain effects don't work, can't tell if others work/don't work
Here  is some info about water plugin
[http://wiki.beryl-project.org/wiki/Plugins/PluginOptions#Water](http://wiki.beryl-project.org/wiki/Plugins/PluginOptions#Water)

---

### Post by Waappu on 2007-02-06
> **araz said:**
> It woked 75%(no totem, to slow(still finding solutions))
Hi
You can try this to your video problem
Type in terminal```
gstreamer-properties
``` Go to video tab and select to output X Window system (No XV)

I use VLC for videos and it's working ok

---

### Post by ryaaan on 2007-02-06
Hello!  Are there any breakthroughs for the mobility X1*00 Cards?  I have a Dell E1505 laptop with mobility X1300.  I would really love to use AIGLX instead of XGL.   :confused: 

~Ryan

---

### Post by l0k1_ on 2007-02-07
> **Waappu said:**
> 
Sorry, but I don't understand what you mean. Could you please post steps that do to get Beryl working. It might help others and I can change script if needed.

1) Installed radeon open source driver and made standard modifications to xorg.conf (mainly added extensions section and Option  "Aiglx"  "Enable"

2) Changed xserver user permission from "console" to "anybody"

3) Installed script for install Beryl/ATI/AIGLX 

4) Went to Beryl wiki and installed beryl with emerald themes manager


*After I ran the script and rebooted the x server, I couldn't run beryl or beryl-manager. When I tried rerunning the script it said it was already run.

---

### Post by Max_Might on 2007-02-07
I am using beryl with ATI x550 and XGL. Can I switch to AIGLX and is it better than XGL?
XGL takes about 80 MB RAM here.

---

### Post by p51d78th on 2007-02-07
i ran the script and everything installs fine. however when i rebooted and ran beryl-manager i locked up X and i had to restart X. this happens everytime i try to start beryl.

when i run 
lspci | grep 'ATI'

i get
01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)

---

### Post by Waappu on 2007-02-07
> **p51d78th said:**
> i ran the script and everything installs fine. however when i rebooted and ran beryl-manager i locked up X and i had to restart X. this happens everytime i try to start beryl.

when i run 
lspci | grep 'ATI'

i get
01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)

Hi

Could you please post output
```
glxinfo | grep "direct rendering"
```
and
```
glxinfo | grep vendor
```

---

### Post by AlexTheMad on 2007-02-07
Worked wonders on my HP Compaq nc8230 with a Radeon x600, and I've been trying to get beryl with fgxl to work all day without luck. Great script man :)

---

### Post by klein de usa on 2007-02-07
hi
Hats off to Waappu! i'v tryed numerious times to install drivers and beryl on this dell xps finely today i got the cube thank you script ran with no problems or tweaks.
my video card is a Radeon R350 [ Radeon 9800 Pro]

paul@ubuntuxps:~$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

thanks again

---

### Post by p51d78th on 2007-02-07
glxinfo | grep "direct rendering"
    direct rendering: No

glxinfo | grep vendor
    server glx vendor string: SGI
    client glx vendor string: ATI
    OpenGL vendor string: Tungsten Graphics, Inc.

---

### Post by JettCRX on 2007-02-07
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Radeon 9700 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9700 Pro] (Secondary)

```

The card is actually a Tyan Tachyon 9500 Pro.  Not sure why it identifies itself as a 9700 Pro.  

Tyan Tiger 230T Motherboard (S2507T), VIA Apollo Pro 133T Chipset
Tyan Tachyon 9500 Pro (ATI-based)
Dual 1.4ghz Pentium III (Tualatin) Processors
1GB of RAM

Fresh install of Edgy... I had tried for 2 days to get this to work on my own... eventually wiped my drive and started over.  Finished installing before I left for work this morning.  Found this thread while doing research at work... as soon as I got home I tried your script.  Worked FLAWLESSLY the first try.

Thanks a bundle!  This is fun.  :)

EDIT: Oh and by the way, my wife thinks I'm a dork.  I made her come look at this... she said I looked like a kid in a candy store... oh but I am... the eye-candy store!

---

### Post by Waappu on 2007-02-08
> **p51d78th said:**
> glxinfo | grep "direct rendering"
    direct rendering: No

glxinfo | grep vendor
    server glx vendor string: SGI
    client glx vendor string: ATI
    OpenGL vendor string: Tungsten Graphics, Inc.

Hi

I think you video card not supported.
[Please see this link]("https://help.ubuntu.com/community/RadeonDriver#head-be424fb21464afc861c5cc308dac1876a4807de1")

---

### Post by hito1 on 2007-02-10
> **Waappu said:**
> 
Edit:
If you have tested this script please post 
- did Beryl work
- modifications to script
- modifications to your /etc/X11/xorg.conf
- output of ```
lspci | grep 'ATI'
```

First of all, thank you, Waappu! :)

-yes, Beryl is working with a minor problem. Videos don't work. Even after I adjusted the gstreamer options like you said.

lscpi | grep "ATI":
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
```

Also, I'm having 74fps max, is that a good speed?

---

### Post by Waappu on 2007-02-10
> **hito1 said:**
> Even after I adjusted the gstreamer options like you said
Try to use VLC video player
```
sudo aptitude install vlc
```

> **hito1 said:**
> Also, I'm having 74fps max, is that a good speed?
Thats not good speed. Try change xorg.conf if you have AGP card
```
gksudo gedit /etc/X11/xorg.conf
```
Remove # begin from  these lines and set AGPMode same as your motherboard agp speed
```
Option 		"AGPFastWrite" "on"
Option		"AGPMode" "4"
```
log out and press Ctrl+Alt+backspace. If X not start then commet out those lines```
sudo nano /etc/X11/xorg.conf
```

---

### Post by plantguy on 2007-02-10
This script worked well (so far no bugs) on the following machine:

Dell C610
1MHz Pentium III
1GB ram
ATI Radeon Mobility 9000
Ubuntu 6.10 (with updates as of 2/9/2007)

Thanks! :) 

Great job!!!

---

### Post by hito1 on 2007-02-10
> **Waappu said:**
> Try to use VLC video player
```
sudo aptitude install vlc
```

That's what I'm using.


> Thats not good speed. Try change xorg.conf if you have AGP card
```
gksudo gedit /etc/X11/xorg.conf
```
Remove # begin from  these lines and set AGPMode same as your motherboard agp speed
```
Option 		"AGPFastWrite" "on"
Option		"AGPMode" "4"
```
log out and press Ctrl+Alt+backspace. If X not start then commet out those lines```
sudo nano /etc/X11/xorg.conf
```

Thanks, I'll give it a try. What would be a good speed, btw? Do you think my video problem could be related to this low performance?


EDIT:
The AGPFastWrite and AGPMode didn't work out, the screen would go blank after boot splash screen. :( Here is my section "device" in xorg.conf:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver		"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection
```

I have AGPFastWrite enabled at BIOS. My AGPSize there is 64, though.

---

### Post by ljoslin on 2007-02-10
I ran the script and everything seemed to go well, rebooted and ran beryl-manager, it loaded and briefly showed it passing all the test, then it just restated X.  here is the info:

lspci | grep 'ATI'

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
larry@larry-laptop:~$ 


any help would be great!

Larry](*,)

***EDIT:***  It appears that the drivers will not work with my card, is there another way around this?  any way to get this working with the fglrx drivers?


Larry

---

### Post by Waappu on 2007-02-11
> **ljoslin said:**
> I ran the script and everything seemed to go well, rebooted and ran beryl-manager, it loaded and briefly showed it passing all the test, then it just restated X.  here is the info:

lspci | grep 'ATI'

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
larry@larry-laptop:~$ 


any help would be great!

Larry](*,)

***EDIT:***  It appears that the drivers will not work with my card, is there another way around this?  any way to get this working with the fglrx drivers?


Larry

Hi

Have you read this
[http://ubuntuforums.org/showthread.php?t=341149](http://ubuntuforums.org/showthread.php?t=341149)

---

### Post by ljoslin on 2007-02-11
> **Waappu said:**
> Hi

Have you read this
[http://ubuntuforums.org/showthread.php?t=341149](http://ubuntuforums.org/showthread.php?t=341149)

I have read that forum, and either I'm doing something wrong or it just dosn't work for me.

Any other ideas would be great!

Larry[-o<

---

### Post by Waappu on 2007-02-11
> **hito1 said:**
> That's what I'm using.




Thanks, I'll give it a try. What would be a good speed, btw? Do you think my video problem could be related to this low performance?


EDIT:
The AGPFastWrite and AGPMode didn't work out, the screen would go blank after boot splash screen. :( Here is my section "device" in xorg.conf:
```
Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver		"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection
```

I have AGPFastWrite enabled at BIOS. My AGPSize there is 64, though.

Hi

Can't say what is good speed. I have round 1200 FPS. 
Change xorg.conf AGPSize also to 64.
Did you set AGPMode same as your motherboard AGP speed? I think it might be 8 so ```
Option		"AGPMode" "8"
```

VLC problem try this:
settings->preferences->video->output modules
check advanced check box and then change video output module to "X11 output module"

---

### Post by Waappu on 2007-02-11
> **ljoslin said:**
> I have read that forum, and either I'm doing something wrong or it just dosn't work for me.

Any other ideas would be great!

Larry[-o<

Hi

Hard to say why it wont work for you.

---

### Post by hito1 on 2007-02-14
> **Waappu said:**
> Hi

Can't say what is good speed. I have round 1200 FPS. 
Change xorg.conf AGPSize also to 64.
Did you set AGPMode same as your motherboard AGP speed? I think it might be 8 so ```
Option		"AGPMode" "8"
```


1200 FPS!!! :shock: :shock: 

I uncommented AGPMode (is just 4 for me) and set AGPSize to 64. But fast write locks the computer. I guess I just have a crappy motherboard (Asus AS333, or something like that) and will have to live with that. :( At least metacity is faster now and your script works, good job! :)

Can I ask what are your system specs? Is it normal to achieve 1200fps?

---

### Post by Waappu on 2007-02-14
> **hito1 said:**
> Can I ask what are your system specs?

Hi

My PC is modified Fujitsu&Siemens Scenic L (816e)

CPU: PIII 1GHz
RAM: 512MB
Video card: ATI 9250 128MB(64bit)

> **hito1 said:**
> Is it normal to achieve 1200fps?
I don't realy know much about those FSP rates

---

### Post by Waappu on 2007-02-14
> **hito1 said:**
> 1200 FPS!!! :shock: :shock: 

I uncommented AGPMode (is just 4 for me) and set AGPSize to 64. But fast write locks the computer. I guess I just have a crappy motherboard (Asus AS333, or something like that) and will have to live with that. :( At least metacity is faster now and your script works, good job! :)

Can I ask what are your system specs? Is it normal to achieve 1200fps?

Hi

Try to play with other xorg.conf options

Try to e.g. change these lines ```
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
```to ```
	Option		"AccelMethod" "EXA"
	Option		"EXANoOffscreenPixmaps" "on"
```
You can find lot of other options if you type in terminal```
man ati
``` or ```
man radeon
```

---

### Post by cmj_21 on 2007-02-19
thanks worked great for me.

Running fine on a dell inspiron 6000 with M300

---

### Post by sully311 on 2007-02-23
Finally Beryl works! Been at it for hours, tried many. For the record Ati 7000/VE Radeon with TV tuner card, 6.10 edgy eft Dell 4550 p4 2.8ghz 512mb dual boot 60gig and 40gig.

Issues so far,

 when window maximized top bar loses min/max and close buttons

Videos have audio but no visual until beryl turned off

noticable lag while loading programs, switching windows / screens

I've feelings that its one of those things... Oh isn't that neat, and then never gets used???

On the other hand, when friends & relitives come over, could make an impressiion. well see

---

### Post by larryni on 2007-03-01
I just tried your script and everything seemed to install fine. But after rebooting I ended up with a very high resolution (1440x900) and the refresh rate set at 60Hz. That's the only options available. After launching beryl-manager nothing happened. I don't get the rotating cube, no effects...  nothing. It won't let me change themes either. 

Here's the lspci | grep 'ATI' output
```
00:0a.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
00:0a.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
```
and my xorg.conf file
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "PHILIPS 107E"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver      "radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID       "PCI:0:10:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor    "PHILIPS 107E"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "false"
EndSection
```
Any idea what I need to change here?

---

### Post by araz on 2007-03-01
Try change your xorg from
> Section "Extensions"
    Option "Composite" "Disable"
EndSection

to
> Section "Extensions"
    Option "Composite" "Enable"
EndSection

hope it helps:neutral:

---

### Post by Waappu on 2007-03-01
> **larryni said:**
> I just tried your script and everything seemed to install fine. But after rebooting I ended up with a very high resolution (1440x900) and the refresh rate set at 60Hz. That's the only options available. After launching beryl-manager nothing happened. I don't get the rotating cube, no effects...  nothing. It won't let me change themes either.

Try this xorg.conf setup
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      "Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "PHILIPS 107E"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver      "radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID       "PCI:0:10:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor    "PHILIPS 107E"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

---

### Post by Moses on 2007-03-01
If you have tested this script please post
- did Beryl work **NO**
- modifications to script **NONE**
- modifications to your /etc/X11/xorg.conf
- output of  lspci | grep 'ATI'
 
```
01:00.0 VGA compatible controller: ATI Technologies Inc R420 JI [Radeon X800PRO]
01:00.1 Display controller: ATI Technologies Inc Unknown device 4a69
```


Any Ideas? :(

I've followed at least 6 howto's/scripts in an attempt to get beryl working. My best so far has been beryl running without direct rendering - which is pretty useless.

---

### Post by DragonGod13 on 2007-03-05
- did Beryl work - No
- modifications to script - None
- modifications to your /etc/X11/xorg.conf - None
- output of lspci|grep 'ATI'

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)
```

When I type Beryl or Beryl-manager I get this output...

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...
```

Then my whole computer locks up and I have to restart.

Xorg.conf

```
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
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  FontPath "/usr/share/fonts/X11/misc"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Module"
  Load "dbe"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "dri"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "us"
  option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
  identifier "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
  boardname "ATI Radeon"
  busid "PCI:1:0:0"
  driver "ati"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	#Option		"DRI" "true"
  screen 0
  vendorname "ati"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	#Option		"DRI" "true"
  option "MergedFB" "off"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Sylvania"
  modelname "Sylvania F74"
  HorizSync 30.0-70.0
  VertRefresh 55.0-120.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1024x768@60" "1024x768@43" "1024x768@70" "1152x864@75" "1024x768@75" "1280x960@60" "1024x768@85" "1280x1024@60" "832x624@75" "1400x1050@60" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier  "Default Layout"
  Screen      "Default Screen"
  Option      "AIGLX" "true"
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "device" # 
  identifier "device1"
  boardname "ATI Radeon"
  busid "PCI:1:0:0"
  driver "ati"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
  screen 1
  vendorname "ati"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
  option "MergedFB" "off"
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

glxinfo|grep vendor

```
libGL warning: 3D driver claims to not support visual 0x4b
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
```

glxinfo|grep render

```
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
```

Anyone have any ideas? I did all this from a fresh Kubuntu 6.10 install and I really really want to get beryl working.

---

### Post by Waappu on 2007-03-05
Hi

If you run that script you should have /etc/X11/xorg.conf_BERYL_SETUP_BACKUP file.
Could you please post that one also?

---

### Post by Nefi on 2007-03-05
hey man, just wanna say the script worked flawlessly on a radeon 9600! thanks.

my lspci | grep 'ATI' info

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
```

---

### Post by Waappu on 2007-03-06
> **Nefi said:**
> hey man, just wanna say the script worked flawlessly on a radeon 9600! thanks.

Hi

Could you please post output of ```
lspci | grep 'ATI'
```

---

### Post by Mindspin85 on 2007-03-06
I keep having problems with beryl, i used your script which i am very thankful for :)
But unfortunately no results with beryl yet...

```
lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

```

My xorg.conf
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"dbe"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
  Option "Composite" "0" 
EndSection

```

I already changed Option "Composite" "0" to Option "Composite" "1" which didnt work out. (maybe i should use false/true or enabled/disabled?

Thanks in advance!

---

### Post by Waappu on 2007-03-06
Hi

Try this xorg.conf setup
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dbe"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection


Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option	"Composite" "Enable"
EndSection

```

and uninstall XGL if you have installed that

Edit
Type in terminal to uninstall XGL
```
sudo aptitude remove --purge xserver-xgl
```

---

### Post by Oen386 on 2007-03-10
I ran the script, seemed to work ok.

I get

```
$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

```

The issue I am having is when I try to enable Beryl I and used Wobbly Windows, the edges of the window will bend, but they aren't "wobbly".

Also I can't change my screen resolution.

Any help?

---

### Post by Waappu on 2007-03-10
> **Oen386 said:**
> I ran the script, seemed to work ok.

I get

```
$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

```

The issue I am having is when I try to enable Beryl I and used Wobbly Windows, the edges of the window will bend, but they aren't "wobbly".

Also I can't change my screen resolution.

Any help?
Could you post your xorg.conf

---

### Post by Max_Might on 2007-03-10
Thanx for the script, beryl is running cool ;]
the script uninstalled XGL and i`m not sure if it installed something connected to AIGLX
anyway, here is the essential information:

$ lspci | grep 'ATI'
```
05:00.0 VGA compatible controller: ATI Technologies Inc RV370 [ATI Sapphire X550 Silent]
05:00.1 Display controller: ATI Technologies Inc RV370 secondary [ATI Sapphire X550 Silent]
```

my video is ATI x550 256MB

and here is my xorg.conf

```

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
	Option          "AIGLX"         "true"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"dbe"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us,bg"
	Option "XkbVariant" ",phonetic"
	Option "XkbOptions" "grp:alt_shift_toggle"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "T710B"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  	"ATI Technologies, Inc. RadeonX550"
	Driver     	"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "EXA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver      	"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "EXA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RadeonX550"
	Monitor    "T710B"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection


```

I had to set  Option	    "Composite" to "Enable"

and 1 more thing, I think that there is some problem with the video driver
here is the output of glxinfo:

```

max@max-desktop:~$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
........ bla bla ....
.........................
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x26 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x27 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2e 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x2f 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x31 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 Slow
0x4b 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

everything in the last column is set to "Slow" or "None" :(
IS That Normal ?
And btw how do I change the GDM resolution, the script made is really big.
thanx for the script anyway ;]


EDIT: I forgot to mention that the system was somehow laggy (scrolling etc. ) then i added
Option          "AIGLX"         "true" to Server Layout section in xorg.conf
and changet XAA to EXA and now its not so laggy but the output from glxinfo is the same.

---

### Post by Oen386 on 2007-03-11
Thanks for the quick reply, sorry I was at work.

If you have tested this script please post
- did Beryl work **Not really, read above.**
- modifications to script **None**
- modifications to your /etc/X11/xorg.conf **None. I did a fresh Ubuntu 6.10 install, applied all updates avaible, then rant he script.(On a note the script seems to error out if you don't do all updates before running it.**


```
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
	Load	"dbe"
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
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

---

### Post by Oen386 on 2007-03-11
Also when I run "beryl-manager" I get this:

```
$ beryl-manager
$ libGL warning: 3D driver claims to not support visual 0x4b
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libberylsettings: dlopen: /usr/lib/beryl/libbench.so: cannot open shared object file: No such file or directory
libGL warning: 3D driver claims to not support visual 0x4b


```

---

### Post by Waappu on 2007-03-11
> **Oen386 said:**
> Also when I run "beryl-manager" I get this:

```
$ beryl-manager
$ libGL warning: 3D driver claims to not support visual 0x4b
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libberylsettings: dlopen: /usr/lib/beryl/libbench.so: cannot open shared object file: No such file or directory
libGL warning: 3D driver claims to not support visual 0x4b


```

Hi

Try this:
type in terminal```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install beryl-plugins-unsupported
sudo aptitude install beryl-plugins
```

---

### Post by Waappu on 2007-03-11
> **Max_Might said:**
> everything in the last column is set to "Slow" or "None" :(
IS That Normal ?
And btw how do I change the GDM resolution, the script made is really big.
thanx for the script anyway ;]


EDIT: I forgot to mention that the system was somehow laggy (scrolling etc. ) then i added
Option          "AIGLX"         "true" to Server Layout section in xorg.conf
and changet XAA to EXA and now its not so laggy but the output from glxinfo is the same.
Hi

Try uncomment these lines from xorg.conf
```
Option 		"AGPFastWrite" "on"
        Option		"AGPMode" "4"
```
and set AGPMode same as your motherboard

---

### Post by Waappu on 2007-03-11
Hi

This might help if Beryl is running slow.
Use with own risk
[http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087)

---

### Post by Oen386 on 2007-03-11
What was that uppose to do? NOthing appears to have changed. I still can not select my resolution, and some freatures of Beryl are very very unstable, such as wobbly windows.

Thanks for your help though.

---

### Post by dsmarsh on 2007-03-12
I have a problem with my resolution too, its something to do with that fact that i can only run aiglx at 800x600 or worse.  This is a major problem.  I used the script before but now i am running feisty, so i changed it and i am worndering if anyone here knew enough to help me.

```


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
        Option          "AIGLX"         "true"
	Identifier     "Default Layout"
	Screen         "Default Screen"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
#	Load  "dbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
	HorizSync    28.0 - 80.0
	VertRefresh  43.0 - 60.0
EndSection

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option 		"ColorTiling" "on"
        Option 		"EnablePageFlip" "true"
        Option          "XAANoOffscreenPixmaps"
        Option 		"RenderAccel" "true"
	#Option		"AGPFastWrite" "on"
	Option		"AGPMode" "64"
	Option		"AGPSize" "32"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x1050" "1024x768"
        EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection


```


Beryl does work in this resolution i just cant change back to 1400x1050 like it should be.  I have the option to change it but when i do the sides of the screen become distorted and grainy even though everything still works.  
Thanks, 
P.S.   I think this is a problem with my aiglx.

---

### Post by Waappu on 2007-03-12
Hi

I think you didn't run my sricpt or you have modified xorg.conf after that ??

If you have installed XGL try to uninstall that.

You can try if Xorg 7.2 helps
[http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087)

---

### Post by Oen386 on 2007-03-13
Thanks for your help Waappu. I got everything running. The only option that doesn't work properly is the multiple backgrounds (for the cube). I can live without that, since everything else works great!

Thanks again.:popcorn:

---

### Post by NuklearToaster on 2007-03-13
I have only a couple questions, so I'll make this short.

I have ran the script, and after such, it returned this.

```
tux@tux-desktop:~$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
```

Now, before I [update my xorg]("http://ubuntuforums.org/showthread.php?t=373087"), would it be wise to let it do the other required 12 updates? Or could that break something and not let my card be identified properly? (They are mainly beryl updates, with one xorg-fglrx driver update)

---

### Post by Waappu on 2007-03-13
> **NuklearToaster said:**
> I have only a couple questions, so I'll make this short.

I have ran the script, and after such, it returned this.

```
tux@tux-desktop:~$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
01:00.1 Display controller: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) (rev 01)
```

Now, before I [update my xorg]("http://ubuntuforums.org/showthread.php?t=373087"), would it be wise to let it do the other required 12 updates? Or could that break something and not let my card be identified properly? (They are mainly beryl updates, with one xorg-fglrx driver update)

Hi

Update system and then upgrade to Xorg 7.2

---

### Post by NuklearToaster on 2007-03-13
I've updated both. When I run 'beryl' it tells me that suppourt for two textures is missing, then it locks my x (something that has never happened before, I've always been able to 'beryl-manager' my way out of it). However, my card is listed as 3D support available?

---

### Post by Waappu on 2007-03-13
> **NuklearToaster said:**
> I've updated both. When I run 'beryl' it tells me that suppourt for two textures is missing, then it locks my x (something that has never happened before, I've always been able to 'beryl-manager' my way out of it). However, my card is listed as 3D support available?

Hi

Have you installed XGL ?

---

### Post by NuklearToaster on 2007-03-13
tux@tux-desktop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

The update is fglrx driver, from what I've been told I'm to keep this as far away from my ATi as possible. I have managed to get it working (half assed, mind you), with my card, but when I try and use XGL/AIGLX it gives me all sorts of problems, such as amending my xorg.conf to the point that I cannot load Ubuntu because of 'no screens'

---

### Post by Waappu on 2007-03-13
> **NuklearToaster said:**
> tux@tux-desktop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

(The update is fglrx driver, from what I've been told I'm to keep this as far away from my ATi as possible.)

You need uninstall that
```
sudo apt-get remove xserver-xgl
```

Remove also flgrx driver if it still exists in your system

---

### Post by NuklearToaster on 2007-03-13
Still getting the same error.

---

### Post by Waappu on 2007-03-13
> **NuklearToaster said:**
> Still getting the same error.

Hi

Did you restore all changes in xorg.conf before you ran script ?

---

### Post by NuklearToaster on 2007-03-13
Wait for it...

---

### Post by Waappu on 2007-03-13
> **NuklearToaster said:**
> How?

```
tux@tux-desktop:~$ sudo dpkg-reconfigure xorg-X11
Package `xorg-x11' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg-X11 is not installed
```

Is that the right command, even?

Hi

I think command is ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by trxDraxon on 2007-03-13
omg I love you, works like a charm.  I have been having so much trouble getting direct rendering and beryl working together and this did it perfectly.

Dell XPS laptop with a Mobility 9700 (wierd thing is ATI propritary driver picks it up at 9700, open source picks it up as 9600)

```
$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

```
$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes

```

```
$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
10351 frames in 5.0 seconds = 2070.052 FPS
10822 frames in 5.0 seconds = 2164.305 FPS
10646 frames in 5.0 seconds = 2129.057 FPS
10758 frames in 5.0 seconds = 2151.504 FPS
```

---

### Post by Waappu on 2007-03-13
> **trxDraxon said:**
> omg I love you, works like a charm.  I have been having so much trouble getting direct rendering and beryl working together and this did it perfectly.

Dell XPS laptop with a Mobility 9700 (wierd thing is ATI propritary driver picks it up at 9700, open source picks it up as 9600)

```
$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

```
$ glxinfo
name of display: :0.0
libGL warning: 3D driver claims to not support visual 0x4b
display: :0  screen: 0
direct rendering: Yes

```

```
$ glxgears -printfps
libGL warning: 3D driver claims to not support visual 0x4b
10351 frames in 5.0 seconds = 2070.052 FPS
10822 frames in 5.0 seconds = 2164.305 FPS
10646 frames in 5.0 seconds = 2129.057 FPS
10758 frames in 5.0 seconds = 2151.504 FPS
```


Hi

great =)

Did you upgrade to Xorg 7.2 ??

---

### Post by NuklearToaster on 2007-03-13
It works now (Apparently Option     AIGLX "true" didn't exist in my xorg.conf), but it's just a tad choppy, working at about 1000-1600 FPS. I still get this, though.

libGL warning: 3D driver claims to not support visual 0x4b

xserver-xorg (through synaptic manager) claims that it is at 7.2-0edgy5~3v1u

---

### Post by Umut Ya&#351;ar on 2007-03-16
First, thanks much. I used the script and it seemed to work.

But sometimes, &#305; am having freezing problem and I can not recover it without reset. When I typed "beryl" on terminal, it says;

```
Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x4b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

```

I guess there is a problem about that libGL. What do you think?

---

### Post by Umut Ya&#351;ar on 2007-03-17
Isn't there anybody to help?

---

### Post by Waappu on 2007-03-17
> **Umut Ya&#351 said:**
> Isn't there anybody to help?

Hi

Don't wory about warning
libGL warning: 3D driver claims to not support visual 0x4b
You just cant use water plugin because some features are missing from your card.

Try to disable water,snow,blur and Trailfocus plugins.

Try to upgrade to Xorg 7.2
[http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087)

What is your card model ?

---

### Post by Umut Ya&#351;ar on 2007-03-18
Thanks for your attention. My card is Radeon 9200 Pro...

I'am not sure how to make that upgrade by the way...

---

### Post by Waappu on 2007-03-18
> **Umut Ya&#351 said:**
> Thanks for your attention. My card is Radeon 9200 Pro...

Do you still have problems with Beryl?

---

### Post by Umut Ya&#351;ar on 2007-03-18
> **Waappu said:**
> Do you still have problems with Beryl?

:) No, thank you much. Your script and suggestions could help more than I expected. Thank you again...

---

### Post by Shibby73 on 2007-03-18
Hi guys I am quite a newb. I really don't know much about what I am doing or commands, so kinda need detailed information/instructions.

I am still trying to patch my evdo card a Sprint Pantech 500 and since I am lost with that I figured why not just use my broadband connection and atleast get my new ubuntu 6.10 install on my laptop ACER Travelmate 800LCi tweaked out with beryl.

I am running:
Dual boot Win XP
Ubuntu 6.10 Edgy
1.3GHz Intel Processor
ATI Mobility Radeon 9000 3D Graphic/64Mb RAM
256MB DDR Memory (although I upgraded this and don't remember to what a couple years ago)

when I run:
$ uname -r
2.6.17-11-generic

$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)

$ glxinfo | grep "direct rendering"
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

$ glxinfo | grep vendor
libGL warning: 3D driver claims to not support visual 0x4b
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

What steps should I be doing first?

Thank you for all of your time, hard work and knowledge.

-Steve (shibby73)

---

### Post by Waappu on 2007-03-18
> **Shibby73 said:**
> Hi guys I am quite a newb. I really don't know much about what I am doing or commands, so kinda need detailed information/instructions.

I am still trying to patch my evdo card a Sprint Pantech 500 and since I am lost with that I figured why not just use my broadband connection and atleast get my new ubuntu 6.10 install on my laptop ACER Travelmate 800LCi tweaked out with beryl.

I am running:
Dual boot Win XP
Ubuntu 6.10 Edgy
1.3GHz Intel Processor
ATI Mobility Radeon 9000 3D Graphic/64Mb RAM
256MB DDR Memory (although I upgraded this and don't remember to what a couple years ago)

when I run:
$ uname -r
2.6.17-11-generic

$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)

$ glxinfo | grep "direct rendering"
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes

$ glxinfo | grep vendor
libGL warning: 3D driver claims to not support visual 0x4b
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

What steps should I be doing first?

Thank you for all of your time, hard work and knowledge.

-Steve (shibby73)

Hi

I cant help you with evdo problem.

But if you want to install Beryl just follow this guide
[http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html)

---

### Post by Shibby73 on 2007-03-18
Ok so I followed the instructions.

But when I go to run beryl-manager

I get:

The location or file could not be found.

Like I said I am a total newbie.

Much appreciation for any help.

-Steve

---

### Post by Shibby73 on 2007-03-18
Well I got it to install and run.
Initially had the white screen of death, but fortunately it worked rather well after a reboot.
Problem is that often windows are empty with whitespace.
For example my Opera browser favorites drop-down was blank, I had to guess where the favorite for this present thread was located.  Then it suddenly came back.

Any ideas for a fix?

Best regards,

-Steve

---

### Post by Waappu on 2007-03-19
> **Shibby73 said:**
> Well I got it to install and run.
Initially had the white screen of death, but fortunately it worked rather well after a reboot.
Problem is that often windows are empty with whitespace.
For example my Opera browser favorites drop-down was blank, I had to guess where the favorite for this present thread was located.  Then it suddenly came back.

Any ideas for a fix?

Best regards,

-Steve

Hi

Did you upgrade to Xorg 7.2 ?
[http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087)

---

### Post by Shibby73 on 2007-03-19
Yes I followed all of the instructions.  I may have messed something up though (more than likely).

I will keep at it, but I am going on a trip in a few hours so while in the airport I will see if I can log on and get things working better, may switch to working with the EVDO card, but this beryl is kinda annoying with the glitch of not refreshing the windows unless I minimixe and then maximize them. 

-Steve

---

### Post by Shibby73 on 2007-03-19
Great...  I didn't do anything new.

I go to start-up in Ubuntu and get a blank screen (not a white one either).

I see the little startup bar in the middle of the screen it even has the beryl gem on it.
Then NOTHING... basically just a background screen.

I tried going into safe mode, I tried starting up the older kernal, no JOY.

Then I even tried a Live CD, it gets weird buffer errors.
So I guess I need to erase the whole install, good thing I still have XP which atlease is on another partition so I can still get online (with my EVDO at the airport etc).

I don't think I will be testing out this beryl thing ever again, just to be able to flip my screen like a cube.  I don't have free time to waste as a luxury, I will have to wait for others to pioneer (and well document) the way.

Thank you for the links however.

Best regards,

-Steve

---

### Post by Waappu on 2007-03-19
> **Shibby73 said:**
> Great...  I didn't do anything new.

I go to start-up in Ubuntu and get a blank screen (not a white one either).

I see the little startup bar in the middle of the screen it even has the beryl gem on it.
Then NOTHING... basically just a background screen.

I tried going into safe mode, I tried starting up the older kernal, no JOY.

Then I even tried a Live CD, it gets weird buffer errors.
So I guess I need to erase the whole install, good thing I still have XP which atlease is on another partition so I can still get online (with my EVDO at the airport etc).

I don't think I will be testing out this beryl thing ever again, just to be able to flip my screen like a cube.  I don't have free time to waste as a luxury, I will have to wait for others to pioneer (and well document) the way.

Thank you for the links however.

Best regards,

-Steve

Hi

See this guide. I think it's for same card you have
[http://ubuntuforums.org/showthread.php?t=291464](http://ubuntuforums.org/showthread.php?t=291464)

---

### Post by Jpfan017 on 2007-03-19
/home/jpfan01/ati-aiglx-beryl.sh: 76: KEY: not found
/home/jpfan01/ati-aiglx-beryl.sh: 141: Syntax error: "else" unexpected
jpfan01@Hobbes:~$ 

This is when first running the script. I'm not sure what KEY I would be missing...

---

### Post by Waappu on 2007-03-20
> **Jpfan017 said:**
> /home/jpfan01/ati-aiglx-beryl.sh: 76: KEY: not found
/home/jpfan01/ati-aiglx-beryl.sh: 141: Syntax error: "else" unexpected
jpfan01@Hobbes:~$ 

This is when first running the script. I'm not sure what KEY I would be missing...

Hi

Thanks. Script is now corrected.
Run command ```
sudo sh ~/.sysreset.sh
```and then run script again

---

### Post by x64Jimbo on 2007-03-22
> **Shibby73 said:**
> Great...  I didn't do anything new.

I go to start-up in Ubuntu and get a blank screen (not a white one either).

I see the little startup bar in the middle of the screen it even has the beryl gem on it.
Then NOTHING... basically just a background screen.

I tried going into safe mode, I tried starting up the older kernal, no JOY.

Then I even tried a Live CD, it gets weird buffer errors.
So I guess I need to erase the whole install, good thing I still have XP which atlease is on another partition so I can still get online (with my EVDO at the airport etc).

I don't think I will be testing out this beryl thing ever again, just to be able to flip my screen like a cube.  I don't have free time to waste as a luxury, I will have to wait for others to pioneer (and well document) the way.

Thank you for the links however.

Best regards,

-Steve
You likely have an unsupported ATI chipset like me. My Radeon Xpress 200M is completely unsupported by the open source driver, which is what this script uses. The big problem is that fglrx (the proprietary driver for ATI cards) doesn't support the way that AIGLX does compositing (built into X.org) so we're stuck in limbo. The driver that supports AIGLX doesn't work with our card, and the driver that works with our card doesn't support AIGLX. The only alternative is Beryl & XGL, but XGL is nowhere near the smoothness and un-hackishness of AIGLX, and is pretty much unusable in my opinion.

---

### Post by Shibby73 on 2007-03-23
> **x64Jimbo said:**
> You likely have an unsupported ATI chipset like me. My Radeon Xpress 200M is completely unsupported by the open source driver, which is what this script uses. The big problem is that fglrx (the proprietary driver for ATI cards) doesn't support the way that AIGLX does compositing (built into X.org) so we're stuck in limbo. The driver that supports AIGLX doesn't work with our card, and the driver that works with our card doesn't support AIGLX. The only alternative is Beryl & XGL, but XGL is nowhere near the smoothness and un-hackishness of AIGLX, and is pretty much unusable in my opinion.

I agree, it was unusable, and I was logging in and had an environment where I couldn't access anything.  Fortunately I started clicking on everything I could ... discovered at login the options tab in the lower left and had to boot into the terminal which typing aptitude showed me some interesting stuff.  Then I tried synaptic and unloaded beryl and Xorg references and fortunately that got me able to boot into the GUI where I could then work on other things.  I look forward to this working sometime in the future.  Now I need to work on EVDO support for my Sprint Pantech 500, none of the helps I have been using have helped ... yet - more than likely due to user error.

Best regards,

-Steve

---

### Post by Peti29 on 2007-03-23
> **x64Jimbo said:**
> You likely have an unsupported ATI chipset like me. My Radeon Xpress 200M is completely unsupported by the open source driver, which is what this script uses. The big problem is that fglrx (the proprietary driver for ATI cards) doesn't support the way that AIGLX does compositing (built into X.org) so we're stuck in limbo. The driver that supports AIGLX doesn't work with our card, and the driver that works with our card doesn't support AIGLX. The only alternative is Beryl & XGL, but XGL is nowhere near the smoothness and un-hackishness of AIGLX, and is pretty much unusable in my opinion.

Hmm. I have an Ati Radeon 9600XT - pretty old that is. Still, I use fglrx as it is much faster than AIGLX (on my machine). I don't really like XGL either but I can live with it without problem. Only thing is: if I want to watch a movie or use some 3D app (like games) I log into a simple Gnome session without XGL (and Beryl).

---

### Post by cprofitt on 2007-03-24
If you have tested this script please post
- did Beryl work
- modifications to script
- modifications to your /etc/X11/xorg.conf
- Upgraded to Xorg 7.2 Yes/No
- output of

[LIST]
[*]Beryl -- Worked
[*]Modifications to script -- None, other than one to make up for a mistake -- I removed your test to see if the script had been run before.
[*]Modifications to my /etc/X11/xorg.conf -- none yet, but want to try to get dual-head working now.
[*]Upgraded to Xorg 7.2 -- Not yet, but going too.
[*]Output - 01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)
[/LIST]

Thank you very much for your script. I truly think posts like yours should be made in to HOWTO documents and posted on a wiki.

I had tried to get this working myself (I am very noob to Linux) and failed to the point I loaded openSuSE because of their help documents being far superior to what I was finding here. Wading through layer upon layer of crap posts here on the topic ended when I found your post, but prior to that it was a painful experience.

Your script is well done so I was able to go in afterwards and review your steps.

I am curious if you have had success getting Beryl to run under the official ATI driver or not.

Thanks again!

---

### Post by Waappu on 2007-03-24
Hi

Thanks =) I'm glad that script help you.

I haven't tested beryl with official driver.
Using AIGLX is preferred on Edgy Eft because it is included with X.org on Edgy. 

But there is lot of guides for XGL and fglrx driver.

If you want to try use envy to install driver
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
and here is guide to install XGL
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL#Installing_Xgl_and_Beryl)

---

### Post by cprofitt on 2007-03-24
I am curious if the Nvidia script has been updated for Edgy as well -- it looks to be for Dapper.

---

### Post by Waappu on 2007-03-25
> **PrivateVoid said:**
> I am curious if the Nvidia script has been updated for Edgy as well -- it looks to be for Dapper.


For nvidia use envy to install diver and configure xorg.conf
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Then follow this guide to install Beryl
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Add_repositories](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#Add_repositories)

---

### Post by x64Jimbo on 2007-03-26
> **Peti29 said:**
> Hmm. I have an Ati Radeon 9600XT - pretty old that is. Still, I use fglrx as it is much faster than AIGLX (on my machine). I don't really like XGL either but I can live with it without problem. Only thing is: if I want to watch a movie or use some 3D app (like games) I log into a simple Gnome session without XGL (and Beryl).
Age of the video card doesn't really matter as much with Beryl. It is not a demanding 3D app. What DOES matter is the chipset that the card uses. Some are well supported by the open source driver, and others are not. fglrx is the proprietary, closed-source driver from ATI, and AIGLX is the extension that is built into Xorg that allows 3D compositing to be built into the X server. You can't really compare those two because they don't do the same thing. XGL is not an integrated solution, and it requires you to have separate sessions in Gnome for 3D and Non-3D. It's supposed to be something you can switch on and off easily, and that is why AIGLX is the future of desktop 3D compositing.

---

### Post by Cloudy on 2007-03-30
Beryl works! Yay! I'm running it on a Dell Latitude C640.

No mods to the script or xorg.conf, upgraded xorg when the script asked, aaaaand

```

travis@travis-laptop:~$ lspci | grep 'ATI'
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
travis@travis-laptop:~$ 

```

---

### Post by Campingman on 2007-03-31
Thanks Waappu
Three times I have tried, three times It has screwed up.  This script worked like a charm, Beryl all up and running for the first time.  No slow down in Firefox scrolling either.

Thank you, Thank you, Thank you!

---

### Post by Oen386 on 2007-04-24
:(

Xorg 7.2 appears not to work in Feisty. Now I have to wait.

---

### Post by Waappu on 2007-04-24
> **Oen386 said:**
> :(

Xorg 7.2 appears not to work in Feisty. Now I have to wait.

Feisty has Xorg 7.2
[https://wiki.ubuntu.com/7.04Tour#head-13cd805df19239fb07f50d506d6ce5d28805b1eb](https://wiki.ubuntu.com/7.04Tour#head-13cd805df19239fb07f50d506d6ce5d28805b1eb)

---

### Post by Paqman on 2007-04-24
Fantastic, just installed completely hassle-free with this script and it's how-to. Great work!

---

### Post by Oen386 on 2007-04-26
> **Waappu said:**
> Feisty has Xorg 7.2
[https://wiki.ubuntu.com/7.04Tour#head-13cd805df19239fb07f50d506d6ce5d28805b1eb](https://wiki.ubuntu.com/7.04Tour#head-13cd805df19239fb07f50d506d6ce5d28805b1eb)

I never said it didn't have 7.2, I said it didn't work for me.

"Xorg 7.2 appears not to work in Feisty. Now I have to wait."

I can not get Beryl or any 3d working correctly after updating to Feisty. Not sure what got changed. :(

---

