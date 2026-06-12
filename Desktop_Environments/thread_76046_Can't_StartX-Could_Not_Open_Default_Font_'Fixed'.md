---
title: "Can't StartX-Could Not Open Default Font 'Fixed'"
date: 2005-10-14
forum: Desktop Environments
---

### Post by awtomlinson on 2005-10-14
This thread was closed earlier, so I have to open this issue with a new thread.  I am getting the Could Not Open Default Font 'Fixed' error & I can't start x.  I have completed all steps in the related threads.  My systems specs are:

NVIDIA 5600Ultra video card
athlon xp 3200+ cpu
asus motherboard
1 gb RAM
sony vaio 17 inch trinitron flat screen monitor

I did a fresh install of the final release candidate of Breezy the day before the official release.  I have tried the following steps to resolve the issue, yet the error persists:

1.  sudo dpkg-reconfigure xserver-xorg
2.  sudo apt-get install ubuntu-base ubuntu-desktop
3.  sudo apt-get update & then apt-get dist-upgrade after the official Breezy release on the 13th
4.  sudo /etc/init.d/udev restart & then sudo /etc/init.d/gdm restart
5.  rolled back to the previous udev version & then updated udev
6.  changed ownership of .Xauthority file to my account
7.  tried to change ownership of the .ICEauthority file, but was told that this file did not exist (perhaps this is the issue?)
8.  ensured that x-fonts-base was installed with the latest version
9.  changed font directories from /etc/X11/xorg.conf to /usr/share/X11/fonts
10.  in the /usr/share directory, i made symlinks by:  sudo ln -s /usr/X11R6/lib/X11
11.  changed the nvidia setting from nv to another one recommended in a previous thread (can't remember which one right now, can find out if necessary) & then changed back to nv

Can anyone please help?  This is driving me crazy.  I have never had any issues with the exact same system specs using both Warty & Hoary.  As I stated earlier, everyone else resolved the issue by using one of the above 11 fixes, but I still get the same error.

---

### Post by Stormy Eyes on 2005-10-14
Did you try running **fc-cache --fv** with sudo?

---

### Post by awtomlinson on 2005-10-14
thanks.  so, i do:

sudo fc-cache --fv

what will this do?

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=awtomlinson]thanks.  so, i do:

sudo fc-cache --fv

what will this do?[/QUOTE]

fc-cache creates indexes of fonts compatible with X.org's FreeType library in each font directory. This should let X find your fonts.

---

### Post by awtomlinson on 2005-10-14
nope, sudo fc-cache --fv produces the exact same error.  someone, anyone, PLEASE HELP!  this is killing my productivity & making me use (gasp) winxp.

---

### Post by awtomlinson on 2005-10-14
someone please help, i don't want to give up on ubuntu, i've been using it since the day it came out!  it does seem that hardware detection has taken a step backward with breezy.

---

### Post by chaumurky on 2005-10-14
This makes no sense. With those steps it should work. Post your xorg.conf just to confirm it's all fine. Also, perhaps /var/log/Xorg.0.log may have more verbose errors.

---

### Post by awtomlinson on 2005-10-14
thanks.  how can send the output of these files in an email message?  i have only a terminal so i would like to email these files to myself, then use winxp to copy & paste into my reply.

---

### Post by chaumurky on 2005-10-14
You got me on that one. If you have ssh installed you could download and run the free '**putty'** ssh client in windows to log into your Ubuntu machine. You can then list, copy and paste the file info from the putty console. That's my only suggestion. I'm not familiar with console based email.

---

### Post by awtomlinson on 2005-10-14
o.k.  then, is there any other way i can copy the entire file from the terminal and paste it into a response?

---

### Post by awtomlinson on 2005-10-15
[QUOTE=chaumurky]This makes no sense. With those steps it should work. Post your xorg.conf just to confirm it's all fine. Also, perhaps /var/log/Xorg.0.log may have more verbose errors.[/QUOTE]

How can I post my xorg.conf or  /var/log/Xorg.0.log files when all I have is a terminal?

---

### Post by awtomlinson on 2005-10-15
o.k.  i perfomed the following:

1.  sudo apt-get install nvidia-glx
2.  sudo apt-get install nvidia-settings
3.  sudo nvidia-glx-config enable

i then tried to startx again.  the nvidia logo appeared, but x still would not start, and i received the same error.  i had to manually write down my xorg.conf file errors, so here they are:

warning:  font renderer for .bdf already registered at priority 0
warning:  font renderer for .bdf.Z already registered at priority 0
warning:  font renderer for .bdf.gz already registered at priority 0
warning:  font renderer for .pmp already registered at priority 0

fatal server error:
could not open default font 'fixed'
the x server's font paths might be misconfigured, remote font server(s) may be unreachable, and/or local fonts may not be installed or are not configured correctly

---

### Post by chaumurky on 2005-10-15
[quote=awtomlinson]How can I post my xorg.conf or /var/log/Xorg.0.log files when all I have is a terminal?[/quote]

go:

```
less /var/log/Xorg.0.log
```

in a putty terminal. Find the bit where the errors are and select and copy it. Then paste it in a new post.

---

### Post by awtomlinson on 2005-10-15
[QUOTE=chaumurky]go:

```
less /var/log/Xorg.0.log
```

in a putty terminal. Find the bit where the errors are and select and copy it. Then paste it in a new post.[/QUOTE]

dude, i have no clue how to do what you are talking about

---

### Post by awtomlinson on 2005-10-15
the point is, ubuntu should automatically detect all of my hardware, its not like i have some weird setup.  hoary used xorg instead of xfree86, and this was not an issue.  if i want to edit configuration files in terminal mode, i'll use slackware.  ubuntu has taken a giant step backward in my opinion.  i've been using ubuntu since the original warty release, but maybe its just time to go back to windows.  i want something that just works.  breezy just does not work out of the box.

---

### Post by chaumurky on 2005-10-15
you forgot [/ENDRANT] :p

It has nothing to do with hardware, and I agree it should be working. Coming to the conclusion that Ubuntu has gone a step backward because of your single and personal experience is, frankly, petulant and defeatist. I'm trying to help you if you still want it. 

* Install ssh: [B]sudo apt-get install ssh

[/B]* Then, in Windows download and install this: [http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe]("http://the.earth.li/%7Esgtatham/putty/latest/x86/putty.exe")

* Run it and enter your Ubuntu box's IP and connect, login and you will have a terminal in XP - now you can display stuff witout having to email.

* In the terminal go **less /etc/X11/xorg.conf  **to display the contents.

* Copy the contents displayed and post them here.

This is the only way I know how to get information from another box that doesn't have X running. If you manage to do this it'll serve you well in other situations. Good luck, and chin up.

---

### Post by awtomlinson on 2005-10-15
thanks, chaumurky.  i'll try this in a second.  i've just been so spoiled with ubuntu in the past, i'm not used to everything not just working.  i still believe that linux is far better than windows, i'm just very frustrated, this has been going on since wednesday.

---

### Post by awtomlinson on 2005-10-15
the thing is, i have a dual boot system, with ubunutu & winxp.  so, they have the same ip address.  i don't have another computer.  will this still work?

---

### Post by chaumurky on 2005-10-15
Ahh, bugger, it won't work then. Do you have a usb key or floppy disk to put the files on?

---

### Post by awtomlinson on 2005-10-15
i have an sd card, but no card reader, no floppy drive.  all i have is my canon camera, and i don't think i can write to the card like this via the camera.  how can i mount the sd card in ubuntu?  or, how can i write to a cd in ubuntu from the command line?  i don't mind wasting a cd if i can fix this.

---

### Post by awtomlinson on 2005-10-15
another option is, i actually do have two computers, one is my work computer.  but i have only one internet connection.  however, i had already planned to buy a router tomorrow, so when i have the router set up, i can install putty on my work system and connect to my ubuntu machine from my work machine.  this would probably be the easiest solution, no?

---

### Post by chaumurky on 2005-10-15
Yes. That sounds like the best way. Make sure both boxes allow port 22 in any firewalls you're running. 

Doing all this may seem to be a red herring but, like I said earlier, it will be useful future. Unfortunately, the only way all this is going to help you is that we will be able to see your logs and config. I hope there will be a clue in there. Still, all this is a learning experience. I too had the same fonts issue when I upgraded and it also appeared in VNC. Changing the paths did it for me so that's why I'm intrigued that it didn't work for you. It may still just be a typo - that's why seeing the actual file data might help.

---

### Post by awtomlinson on 2005-10-15
i can't connect via putty.  how can i ensure that port 22 is open on my ubuntu box?

---

### Post by chaumurky on 2005-10-15
If you're not running a firewall it should not be blocked. Can you ping the IP from a windows command-line? Make sure your windows firewall is off. I'll try to help you out today but I've got several things going on so I may not be around as often.

---

### Post by awtomlinson on 2005-10-15
nope, can't ping it.  no software firewall, just the router.  my ip address is dynamically assigned, so what to do?

---

### Post by awtomlinson on 2005-10-15
do i need to configure my new router with ubuntu?  with the winxp partition, everything was automatic.  i installed ssh on ubuntu, and i am currently logged into ubuntu.  sending this from my work system with winxp.

---

### Post by chaumurky on 2005-10-16
To make sure you're using the right ip go **ifconfig** on the ubuntu box. If you can't ping that ip from the XP box there's something strange going on.

EDIT: If this is getting too painful maybe you should get hold of a live CD if you have any laying around - Knoppix, Ubuntu Live etc. Boot up on that and mount your Ubuntu partition. Then you can open the files and post the contents.

---

### Post by awtomlinson on 2005-10-16
chaumurky, thank you so much.  here is the file, minus the comments:

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
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
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV31 [GeForce FX 5600 Ultra]"
        Driver          "nv"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "SONY HMD-A20"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV31 [GeForce FX 5600 Ultra]"
        Monitor         "SONY HMD-A20"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by cpminga on 2005-10-16
Hey... I'm a complete noob when it comes to Linux so if what i say makes no sence then please disregaurd!

I think i had a similar problem earlier this evening. I tried the same steps you outlined above and they didn't work for me either. What i did was

sudo gdm restart

and everything was back.

Again, i'm not sure if this is what you're looking for but there you have it anyway :)

---

### Post by chaumurky on 2005-10-16
Looks fine. The problem isn't there.

Try:
[B]apt-get --reinstall install xfonts-base

[/B]just in case.

Other ideas :

* Is **/usr/share/X11/fonts/misc/fonts.alias** missing?

* Lets have a look at **/var/log/Xorg.0.log** can you post that?

---

### Post by awtomlinson on 2005-10-16
here's the /usr/share/X11/fonts/misc/fonts.alias file:

fixed        -misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-1
variable     -*-helvetica-bold-r-normal-*-*-120-*-*-*-*-iso8859-1
5x7          -misc-fixed-medium-r-normal--7-70-75-75-c-50-iso8859-1
5x8          -misc-fixed-medium-r-normal--8-80-75-75-c-50-iso8859-1
6x9          -misc-fixed-medium-r-normal--9-90-75-75-c-60-iso8859-1
6x10         -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-1
6x12         -misc-fixed-medium-r-semicondensed--12-110-75-75-c-60-iso8859-1
6x13         -misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-1
6x13bold     -misc-fixed-bold-r-semicondensed--13-120-75-75-c-60-iso8859-1
7x13         -misc-fixed-medium-r-normal--13-120-75-75-c-70-iso8859-1
7x13bold     -misc-fixed-bold-r-normal--13-120-75-75-c-70-iso8859-1
7x14         -misc-fixed-medium-r-normal--14-130-75-75-c-70-iso8859-1
7x14bold     -misc-fixed-bold-r-normal--14-130-75-75-c-70-iso8859-1
8x13         -misc-fixed-medium-r-normal--13-120-75-75-c-80-iso8859-1
8x13bold     -misc-fixed-bold-r-normal--13-120-75-75-c-80-iso8859-1
8x16         -sony-fixed-medium-r-normal--16-120-100-100-c-80-iso8859-1
9x15         -misc-fixed-medium-r-normal--15-140-75-75-c-90-iso8859-1
9x15bold     -misc-fixed-bold-r-normal--15-140-75-75-c-90-iso8859-1
10x20        -misc-fixed-medium-r-normal--20-200-75-75-c-100-iso8859-1
12x24        -sony-fixed-medium-r-normal--24-170-100-100-c-120-iso8859-1
nil2         -misc-nil-medium-r-normal--2-20-75-75-c-10-misc-fontspecific


k14          -misc-fixed-medium-r-normal--14-*-*-*-*-*-jisx0208.1983-0
a14          -misc-fixed-medium-r-normal--14-*-*-*-*-*-iso8859-1
r14          -misc-fixed-medium-r-normal--14-*-*-*-*-*-jisx0201.1976-0
rk14         -misc-fixed-medium-r-normal--14-*-*-*-*-*-jisx0201.1976-0
r16          -sony-fixed-medium-r-normal--16-*-*-*-*-*-jisx0201.1976-0
rk16         -sony-fixed-medium-r-normal--16-*-*-*-*-*-jisx0201.1976-0
r24          -sony-fixed-medium-r-normal--24-*-*-*-*-*-jisx0201.1976-0
rk24         -sony-fixed-medium-r-normal--24-*-*-*-*-*-jisx0201.1976-0
kana14       -misc-fixed-medium-r-normal--14-*-*-*-*-*-jisx0201.1976-0
8x16kana     -sony-fixed-medium-r-normal--16-120-100-100-c-80-jisx0201.1976-0
8x16romankana -sony-fixed-medium-r-normal--16-120-100-100-c-80-jisx0201.1976-0
12x24kana     -sony-fixed-medium-r-normal--24-170-100-100-c-120-jisx0201.1976-0
12x24romankana -sony-fixed-medium-r-normal--24-170-100-100-c-120-jisx0201.1976-0
kanji16      -jis-fixed-medium-r-normal--16-*-*-*-*-*-jisx0208.1983-0
kanji24      -jis-fixed-medium-r-normal--24-*-*-*-*-*-jisx0208.1983-0

hanzigb16st "-isas-song ti-medium-r-normal--16-160-72-72-c-160-gb2312.1980-0"
hanzigb24st "-isas-song ti-medium-r-normal--24-240-72-72-c-240-gb2312.1980-0"
hanzigb16fs "-isas-fangsong ti-medium-r-normal--16-160-72-72-c-160-gb2312.1980-0"

olcursor   "-sun-open look cursor-----12-120-75-75-p-160-sunolcursor-1"
olglyph-10 "-sun-open look glyph-----10-100-75-75-p-101-sunolglyph-1"

---

### Post by awtomlinson on 2005-10-16
woops, here's the rest of the fonts.alias file:

-misc-fixed-medium-r-normal--7-50-100-100-c-50-iso8859-1 -misc-fixed-medium-r-normal--7-70-75-75-c-50-iso8859-1
-misc-fixed-medium-r-normal--8-60-100-100-c-50-iso8859-1 -misc-fixed-medium-r-normal--8-80-75-75-c-50-iso8859-1
-misc-fixed-medium-r-normal--9-80-100-100-c-60-iso8859-1 -misc-fixed-medium-r-normal--9-90-75-75-c-60-iso8859-1
-misc-fixed-medium-r-normal--10-70-100-100-c-60-iso8859-1 -misc-fixed-medium-r-normal--10-100-75-75-c-60-iso8859-1
-misc-fixed-medium-r-semicondensed--12-90-100-100-c-60-iso8859-1 -misc-fixed-medium-r-semicondensed--12-110-75-75-c-60-iso8859-1
-misc-fixed-medium-r-semicondensed--13-100-100-100-c-60-iso8859-1 -misc-fixed-medium-r-semicondensed--13-120-75-75-c-60-iso8859-1
-misc-fixed-bold-r-semicondensed--13-100-100-100-c-60-iso8859-1 -misc-fixed-bold-r-semicondensed--13-120-75-75-c-60-iso8859-1
-misc-fixed-medium-r-normal--13-100-100-100-c-70-iso8859-1 -misc-fixed-medium-r-normal--13-120-75-75-c-70-iso8859-1
-misc-fixed-bold-r-normal--13-100-100-100-c-70-iso8859-1 -misc-fixed-bold-r-normal--13-120-75-75-c-70-iso8859-1
-misc-fixed-medium-r-normal--13-100-100-100-c-80-iso8859-1 -misc-fixed-medium-r-normal--13-120-75-75-c-80-iso8859-1
-misc-fixed-bold-r-normal--13-100-100-100-c-80-iso8859-1 -misc-fixed-bold-r-normal--13-120-75-75-c-80-iso8859-1
-misc-fixed-medium-r-normal--14-110-100-100-c-70-iso8859-1 -misc-fixed-medium-r-normal--14-130-75-75-c-70-iso8859-1
-misc-fixed-medium-r-normal--15-120-100-100-c-90-iso8859-1 -misc-fixed-medium-r-normal--15-140-75-75-c-90-iso8859-1
-misc-fixed-bold-r-normal--15-120-100-100-c-90-iso8859-1 -misc-fixed-bold-r-normal--15-140-75-75-c-90-iso8859-1
-misc-fixed-medium-r-normal--20-140-100-100-c-100-iso8859-1 -misc-fixed-medium-r-normal--20-200-75-75-c-100-iso8859-1
-sony-fixed-medium-r-normal--16-150-75-75-c-80-iso8859-1 -sony-fixed-medium-r-normal--16-120-100-100-c-80-iso8859-1
-sony-fixed-medium-r-normal--16-150-75-75-c-80-jisx0201.1976-0 -sony-fixed-medium-r-normal--16-120-100-100-c-80-jisx0201.1976-0
-sony-fixed-medium-r-normal--24-230-75-75-c-120-iso8859-1 -sony-fixed-medium-r-normal--24-170-100-100-c-120-iso8859-1
-sony-fixed-medium-r-normal--24-230-75-75-c-120-jisx0201.1976-0 -sony-fixed-medium-r-normal--24-170-100-100-c-120-jisx0201.1976-0
-jis-fixed-medium-r-normal--16-110-100-100-c-160-jisx0208.1983-0 -jis-fixed-medium-r-normal--16-150-75-75-c-160-jisx0208.1983-0
-jis-fixed-medium-r-normal--24-170-100-100-c-240-jisx0208.1983-0 -jis-fixed-medium-r-normal--24-230-75-75-c-240-jisx0208.1983-0
(END)

---

### Post by awtomlinson on 2005-10-16
chaumurky, & here is var/log/Xorg.0.log:  the forums won't let me post the whole file, it says its too long, so i have to break it up:

Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:
36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 16 11:53:27 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SONY HMD-A20"
(**) |   |-->Device "NVIDIA Corporation NV31 [GeForce FX 5600 Ultra]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
        Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
        Entry deleted from font path.
        (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fon
ts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.2
        X.Org Video Driver: 0.7
        X.Org XInput driver : 0.4
        X.Org Server Extension : 0.2
        X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 147b,1c00 rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 147b,1c00 rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 147b,1c00 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 147b,1c00 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 147b,1c00 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 147b,1c00 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 147b,1c00 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,006b card 147b,1c00 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 147b,1c00 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 147b,1c00 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0d:0: chip 10de,006e card 147b,1c00 rev a3 class 0c,00,10 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 02:00:0: chip 10de,0311 card 270f,1944 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
        [0] -1  0       0x00009000 - 0x0000afff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xda000000 - 0xdbffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation NV31 [GeForce FX 5600 Ultra] rev 161, Mem @ 0xd8000000/24, 0xd0000000/27
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [6] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xcfffffff to 0xbfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [1] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [2] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [3] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [4] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [5] -1  0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [6] -1  0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [7] -1  0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [8] -1  0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [9] -1  0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [10] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [11] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [12] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [13] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [14] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [15] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [1] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [2] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [3] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [4] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [5] -1  0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [6] -1  0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [7] -1  0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [8] -1  0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [9] -1  0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [10] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [11] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [12] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [13] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [14] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [15] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [6] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [6] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [7] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [8] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [9] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [10] -1 0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [11] -1 0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [12] -1 0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [13] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [14] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [15] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [19] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [20] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [21] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 6.8.2, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.7667
        Module class: XFree86 Server Extension
        ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.2
        Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.1.0
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nv"
(II) Loading /usr/X11R6/lib/modules/drivers/nv_drv.o
(II) Module nv: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.4
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
        Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
        Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
        GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
        GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
        Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
        GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
        GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
        GeForce4 440 Go 64M, Quadro4 NVS, Quadro4 500 GoGL,
        GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
        GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
        GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
        Quadro4 280 NVS, Quadro4 380 XGL, Quadro NVS 50 PCI, GeForce4 448 Go,
        GeForce4 MX Integrated GPU, GeForce3, GeForce3 Ti 200,
        GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600, GeForce4 Ti 4400,
        0x0252, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
        Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
        GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
        Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
        GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
        GeForce FX 5600 Ultra, GeForce FX 5600, 0x0313, GeForce FX 5600SE,
        0x0316, 0x0317, GeForce FX Go5600, GeForce FX Go5650,
        Quadro FX Go700, 0x031D, 0x031E, 0x031F, GeForce FX 5200,
GeForce FX 5200 Ultra, GeForce FX 5200, GeForce FX 5200SE,
        GeForce FX Go5200, GeForce FX Go5250, GeForce FX 5500,
        GeForce FX 5100, GeForce FX Go5200 32M/64M, 0x0329,
        Quadro NVS 280 PCI, Quadro FX 500/600 PCI, GeForce FX Go53xx Series,
        GeForce FX Go5100, 0x032F, GeForce FX 5900 Ultra, GeForce FX 5900,
        GeForce FX 5900XT, GeForce FX 5950 Ultra, Quadro FX 700,
        GeForce FX 5900ZT, Quadro FX 3000, GeForce FX 5700 Ultra,
        GeForce FX 5700, GeForce FX 5700LE, GeForce FX 5700VE, 0x0345,
        GeForce FX Go5700, GeForce FX Go5700, 0x0349, 0x034B,
        Quadro FX Go1000, Quadro FX 1100, 0x034F, GeForce 6800 Ultra,
        GeForce 6800, GeForce 6800 LE, 0x0043, GeForce 6800 GT, 0x0049,
        Quadro FX 4000, 0x00C0, GeForce 6800, GeForce 6800 LE,
        GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400, 0x00CD,
        Quadro FX 1400, GeForce 6600 GT, GeForce 6600, 0x0142, 0x0143,
        GeForce Go 6600, GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, 0x0147,
        GeForce Go 6600, 0x0149, 0x014B, 0x014C, 0x014D, Quadro FX 540,
        GeForce 6200, 0x0160, GeForce 6200 TurboCache(TM), 0x0162, 0x0163,
        GeForce Go 6200, 0x0163, GeForce Go 6250, GeForce Go 6200,
        GeForce Go 6250, 0x0169, 0x016B, 0x016C, 0x016D, 0x016E, 0x0210,
        GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, 0x0220, 0x0221,
        0x0222, 0x0228

---

### Post by awtomlinson on 2005-10-16
here's part 2 of the file:

(II) Primary Device is: PCI 02:00:0
(--) Chipset GeForce FX 5600 Ultra found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [6] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [7] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [8] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [9] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [10] -1 0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [11] -1 0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [12] -1 0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [13] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [14] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [15] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [19] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [20] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [21] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
[1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [6] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [7] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [8] -1  0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [9] -1  0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [10] -1 0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [11] -1 0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [12] -1 0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [13] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [14] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [15] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [16] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [17] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [18] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [21] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [22] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [23] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [24] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [25] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [26] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [27] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce FX 5600 Ultra"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xD0000000
(--) NV(0): MMIO registers at 0xD8000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): SONY HMD-A20: Using default hsync range of 28.00-33.00 kHz
(II) NV(0): SONY HMD-A20: Using default vrefresh range of 43.00-72.00 Hz
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (hsync out of range)
(II) NV(0): Not using default mode "320x175" (hsync out of range)
(II) NV(0): Not using default mode "640x400" (hsync out of range)
(II) NV(0): Not using default mode "320x200" (hsync out of range)
(II) NV(0): Not using default mode "720x400" (hsync out of range)
(II) NV(0): Not using default mode "360x200" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1280x768" (hsync out of range)
(II) NV(0): Not using default mode "640x384" (hsync out of range)
(II) NV(0): Not using default mode "1280x800" (hsync out of range)
(II) NV(0): Not using default mode "640x400" (hsync out of range)
(II) NV(0): Not using default mode "1152x768" (hsync out of range)
(II) NV(0): Not using default mode "576x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using mode "1280x1024" (no mode of this name)
(II) NV(0): Not using mode "1152x864" (no mode of this name)
(II) NV(0): Not using mode "1024x768" (no mode of this name)
(II) NV(0): Not using mode "800x600" (no mode of this name)
(--) NV(0): Virtual size is 640x480 (pitch 640)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(++) NV(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 1.2.0
        ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 6.8.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
        [1] 0   0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B]
        [2] -1  0       0xffe00000 - 0xffffffff (0x200000) MX[B](B)
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xdc085000 - 0xdc08503f (0x40) MX[B]
        [8] -1  0       0xdc084000 - 0xdc0847ff (0x800) MX[B]
        [9] -1  0       0xdc081000 - 0xdc081fff (0x1000) MX[B]
        [10] -1 0       0xdc000000 - 0xdc07ffff (0x80000) MX[B]
        [11] -1 0       0xdc087000 - 0xdc087fff (0x1000) MX[B]
        [12] -1 0       0xdc086000 - 0xdc0860ff (0x100) MX[B]
        [13] -1 0       0xdc083000 - 0xdc083fff (0x1000) MX[B]
        [14] -1 0       0xdc080000 - 0xdc080fff (0x1000) MX[B]
        [15] -1 0       0xc0000000 - 0xbfffffff (0x0) MX[B]O
        [16] -1 0       0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
        [17] -1 0       0xd8000000 - 0xd8ffffff (0x1000000) MX[B](B)
        [18] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [19] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [20] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [21] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [22] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [23] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [24] -1 0       0x0000b800 - 0x0000b87f (0x80) IX[B]
        [25] -1 0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [26] -1 0       0x0000b000 - 0x0000b007 (0x8) IX[B]
        [27] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [28] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [29] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xd0000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
 Solid Lines
        Scanline Image Writes
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
AUDIT: Sun Oct 16 11:53:33 2005: 9573 X: client 6 rejected from local host

---

### Post by chaumurky on 2005-10-16
OK, here's where I teeter on the edge of my knowledge, but 2 things stand out in that log although they may not be important in this case:

** (EE) Failed to initialize GLX extension (NVIDIA X driver not found)**

and

** AUDIT: Sun Oct 16 11:53:33 2005: 9573 X: client 6 rejected from local host**

It looks like you have tried step 11 so I'm out of ideas. I'm hoping other members have a better insight as to where to go from here. Perhaps other logs to check.

---

### Post by awtomlinson on 2005-10-16
can anyone please help?  this is driving me crazy!  i want to use ubuntu again!

---

### Post by awtomlinson on 2005-10-16
o.k. i no longer get the "could not open default font 'fixed'" error.  i uninstalled and reinstalled all nvidia files (nvidia-glx & nvidia-settings).  i now get the following error:

skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o" No symbols found

symbol _glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unrresolved!

symbol _glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unrresolved!

warning: font renderer for .bdf already registered at priority 0
warning: font renderer for .bdf.Z already registered at priority 0
warning: font renderer for .bdf.gz already registered at priority 0
warning: font renderer for .pmp already registered at priority 0

any ideas?

---

### Post by manatlan on 2005-10-17
[QUOTE=awtomlinson]can anyone please help?  this is driving me crazy!  i want to use ubuntu again![/QUOTE]

i had got the same trouble when i migrate from hoary to breezy
i've just done a :
apt-get install xfs
and a:
dpkg-configure xserver-xorg

and no more fixed font trouble !
hope it helps someone

---

### Post by awtomlinson on 2005-10-17
tried to install xfs, & received the following error:

Package xfs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xfs has no installation candidate

---

### Post by awtomlinson on 2005-10-17
manatlan, THANK YOU THANK YOU THANK YOU THANK YOU!!!!!!!!!  i just enabled universe & multiverse, installed xfs, & now i'm up & running.  thank you so much & thank you so much chaumuky for your patience & help.

---

### Post by chaumurky on 2005-10-17
:)

---

### Post by Stormy Eyes on 2005-10-17
Oh, bugger. I didn't even think to mention xfs; I thought the demon-ridden thing was installed by default. Time to fall on my sword, I guess.

---

### Post by fortran01 on 2006-06-28
Re-install xfonts-base

---

### Post by Fisslefink on 2006-07-16
> **fortran01 said:**
> Re-install xfonts-base

Thank you fortran01!  You just saved the day for my Kubuntu box.  I did a dist-upgrade on Kubuntu Edgy, which had been working fine for over a week, and suddenly my Xorg was broken with this darn "default font fixed" fatal server error.

**apt-get install --reinstall xfonts-base** fixed it, and I was able to start Kubuntu with **startx** or rebooting.

For those who care, more details in this thread:

[http://www.ubuntuforums.org/showthread.php?p=1264361#post1264361](http://www.ubuntuforums.org/showthread.php?p=1264361#post1264361)

Fisslefink

---

### Post by glenner on 2006-10-21
There is a related bug created here. [https://launchpad.net/distros/ubuntu/+source/xorg/+bug/66809](https://launchpad.net/distros/ubuntu/+source/xorg/+bug/66809)

---

### Post by CLod on 2007-06-07
I don't understand how u resolved this problem.. I still have the same problem about fixed fonts.. I checked all paths, the config is ok, xfs is installed... but the problem remains...

---

### Post by NoobieDoobieDo on 2007-08-05
I had this same problem.

I did an upgrade from 6.06 to 6.10 and that broke gnome so I've been using XFCE.  I did apt-get upgrade and then when I exited XFCE I got the "could not open default font 'fixed'" message.

Playing aroung with apt-get I noticed xserver-xorg wasn't installed !

I did apt-get install xserver-xorg and then GDM started fine (still no gnome !)

Cheers

---

