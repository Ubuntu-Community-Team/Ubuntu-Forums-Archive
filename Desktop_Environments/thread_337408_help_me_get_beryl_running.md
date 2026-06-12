---
title: "help me get beryl running"
date: 2007-01-12
forum: Desktop Environments
---

### Post by polkajunior on 2007-01-12
ive followed this guide so far.. found here
[http://ubuntuexperiences.wordpress.com/2006/12/05/installing-beryl-and-xgl/](http://ubuntuexperiences.wordpress.com/2006/12/05/installing-beryl-and-xgl/)

but it seems that something wrong. i am unable to get xgl running. i can get the beryl-manager going and the emerald themes, but the actuall window decorations dont come up and im thinking that xgl or beryl isnt actuallly running. ive gotten it to work in suse linux but im using ubuntu now. i try to reload the window manager but that doesnt work. i dont get the beryl wobbly splash screen so im thinking its not running.

this is some of the stuff i get when i try to load beryl-manager in the term.
> justin@linuxbox:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension

thats what i get when i try to use beryl as window manager

thanks for the help

---

### Post by floke on 2007-01-13
Have you edited you xorg.conf file to include composite extensions?

---

### Post by floke on 2007-01-13
You have to add this to the end of your xorg.conf file

To edit it and make the changes go to a terminal and use: sudo nano /etc/X11/xorg.conf

Go to the end and enter

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Then use ctrl-X to exit

---

### Post by polkajunior on 2007-01-13
unfortunately that didn't help any.
its strange because the beryl-manager comes up and the tray icon is there on the taskbar, but i get no beryl

---

### Post by floke on 2007-01-13
You also have to enter

Load "dri"
Load "dbe"
Load "glx"

into the Modules section of the xorg.conf file

Full installation instructions for AIGLX on Edgy are here:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX#How-to_install_Beryl_with_AIGLX_on_Edgy_Eft)

To start beryl you have to enter 'beryl-manager' in a terminal

---

### Post by polkajunior on 2007-01-13
from what i gather im not trying to run it on aiglx?  i get the beryl-manger but the window decorator and effects are loading. if i click on the diamond beryl icon the popup list comes up and where you can select "window decorator" its greyed out and not selectable
but i have installled emerald. its crap because i got it working so easily in suse.

---

### Post by floke on 2007-01-13
There are alternative instructions for installing Beryl other than using AIXGL on the beryl wiki.
I suggest that you follow the instructions properly before pronouncing on its crapness or otherwise.

---

### Post by polkajunior on 2007-01-13
yeah ive been through those a number of times. im not trying to offend. if you were, im just frustrated because it seem like it should be simpler.

---

### Post by medley on 2007-01-13
> **polkajunior said:**
> yeah ive been through those a number of times. im not trying to offend. if you were, im just frustrated because it seem like it should be simpler.

FWIW, I have been trying to get beryl to run for several weeks, unsuccessfully. It sounds like the symptoms you are describing are the same as mine. Windows come up without any borders, and no beryl-type effects at all. 

I did have it working (sort of) once, after I did a clean re-install. This included deleting /home/.beryl

I had seen this tip somewhere. However, when I ended the session and restarted, I was right back at where I had been (IE, no joy)

My environment is

NV FX5200 with 9746 driver
Kubuntu Edgy
AMD 2400+
780M ram

It's not as simple as people make it out to be. I still haven't got it working.

---

### Post by polkajunior on 2007-01-13
........... im hoping someone can help

---

### Post by koshari on 2007-01-13
if you have a nvidia card IMHO i have found it a lot easier to get beryl going with aiglx.

simple as downlaoding envy, and using that to install the latest nvidia drivers then install beryl and emerald , then run beryl-manager.

dont get much simpler than that.

---

### Post by dabl on 2007-01-13
.... and I'm hoping right along with you, polk.  I have all features working EXCEPT the window decorations, I think.  I can spin the 4 desktops around with the mouse wheel, watch my windows swoosh out of the taskbar, etc. When I change the Window Manager from Beryl to KDE (I'm running Kubuntu Edgy), I get normal windows, but of course no Beryl special effects. Like medley, I had it working with window borders last night for awhile, but it seemed pretty unstable.  I tried setting Aquamarine for the window decorations, and my entire taskbar kind of fell apart and went bye-bye. I'm not sure what I've subsequently done that "turns off" the window borders. It seems pretty stable today -- I've been through multiple reboots and xserver restarts, and I think it's OK except for these %$#^! missing borders.


System: Kubuntu Edgy 386
Intel Core 2 Extreme on D975XBX motherboard
EVGA Nvidia GeF 7900 GS
Samsung 1100MB crt monitor


ADDED LATER:

OK, I have reviewed the Beryl FAQs, and learned (again) that us Nvidia folk need to add this line to the "Device" stanza of your xorg.conf file:

  Option "AddARGBGLXVisuals" "True"

This appears to have fixed the window decorations problem.

---

### Post by polkajunior on 2007-01-13
anyone know what this means, i got beryl up but no window decorations.

> (emerald:6315): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32

(emerald:6374): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6374): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6374): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6374): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6374): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6374): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6374): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(emerald:6374): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32



---

### Post by dabl on 2007-01-13
Hmmmm -- all the advice says set depth = 24, so it's odd that yours is complaining about 32.  You could try depth = 32 in your xorg.conf and see what happens.

I've been retesting my setup, and all I can say for sure is that it isn't very stable.  Sometimes Aquamarine can be loaded as my Windows Decorator, and sometimes it crashes with a "Signal 8" error message.  In that case, I can't get it to run without crashing, and have to restart the xserver.  But sometimes that's all it takes to get it going.  Once its running, it seems to be OK for that session.  All window borders aren't consistent -- Krusader gets a jet black border with no indicators, but if I hover the cursor over the upper right corner, I get the "close" indicator, and it works.  Firefox shows the Firefox logo in the upper left corner, but if I click it I get the Beryl/Aquamarine menu to set opacity, brightness, how many desktops I want it on, etc.  Upon close inspection of the window borders with Beryl running and Aquamarine as the decorator, there is some funkiness near the top of both sides of the side borders -- tiny little random color spots.  So, it's very cool and very shaky, on my system ...


BTW, I learned yesterday, in System Settings>Window Behavior, you must not check the box on the "Translucency" tab.  It will interfere with getting the window borders to work.

---

### Post by Yuske on 2007-02-27
so, here's my 2 cents:
downgrade your visuals from 32 bits to 24 or 16. from the looks of the error, you're being able to run beryl on true depth, but not getting visuals with it, it's asking more than your graphics card is able to deliver.

I was having this problem where I couldn't even run Beryl. and I found out that my card had less memory than needed to run Beryl at 1280x800@32 bits, so I downgraded to 24 bits and it's working now.

I still get this one error though, when changing visual styles...
```
(emerald:4879): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)' failed
```

anyone have ideas?

---

