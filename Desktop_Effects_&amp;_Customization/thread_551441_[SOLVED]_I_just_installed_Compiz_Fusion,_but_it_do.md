---
title: "[SOLVED] I just installed Compiz Fusion, but it doesn't seem to do anything"
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by NovaAesa on 2007-09-15
Hi everyone.

I just installed Compiz Fusion (I used the walk through [here]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty")), but nothing special seems to be happening. My screen blinked a bit for about a second but then everything went back to normal.
I tried to run it in the terminal, and got the following output:
> ps@compaq-ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


Could anyone help me to get things working?

EDIT: My graphics card is an ATi Radeon X800XL

---

### Post by Happy_Man on 2007-09-15
Hmmm.... do you have a Nvidia card? Because if you do, you will have to install the Restricted Drivers first. And if that doesn't work, then you may have to add this line to your xorg.conf: ```
Option "AddARGBVisuals" "True"
Option "Add ARGBGLXVisuals" "True"
```

Keep in mind that if you have an ATI card, none of this applies to you, with the possible exception of the Restricted Drivers, and you will have to use XGL to get Fusion working. I suggest this guide: [http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+fusion+feisty+xgl](http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+fusion+feisty+xgl)

---

### Post by NovaAesa on 2007-09-18
Hi again,

Yes, I have an ATi card, an X800XL. I've messed around with the drivers a bit but I think I now have the 'restricted ones' (from System->Administration->Restricted Drivers Management).

I tried to follow the link to the guide posted but ran into some problems. I got up to the part where I had to logout and set my session to GNOME with XGL. When I logged back in, the desktop was all garbled up. I could see well enough to log back out, but it was completely unusable in that state so I changed my session back to just GNOME.

Does anyone know what I'm doing wrong?

---

### Post by NovaAesa on 2007-09-18
I think I have the same problem as the person from [this]("http://ubuntuforums.org/showthread.php?t=553717") thread. Forlong suggested to use the fglrx drivers from Ubuntu's repositories. Does anyone know which packet(s) I should install to do this? (I searched for fglrx in Synaptic, but about half of the packets are already installed, I found it somewhat confusing).

So does anyone know the names of the packets I should install?

---

### Post by Forlong on 2007-09-18
Please post the output of
```
fglrxinfo
```

---

### Post by NovaAesa on 2007-09-18
Here's the output:
> ps@compaq-ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.0.6747 (8.40.4)

ps@compaq-ubuntu:~$ 

---

### Post by Forlong on 2007-09-18
That's not the one from the Ubuntu repostories.
You have to remove it, but unfortunately I can't tell you how to do that, because I don't know how you installed it in the first place...

---

### Post by NovaAesa on 2007-09-18
I installed it using Envy.

After uninstalling, when I ran fglrxinfo I got the following

> ps@compaq-ubuntu:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
Make sure you have the 'restricted' component enabled
bash: fglrxinfo: command not found
ps@compaq-ubuntu:~$ 

which makes sense, right? as it's no longer installed?
What should I do now?

---

### Post by okanss on 2007-09-18
Hello, i want to continue from this thread cause i have the same problem with NovaAesa.
I installed compiz and i have this warning when i load it,
> okan@okan-desktop:~$ compiz --replace
Checking for Xgl: not present.
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity

And i have an Intel video card and my output with "fglrxinfo" is

> display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2

I installed Compiz-Fusion on Fetsy Dawn 7.04 as Forlong mensioned in his blog.
I dont get my video card is supported or not but it seems that it is not. Any help would be helpful.
Thanks.

---

### Post by NovaAesa on 2007-09-18
Would I be right in asuming that I should install the packages named "xorg-driver-fglrx" and "xorg-driver-fglrx-dev"? or only the first one?

I'm on a 28.8k connection, so I don't really want to download any more than I have to.

---

### Post by Forlong on 2007-09-18
If you are on GNOME just install it via *System &#8594; Administration &#8594; Restricted Drivers Manager* - this will take care of everything (including configuring your xorg.conf)

---

### Post by Forlong on 2007-09-18
> **okanss said:**
> Hello, i want to continue from this thread cause i have the same problem with NovaAesa.
But the symptom is different. Your graphics driver isn't running at all.
Please post he output of
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by okanss on 2007-09-18
Hi  Forlong,
My output as you wanted is
```
okan@okan-desktop:~$ grep -v ^# /etc/X11/xorg.conf

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "dbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "tr"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "Intel 945G"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
        Option          "DRI"                   "true"
        Option          "XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
        Identifier      "Philips 170c6"
        Option          "DPMS"
        HorizSync       30-90
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 945G"
        Monitor         "Philips 170c6"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        Option          "AIGLX"         "true"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by Forlong on 2007-09-18
Erm... your problem has nothing to do with this thread at all. I must've missed the part, where you said you're on an intel chip. Sorry.

Did *you* put all those options in your xorg.conf - if so, did you know what you were doing?
I'll recommend you make a "reset" of your xorg.conf
You can make a backup first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then run this:
```
sudo dpkg-reconfigure xserver-xorg
```
If it still doesn't work for you (after a reboot), go [here](http://wiki.compiz-fusion.org/Intel_with_AiGLX) and see if this will help you out.

---

### Post by NovaAesa on 2007-09-18
> **Forlong said:**
> If you are on GNOME just install it via *System &#8594; Administration &#8594; Restricted Drivers Manager* - this will take care of everything (including configuring your xorg.conf)

When I do this, it just says:
> You hardware does not need any restricted drivers.

---

### Post by Forlong on 2007-09-18
Please post the output of
```
lspci | grep VGA
```
As well as your xorg.conf (you can use the command I posted earlier for okanss)

---

### Post by okanss on 2007-09-18
HEllo back, 
I remade the xconf.org file of mine and added the missing part due to the link you provide. 
Now nothing has changed now:( The same problem is still on and as a last resort, i will try to install intel driver manually. If you have some thought i love to listen, and thanks for the support till now.

---

### Post by NovaAesa on 2007-09-18
When I booted my computer this morning, it came up with a message that the X server could not start. Some of the output on that screen said something about fglrx not being loaded (or something like that, I think).

I got to log in, but to the command line. The output of lspci | grep VGA was:

> 01:00.0 VGA compatible controller: ATI Technologies Inc R430  [Radeon X800XL] (PCIe)

In the xorg.conf file, here's the device section:

> Section "Device"
Identifier "ATI technologies  Inc R430 [Radeon X800XL] (PCIe)
Driver "fglrx"
Build "RCI:1:0:0"
End Section

I can quote any other parts of the xorg.conf file if you need them

---

### Post by Forlong on 2007-09-18
So you still can't log into GNOME?

Post your whole xorg.conf then.

---

### Post by okanss on 2007-09-19
I've discovered another problem now and want some help.
```
okan@okan-desktop:~$ glxinfo name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```

This is my > glxinfo respond and its clear that direct rendering is not supported. And i dont know where i am wrong because i reconfigured xorg.conf and fixed it.
Thanks again

---

### Post by mattgaunt on 2007-09-19
Hey okans

This thread isnt the right place to be talking about your problems.

Search the forums for graphics card (Intel chip i think you said), and see if you can find anyone who has managed to get direct rendering working.

But i did read that someone did the following to make it work for them

Install "xserver-xorg-video-intel" via Synaptic and then chage "i810" to "intel" in your xorg.conf file

Your not fixing anything by resetting your xorg.conf file, your just setting everything back to fail-safe sort of settings. The fglrx drivers are for ati cards, you need the drivers for intel to get direct rendering to work

Matt

---

### Post by NovaAesa on 2007-09-19
Here's my xorg.conf file:

> Section "Files"
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
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
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
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LG Flatron L1750SQ"
	Option		"DPMS"
	Horizsync	30-83
	Vertrefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"LG Flatron L1750SQ"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
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
	Option		"Composite"	"Disable"
	Option		"Composite"	"0"
EndSection



---

### Post by Forlong on 2007-09-19
Please boot into recovery mode and do what I said [here](http://ubuntuforums.org/showpost.php?p=3384547&postcount=14) earlier in the thread.

Then you should be able to boot into GNOME again and we can try to sort things out.

---

### Post by NovaAesa on 2007-09-19
okay, I did what you said and it worked well. I'm now back in Gnome.

So what next?

---

### Post by Forlong on 2007-09-19
Now open your xorg.conf being root:
```
sudo gedit /etc/X11/xorg.conf
```
and change this line
```
	Driver		"ati"
```
located in the *Section "Device"* to
```
	Driver		"fglrx"
```
And add this to the very end of the file:
```
Section "Extensions"
        Option          "Composite"     "0"
EndSection
```
Then save and reboot.

If GNOME loads fine, post the oputput of
```
fglrxinfo
```
As well as
```
 glxinfo | grep "direct rendering"
```

---

### Post by NovaAesa on 2007-09-19
I made the changes and restarted but it wouldn't boot into Gnome. Rather, it came up with the message

> Failed to start the X server... would you like to view the xserver output (something similar to this)

---

### Post by yang2iu on 2007-09-19
I'm also using Intel chip.

I installed and uninstalled compiz-fusion quite a bit before I re-installed ubuntu, but this time it just doesn't work. I don't think I did anything other than what was mentioned in the how-to thread to get compiz-fusion work, but now I just cannot get it back =(

---

### Post by Forlong on 2007-09-19
> **NovaAesa said:**
> I made the changes and restarted but it wouldn't boot into Gnome.
Then there's some kind of trouble with the fglrx driver.
You have to change it back to "ati" with
```
sudo nano /etc/X11/xorg.conf
```
in the recovery mode.


@yang2iu: this is NovaAesa's thread and he doesn't have an intel chip, so please ask in an appropriate thread.

---

### Post by NovaAesa on 2007-09-19
I changed it back to 'ati' and now im back into Gnome.

I think maybe the fglrx drivers aren't working because I haven't installed them? Since uninstalling the drivers from Envy, I don't think I've installed any other ones (I've only done what has been indicated in this thread, I haven't been messing around with anything else). This is just a guess though, you obviously would know more about it than I.

---

### Post by Forlong on 2007-09-19
Try *System &#8594; Administration &#8594; Restricted Drivers Manager* now.

---

### Post by NovaAesa on 2007-09-19
When I do that, it comes up with

> Your hardware does not need any restricted drivers

---

### Post by Forlong on 2007-09-19
Oh well, maybe your graphics card isn't supported by the driver version included in Ubuntu (stupid ATI).

Try this guide then: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) (Method 2)
And still keep in mind you will have to use [Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) for Compiz then.

if this driver doesn't work with Xgl, we're screwed...

---

### Post by NovaAesa on 2007-09-19
Ok, I think I might give this a try tomorrow (no school tomorrow :)) cos it's almost midnight in Australia.

You've been very helpful so far! Thankyou.

---

### Post by NovaAesa on 2007-09-20
Yay! I installed the drivers that way and it worked!

I have a few problems though. OpenOffice won't startup and neither will any of my wine applications. They will only work if I start a session without XGL (but then compiz fusion won't work).

---

### Post by Forlong on 2007-09-20
> **NovaAesa said:**
> Yay! I installed the drivers that way and it worked!
Phew, that's great to hear! :)
> **NovaAesa said:**
> I have a few problems though. OpenOffice won't startup and neither will any of my wine applications. They will only work if I start a session without XGL (but then compiz fusion won't work).
Sorry, I haven't used Xgl since Edgy (and I never used wine at all), so I'm afraid can't help you there.
I know Xgl is a pain in the *** (that's why I switched to the open radeon driver ;))

---

### Post by NovaAesa on 2007-09-21
ok, I'll probably stick with compiz for the odd occasion when I want to show off to friends, but I'll disable it for everyday use. I'll probably come back and sort things out when I get a new laptop for university next year though :)

Thankyou so much for helping me. Maybe one day when I know more about computers, I can give back to the Ubuntu community also.

---

### Post by Forlong on 2007-09-21
> **NovaAesa said:**
> I'll probably come back and sort things out when I get a new laptop for university next year though :)
No prob, but by then hopefully nobody will have to use Xgl anymore. :)


edit: I just found out that OOo has issues with the latest fglrx driver. So I'm afraid you are in a lose-lose situation for now. Again: stupid ATI.

---

