---
title: "Lost title bar in Xgl/Beryl"
date: 2006-11-26
forum: Desktop Effects &amp; Customization
---

### Post by richardgundersen on 2006-11-26
Hi

I love Ubuntu and just upgraded to Edgy. I've also got Xgl/Beryl working, which has to be the coolest thing I've seen for ages (I really can't see why anyone would bother with Vista now!)

But, every now and again, I stupidly mash the keyboard somehow and my windows' title bars disappear. Its got something to do with the ALT-CTRL-<insert,page-up/down> keys I think. I can't figure out which ones.

Please, someone tell me how to get them back without restarting X - it has to be a simple keystroke combination!

PS in case its of use to anyone, use Automatix instead of EasyUbuntu for now (for Edgy). Took me a while to realise it didn't work yet (although I'm sure it will v soon). 

Thanks!

Richard

---

### Post by finferflu on 2006-11-26
I had the same problems, I don't think it has to do with the keyboard, but must be some sort of bug, and sorted them in this way:

```
killall -9 emerald
```

Then go on the beryl-manager in your taskbar and select Restart windows decorator (or something like that).

Hope it helps

---

### Post by Portable_Jim on 2006-11-30
Typeing  ```
metacity
``` may work

(is it similar to [http://www.ubuntuforums.org/showthread.php?p=1825559](http://www.ubuntuforums.org/showthread.php?p=1825559)???)

---

### Post by bmathis on 2006-11-30
i had the same problem and it turns out the window was moved up and under the  menu panel. Right click the app on the window list panel and click on Move, then move it down a little until the title bar is visible.

---

### Post by ashmew2 on 2007-02-17
try Beryl instead of Compiz!

---

### Post by ajesh on 2007-03-26
Typing "metacity --replace" worked for me.

I still don't know what key stroke caused it. My 9 month daughter was typing randomly on the keyboard when this occurred.

---

### Post by ~SkyBlue~ on 2007-04-21
To all beryl newb out there (including me), I just found the solution of this missing decoration (titlebar)..

Check your settings in ~/.beryl, make you have the decoration plugin enabled :

```
[decoration]
a    plugin_enabled = true

```

This looked like a silly problem but took me about 3hrs to solve :confused: . Hope this helps

---

### Post by disc on 2007-05-09
I have this same problem, and haven't found a solution yet. I can switch back to Metacity, but whenever I load Beryl or Compiz, the titlebar disappears. Not only this, but I noticed that when I open a terminal, the text doesn't appear(a plain white window comes up) until I switch back to Metacity. I edited my ~/.beryl/settings to enable the decoration plugin, but no luck. I can live with using keyboard shortcuts to manage my windows, but I wonder why this also affects the terminal.

---

### Post by Sakumo on 2007-05-10
I had the same problem and this is what helped me: 

[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

The command 

sudo nvidia-xconfig --add-argb-glx-visuals --composite

was the trick.

---

### Post by montgoss on 2007-05-20
I'm having this issue too.  But none of the suggested fixes work.  The only thing that kinda works is changing the window manager to Metacity via the red diamond.

This is not a solution.  This is a workaround.  Where's the fun in Beryl if I'm still using the Gnome window manager?

Some background.  The root of the disappearance was me running nvidia-settings.  I think that overwrote my xorg.conf file and erased some vital setting Beryl needed.  Any idea what that could be?

---

### Post by jacquesvn on 2007-05-21
> **montgoss said:**
> I'm having this issue too.  But none of the suggested fixes work.  The only thing that kinda works is changing the window manager to Metacity via the red diamond.

This is not a solution.  This is a workaround.  Where's the fun in Beryl if I'm still using the Gnome window manager?

Some background.  The root of the disappearance was me running nvidia-settings.  I think that overwrote my xorg.conf file and erased some vital setting Beryl needed.  Any idea what that could be?

Not sure if you have double checked this but found that this was my problem:

Firstly the  [Option         "AddARGBGLXVisuals" "True"]  Originally fixed my problem - so make sure you have this under the device entry.

Next in changing my conf file to get my tv out to work I used a DefaultDepth  of 16 with the corresponding entry. After this no more title bar - changing it to 24 and updating the relevant entry to 24 fixed the problem. Not sure why the difference between 16 and 24 but there you have it.

So in a nutshell:

Ensure Option         "AddARGBGLXVisuals" "True" exists in Device
Ensure Depth Value of 24 e.g. 
Section "Screen"
.... 
    DefaultDepth    24 
    SubSection     "Display"
        Depth      24 
        Modes      "1024x768"
    EndSubSection
....
EndSection

Hope this worked - else post your conf file and lets have a look at it.

Cheers :)

---

### Post by montgoss on 2007-05-22
Adding Option "AddARGBGLXVisuals" "True" manually to my xorg.conf file fixed it.  Funny that the command that supposedly did that didn't make a difference...

---

### Post by Nehvrook on 2007-05-22
Hi. I just installed Beryl and I'm having a similar problem. Whenever I have Beryl enabled I loose my title bars with the cross and minimise buttons etc. It's not such a big deal since I only inted to use Beryl ocasionaly but I'd love to know how to fix it.
When i switch the window manager to metcity I get my bars back, but as far as I can tell this is the same as turning Beryl off since none of the effects work.
I tried editing the beryl config file in /home/user/.beryl but that didn't work. There's a suggestion in this thread to add something to xorg.conf but I'm not sure how to do that.

Does anyone know how to get the title bars back with beryl still enabled?

---

### Post by jkflying on 2007-05-22
Make sure you have 'emerald' and 'emerald-themes' installed. They should really be dependancies of the package 'beryl'

---

### Post by Nehvrook on 2007-05-23
I have emerald and emerald-themes at the newest version (I just did an apt-get install and they were already there)

I also just noticed that the terminal doesn't work, it just shows up as a white box. 

Any idea's?

EDIT: Sorry this problem has apparently fixed it's self. Terminal and title bars are here now and working perfectly :)

---

### Post by Ub1476 on 2007-05-23
The newest version of Beryl  (0.2.1) is a little buggy, so you should downgrade to v. 0.2.0 if you don't find another solution. This worked for me at least..

---

### Post by DUNC4N on 2007-05-23
I'm having the same issue. 

I tried to uninstall beryl/emerald, now I have the same issue, but I can't click the use medacity (spelling) and see my title bar buttons. 

Terminal is white too. Frustrating to say the least.

I feel like I should just re-install.:(

---

### Post by KyleBrandt on 2007-05-23
This is kind of a weak solution, but it worked for me.  I killed Beryl, Then Enabled Compiz (Aka, Turned on "Desktop Effects"), Then Disabled Compiz (The same way), Then ran Beryl again.  This got the title Bars back.  Let me know if this works for anyone, and if it does if anyone knows why it works.  -Kyle

---

### Post by bambit on 2007-05-27
> **Miles800 said:**
> This is kind of a weak solution, but it worked for me.  I killed Beryl, Then Enabled Compiz (Aka, Turned on "Desktop Effects"), Then Disabled Compiz (The same way), Then ran Beryl again.  This got the title Bars back.  Let me know if this works for anyone, and if it does if anyone knows why it works.  -Kyle

Tried this to the letter, didn't work. It may have something to do with the video card on the machine. I have an NVIDIA GeForce4™ 420 Go on a Toshiba Satellite Pro M10 -- and using Beryl on it has been problematic from the start.

I have also placed the codes in  xorg.conf to no avail. I'm stuck with Metacity and would like to have more than two desktops. Looks like Beryl isn't the answer for me.

---

### Post by bambit on 2007-05-27
> Ensure Option "AddARGBGLXVisuals" "True" exists in Device
Ensure Depth Value of 24 e.g.
Section "Screen"
....
**DefaultDepth 24**
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
....
EndSection

This worked like a miracle for me! All the while I thought I had put in all the suggested codes in xorg.conf, only to find out that my DefaultDepth was at 16 ! Promptly changed it to 24 - restarted my laptop to be sure, and voila!

Beryl!

---

### Post by spyke01 on 2007-05-28
my xorg.conf is correct, and ive also uninstalled and reinstalled beryl, beryl-manager, emerald, emerald-themes, and removed kib-dock, ive also tried doing killall -9 emerald to no avail, kind of looks like emerald never starts, any ideas?

ok i ran beryl-manager from the menu and everything started working

---

### Post by mrklaw on 2007-06-01
> **Sakumo said:**
> I had the same problem and this is what helped me: 

[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

The command 

sudo nvidia-xconfig --add-argb-glx-visuals --composite

was the trick.

Thanks for this. This fixed my problem after I had been banging my head against it for a while.

---

### Post by Eoghanalbar on 2007-06-03
Don't know if anyone has posted this already, but I fixed the same problem for me by **enabling window decoration under visual effects.**

I would guess that there are other, more difficult causes for it, though.

---

### Post by Bostonian on 2007-06-23
> **disc said:**
> I have this same problem, and haven't found a solution yet. I can switch back to Metacity, but whenever I load Beryl or Compiz, the titlebar disappears. Not only this, but I noticed that when I open a terminal, the text doesn't appear(a plain white window comes up) until I switch back to Metacity. I edited my ~/.beryl/settings to enable the decoration plugin, but no luck. I can live with using keyboard shortcuts to manage my windows, but I wonder why this also affects the terminal.

I have the same problem. My xorg.conf looks fine (AddARGBGLXVisual true, DefaultDepth 24), and beryl was running fine this morning. I'm not quite sure what I changed. I've tried killall -9 emerald, beryl and compiz and then reloading, i've tried restarting. not sure hwat else to do.

when i run beryl in a terminal (my terminal comes back when i use metacity instead of beryl)
i get
```
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

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2600020 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2600020 to texture
beryl: No GLXFBConfig for depth 32
beryl: Couldn't bind redirected window 0x2600020 to texture
beryl: No GLXFBConfig for depth 32

ect.

```
and when the focus goes to the terminal
```

[IPCS]: Unable to change values during paint operations!
[IPCS]: Unable to change values during paint operations!
[IPCS]: Unable to change values during paint operations!
[IPCS]: Unable to change values during paint operations!
[IPCS]: Unable to change values during paint operations!

```

while grabbing this info to post, metacity stopped rendering the window decorations. quick reload fixed it though.



EDIT: found solution here [http://ubuntuforums.org/showthread.php?p=2900038#post2900038](http://ubuntuforums.org/showthread.php?p=2900038#post2900038)



sudo nvidia-xconfig --add-argb-glx-visuals

was putting

Option "AddARGBGLXVisuals" "True"
into the "screen" section.

I put

Option "AddARGBGLXVisuals" "True"
Option "AllowGLXWithComposite" "True"

---

### Post by nixego on 2007-07-11
Hello all;

First off, I'm a total linux newb, no really, I just popped out of the womb. Yea, yea, "Beryl is not for beginners" - I've heard it all before - but the only reason I installed kubuntu is to make my desktop as sexy as f*cking possible. I'm pretty experienced with windoze PC's and am VERY curious about linux so I dove right in. 

Essentially, I want to install this theme cause it looks oh so sexy. 
[http://www.kde-look.org/content/show.php/Kore+Suite?content=54701](http://www.kde-look.org/content/show.php/Kore+Suite?content=54701)

I'll give you guys all the info I know how to give, so bear with me.

I have an nVidia driver that I installed using Automatix. I am using Kubuntu 7.04 x64 with a Geforce 6150. 

I installed Beryl and I see the little red diamond in my taskbar.

When I switch to the windows manager to Beryl, my titlebars disappear and I'm unable to move my windows. My terminal window does NOT become white as with some people. Ctr+Alt+Left(Right) moves the 'cube' so at least some of Beryl works ok. 

When I type "beryl" into the terminal window I get this:

```
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

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
X connection to :0.0 broken (explicit kill or server shutdown).
```

And this is how my xorg.conf file looks like. 

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:37:58 PST 2007

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
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation C51 [Geforce 6150 Go]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation C51 [Geforce 6150 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

I've tried some suggestions, like this one:

[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

but everything under "Adding Source list" I simply don't understand and more detail is required.

Some say I should edit xorg.config but I am having trouble with write access, even after following some suggestions on that. 

Can someone point me in the right direction? Let me know of any more info I can give to help you help me. 

But please remember to make the instructions as if it were for an infant; I'm terrible at the terminal.

Thanks!!!

---

### Post by Aurixious on 2007-07-12
Ok I had the same problem but ended up fixing this.  I'm a linux noob too but the solution seemed obvious to me.  I wanted to change my resolution from 1024X768 to 1152X864 but the latter res wasn't an option under sys>prefs>screen res.  I have an nvidia generic driver so I did a file search for "nvidia" and found the file "nvidia-settings".  It seems that when you double click it from the search app it doesn't launch so I checked the file path and found it through "computer".  Once you double click it from here it does launch.  Seems strange to me that it wouldn't launch from the search app but anyway the nvidia settings app launched and I went to "x server display configuration".  Changed to the res I wanted and clicked apply.  Clicked to accept the settings.  

[SIZE="5"]DON'T CLICK ON THE "SAVE TO X CONFIGURATION FILE" BUTTON![/SIZE]

This replaces everything in your xorg.conf file!  This is where I traced the problem back to because I was able to get Beryl to work at the lower res but I didn't like that res.  What I did to fix my problem at my new res was this:

[SIZE="5"]NOTE:BACKUP YOUR XORG.CONF FILE BEFORE DOING THIS![/SIZE]

You must be logged in as root from the login screen.  To do this go to sys>admin>login window>security (tab)> check "allow local system administrator login".

Then: sys>admin>users and groups>click on root>click on properties> change "user password" and "confirmation" to what ever pass you want.

Finally: Logout>type "root" for the user name>then type the pass you just made up. 

(only if you have beryl as a startup app under root) DO ALL THESE CHANGES IN METACITY!

1. Once in the nvidia-settings app I went to "x server display configuration". 

2. Clicked on "save to x configuration file"

3. Clicked on "show preview" 

[SIZE="5"]WARNING DON'T EVER CLICK "SAVE" FROM THIS MENU!!![/SIZE]

From here I copied some code and pasted it to my xorg.conf file

This is what I did:

6. Copied the "HorizSync" and "VertRefresh "numbers to my xorg.conf file therefore replacing them.

7. Copied this entire section:

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GT"
EndSection

and replaced the one in the xorg.conf file which looked like this before replacing:

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

8. Under [SIZE="3"]Section "Screen"[/SIZE] I changed [SIZE="3"]Device         "Generic Video Card"[/SIZE] to [SIZE="3"]Device         "Videocard0"[/SIZE].  The reason for this is to keep the names the same or else it will become confused and not work.

9. Copied this line which was right under [SIZE="3"]DefaultDepth 24[/SIZE]:

Option         "metamodes" "1152x864 +0+0; 800x600 +0+0; 640x480 +0+0"

and pasted it under [SIZE="3"]DefaultDepth 24[/SIZE] in my xorg.conf file.  It seems that the first res, wich in my case is 1152x864, is the current res being used so don't panic if yours is different.  

10. Copied 

Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"

which is underneath [SIZE="3"]Depth     24[/SIZE] and pasted/replaced below [SIZE="3"]Depth     24[/SIZE] in my xorg.conf file. 

11. This is all the copying you need to do from nvidia's preview.  Click "Cancel".  Click "quit" twice.

12. [SIZE="5"]Save all your changes to "xorg.conf"![/SIZE]

13.  Press ctrl+alt+back space

14. Login to root again and see if your res is still there and if you have your title bar back.  If you have your title bar back but not your res then go to sys>pref>screen res> and your res should be listed in there.  When prompted to keep that res click yes.  Log out then log back into root to see your new res and beryl are working :).  Log out then log into your real user name and select your res from sys>pref>screen res.  Log out then back into your real user name to see your new res and beryl are working :).

I hope that works for you guys since it has for me.  And notice we didn't even touch the terminal once ;).

---

### Post by jeskuruvilla on 2007-08-28
One point to note and already discussed in the forums here ([http://forum.compiz-fusion.org/showthread.php?t=3578](http://forum.compiz-fusion.org/showthread.php?t=3578)) is that all the programs have to be the same version. I fixed the same problem by uninstalling emerald(0.52) and installing heliodor and aquamarine window decorators using synaptic. Hit Ctrl+Alt+backspace. Go to the beryl diamond, click on beryl window manager and the click on heliodor window as window decorator.
Hope this helps anybody who has exhausted all options from above.

---

### Post by vyralsurfer on 2007-09-09
My problem was solved in a rather hackish way...

I had the same issue of not having a titlebar. I had installed Compiz following a guide for Gentoo Linux (my old distro), and have compiz being launched from a script.

I have the KDE window manager environment variable set in /etc/envronment like so:
```
KDEWM=/usr/local/bin/compiz-fusion
```

At /usr/local/bin/compiz-fusion lies a script with the following contents:
```
compiz --replace ccp --sm-disable
```

...so when KDE starts, compiz replaces KDE's default window manager.

What solved my problem was to run the command "emerald" from a terminal window under X, however I had to leave that window open, so I edited my script:
```

daemon -- compiz --replace ccp --sm-disable
emerald

```

What this did was launch compiz, like it did before, except it then put it in the background and start emerald afterwards. Only problem now is that I cant *change* the window decorations :)

---

### Post by iamah on 2007-09-09
> **Sakumo said:**
> I had the same problem and this is what helped me: 

[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

The command 

sudo nvidia-xconfig --add-argb-glx-visuals --composite

was the trick.

thanks, that worked for me too.. I've tried many things but only this worked... I even tried manually  adding the variable to xorg.conf...

---

### Post by adza on 2007-10-09
I have tried all of these solutions posted but alas, a solution still evades me... so after starting beryl in the terminal i see that i have 20070319 version of beryl but 20061011 of the beryl-plugin and this is causing a conflict... question is though, how do i ensure to get the right version of beryl plugin???


****Edit*** Turns out i've found a much better solution than beryl, and that is compiz fusion... great how-to can be found [here]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion")

---

