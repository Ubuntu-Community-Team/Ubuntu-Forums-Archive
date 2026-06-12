---
title: "Dual monitor with ATI card in Ubuntu8.04"
date: 2008-08-06
forum: Desktop Environments
---

### Post by chenjin824 on 2008-08-06
Hi all

I was trying to set up my dual monitor according to Ziox's method at [http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)
basically, it is this 5 steps:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo aticonfig --initial --overlay-type=Xv
sudo aticonfig --desktop-setup=horizontal --sync-vsync=on --add-pairmode=Width0xHeight0+Width1xHeight1
sudo aticonfig --query-monitor
sudo aticonfig --enable-monitor=STRING,STRING <==replaced with the result from the query.
sudo aticonfig --force-monitor=STRING,STRING <==replaced with the result from the query.

Something I should tell is: it's Ubuntu 8.04 + ATI HD2400 vedio card + Gnome. I think ubuntu has installed Fglrx cuz when i type in $fglrxinfo, it reports some information like "ATI Inc."

When i finished those 5 steps and restart X, its resolution becomes 2560*768, which is samller than 1280x1024+1280x1024. And I can't use the system config tool in the Gnome to change it-it is already the maximum option i can use. These two monitor are 19'' and have the same original resolution 1280x1024.

Then I was trying to start over the whole procedure and didn't work out. Then i searched on other bbs and found out somebody did this:
aticonfig --initial=dual-head --screen-layout=right
aticonfig --dtop=horizontal,reverse --overlay-on=1
aticonfig --resolution=0,2650x1024,1280x1024,1280x1024

I tried his method too, but it still didn't work. I did all this
in the X environment and with the two monitors plugged in.
What do you think I should do to fix this? 

BTW, a trivial question is, even if I backuped the original xorg.conf file, what should i do to reuse this file when i found I didn't do everything correctly? I mean, when I just copy the backup file to xorg.conf and restart X, it does change anything at all. I can't go back to the nature resolution any more!!! How to do with this?:confused:

Sorry about this long question, i've been stuck on it for days and really need to proceed my real work, so please take a look and give me some hints to conquer it. Thanks for your time.

Jin

---

### Post by chenjin824 on 2008-08-06
BTW, when i type in the query-monitor command, 
it says tmds1 and tmds2i have collected, how to figure out
which one is the primary one and the other secondary one?

---

### Post by chenjin824 on 2008-08-08
Keep watching this thread and receive no reply yet,
is this problem really so hard to fix?:(

---

### Post by mrmiserable on 2008-08-09
ok i'll try to help

firstly dont know if this is a typo but you put

aticonfig --resolution=0,[COLOR="Red"]2650[/COLOR]x1024,1280x1024,1280x1024

and not 2560x1024

secondly you could try and edit xorg.conf manually and put that resolution in

then goto preference-screen resolution after reboot and that resolution should be there and set as default 

also if you installed driver from ubuntu also install fglrx-control its ati control gui which is easy to use

hope this works 

good luck

---

### Post by chenjin824 on 2008-08-09
Thanks for your reply, mrmiserable,

Actually, that's a typo in the resolution line, I apologize.

Plus, I did try your method to add the resolution manually in xorg.conf file
but each time I save and restart X. The resolution has been changed to 1024x768+1024x768, which is the displaying screen resolution, not the natural resolution(1280x1024). 

When i tried to use the backed-up file xorg.conf.backup to restore to the original xorg.conf, it never works---I can never go back to the nature resolution of the LCD again, which is 1280x1024. It's weird to me.

Anybody know how to fix this?

---

### Post by mrmiserable on 2008-08-10
just a question but can your card handle 2560x1024 i say this because in the past for me to get compiz and dual screen i had to put 2048x1024 in my screen section (im not saying you want compiz)  but maybe your graphics card can only handle 2048 also i have an old xorg config maybe you can see something in it for you

Section "ServerLayout"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
Identifier "Default Layout"
Screen "Default Screen" 0 0
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "fr"
Option "XkbVariant" "oss"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "Generic Monitor"
HorizSync 30.0 - 70.0
VertRefresh 50.0 - 160.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "second Monitor"
HorizSync 30.0 - 70.0
VertRefresh 50.0 - 80.0
Option "DPMS"
EndSection

Section "Device"
Identifier "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
Driver "fglrx"
Option "XAANoOffscreenPixmaps" "true"
Option "AllowGLXWithComposite" "true"
Option "AccelMethod" "XAA"
Option "DesktopSetup" "horizontal"
Option "Capabilities" "0x00000800"
Option "PairModes" "1024x1024+1024x1024,0x0+0x0"
Option "EnableMonitor" "tmds1,crt1"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Modes "2048x1024" "1280x1024" "1024x768"
EndSubSection
EndSection

---

### Post by Gallardo Spyder on 2008-08-10
> **chenjin824 said:**
> Thanks for your reply, mrmiserable,

Actually, that's a typo in the resolution line, I apologize.

Plus, I did try your method to add the resolution manually in xorg.conf file
but each time I save and restart X. The resolution has been changed to 1024x768+1024x768, which is the displaying screen resolution, not the natural resolution(1280x1024). 

When i tried to use the backed-up file xorg.conf.backup to restore to the original xorg.conf, it never works---I can never go back to the nature resolution of the LCD again, which is 1280x1024. It's weird to me.

Anybody know how to fix this?


After several days of having the same issue with my new Quad Core Dual Monitor setup (trying to get one big desktop over both monitors). I have a FireGL 3600 (dual output card) just for reference.


You had a question that I will answer first - you want to go back to your original Xorg - and it wasn't sticking / resolution issue...

Make sure you have the correct Xorg.conf file ready...  then go to a terminal (root) or do a sudo in front of this command:

aticonfig --input=/etc/X11/xorg.conf --tls=1


Restart and you should be good on the resoltion/making the Xorg.conf current.


OK - Easy Solution to make Dual Monitors act like one big one...

I have a very very easy solution to this - without changing to the Xorg file!


1.) This assumes that you already have the video card working ok - if not there are 20 posts on getting your video card working properly.  Check that out and come back to step 2.

2.) Download from Synaptic a program called 'grandr'

3.) In a terminal type grandr

4.) you will see a pull down menu where you can select the resolution of the "Default" monitor.  Select double of what it is defaulted to (so for instance) if you are currently at 1024X768 - Look at the list and you will see 2048X768 ...

Select the double Horizontal setting resolution.  Click Apply...  and you should now see your 2 screens as one big one.

That is it - no changes to the Xorg, nothing else to do...

---

### Post by charonred on 2008-08-14
I using a ASUS ATi Radeon 2600 Pro card with Ubuntu 8.04.1 on dual 19¨ LCD monitors. 

All I did was install the restricted drivers for the ATI cards with the Catalyst Control Centre and have it running as ´Big Desktop´ at 2560 x 1024 resolution and all is working fine (except for a little prob I´m having with [Compiz and 2 identical monitors]("http://ubuntuforums.org/showthread.php?p=5591182#post5591182"))

---

