---
title: "monitor not detected"
date: 2010-09-04
forum: Desktop Environments
---

### Post by strange on 2010-09-04
im running ubuntu 10.04 32bit on a atom 230 ION the nvidia drivers installed fine and are detected but on my 26" iiyama monitor the resolutions arent supported (maximum is 640x480) but the screen should run on 1920x1200 when i run xrandr it doesnt give me a name for the screen either (in nvidia settings it shows dfp-0) but xrandr says just default i would like to force my nvidia to output 1920x1200?

thanks

---

### Post by realzippy on 2010-09-04
Please create and post the nvidia-bug-report file:

```
sudo nvidia-bug-report.sh
```

...file will be in your /home folder.
for xrandr you can use  "default" as term...

---

### Post by strange on 2010-09-04
[http://pastebin.com/9CE8JHkn](http://pastebin.com/9CE8JHkn)

---

### Post by realzippy on 2010-09-04
The nvidia-driver cannot read your monitor's data (EDID)...

(WW) Sep 04 16:06:00 NVIDIA(0): No valid modes for "1920x1200"; removing.
(WW) Sep 04 16:06:00 NVIDIA(0): No valid modes for "1680x1050"; removing.
(WW) Sep 04 16:06:00 NVIDIA(0):
(WW) Sep 04 16:06:00 NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) Sep 04 16:06:00 NVIDIA(0):     "nvidia-auto-select".
(WW) Sep 04 16:06:00 NVIDIA(0):
(II) Sep 04 16:06:00 NVIDIA(0): Validated modes:
(II) Sep 04 16:06:00 NVIDIA(0):     "nvidia-auto-select"
(II) Sep 04 16:06:00 NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) Sep 04 16:06:00 NVIDIA(0): [COLOR="Red"]Unable to get display device DFP-0's EDID[/COLOR]; cannot compute DPI
(WW) Sep 04 16:06:00 NVIDIA(0):     from DFP-0's EDID.

Which monitor do you have?Have a datasheet?

---

### Post by strange on 2010-09-04
iiyama prolite E2607WS im not sure what a data sheet is

---

### Post by realzippy on 2010-09-04
run :

```
gksudo gedit /etc/X11/xorg.conf
```


change:


[COLOR="Red"]HorizSync       28.0 - 33.0
VertRefresh     43.0 - 72.0[/COLOR]

to:

[COLOR="SeaGreen"]HorizSync       31.0 - 80.0
VertRefresh     56.0 - 75.0[/COLOR]

Save changes,reboot.
Then open nvidia-settings;hopefully more resolutions will be available...

---

### Post by strange on 2010-09-04
nvidia-settings still doesnt list it :(

my xorg.conf [http://pastebin.com/2cxzEs4J](http://pastebin.com/2cxzEs4J)

---

### Post by realzippy on 2010-09-04
You have rebooted?
Nothing changed in nvidia-settings?Any higher resolutions than 640x480 available after you edited xorg.conf?

---

### Post by strange on 2010-09-04
yup i rebooted and nothing changed

---

### Post by realzippy on 2010-09-04
...thats strange.Make a new nvidia-bugreport please.

(you can upload the file here too,no need for pastebin...)

---

### Post by strange on 2010-09-04
attached

---

### Post by realzippy on 2010-09-04
Think I got it or my last idea :)   :

    
    Modes      "1920x1200" "1680x1050"

was made by you?
And no mode "nvidia" autoselect specified...

Delete current xorg.conf file,make a vanilla one,edit again:


```
sudo rm /etc/X11/xorg.conf
```

```
sudo nvidia-xconfig
```

```
gksudo gedit /etc/X11/xorg.conf
```

make changes again:
[I]HorizSync 31.0 - 80.0
VertRefresh 56.0 - 75.0
[/I]

**reboot** (or restart X)

check again nvidia-settings,if still not working,please create new bug-report file...sorry   ;-)

---

### Post by strange on 2010-09-04
still no go attached nvidia-bug-report

---

### Post by realzippy on 2010-09-04
There had to be more resolutions available in nvidia-settings due to the xorg.conf H/Vsync changes.

What does xrandr now say?Any changes?

```
xrandr -q
```

---

### Post by strange on 2010-09-04
still nothing above 640x480 in xrandr output

---

### Post by realzippy on 2010-09-04
Ok,now you could start adding options to xorg.conf...
Would start with:

Option "UseEDID" "FALSE"

pasted into "device" section.


BTW -as you might have mentioned- this starts becoming try and error method if
the bug-report file (you again will create) contains any good news concerning EDID.
(BTW,you looked into them?)

Another possibility if try & error fails is to extract the monitor's EDID -if you have windows installed and "feed" the driver with the extracted EDID.BIN file...


EDIT:
Which cable do you use? hdmi ?

---

### Post by strange on 2010-09-04
i use a dvi cable and no windows

---

### Post by strange on 2010-09-04
ok no changes and new bug-report

---

### Post by realzippy on 2010-09-04
Run:
```
cvt 1920 1200
```

Copy the produced modeline in xorg.conf "Monitor" Section like:

[I]Section "Monitor"
	Identifier	"XXXXXX"
	Modeline "1920x1200_60.00"  19........... -hs
EndSection
[/I]
In "Screen" Section add:

[I]Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Monitor	"Default Monitor"
	Option "MetaModes" "1920x1200_60.00"[/I]

Increase max *Hsync* to *100*

Reboot.
If problems (no X) run sudo nvidia-xconfig


I am running out of time,thought this would be a drive-by assist.Sorry,familiar duties.
Tomorrow I will be back.As mentioned,connecting your monitor to a windows machine and extracting EDID with e.g. Phoenix Edid Extractor,
importing this file to ubuntu and feeding your driver with it should work 99%....
Please post bug report again,will be back tomorrow.
And testing other cable if possible (HDMI?) might do the trick also..

---

### Post by strange on 2010-09-04
ok that made no changes i think i should install windows to get the driver.

thanks for helping me today and when you find some time i'd appreciate it if you could guide me to the steps after i extract the driver in windows

---

### Post by realzippy on 2010-09-04
...found something on mandriva forum searching for an EDID file for your monitor.
Looks like as someone extracted an EDID for a Iiyama Prolite E2607WS (is it the same as yours?):
[http://lists.mandriva.com/bugs/2009-10/msg00311.php](http://lists.mandriva.com/bugs/2009-10/msg00311.php)
It should be possible to create an EDID for you with that data,using
Phoenix Edid Creator,so you do not have to install windows.But you had to wait until tomorrow...
Meanwhile you could try the modelines from the link (if they differ from yours).
And send the current bug-file please..

---

### Post by realzippy on 2010-09-04
Never thought I ever would search AMD developers forum,but found this
thread:
[http://forums.amd.com/forum/messageview.cfm?catid=347&threadid=121887](http://forums.amd.com/forum/messageview.cfm?catid=347&threadid=121887)

In user Jotschi's ATI driver log I found this:

```
(II) fglrx(0): Monitor name: [COLOR="Lime"]PLE2607WS[/COLOR]
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):    00ffffffffffff0026cd08561ecb0000
(II) fglrx(0):    31120103813722782a7b65a555489926
(II) fglrx(0):    125054bdef80714f8180818f9500950f
(II) fglrx(0):    a940b3000101283c80a070b023403020
(II) fglrx(0):    360026582100001a1a3680a070381f40
(II) fglrx(0):    5020850426582100001a000000fd0037
(II) fglrx(0):    4c1d5111000a202020202020000000fc
(II) fglrx(0):    00504c453236303757530a20202000a6

```

That's the EDID you need in HEX  !!!!!!!!!   :p 

Will convert it in .bin to make it usable for you ...

---

### Post by realzippy on 2010-09-04
First change your xorg.conf to:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "UseDisplayDevice" "DFP-0"
    Option         "CustomEDID"  "DFP-0:/etc/X11/edid.bin"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

then copy the attached *edid.bin* file in your /etc/X11 directory.
Restart.

maybe this will not be the last "attempt";2 weeks ago we had the problem
that nvidia-driver refused the .bin file and worked with .raw version.
Also this edid.bin has 256 byte;I am not sure if the nvidia-driver would
prefer a 128 byte version of it:which can be made,but I am afraid of
the file's checksum.To tired now to figure this out,but tomorrow (ok,today,got late..)is another day.
Please post bug-report if it does not work...
goodnight!

---

### Post by strange on 2010-09-05
IT WORKS!

you are a god.
i actually logged on because i just found out that the problem wasnt with linux but with my monitor it seems the edid is actually broken on dvi because i have another identical screen and when i hooked up that worked but now with your fix they both work!
(the resolution was screwed in windows too and i couldnt even fix it with a driver inthere so i figured i had to rma it) but this is AWESOME.

thanks alot

/strange

---

### Post by realzippy on 2010-09-05
Nah,was kind of sport.
Please set thread as solved (Threadtools).
I still do not understand completely:
Identical monitors,*same* dvi cable,one works,the other not???!
BTW,if you had mentioned this before,we (you) could have extracted the EDID with
linux/nvidia-settings....anyway it was interesting,since I now know that the newest nvidia-
driver reads also EDIDs in 256 byte (Newer EDID standard).
Although problem solved,I am interested in the nvidia-bug-report file from the working machine.Can you create a last one?
Have a nice day...

---

### Post by strange on 2010-09-05
i changed monitors now the computer i fixed it on is not the same as we started on but it had the same issues is a bug report from this computer sufficient or should i do the same trick on the other one ?

and i wasnt aware it was a monitor problem i only found out after you left last night

---

### Post by realzippy on 2010-09-05
If the computer is not the same,but the problem is the same,you can try the fix.Of course it will only work if new computer also has nvidia graphics.If it does not work,same procedure (send bug-file...).In this case please open a new thread (send me a link then),since the problem (and solution) is different.

---

### Post by strange on 2010-09-05
ok let me run bug report here and yes it fixed it on this computer and im sure it would work on the other too but seeing i have 2 identical working screens now i didnt see a reason to fix it on the other aswell :) bug report attached

this runs nvidia 195 btw so that can read those edid things too :D

if you want some more sport i have something harder than this :P

---

### Post by realzippy on 2010-09-05
I don't see any problem in the attached bug-file.
What is the problem with that machine?

---

### Post by strange on 2010-09-05
oh there is no problem i thought you wanted to see the bug report after the fix it works perfectly

---

### Post by strange on 2010-09-05
if you are interested in something harder try 

[http://ubuntuforums.org/showthread.php?t=1455289](http://ubuntuforums.org/showthread.php?t=1455289)

i'd appreciate the help i upgraded this box to 256 driver now too because some people had positive results not me :)

---

### Post by realzippy on 2010-09-05
CAUTION:

If you ever should connect other monitors to the machines providing that special edid.bin for your Ilyama monitor,you have to delete our comment out (#) the
"Use Custom EDID" line in xorg.conf of course;
otherwise a different monitor will not run at all or suffer damage.

---

