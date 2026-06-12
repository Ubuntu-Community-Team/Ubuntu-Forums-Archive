---
title: "ut2004 &amp; doom 3"
date: 2006-09-14
forum: Gaming &amp; Leisure
---

### Post by hoagie on 2006-09-14
I have been facing problems with the installation of these 2 game. 
ut2004: I put in the dvd and I run the linux installer...installation completed. I try to run the game but nothing happens. The ut2004 logo appears on the scrren but then nothing happens.

doom 3: Em basically how can I install this game?

I would admire it if anyone helps me out.:confused:

---

### Post by Carrots171 on 2006-09-14
You can find the Doom 3 Linux installer along with instructions on how to install it here: [http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

---

### Post by Perfect Storm on 2006-09-14
Ut2004 howto here: [http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63](http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63)

---

### Post by hoagie on 2006-09-15
I can't view that webpage. It says You are not authorized to view this resource. I am a member of ubuntu gamers arena though...

---

### Post by hoagie on 2006-09-15
Lately I found myself to play ut2004 long hours so if anybody can post a guide that **works[B]**[/B] I would really appreciate it.:D

---

### Post by Perfect Storm on 2006-09-15
It seems one of the other admins have closed it for the public eye by an accident. I'll get back when it's viewable for the public eye.

---

### Post by hoagie on 2006-09-15
Thanks alot. When it's available for public view again please inform me by posting here or by sending me a messeage=D>

---

### Post by darundal on 2006-09-16
To install doom3, browse to usr/local/games and create a folder called doom3. Then create, inside of it, a folder called base. Now, put in CD 1, go into setup, and base, and copy the pak files from the cd base folder into the doom 3 base folder. When finished, eject and repeat for the other two cd's. Then, download the linux installer (i'll let you find that) put it in the base directory, give it read/write permissions, and run it. Then turn off the lights, change into some rubber pants, and play.

---

### Post by hoagie on 2006-09-17
> **darundal said:**
> To install doom3, browse to usr/local/games and create a folder called doom3. Then create, inside of it, a folder called base. Now, put in CD 1, go into setup, and base, and copy the pak files from the cd base folder into the doom 3 base folder. When finished, eject and repeat for the other two cd's. Then, download the linux installer (i'll let you find that) put it in the base directory, give it read/write permissions, and run it. Then turn off the lights, change into some rubber pants, and play.

Haha great but where is that installer?

---

### Post by pay on 2006-09-17
[http://zerowing.idsoftware.com/linux/doom/](http://zerowing.idsoftware.com/linux/doom/)

---

### Post by hoagie on 2006-09-17
To do all that I need to have root access, is there anyway to do that or do I have to do it via the terminal using sudo?

---

### Post by pay on 2006-09-17
I don't think that you have to install doom3 as the root user, but if you dont you'll only be able to install the game into your home directory. If you need to use the root user to install it then use the terminal and sudo...

---

### Post by Stew2 on 2006-09-17
Does UT2004 hard lock at the logo screen or just close on its own? It was hard locking on mine and it turned out to be that I had the wrong ATI drivers installed for my video card. Once I got the drivers straightened out it plays beautifully! Hope this helps! :D 

P.S. Unfortunately, Doom 3 seems to run quite a bit slower in ubuntu than Windows but I haven't tried tweaking it too much yet, so I'm not certain.

Regards,
Stew2

Edit: I just remembered too, there is a patch for UT2004 (linux) at the Epic site, although I think it is a gameplay patch and shouldnt affect starting or running the game.

---

### Post by hoagie on 2006-09-17
I can't copy those pak files into the usr/local/games/doom3/nase because I I'm not the owner any ideas? I quess I neeed to log as root, but how do I do that?

---

### Post by hoagie on 2006-09-17
I finally installed doom 3 but it won't run. When I type doom3 in the terminal nothing happens. 
CODE:
$ doom3
  DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 10.170.165.120/255.255.0.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/andrew/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg

Any ideas how I can fix this?

---

### Post by Stew2 on 2006-09-17
> **hoagie said:**
> I finally installed doom 3 but it won't run. When I type doom3 in the terminal nothing happens. 
CODE:
$ doom3
  DOOM 1.3.1302 linux-x86 May 12 2005 14:56:44
found interface lo - loopback
found interface eth0 - 10.170.165.120/255.255.0.0
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0xe9d5adcf
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0x80401dd2
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x351c23e8
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Current search path:
/home/andrew/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg

Any ideas how I can fix this?

I still have a suspicion that your problems are stemming from a lack of 3d acceleration. Could you post the output of "fglrxinfo"?

---

### Post by Perfect Storm on 2006-09-17
> Sys_Error: Couldn't load default.cfg

Perhaps a permission problem?

---

### Post by hoagie on 2006-09-17
AI: I tried sudo doom3 and I got the smae message.
Stew: That comand doesn't excist. I get bash](*,)

---

### Post by darundal on 2006-09-17
To install in usr, just enter "sudo nautilus" in the terminal, browse there, and create the proper files. Stew assumed you had the ATI FGLRX driver installed when he gave you that command. If you don't, and you have an ATI card, then you should probably install the FGLRX driver. To do that, open up the terminal, and type in "sudo apt-get install xorg-driver-fglrx", say yes to everything. Then, enter in "sudo dpkg-reconfigure xserver-xorg" and when it asks to autodetect your video hardware, say no and select the fglrx driver. After that, just hit yes (the defaults should be just fine for everything) untill it shows you a list of screen resolutions. Select all the resolutions you want to use, then continue forward. Just go with the defaults for everything else, then after it is completed (the terminal will offer you a line for commands again when it is finished) just restart your system. Then you should try to run the games...good luck.

---

### Post by Stew2 on 2006-09-17
Actually, I have a link to the [Nvidia video driver installation]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29"), if you scroll down some they also have a link to install the ATI video drivers as well. This is from the unofficial Dapper guide (my bible :D ) So depending on what kind of video card you have there is a how to for each one. I know neither one of these games worked for me initially, once I got the 3D acceleration going they both worked fine, other than patching and such. I do believe that the error at the end-

Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg

is related to your lack of 3D acceleration.

---

### Post by hoagie on 2006-09-18
Thanks guys I'll try what you said by the time I get home:-\" =D>

---

### Post by hoagie on 2006-09-18
Reinstalled doom3, and installed nvidia drivers and I still get the same error message. Maybe I got the worng installer?

---

### Post by hoagie on 2006-09-18
Neither ut20004 worked, arg maybe I shall stop right here, except if you guys can think of something else. ](*,)

---

### Post by Perfect Storm on 2006-09-18
By any chance: Do you run XGL and compiz?

---

### Post by hoagie on 2006-09-18
Nope

---

### Post by Stew2 on 2006-09-19
Sorry man, I'm stumped. I thought for sure that it was your video drivers giving you trouble as I had similiar problems until I got my 3D acceleration working. What type of video card do you have?

Regards,
Stew2

---

### Post by hoagie on 2006-09-19
I'm using an Nvidia Geforce FX 5700 LE (128 mb)

---

### Post by Perfect Storm on 2006-09-19
How's your xorg.conf looks like?

```
cat /etc/X11/xorg.conf
```

---

### Post by Pinoy915 on 2006-09-19
I had the same problem. I installed a smaller file that says Doom 3 1.3. There is a huge demo version compared to the one I downloaded. It was like 400mb vs 60mb. My Enemy Territory works flawlessly so I do have 3d acceleration enabled. I have not installed the bigger demo file though. I'll try it out later.

---

### Post by hoagie on 2006-09-19
> **Artificial Intelligence said:**
> How's your xorg.conf looks like?

```
cat /etc/X11/xorg.conf
```

Ok here we go: (I won't post the comments #)

```
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
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
        Identifier      "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "LM720/LM720A"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
        Monitor         "LM720/LM720A"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
EndSection

Section "DRI"
        Mode    0666
EndSection
```

---

### Post by Pinoy915 on 2006-09-19
I installed the huge file one and it works...somewhat. The sound is all weird and my fps isn't as good compared to running it on Windows. I've yet to tweak it though.

---

### Post by espikenl on 2007-11-06
the whole Sys_Error: Couldn't load default.cfg is coused by not putting the big pk4 files in the correct map. do that, and the game will start

---

