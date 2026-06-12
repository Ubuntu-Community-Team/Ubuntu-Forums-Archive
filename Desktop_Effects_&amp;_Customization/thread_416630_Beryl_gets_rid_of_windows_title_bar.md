---
title: "Beryl gets rid of windows title bar"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by Nano on 2007-04-21
It seems that it all works ok except that it get rids of the title bar, which I use, of course, to drag windows, minimize and close.

Am I the only one out there having this problem?

---

### Post by Compyx on 2007-04-21
Unfortunately not.

Make sure you have
```

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24
``` in your Screen section of /etc/X11/xorg.conf.

You can either hand-edit xorg.conf or use this command to set AddARGBGLXVisuals:
```
sude nvidia-xconfig --add-argb-glx-visuals
```,
then restart X and see if it works.

---

### Post by Nano on 2007-04-21
> **Compyx said:**
> Unfortunately not.

Make sure you have
```

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24
``` in your Screen section of /etc/X11/xorg.conf.

You can either hand-edit xorg.conf or use this command to set AddARGBGLXVisuals:
```
sude nvidia-xconfig --add-argb-glx-visuals
```,
then restart X and see if it works.

Ok, dude, how much do I owe you? :D
It works perfectly now.

Thanks a lot!

---

### Post by ronocdh on 2007-04-21
Worked like a charm!! Thank you!

---

### Post by ronocdh on 2007-04-21
Unfortunately I lose the title bar every time I start Beryl Manager. =( If I restart X, though, it I'm fine everywhere... until I start BM. Any ideas?

---

### Post by Compyx on 2007-04-21
In Beryl Manager, check Visual Effects -> Window Decoration: this should be enabled.

---

### Post by ronocdh on 2007-04-21
> **Compyx said:**
> In Beryl Manager, check Visual Effects -> Window Decoration: this should be enabled.
Thank you for the reply. I have tried this, and yet still when I start Beryl Manager I lose the title bar on all windows. I have tried just checking the box beside Apply Transparency, and also checking that in addition to Draw Shadows and Mipmap (on the next tab).

=(

---

### Post by serialdae on 2007-04-21
Right click on beryl manager - window decorator - select emerald

then click reload window decorator

---

### Post by ZeBadger on 2007-04-21
I had the problem where the window decorators were missing.

I took an extreme step and deleted the .gconf and .gconfd directories in my home dir.
When I logged out and in again, started Desktop Effects and had no problems.

---

### Post by teknorah on 2007-04-21
> **Compyx said:**
> Unfortunately not.

Make sure you have
```

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24
``` in your Screen section of /etc/X11/xorg.conf.

You can either hand-edit xorg.conf or use this command to set AddARGBGLXVisuals:
```
sude nvidia-xconfig --add-argb-glx-visuals
```,
then restart X and see if it works.

Did the terminal command, works perfectly now!  Thx!

---

### Post by atbnet on 2007-04-22
> **Compyx said:**
> Unfortunately not.

Make sure you have
```

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24
``` in your Screen section of /etc/X11/xorg.conf.

You can either hand-edit xorg.conf or use this command to set AddARGBGLXVisuals:
```
sude nvidia-xconfig --add-argb-glx-visuals
```,
then restart X and see if it works.

Thank you thank you! I thought I was going to have to reinstall beryl or redo my xconfig completely because I kept losing my title bar. This fixed it.

---

### Post by hackenoff on 2007-04-22
OMG!!!!  Thank you so much for this post.....  I was trying everything to fix this and a simple little fix like this was all I needed.

---

### Post by Equilux on 2007-04-22
Thx....that solves my issue as well, but I wonder why this issue can occour...... I'd expected it to run smoother out of the box.

---

### Post by coolcalt on 2007-04-24
> **Equilux said:**
> Thx....that solves my issue as well, but I wonder why this issue can occour...... I'd expected it to run smoother out of the box.

Go put your head back in the sand.  Last time I checked beryl wasn't the default.  It takes a huge effort to bring this much kick microsoft butt to the table.   Bugs creep in.  Do something helpful next time, instead of moaning about it.

Hey it fixed my problem too.  Unlike this monkey, I'm very very grateful.  I had this problem 2x now.  I'm gonna try putting the ```
nvidia-xconfig --add-argb-glx-visuals
``` into the Command Line box in The Window Decorations  tab under visual effects in the beyrl setting manager.  I'll see if that fixes it.  

I

---

### Post by toobitz on 2007-04-30
I've got the very same problem after upgrading to feisty: using beryl as window manager and emerald as decorator, and the title bars of all windows are gone. 

I've tried to enable that manually in xorg.conf, here are the relevant parts:
```

Section "Monitor"
        Identifier      "aticonfig-Monitor[0]"
        Option          "VendorName"    "ATI Proprietary Driver"
        Option          "ModelName"     "Generic Autodetecting Monitor"
        Option          "DPMS"  "true"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. M24 1T [FireGL M24 GL]"
        Driver          "fglrx"
        Option          "UseFBDev"      "true"
        Busid           "PCI:1:0:0"
        Option          "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
        Identifier      "aticonfig-Device[0]"
        Driver          "fglrx"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Option          "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M24 1T [FireGL M24 GL]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth   1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "aticonfig-Screen[0]"
        Device          "aticonfig-Device[0]"
        Monitor         "aticonfig-Monitor[0]"
        Option          "AddARGBGLXVisuals" "True"
        Defaultdepth    24
        SubSection "Display"
                Viewport        0       0
                Depth   24
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option          "Composite"     "0"
        Option          "Composite"     "0"
EndSection

```

I've also deleted ~/.beryl, ~/.beryl-managerrc, ~/.emerald, ~/.gconf, ~/.gconfd - nothing worked. I'm quite stuck, has anyone got a hint for me?

---

### Post by mayamaniac on 2007-05-01
tried the method on the first post, I can't get beryl or compiz to work, the title bars always get lost. Any other suggestions???

---

### Post by toobitz on 2007-05-01
Well I solved my problem and wrote about it [here]("http://ubuntuforums.org/showthread.php?t=428442"), but I don't know if that helps.

---

### Post by Tristan9669 on 2007-05-02
when I to window decorator to choose Emerald its not there, only GTK how can I fix this?

---

### Post by OlorinIWas on 2007-05-02
I have a similar problem, that emerald or aquamarine will not load....rgb visuals are correct as is default depth...
Did some tinkering with xorg with no success, besides disallowing terminal access to the beryl itself now...though still works through manager...while trying to load emerald from terminal xlib repots :0.0 refusal and no protocal specified, along with a myriad of gtk warnings (cannot open display) I am fed up...also nvidia setting s wont save...again, joy!    Beryl works fine though except for emerald.

Using 9755 driver in kubuntu feisty64

xorg:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:37:58 PST 2007

 # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Mon Feb 26 23:38:28 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SceptreX20WG-Naga"
    HorizSync       30.0 - 81.0
    VertRefresh     40.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "RenderAccel" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "metamodes" "1680x1050_60 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

--

---

### Post by Tristan9669 on 2007-05-02
> **Tristan9669 said:**
> when I to window decorator to choose Emerald its not there, only GTK how can I fix this?
its works! I just rebooted and it everything is working fine.

---

### Post by Awkronym on 2007-05-07
This is what I'm doing, and the problem will be apparent.  

Step one:  click on Applications: System Tools: Beryl Manager
Step two:  Right Click on the Beryl Manager's icon, and Select Window Manager to Beryl
Observation one:  My title bars are missing.  
Step three:  Open terminal.  
Observation two:  A blank white glitchy box pops up, where Terminal should be.
Step four:  Change Select Window Manager back to Metacity.
Observation three:  The blank white glitchy box is now "Terminal" program.
Step five:  
user@compname:~$ sudo nvidia-xconfig --add-argb-glx-visuals

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

user@compname:~$ 

Step six:  Repeat steps one - three.
Observation four:  Same Problem.  :(

---

### Post by dionisi on 2007-05-09
thnx it works perfectly. now i have beryl and 3d options with all features.
thnx again

---

### Post by vradovic on 2007-05-09
@Compyx THANKSSSSSSSSSSSSSSSSSSSS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! 10000x

Command dont work for me but i edit xorg.conf and now work just fine.

---

### Post by _Paladin on 2007-05-14
Thank you! This worked unlike a useless charm!

---

### Post by jmervyn on 2007-05-14
> **Compyx said:**
> Unfortunately not.
All hail Compyx!  You just saved me from yet another painful night of tweaking!

Many, many thanks.

---

### Post by jaims on 2007-05-15
thank you very much, I 'kedited' xorg.conf and it wors fine

there's an issue, maybe someone could tell... The adept_updater icon gets visible and locates itself in the top left corner

¿?

Anyway, very good stuff, proud of using kubuntu :-)

---

### Post by Alex74447 on 2007-06-09
Worked better than perfect! Thanks!

---

### Post by mister_p_1998 on 2007-06-11
> **Nano said:**
> It seems that it all works ok except that it get rids of the title bar, which I use, of course, to drag windows, minimize and close.

Am I the only one out there having this problem?

I has this on Edgy, the only way to get rid of it is to delete all your Gnome config settings, (Theres a lot!) you'll find if you create a new user, all your max, min, close buttons will reappear, the corrupt files are in your user profile. I fixed it myself in the end, see this thread... Steve

[http://ubuntuforums.org/showthread.php?t=446763](http://ubuntuforums.org/showthread.php?t=446763)

---

### Post by powdermnky007 on 2007-07-11
This is how I fixed my beryl, I was having lots of the same errors everyone else was.
Mainly, the title bars are missing and A blank white glitchy box pops up, where Terminal should be.
I couldn't install emerald no matter what I tried, I got an error similar to this.  
Depends: emerald (>= 0.1) but it is not going to be installed
E: Broken packages
So I said forget emerald, and used heliodor instead...  same difference.  :)



I used envy to install video card drivers.  Once thats done type this in a terminal
sudo nvidia-xconfig --add-argb-glx-visuals --composite

check your xorg.conf to be sure your running in 24 bit mode
xorg.conf is located in /etc/X11/
the 24 bit color option is under the screen section


Add this repository in "system>admin>software sources" or /etc/apt/sources.list
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main


once thats finished start synaptic
click update
do a search for beryl
install or update the following packages
beryl
beryl-core
beryl-manager
beryl-plugins
beryl-plugins-data
beryl-settings
beryl-settings-bindings
heliodor
libberyldecoration0       (MAKE SURE THIS IS MOST RECENT VERSION)
libberylsettings0
python-compizconfig


if it give you any warings, just click ok... like usual :)
keep clicking ok until your done and back at desktop.

Now press Crtl+Alt+Bkspace to restart X

once all that is done click 
applications \ system tools \ beryl manager
now right click the red diamond on your taskbar
select window decorator
choose Beryl GTK Decorator (Heliodor)
right click diamond again
select window manager
choose Beryl

If your lucky, your beryl should be running now with no issues.
To edit cool 3d settings goto applications \ system tools \ beryl settings manager

---

### Post by tdm on 2007-07-12
> **Compyx said:**
> Unfortunately not.

Make sure you have
```

Option "AddARGBGLXVisuals" "True"
DefaultDepth 24
``` in your Screen section of /etc/X11/xorg.conf.

You can either hand-edit xorg.conf or use this command to set AddARGBGLXVisuals:
```
sude nvidia-xconfig --add-argb-glx-visuals
```,
then restart X and see if it works.

The running a command way worked like a dream!
:)

---

### Post by Aurixious on 2007-07-12
It seems alot of people are succeeding in fixing this problem but I will post my fix just in case there is that one person who still can't get it to work.

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

