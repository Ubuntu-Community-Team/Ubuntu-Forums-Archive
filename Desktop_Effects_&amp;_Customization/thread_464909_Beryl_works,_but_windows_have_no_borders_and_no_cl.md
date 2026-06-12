---
title: "Beryl works, but windows have no borders and no close/minimize buttons"
date: 2007-06-05
forum: Desktop Effects &amp; Customization
---

### Post by mikledet on 2007-06-05
I installed beryl on Ubuntu 7.04, installation seems to work, since beryl-manager is up and running, and I get the cube effect and some other stuff.  The problem is that the windows are drawn without its edges like in the top right hand corner there's no 'X' or ' _ '  buttons to close/minimize the window.  Also I can't move the windows around.  Terminal window comes all messed up and I can't see what's written there.  Help...

---

### Post by Hund on 2007-06-05
Do you have Nvidia?
If you do, try this:

sudo nvidia-xconfig --add-argb-glx-visuals

and then

Ctrl + Alt + Backspace to restart X.

---

### Post by nwgray on 2007-06-05
> **Hund said:**
> Do you have Nvidia?
If you do, try this:

sudo nvidia-xconfig --add-argb-glx-visuals

and then

Ctrl + Alt + Backspace to restart X.

Hund
   I've had the same problem since going to 7.04. I just tried your fix above - no change. Any window I open up is immediately drawn to the upper left side and very top. No handles, controls, or anything. There's no title bar to grab either.

---

### Post by douseej85 on 2007-06-05
Are these windows the normal Ubuntu ones. or has the Emerald theme been changed as well.?

Do you get any benefit from changing to a different theme in Emerald?

Only asking because I install Ubuntu 7.04 last night and had a challenge getting my Nvidia card to work properly...One driver didn't give me max res, the other gave the right res but damaged my OpenGL, and the last (which is the most recent) worked fine.

In the end I used nvidia-glx-new.....

Have you got any more info, like your setup/xorg.conf/glxinfo

---

### Post by mikledet on 2007-06-05
> **Hund said:**
> Do you have Nvidia?
If you do, try this:

sudo nvidia-xconfig --add-argb-glx-visuals

and then

Ctrl + Alt + Backspace to restart X.

I do have nVidia and I used this: [http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html]("http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html")
to install beryl.
Changing themes doesn't do anything as well.  For me the windows (firefox for example) starts up maximized, and I can only minimize it via hot-keys or the taskbar.  Terminal opens in the bottom left, can't be moved, resized or minimized, and it views as a blank white window.  It's not stuck though, because when I shut beryl down I can see everything I typed there.

---

### Post by monstermunch on 2007-06-05
Don't ask me why, but if you're using KDE, do a "killall kdesktop" before starting beryl and/or try running beryl with the failsafe windows manager. Make sure your card is set to 24bit colour too. Worked for me.

---

### Post by Balistic on 2007-06-05
I have the same problem, when I type "beryl-manager" in the terminal I get an error message saying:

"beryl: No GLXFBconfig for depth 32"  and
"beryl: Couldn't bind redirected window 0x2800.. to texture"

Is this related to the problem? and if so how do I solve it?

---

### Post by Cresho on 2007-06-05
I just read a couple of your posts.  you have a 7900go nvidia but you where asking about temp (not related to this topic)

1. anyway, im gona post how I installed my drivers.

sudo apt-get install nvidia-glx nvidia-kernel-common

2. then this part is important to get the nvidia working.  Use nvidia instead of generic.

sudo dpkg-reconfigure xserver-xorg

3. nvidia-settings in terminal to get the nvidia settings.  you can also vrete one in the menu with by adding this cammand.

4. enabling aa at startup.

startup sequence to run "nvidia-settings -l"(copy and paste this command) before beryl - this will turn on the settings and can be setup in System->Preferences->Sessions

Now for Beryl.  This is the way I managed to get it working and fixing the border issue which was giving me problems.

1. I used add and remove program to install both beryl applications.

2.  this part is for the vanishing borders.
sudo gedit(do this after you have your xorg configured.)  if you reconfigure, this part vanishes.
/etc/X11/xorg.conf in the &#8220;Device&#8221; section:

Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

3. to auto load, put in "beryl-manager" in the prefferences-> sessions.

4.
hmm....There are tons and tons of other stuff to get you startd.  ahh here is one.  under synaptic, install emerald and emerald themes.  these are the beryl border themes.

5.  make sure you exit the desktop or reboot for this to take effect.

---

### Post by alex30002 on 2007-06-16
> **Hund said:**
> Do you have Nvidia?
If you do, try this:

sudo nvidia-xconfig --add-argb-glx-visuals

and then

Ctrl + Alt + Backspace to restart X.

this worked for me. thanks 
i`m running 7.04 64bit on core 2 duo e6300

---

### Post by orb9220 on 2007-06-16
Also try and disable the benchmark plugin in extra's.
This has caused beryl to crash lately If I enabled it then beryl crashes.

Make sure you have Launch fall back manger if beryl crashes checked in beryl right click selections.

---

### Post by SLA_leandrin on 2007-06-20
I have the same problem, but none of this solutions worked for me yet. I'll keep trying of course...

---

### Post by Mizarus on 2007-06-21
> **Hund said:**
> Do you have Nvidia?
If you do, try this:

sudo nvidia-xconfig --add-argb-glx-visuals

and then

Ctrl + Alt + Backspace to restart X.
this partialy worked for me, i can now see the windows title bar but i still cant move them, any ideas on how i could fix that? i had the exact same issue then the TC

edit> fixed the "move window" box was unchecked (sandly enough yes that was why i coudnt move the windows)

---

### Post by Bostonian on 2007-06-23
> this part is for the vanishing borders.
sudo gedit(do this after you have your xorg configured.)  if you reconfigure, this part vanishes.
/etc/X11/xorg.conf in the “Device” section:

Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

this worked for me... the command

sudo nvidia-xconfig --add-argb-glx-visuals

was putting     

Option         "AddARGBGLXVisuals" "True"
into the "screen" section. 

I put

Option         "AddARGBGLXVisuals" "True"
Option         "AllowGLXWithComposite" "True"

into the "Device" section, hit Ctrl+Alt+Backspace and everything started working again.

thanks.

---

### Post by qirun on 2007-06-28
> **Cresho said:**
> I just read a couple of your posts.  you have a 7900go nvidia but you where asking about temp (not related to this topic)


2.  this part is for the vanishing borders.
sudo gedit(do this after you have your xorg configured.)  if you reconfigure, this part vanishes.
/etc/X11/xorg.conf in the “Device” section:

Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

.

Hi,

I have same problem but mine is using Mobile Intel® 945GM Express Chipset. Is it your work around will be working on those chipset?
Most of the solution that I found on the web is is working for Nvidia Chipset. Can you hel me to troubleshoot with this kind of chipset?

Thanks, really appreciated your helps..

---

### Post by sagara on 2007-07-28
Tried all the solutions posted here... nothing worked :(
I have to manually **shade** all my windows for my max/min/close buttons to reappear.

Any other suggestions?

---

### Post by ilkkal on 2007-08-01
I have the same problem with Intel GMA X3000.

---

### Post by da644 on 2007-08-09
Hi All.

I had exactly the same issue. Tried all the thing above and nothing worked. I fixed it by installing  Beryl Manager and running it via that instead of running beryl directly.

Kind regards,

Andrew.

---

### Post by newdamage1 on 2007-08-09
I had a the same error pop up on me while I was first trying to get it to work. What did the trick for me was changing the color depth to 32, bit 15,16,24 left me border-less. Probably not your issue, but I figured I suggest none-the-less.

Kelly

---

### Post by Twitch3z on 2007-11-02
I'm also having the disappearing window border issue. I've just installed Ubuntu, using the stock options, for the first time today after downloading Gutsy Gibbon for AMD64. I was able to get my dual-screen setup working after a couple of initial hurdles using nvidia-settings; I have them configured in TwinView and being run by an NVIDIA 7600GT, using whichever version of the proprietary driver the automatic Ubuntu Update got for me (according to the settings, it's 100.14.19). I'm running Gnome. 

When I download and install Beryl, I can use Compiz alright, and Emerald works fine with Compiz, but when I switch to Beryl the window title bars and borders disappear. I can move windows by right-clicking on the taskbar? and selecting "Move", then dragging the mouse. All the other features that I'm aware of seem to be working just fine. 

I've tried some troubleshooting. My xorg.conf file has been edited to look like this:
 
> 
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:53 PDT 2007

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

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL 2005FPW"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2005FPW"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "DELL 2005FPW"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1680x1050 +0+0, DFP-1: nvidia-auto-select +1680+0; DFP-0: 1280x1024 +0+0, DFP-1: nvidia-auto-select +1280+0; DFP-0: 1152x864 +0+0, DFP-1: nvidia-auto-select +1152+0; DFP-0: 1024x768 +0+0, DFP-1: nvidia-auto-select +1024+0; DFP-0: 800x600 +0+0, DFP-1: nvidia-auto-select +800+0; DFP-0: 640x480 +0+0, DFP-1: nvidia-auto-select +640+0"
EndSection


I've rebooted the X Window System using ctrl-alt-backspace, as well as the entire computer, to no avail. I've tried completely removing Beryl using apt-get remove and apt-get clean followed by manually deleting some directories (based on another post) and reinstalling it and the issue replicates exactly. I've also at various stages tried forcing the Rendering Path to Copy, which didn't fix it.

I also read that running metacity --replace causes the borders to redraw, though it seems intuitively to me that that should just replace Beryl with Metacity as the window manager, though I'm new to Linux so I could be way off base. Either way, this does not work for me. The output from metacity --replace is:
> 
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.


For further debugging notes, the beryl --replace output with beryl already running is:
> 
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.4)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.4)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 141 requests (140 known processed) with 0 events remaining.



To reiterate the important details:
[LIST]
[*]**No Window Borders or Title Bars in Beryl**
[*]Ubuntu 7.10 Gutsy Gibbon Fresh Install from LIve CD using all the default options
[*]NVidia 7600GT PCIx16 Video Card with two Dell LCDs attached, running driver 100.14.19 (the latest that Ubuntu automatically downloaded)
[*]Latest version of Beryl
[*]Rendering Path -> Copy does **not** resolve issue
[*]Adding various lines to xorg.conf does **not** resolve issue
[*]Emerald works fine with Compiz
[*]Compiz works fine
[*]Metacity works fine but cannot --replace with Beryl running
[*]beryl --replace ends with some error, see above
[/LIST]

I'd really like to get Beryl working as I'm excited about replacing the Windows XP Pro / MCE2005 dual boot on my machine with Ubuntu, as opposed to upgrading to Vista, but can't seem to get beryl working! (Or my soundblaster X-Fi, but that's a whole different and notorious kettle of fish). Any help would be appreciated, as I've already tried just about everything that's I could readily find. I've been trying to debug this thing for several hours now to no avail. Thanks!

---

### Post by ruibernardo on 2007-11-10
> **Hund said:**
> Do you have Nvidia?
If you do, try this:

sudo nvidia-xconfig --add-argb-glx-visuals

and then

Ctrl + Alt + Backspace to restart X.

I had done this in Feisty and, after I upgraded, I had to do it again in Gutsy to get the borders on the windows and the cube.

Thanks

---

