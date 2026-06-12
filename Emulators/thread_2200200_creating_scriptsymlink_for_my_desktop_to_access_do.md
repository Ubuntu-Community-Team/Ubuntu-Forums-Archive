---
title: "creating script/symlink for my desktop to access dosbox duke1.exe"
date: 2014-01-18
forum: Emulators
---

### Post by Drone4four on 2014-01-18
I bought Duke Nukem 1 + 2 and Keen 1-5 on Steam on Windows for a few bucks the other day.  Steam automatically installs dosbox which is used to play those old games.  I copied the folders and exes directly from steam on Windows over to my home directory on Ubuntu.   I installed dosbox from the Ubuntu repos and these dos games from the early 90s run flawlessly.  What I am trying to do now is create an icon on my desktop which will run the command ‘dosbox ~/Duke\ Nukem\ 1/DN1.EXE’.  I initially thought that its possible to pull this off by creating a symbolic link, writing a bash script, creating an environmental variable or some combination of the above.

My first thought, which was to use a symlink, I believed was a good idea, but from what I gather from Google, symlinks are used more so to refer to a special file or folder.  I’m trying to bind a command to an exe.

The I ventured to look into how to make ‘dosbox ~/Duke\ Nukem\ 1/DN1.EXE’ an environmental variable in /usr/bin?  Is that even possible?  I Googled, create environment variables linux.  As per [this guide]("http://stackoverflow.com/questions/3035427/how-to-create-a-new-environment-variable-in-unix"), I sorta guessed correctly that using ‘export myvar=duke1 dosbox ~/Duke\ Nukem\ 1/DN1.EXE’ wasn’t gonna work.  I then tried, ‘myvar=duke1 dosbox ~/Duke\ Nukem\ 1/DN1.EXE’.  This was the output of entering that command (and then me hopelessly entering ‘duke1’):
```

l(gnull@raring)-(0)-(12:25 AM Sat Jan 18)->
m-(~)-(39 files, 26Mb)--> sudo myvar=duke1 dosbox ~/Duke\ Nukem\ 1/DN1.EXE
[sudo] password for gnull: 
DOSBox version 0.74
Copyright 2002-2010 DOSBox Team, published under GNU GPL.
---
CONFIG:Loading primary settings from config file /home/gnull/.dosbox/dosbox-0.74.conf
MIXER:Got different values from SDL: freq 44100, blocksize 512
ALSA:Can't subscribe to MIDI port (65:0) nor (17:0)
MIDI:Opened device:none

l(gnull@raring)-(0)-(12:26 AM Sat Jan 18)->
m-(~)-(39 files, 26Mb)--> duke1
duke1: command not found

l(gnull@raring)-(0)-(12:26 AM Sat Jan 18)->
m-(~)-(39 files, 26Mb)-->

```
For something specific to dosbox and exes, I Googled ‘set environment variables dosbox exe’.  No dice.

The final alternative that I mentioned was to write a bash script.  Learning to script sounds like a promising, rewarding endeavour, but The Linux Documentation Project’s [Bash Beginner’s Guide ]("http://www.tldp.org/LDP/Bash-Beginners-Guide/html/") is so goddamned overwhelming.  I don’t have dozens of hours to sit down and figure out how to script just to solve my basic problem.  

Can some kind soul out there please help me out?

Thanks for your attention.

---

### Post by MikeCyber on 2014-01-18
For ex. I start as below FSX with wine by clicking the sh script on my desktop.

#!/bin/sh
sed -i '99s/.*/PageID=0/g' /home/michael/.wine/drive_c/users/michael/Application\ Data/Microsoft/FSX/fsx.CFG 
cd /media/michael/WineDATA/FSX/
wine fsx.exe


I remember wine doing better when installing an app with wine but I don't have such a start icon right now.

---

### Post by R33D3M33R on 2014-01-18
This is how I run my gog version of Duke Nukem:

.desktop file
```

[Desktop Entry]
Comment=Duke Nukem 1+2
Exec=dosbox -conf '/home/andrej/Igre/3DRealms/Duke Nukem 1+2/dosbox_duke_linux.conf'
Icon=dosbox
Name=Duke Nukem
NoDisplay=false
Path[$e]=
StartupNotify=true
Terminal=0
TerminalOptions=
Type=Application
X-KDE-SubstituteUID=false
X-KDE-Username=
```

In the file dosbox_duke_linux.conf I just edited the mount command to the Linux version:

```

[autoexec]
# Lines in this section will be run at startup.
@echo off
mount C "/media/Podatki/Igre/3DRealms/Duke Nukem 1+2/"
```

---

### Post by Irihapeti on 2014-01-18
*Thread moved to **Emulators**.*

---

### Post by Drone4four on 2014-01-18
I did my best to adapt R33D3M33R&#8217;s .desktop file and duke conf. I first tried this:

```

 [Desktop Entry]
Comment=Duke Nukem 1
Exec=dosbox -conf '/home/gnull/Duke Nukem 1/dosbox_duke_linux.conf'
Icon=dosbox
Name=Duke Nukem
NoDisplay=false
Path[$e]=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-KDE-SubstituteUID=false
X-KDE-Username=

```
and
```

[autoexec]
# Lines in this section will be run at startup.
@echo off
mount C "/home/gnull/Duke Nukem 1/"

```

According to [Arch Linux wiki]("https://wiki.archlinux.org/index.php/Desktop_Entries"), desktop-file-validate is deprecated, but I used it anyways. Is this foolish of me?  Here it is:

```

l(gnull@raring)-(0)-(01:00 PM Sat Jan 18)->
m-(~)-(39 files, 26Mb)--> desktop-file-validate .desktop 
.desktop: error: value "dosbox -conf '/home/gnull/Duke Nukem 1/dosbox_duke_linux.conf'" for key "Exec" in group "Desktop Entry" contains a reserved character ''' outside of a quote
.desktop: error: value "dosbox -conf '/home/gnull/Duke Nukem 1/dosbox_duke_linux.conf'" for key "Exec" in group "Desktop Entry" contains a reserved character ''' outside of a quote
.desktop: error: file contains key "Path[$e]" in group "Desktop Entry", but key names must contain only the characters A-Za-z0-9- (they may have a "[LOCALE]" postfix)
.desktop: warning: key "TerminalOptions" in group "Desktop Entry" is deprecated

l(gnull@raring)-(0)-(01:01 PM Sat Jan 18)->
m-(~)-(39 files, 26Mb)-->

```
A reserved character is defined [here]("http://www.computerhope.com/jargon/r/resechar.htm") as:
>  
a character or set of characters that cannot be used because of their use in other locations or by the operating system. For example, many operating systems reserve the following characters: "\, /, :, *, ?, ", <, >, and |" and will not allow these characters to be used when saving or renaming a file.


So I figure the validator doesn&#8217;t like the single quotation marks.  Here is my .desktop file without the single quotes:

```

[Desktop Entry]
Comment=Duke Nukem 1
Exec=dosbox -conf /home/gnull/Duke\ Nukem\ 1/dosbox_duke_linux.conf
Icon=dosbox
Name=Duke Nukem
NoDisplay=false
Path[$e]=
StartupNotify=true
Terminal=false
# TerminalOptions=
Type=Application
X-KDE-SubstituteUID=false
X-KDE-Username=

```

Here is the desktop-file-validate of the new file:

```

l(gnull@raring)-(0)-(01:01 PM Sat Jan 18)->
m-(~)-(39 files, 26Mb)--> desktop-file-validate .desktop 
.desktop: error: file contains key "Path[$e]" in group "Desktop Entry", but key names must contain only the characters A-Za-z0-9- (they may have a "[LOCALE]" postfix)

l(gnull@raring)-(0)-(08:15 PM Sat Jan 18)->
m-(~)-(39 files, 26Mb)--> 

```
This error says that characters in use are restricted to A-Za-z0-9-.  I thought that could be indicating that my usage of the backslashes in the Duke Nukem 1 file reference are the problem.  So I removed them and still no dice.  My last ditch effort was to actually rename the Duke Nukem 1 folder by removing all the spaces.  I still get the same desktop-validate-validate error. 

What could I try next?

---

### Post by R33D3M33R on 2014-01-19
I copied the .desktop file contents created with KmenuEdit and it appears Path[$e] is a [KDE specific thing]("https://bugs.kde.org/show_bug.cgi?id=321152") that might not work on other desktop environments. I think you can safely omit it.

---

### Post by Drone4four on 2014-01-19
Aye, R33D3M33R, that was a very simple solution.  Removing the instance of Path[$e]= was easy.  I shoulda figured that out for myself. The desktop file now validates.

I renamed my .desktop file to duke1-a.desktop.  duke1-a.desktop now is validated.  I read a small gnome 3 doc [on desktop files]("https://developer.gnome.org/integration-guide/stable/desktop-files.html.en").  As per this doc, I moved my duke1-a.desktop to ~/.local/share/applications.  Now when I search for Activities, Duke Nukem appears.  When I run it, dosbox loads, but Duke Nukem 1 does not.  What could I be doing wrong now?

Here is my duke1-a.desktop:

```

[Desktop Entry]
Comment=Duke Nukem 1
Exec=dosbox -conf /home/gnull/DukeNukem1/dosbox_duke_linux.conf
Icon=dosbox
Name=Duke Nukem
NoDisplay=false
#Path[$e]=
StartupNotify=true
Terminal=false
# TerminalOptions=
Type=Application
#X-KDE-SubstituteUID=false
#X-KDE-Username=
```

Here is my dosbox_duke_linux.conf:

```

[autoexec]
# Lines in this section will be run at startup.
@echo off
mount C "/home/gnull/DukeNukem1/"
```

---

### Post by R33D3M33R on 2014-01-20
You should copy the Steam version dosbox.conf and change the mount to your proper Linux path.

---

### Post by Drone4four on 2014-01-20
I moved my DukeNukem* directories into a new directory under my home folder.  I called it, DOSGAMES.  I changed the Exec line to: ```
 Exec=dosbox -conf /home/gnull/DOSGAMES/DukeNukem1/DN.conf 
``` 

As for my Duke Nukem configuration file, I tried a number of different mount points and none of them seemed to work.  I also tried a different cd parameter. 

Here is my duke1-a.desktop file:

```

[Desktop Entry]
Comment=Duke Nukem 1
Exec=dosbox -conf /home/gnull/DOSGAMES/DukeNukem1/DN.conf
Icon=dosbox
Name=Duke Nukem 1
NoDisplay=false
StartupNotify=true
Terminal=false
Type=Application

```

Here is my newly referenced unmodfied stock DN.conf from Steam:

```

# This is the configurationfile for DOSBox 0.72.
# Lines starting with a # are commentlines.
# They are used to (briefly) document the effect of each option.

[sdl]
# fullscreen -- Start dosbox directly in fullscreen.
# fulldouble -- Use double buffering in fullscreen.
# fullresolution -- What resolution to use for fullscreen: original or fixed size (e.g. 1024x768).
# windowresolution -- Scale the window to this size IF the output device supports hardware scaling.
# output -- What to use for output: surface,overlay,opengl,openglnb,ddraw.
# autolock -- Mouse will automatically lock, if you click on the screen.
# sensitiviy -- Mouse sensitivity.
# waitonerror -- Wait before closing the console if dosbox has an error.
# priority -- Priority levels for dosbox: lowest,lower,normal,higher,highest,pause (when not focussed).
#             Second entry behind the comma is for when dosbox is not focused/minimized.
# mapperfile -- File used to load/save the key/event mappings from.
# usescancodes -- Avoid usage of symkeys, might not work on all operating systems.

fullscreen=true
fulldouble=false
fullresolution=fixed
windowresolution=original
output=OpenGl
autolock=true
sensitivity=100
waitonerror=true
priority=higher,normal
mapperfile=mapper.txt
usescancodes=true

[dosbox]
# language -- Select another language file.
# memsize -- Amount of memory DOSBox has in megabytes.
# machine -- The type of machine tries to emulate:hercules,cga,tandy,pcjr,vga.
# captures -- Directory where things like wave,midi,screenshot get captured.

language=
machine=vga
captures=capture
memsize=16

[render]
# frameskip -- How many frames DOSBox skips before drawing one.
# aspect -- Do aspect correction, if your output method doesn't support scaling this can slow things down!.
# scaler -- Scaler used to enlarge/enhance low resolution modes.
#           Supported are none,normal2x,normal3x,advmame2x,advmame3x,hq2x,hq3x,
#                         2xsai,super2xsai,supereagle,advinterp2x,advinterp3x,
#                         tv2x,tv3x,rgb2x,rgb3x,scan2x,scan3x.
#           If forced is appended (like scaler=hq2x forced), the scaler will be used
#           even if the result might not be desired.

frameskip=0
aspect=false
scaler=normal2x

[cpu]
# core -- CPU Core used in emulation: normal,simple,dynamic,auto.
#         auto switches from normal to dynamic if appropriate.
# cycles -- Amount of instructions DOSBox tries to emulate each millisecond.
#           Setting this value too high results in sound dropouts and lags.
#           You can also let DOSBox guess the correct value by setting it to max.
#           The default setting (auto) switches to max if appropriate.
# cycleup   -- Amount of cycles to increase/decrease with keycombo.
# cycledown    Setting it lower than 100 will be a percentage.

core=auto
cycles=max
cycleup=500
cycledown=20

[mixer]
# nosound -- Enable silent mode, sound is still emulated though.
# rate -- Mixer sample rate, setting any devices higher than this will
#         probably lower their sound quality.
# blocksize -- Mixer block size, larger blocks might help sound stuttering
#              but sound will also be more lagged.
# prebuffer -- How many milliseconds of data to keep on top of the blocksize.

nosound=false
rate=22050
blocksize=2048
prebuffer=10

[midi]
# mpu401      -- Type of MPU-401 to emulate: none, uart or intelligent.
# device      -- Device that will receive the MIDI data from MPU-401.
#                This can be default,alsa,oss,win32,coreaudio,none.
# config      -- Special configuration options for the device. In Windows put
#                the id of the device you want to use. See README for details.

mpu401=intelligent
device=default
config=

[sblaster]
# sbtype -- Type of sblaster to emulate:none,sb1,sb2,sbpro1,sbpro2,sb16.
# sbbase,irq,dma,hdma -- The IO/IRQ/DMA/High DMA address of the soundblaster.
# mixer -- Allow the soundblaster mixer to modify the DOSBox mixer.
# oplmode -- Type of OPL emulation: auto,cms,opl2,dualopl2,opl3.
#            On auto the mode is determined by sblaster type.
#            All OPL modes are 'Adlib', except for CMS.
# oplrate -- Sample rate of OPL music emulation.

sbtype=sb16
sbbase=220
irq=5
dma=1
hdma=5
mixer=true
oplmode=auto
oplrate=22050

[gus]
# gus -- Enable the Gravis Ultrasound emulation.
# gusbase,irq1,irq2,dma1,dma2 -- The IO/IRQ/DMA addresses of the 
#            Gravis Ultrasound. (Same IRQ's and DMA's are OK.)
# gusrate -- Sample rate of Ultrasound emulation.
# ultradir -- Path to Ultrasound directory.  In this directory
#             there should be a MIDI directory that contains
#             the patch files for GUS playback.  Patch sets used
#             with Timidity should work fine.

gus=false

[speaker]
# pcspeaker -- Enable PC-Speaker emulation.
# pcrate -- Sample rate of the PC-Speaker sound generation.
# tandy -- Enable Tandy Sound System emulation (off,on,auto).
#          For auto Tandysound emulation is present only if machine is set to tandy.
# tandyrate -- Sample rate of the Tandy 3-Voice generation.
# disney -- Enable Disney Sound Source emulation. Covox Voice Master and Speech Thing compatible.

pcspeaker=true
pcrate=22050
tandy=auto
tandyrate=22050
disney=true

[joystick]
# joysticktype -- Type of joystick to emulate: auto (default), none,
#                 2axis (supports two joysticks,
#                 4axis (supports one joystick, first joystick used),
#                 4axis_2 (supports one joystick, second joystick used),
#                 fcs (Thrustmaster), ch (CH Flightstick).
#                 none disables joystick emulation.
#                 auto chooses emulation depending on real joystick(s).
# timed -- enable timed intervals for axis. (false is old style behaviour).
# autofire -- continuously fires as long as you keep the button pressed.
# swap34 -- swap the 3rd and the 4th axis. can be useful for certain joysticks.
# buttonwrap -- enable button wrapping at the number of emulated buttons.

joysticktype=auto
timed=true
autofire=false
swap34=false
buttonwrap=true

[serial]
# serial1-4 -- set type of device connected to com port.
#              Can be disabled, dummy, modem, nullmodem, directserial.
#              Additional parameters must be in the same line in the form of
#              parameter:value. Parameter for all types is irq.
#              for directserial: realport (required), rxdelay (optional).
#              for modem: listenport (optional).
#              for nullmodem: server, rxdelay, txdelay, telnet, usedtr,
#                             transparent, port, inhsocket (all optional).
#              Example: serial1=modem listenport:5000

serial1=dummy
serial2=dummy
serial3=disabled
serial4=disabled

[dos]
# xms -- Enable XMS support.
# ems -- Enable EMS support.
# umb -- Enable UMB support.
# keyboardlayout -- Language code of the keyboard layout (or none).

xms=true
ems=true
umb=true
keyboardlayout=none

[IPX]
Enable=1
Connection=1
ipx=true


[autoexec]
# Lines in this section will be run at startup.

@ECHO OFF
mount C "."
c:
cd dukenuk~1
cls
nukem.bat
exit

```

Below are the slight modifications (different mount point and cd parameter) to the above conf:

```

mount C "/home/gnull/DOSGAMES/"
c:
cd DukeNukem1
cls
nukem.bat
exit

```

I feel kinda silly coming back here like this because it makes me sound a newb, but I honestly don't know what to try next.

Thank-you for your attention, R33D3M33R.

---

### Post by LostFarmer on 2014-01-20
For the  conf file try:

```
mount C /home/gnull/DOSGAMES/DukeNukem1
c:
nukem.bat
exit

```

if that does not work, you will have to have a look at the nukem.bat file. It may have paths that you 
need to fix or modify the conf.  


Your basic desktop file with my posted conf file works for my dbase.exe program.

---

### Post by R33D3M33R on 2014-01-21
Yes, I agree with [**[COLOR=#000000]LostFarmer[/COLOR]**]("http://ubuntuforums.org/member.php?u=1268688") , there might be something in nukem.bat that is preventing you to correctly launch the game. Here is the full autoexec line from my GoG version of the game:

```
[autoexec]
# Lines in this section will be run at startup.
@echo off
mount C "/media/Podatki/Igre/3DRealms/Duke Nukem 1+2/"
c:
cls
ECHO [42;1mÉÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍ»
ECHO º ------------------------------------------ º
ECHO º Duke Nukem Pack                            º
ECHO º ------------------------------------------ º
ECHO º  1) Duke Nukem Ep.1: Sharpnel City         º
ECHO º  2) Duke Nukem Ep.2: Mission: Moonbase     º
ECHO º  3) Duke Nukem Ep.3: Trapped in the Future º
ECHO º                                            º
ECHO º  4) Duke Nukem 2                           º
ECHO º ------------------------------------------ º
ECHO º  5) exit program                           º
ECHO º ------------------------------------------ º
ECHO ÈÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍÍŒ[0m

choice /c12345 /s Which game do you want to run? [1-5]: /n 
if errorlevel 5 goto exit
if errorlevel 4 goto dn2
if errorlevel 3 goto e3
if errorlevel 2 goto e2
if errorlevel 1 goto e1

:e1
@echo off
dn1.exe
exit

:e2
@echo off
dn2.exe
exit

:e3
@echo off
dn3.exe
exit

:dn2
@echo off
CONFIG -set "cycles=8000"
cls
nukem2.exe
exit

:exit
exit

```

nukem.bat probably contains something similar.

---

### Post by Drone4four on 2014-01-21
Lost Farmer's suggestion is what worked. I now have Duke Nukem 1 and 2 running flawlessly whilst starting them from my Gnome 3 Activities search menu.

My thanks goes out to Lost Farmer, R33D3M33R + MikeCyber for all your help.

I have one further query.

Duke Nukem Wikia [says]("http://dukenukem.wikia.com/wiki/Cheat_codes") that to get cheats working, you have to pass the asp parameter to the launch command in DOS.  I can't figure out the equivalent on Ubuntu.  I tried adding asp after nukem.bat in my DN.conf.  No dice.  Where else would be an appropriate place to try?

---

### Post by LostFarmer on 2014-01-21
I can only make a guess not knowing what is in the 'bat' file, but if it looks like the one   33D3M33R posted would put the code after the exe.  The bat file is what is calling the program.exe.
 

```

:e1
@echo off
dn1.exe   '**duke1** **asp**'
exit
```

Drone4four, I want to thank you for the .desktop file, I did not know how to do that . I was using  dosbox-0.74.conf file limiting me to one dos program.

---

### Post by Drone4four on 2014-01-25
I tried adding 'duke1 asp' next to the dn1.exe which didn't work.  Then I tried just dn1.exe asp and that worked.  Here is my nukem.bat for reference:```
@echo off
cls
echo. 
echo [29;1m      Duke Nukem - For Steam
echo [30;1m      by Interceptor Entertainment                                                   
echo. 
echo [32;1m      1. Episode 1 - Shrapnel City
echo [33;1m      2. Episode 2 - Moonbase
echo [34;1m      3. Episode 3 - Trapped in the Future
echo [31;1m      4. Exit
echo [0m
choice /c1234 /s Choose your episode:  /n 



if errorlevel 4 goto exit
if errorlevel 3 goto e3
if errorlevel 2 goto e2
if errorlevel 1 goto e1


:e1
@echo off
dn1.exe asp
exit

:e2
@echo off
dn2.exe asp
exit

:e3
@echo off
dn3.exe asp
exit

:exit
exit
```

I hope someone else trying to get the original Duke Nukem running through dosbox on Ubuntu finds this thread as helpful for them as it was for me.

Thanks LostFarmer.

---

