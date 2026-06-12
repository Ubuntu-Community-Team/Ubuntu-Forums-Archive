---
title: "How to make the cube rotate in compiz fusion or Beryl svn"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by gupta_sumesh63 on 2007-07-01
I have downloaded Beryl SVN.
Someone please tell me how to make the cube rotate showing all the 4 sides as being shown on videos.
I have intel 915 video card.
If not Bery how do I do that in Compiz fusion.
Someone please tell me the various configurations in the beryl config or compiz config so that i tooo enjoy the fun.

:confused:

---

### Post by Pizzarth on 2007-07-01
you can just install it from the repositories. in synaptic, search for the beryl packages, select the main one and accept whatever else it needs. Then when it's installed, run the beryl manager from the (either applications, or K) menu. from there you can select what window manager you want to use. select beryl

---

### Post by solid0409 on 2007-07-01
if you want to do it in compiz fusion then, follow these steps in the web-site

[http://ubuntuforums.org/showthread.php?p=2902636](http://ubuntuforums.org/showthread.php?p=2902636)

then when compiz-fusion is completely install  you go to **System>>Preferences>>compizconfig setting manager**

then scroll down to where you see  Rotate Cube, and thats it.

P.S I personally think that **Compiz-fusion **is better than **Beryl **because it has more features and more cool stuff you can do with it. 

see yaaa!!!!

---

### Post by bodhi.zazen on 2007-07-01
For me, Beryl rotates the cube in several ways.

Keyboard : Ctrl-Alt-<Arrow keys>
<arrow key = up,down,right,left arrow.

Mouse : 

1. Roll wheel
2. Push wheel down and drag mouse.


Compix-fusion : Default settings are Ctrl-alt-<arrow-key>

---

### Post by hyperair on 2007-07-01
Don't forget Ctrl Alt Click to move the cube.

---

### Post by daverich on 2007-07-01
I changed it to button two so now i can just push in my scrollwheel and the cube appears.

I like compiz-fusion, it feels alot more solid than beryl.

Kind regards

Dave Rich

---

### Post by RelativelyQuantum on 2007-07-10
Here's another Beryl-related question: how do you disable the window cascade-like feature, activated by placing the pointer in the top right-hand corner - It's really been interfering with my power button. Preferable still to removing the feature is moving it into the top left-hand corner.

Is this possible?

---

### Post by Aurixious on 2007-07-10
I too have a problem with beryl.  I cannot use any of the features in beryl but i can initiate the app and play around with its settings.  I looked at the sortcuts in the settings manager but none of them work.  I just got done installing my nvidia driver, which was beyond the realm of difficult, to fix the white screen issue.  How do you use this infernal contraption?

---

### Post by Aurixious on 2007-07-10
Anyone?  I'm not asking how to install I want to know how to use the thing as it seems that nothing works.  If I open the beryl manager it sets an icon up in my task bar but that's it.  A simple guide on how to use it would be nice as I anticipate more questions.

---

### Post by RelativelyQuantum on 2007-07-11
Well, I'm no expert on it, but I might be able to help. First of all, what distro are you running? I use Edgy, and after some tweaking the application works quite well. You might want to try adding "beryl manager" and "emerald" to your startup programs, found in System > Prefs > Sessions > Startup Programs, if you haven't done that already.

Let me know about your results; I would be glad to give any help I can.

---

### Post by Aurixious on 2007-07-11
That you for your willingness to help as it seems as if people like you are vanishing.  I went to beryl's site and they aren't accepting any more people to register to their site!  Back on topic, i haven't added that to the startup programs but is that necessary to get it to work.  Was just wondering that out of curiosity.  Also should the default settings be fine since I'm using an nvidia card and I've seen nvidia listed under some form of rendering.  Almost forgot I'm using 7.04.  Also, once I go to add new startup program it wants me to add a command.  I'm not sure what what to put there, but there is a browse button to find the app.  Only thing is I don't know where it was installed to lol.

---

### Post by Aurixious on 2007-07-11
Ok I found beryl-manager in usr/bin I hope that's the one.  Confirmation would be nice though just to be safe.  As far as I can remember I didn't install emerald.  To my knowledge emerald is an addon that gives extra themes and effects.  Is it worth the download?

---

### Post by Aurixious on 2007-07-11
I just tested that and the app is started on login but that doesn't really do anything for me since I still can't get any of the effects to work.  :(

Just to save a lot of miscommunication and frustration down the line I want to state that I'm new to linux and any way possible to circumvent that terminal would be appreciated.  GUI all the way :).

---

### Post by Aurixious on 2007-07-11
Just noticed that when I went to the add startup programs menu I saw a file with the name "beryl" (in usr/bin) in addition to beryl-manager not sure what it does but it would be appreciated if you could explain what it is and/or what it does.

---

### Post by hyperair on 2007-07-11
Yes it is, otherwise you'll be stuck with the default window borders that you use in Metacity. With Emerald, you can get other window borders, which look much better, and whatnot, including, but not limited to the Vista Aero Glass window borders. To install it, run this command: ```
sudo apt-get install emerald emerald-themes
``` or go to Synaptic Package Manager and install th emerald and emerald-themes packages from there.

As for Beryl forums not accepting any new users, that's because Beryl is a discontinued project, as is Compiz, and they're all focusing on Compiz Fusion. If you really want to join in a forum dedicated to Beryl and the likes of it, you can go to the forum at [http://www.opencompositing.org](http://www.opencompositing.org).

If you're still intent on using Beryl and Beryl Manager, then here goes. You open the Beryl Manager, which brings up the icon, then you right cilck on it, and select window manager. Use Beryl as your window manager. Metacity is the default. If it doesn't work, then there's probably something wrong with your installation. Another thing I noticed is that, since you are in Feisty, if you can gte the regular desktop effects running, through the GUI provided (System->Preferences->Desktop Effects), then running Beryl will be a piece of cake, because the drivers are all set up for you already.

I noticed a question earlier regarding the top right corner initiating the Scale plugin. It can be changed in Beryl Manager, under General Settings->Shortcuts->Screen Edges.

---

### Post by Aurixious on 2007-07-11
Ok when I click on beryl in the window manger it just goes back to metacity.  Also if I go to the default effects I get the error message "the composite extension is not available".  Any suggestions :confused:.

---

### Post by Aurixious on 2007-07-11
It seems that there is a fall back scheme, which is metacity, in case beryl crashes.  So I guess it crashed :mad:.  I have an nvidia 7800 gt and installed nvidia drivers.  Please help. I really want to get this working.

---

### Post by Aurixious on 2007-07-11
I did a file search in my hdd and i get only two files one of which is an image and the other is this "emerald-theme-manager.desktop".  I wouldn't think that's the right file but it's the only one there.  So would I set that file as a startup program?

EDIT: I now know it's installed since it's under sys>prefs.

---

### Post by hyperair on 2007-07-11
Please be patient, and do not double or triple post. It gets irritating, and is practically a written/unwritten rule for all forums across the internet. I was napping earlier, sorry for the late reply. 

Please post the contents of this file: /etc/X11/xorg.conf. Also, add this section to the bottom:
```

Section "Extensions"
        Option "DAMAGE" "Enable"
        Option "Composite" "Enable"
        Option "RENDER" "Enable"
EndSection

```

To add these lines you'll have to have administrative powers. Since you don't like using the terminal, I advise you to install "nautilus-gksu" via Synaptic Package Manager, and then navigate to the specified folder (/etc/X11), right click on the specified file (xorg.conf), and open as administrator.

---

### Post by Aurixious on 2007-07-11
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
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
        Option "DAMAGE" "Enable"
        Option "Composite" "Enable"
        Option "RENDER" "Enable"
EndSection


Something off topic that I might be able to fix now is the resolution.  My max res is 1024x768 can I increase that here?

Also, I asked about emerald so can you look back at my previous post.

---

### Post by hyperair on 2007-07-12
Well does Beryl still complain about the Composite extension? You'll have to have restarted your X server (Ctrl+Alt+Backspace) or restarted your computer at least once since you've made the changes. To add more screen resolutions.. I'm not really sure, but I think the nvidia-settings program can help you.

---

### Post by Aurixious on 2007-07-12
No it wasn't Beryl that gave me that composite error that was when I tried to use the built in effects that come with ubuntu ie sys>pref>desktop effects.  

OK IT WORKS!  Thanks for all your help!

It seems when I did a ctrl>alt>back space, logged back in, and set the windows manager to beryl that fixed it.

---

### Post by Aurixious on 2007-07-12
About EMERALD again.  Would I add the file "emerald" to the list of start up programs or would I add "emerald-theme-manager" to the list of start up programs?  Both of these files are located in usr/bin.

---

### Post by hyperair on 2007-07-13
It's emerald.

---

### Post by skaspud on 2007-07-13
omg! som1 help me use beryl!!! how do i get it to work at all!?!?! i have it, i've launched it, but nothing different.
I have ATI x850 pro (drivers installed with envy)

---

### Post by hyperair on 2007-07-13
Well panicking won't get you anywhere =P. You've installed the ATi drivers through envy, so presumably  your xorg.conf is correctly configured. I don't claim to have any ATi experience, but post the output of ```
glxinfo | grep direct
``` and ```
beryl --replace
``` in the terminal. Hopefully someone with ATi experience will be able to help you out with this. =)

---

### Post by skaspud on 2007-07-13
uh o, 
error:
skaspud@ubuntu-power:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by skaspud on 2007-07-13
duble uh o
skaspud@ubuntu-power:~$ beryl --replace
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by skaspud on 2007-07-13
k i totally removed beryl ( i think ), theres like a million different tutorials, which one works!!!!!!

---

### Post by RelativelyQuantum on 2007-07-25
Here's a good place to start:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

I used the Edgy tutorial and Beryl works flawlessly (and I mean *flawlessly!*) on my machine. It worked for me when I was using Feisty too, so its worth a shot!

Post your results, so that you can be walked through if need be; I would be glad to give any help I can.

~Good Luck!

---

### Post by hyperair on 2007-07-26
On the contrary.. I think Ubuntuguide is NOT the place to go for installing Beryl/Compiz. That howto is quite outdated I reckon. If you want, the best ones are here in Ubuntuforums.

---

