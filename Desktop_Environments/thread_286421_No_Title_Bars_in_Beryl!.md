---
title: "No Title Bars in Beryl!"
date: 2006-10-27
forum: Desktop Environments
---

### Post by matt_risi on 2006-10-27
Hey guys, I just installed Beryl on my laptop (i810), and it is AWESOME, except I don't have any titlebars at all on all my programs. I've searched around and I can't seem to find a solution, any ideas?

---

### Post by autocrosser on 2006-10-27
Well--I can't help you with your problem because I have one very similar--no window decorations of any kind--I remember with the first Compiz you needed to stop Metacity first & then start Compiz--Is this still the case? Tried Beryl-Settings & set a theme in Emerald-Theme-Manager & still have the same problem--also, screen "locks up" but the cursor works--have to control-alt-backspace out.

I used the  [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)  guide--running a Nvidia card with the repro driver---

---

### Post by rachii on 2006-10-27
i dont have title bars either, have to alt-click to move windows and keyboard commands to close out.  also when i open up the terminal its just a blank white square. i can type all i want (and it works) i just cant see what it is i am typing.

---

### Post by gregh on 2006-10-28
I am having shocking problems, my laptop has always worked but after a fresh edgy install yesterday I just cannot get beryl working.

When running beryl-manager the window decorations vanish and gnome locks up. I can alt-tab to another terminal and kill it but I cannot work out why - no error messages I can find !

Help !

> **autocrosser said:**
> Well--I can't help you with your problem because I have one very similar--no window decorations of any kind--I remember with the first Compiz you needed to stop Metacity first & then start Compiz--Is this still the case? Tried Beryl-Settings & set a theme in Emerald-Theme-Manager & still have the same problem--also, screen "locks up" but the cursor works--have to control-alt-backspace out.

I used the  [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)  guide--running a Nvidia card with the repro driver---

---

### Post by autocrosser on 2006-10-28
What way did you use to install Beryl? Is your 'top ATI, Nvidia or Intel graphics? I have been thinking of installing the beta Nvidia drivers, but the last time I tried--I got two black screens for my effort--I've hear that there is a patch to the beta drivers, but I havn't been able to track down the info yet--:???:

---

### Post by h0ser81 on 2006-10-28
Try adding emerald and beryl-manager to your startup sessions in System -> Preferences -> Sessions. That seemed to clear up having no window decorations for me. Also someone pointed out that the update-notifier might cause problems too which you can disable through sessions as well.

---

### Post by aanderse on 2006-10-28
i have this problem too
when i type "beryl-manager" into a terminal to try to start it i get this error:

aaron@64bit:~$ beryl-manager
aaron@64bit:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present


using 64bit edgy with nvidia card (i have not tried to install xgl, i planned on using aiglx which came with edgy).

---

### Post by matt_risi on 2006-10-28
> **h0ser81 said:**
> Try adding emerald and beryl-manager to your startup sessions in System -> Preferences -> Sessions. That seemed to clear up having no window decorations for me. Also someone pointed out that the update-notifier might cause problems too which you can disable through sessions as well.

Worked like a charm, thanks so much.

---

### Post by autocrosser on 2006-10-28
that is the same info I get --then the desktop locks-up except for the cursor--

> **aanderse said:**
> i have this problem too
when i type "beryl-manager" into a terminal to try to start it i get this error:

aaron@64bit:~$ beryl-manager
aaron@64bit:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present


using 64bit edgy with nvidia card (i have not tried to install xgl, i planned on using aiglx which came with edgy).

---

### Post by gregh on 2006-10-28
UPDATE:
I added emerald and beryl-manager to my startup session and it works fine.
Dont know why it would not work if i launched it in a terminal, but all is ok now.

Others should try this if you are getting the locked up gnome session and no window borders.

-Greg

---

### Post by oldmanstan on 2006-10-29
or, make this addition to xorg.conf file, this worked for me:
```
Option         "AddARGBGLXVisuals" "True"
```
this is from the beryl forums here [http://forum.beryl-project.org/topic-5843-window-borders-nvidia-beta-drivers-ubuntu-edgy](http://forum.beryl-project.org/topic-5843-window-borders-nvidia-beta-drivers-ubuntu-edgy)

---

### Post by cytutchi on 2006-11-03
i have the same problem but i use Edgy n Kubuntu...
so does anybody know how to add up n what in the startup for my case??

---

### Post by oldmanstan on 2006-11-03
did you try adding the line i mentioned in the post above yours? because that might solve your problem, as far as adding a startup item in KDE, there should be a "session" settings dialog, check where your other configuration stuff is, sound, theme settings and such.

---

### Post by barney_1 on 2006-11-10
I also have no titlebars.  Rather, when I maximize any window, the titlebar goes completely white, not title or buttons.  I can, however, still click the buttons, they just don't appear to be there.

I have added that line to my xorg.conf screen section but it didn't fix the problem.  I tried adding just emerald and beryl to my session startup list but no luck there either.  Any ideas?

I would like to reiterate, this only happens when the window is maximized, it is not a problem with flashing or anything like that.

Thanks!

---

### Post by cytutchi on 2006-11-27
I tried all sorts of stuff from duzzens of forums...
Maybe the problem is not beryl or Edgy but maybe me!
Anyway though...i found my solutin by going back to Kubuntu Dapper!!!
All problems and small bugs solved!
Just couldnt make Edgy n sony vaio FS series work properly!

---

### Post by melon2006 on 2006-12-12
In my case (twinview+beryl+nvidia+aiglx on 64-bit Edgy Eft) those two options
**have made titlebars visible:**

```
Option         "AddARGBGLXVisuals" "True"
Option         "DisableGLXRootClipping" "True" 
```

in "Screen" section 

whole xorg.conf looks like this (maybe this will help someone):

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Nov  1 19:48:35 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
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
    ModelName      "___ CT1772PF"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 135.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7900 GT/GTO"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True" 
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1024x768 +0+0, DFP: 1280x1024 +1024+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by dyntryx on 2007-03-11
First, let me reiterate that [this post]("http://forum.beryl-project.org/viewtopic.php?f=35&t=1631") will fix most issues.

However, that did not help me, so I was stumped for a while on what my problem was. I'm running Kubuntu+fglrx+XGL+beryl-svn.  Surprisingly, further investigation showed that I was somehow missing the window decorator itself (aquamarine).

If you've tried the link I posted above and are still stumped, here's a [link to where I solved this problem]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4046&p=26815#p26815").

It also includes brief help for **U**buntu--remember I'm on **Ku**buntu; but, I cannot say it provides much information, as I haven't seen any Gnome users with this issue anyway.

Hope that helps someone out there. :)

---

