---
title: "berly"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by Benifited on 2007-04-25
i just installed berly into my feisty and non of the effects work and i cant apply any of the themes. i turned all the stuff that i wanted on but nuttin happens. what should i do

---

### Post by kevinlyfellow on 2007-04-25
This may be a bad response, but are you sure beryl is running?

Use the "Beryl Manager" to verify this.  Right click on the notification icon and see what it says under "select window manager"

---

### Post by Benifited on 2007-04-25
> **kevinlyfellow said:**
> This may be a bad response, but are you sure beryl is running?

Use the "Beryl Manager" to verify this.  Right click on the notification icon and see what it says under "select window manager"

yea itz on berly

---

### Post by kevinlyfellow on 2007-04-25
Shoot... I was hoping for an easy solution :-)

put it on metacity (or kwin) and open up a terminal and type in beryl and see what it complains about.

---

### Post by anaconda on 2007-04-25
I have the same problem.. Last week beryl worked perfectly, but now I noticed that the effects are not active anymore!!

And yes beryl is running and the effects are selected.

might be a recent update or something..

---

### Post by kevinlyfellow on 2007-04-25
is this beryl from the feisty repos or is it from the beryl repos?

---

### Post by Benifited on 2007-04-25
> **kevinlyfellow said:**
> Shoot... I was hoping for an easy solution :-)

put it on metacity (or kwin) and open up a terminal and type in beryl and see what it complains about.

whats the command for berly

---

### Post by Benifited on 2007-04-25
im pretty sure its feisty

---

### Post by AlexenderReez on 2007-04-25
run
> beryl-manager

in terminal.....see the error...

i guess you doesn't enable your 3d support....nvidia or ati ?

---

### Post by kevinlyfellow on 2007-04-25
```
beryl
```
;-)

---

### Post by WakkiTabakki on 2007-04-25
I'm running beryl from ubuntu.beryl-project.org on Feisty and it works flawlessly (ver 0.2.1.dfsg+git20070318-0ubuntu2)...

Try running beryl-manager from a terminal and oibserve the outputi n terminal when you switch to beryl using the tray icon. That should give some clues...

/N

---

### Post by AlexenderReez on 2007-04-25
> **kevinlyfellow said:**
> ```
beryl
```
;-)

close your beryl manager with set beryl as window manager...

> beryl-manager

that is better command...because if you use terminal and use
> beryl

you will lost your beryl when you close that terminal...but if using alt + f2 then it is ok....

---

### Post by Benifited on 2007-04-25
this is what i get:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

and i have an ATI card

---

### Post by kevinlyfellow on 2007-04-25
> **reez0105 said:**
> close your beryl manager with set beryl as window manager...



that is better command...because if you use terminal and use


you will lost your beryl when you close that terminal...but if using alt + f2 then it is ok....

I'm not just explaining how to start it, I'm wondering if it gives any error messages.  beryl-manager doesn't seem like it would provide the necessary info

---

### Post by kevinlyfellow on 2007-04-25
> **Benifited said:**
> this is what i get:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

and i have an ATI card

Have you installed special drivers or are they the ones that came with ubuntu?  Did you follow a howto in installing the ati card/beryl?

Here's a howto for the open source driver
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

and one that uses the proprietary driver and xgl
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

### Post by Benifited on 2007-04-25
> **kevinlyfellow said:**
> Have you installed special drivers or are they the ones that came with ubuntu?  Did you follow a howto in installing the ati card/beryl?

Here's a howto for the open source driver
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

and one that uses the proprietary driver and xgl
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

i have an ATI radeon 9600 xt and it says to use beryl u need full 3d support :(

---

### Post by kevinlyfellow on 2007-04-25
OK, well it looks like you have two options.  Try the experimental 3d support for your card using the open source driver or installing the proprietary driver and using xgl which from what I've heard is very buggy.  

Anyhow, I need to get some sleep for tonight, I'll check back in tomorrow.  Read through those tutorials and if you decide which route you wish to take, you can try and follow the appropriate one.  

best of luck

---

### Post by Benifited on 2007-04-25
lolz i just ****** up my whole system :(

---

### Post by kevinlyfellow on 2007-04-25
Unfortunately playing with an xorg.conf file can do that.

Did you back it up?

---

### Post by Benifited on 2007-04-26
> **kevinlyfellow said:**
> Unfortunately playing with an xorg.conf file can do that.

Did you back it up?

lolz i forgot to back it up. but now im enjoying a fresh feisty

---

### Post by kevinlyfellow on 2007-04-26
> **Benifited said:**
> lolz i forgot to back it up. but now im enjoying a fresh feisty

Haha, you didn't need to reinstall, there's a command to have fixed your problem

```
sudo dpkg-reconfigure xserver-xorg -pcritical
```

---

### Post by Benifited on 2007-04-26
> **kevinlyfellow said:**
> Haha, you didn't need to reinstall, there's a command to have fixed your problem

```
sudo dpkg-reconfigure xserver-xorg -pcritical
```

oh man i feel like the biggest noob ever :)

---

### Post by Benifited on 2007-04-26
do u think i should give it another try? i really what to have beryl in my system

---

### Post by kevinlyfellow on 2007-04-27
If you have the ambition, try it until it works.  Personally, I think I'd try at least a few time ;-)  I've never been afraid of hosing my system, but I make sure that I have everything backed up! (well not always, and that usually has some pretty bad results, you think I'd learn...)  Anyways, its up to you.

If I was in your position, I think that I would try the ati drivers.  If you have moral objection (closed  software is found to be immoral by some) then you should try out the the other way.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

First things are first though, backup your xorg.conf!!!

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

If X doesn't start, it will go into commandline mode, and then you only need to 

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

This site may help you install the ati driver, its seems straightforward.  Sorry for not pointing you here in the first place.

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by Benifited on 2007-04-27
lolz i crashed my system again and i had to restart it again but thx for ur help man if i didnt have u i would be losing hair. :)

---

### Post by kevinlyfellow on 2007-04-27
> **Benifited said:**
> lolz i crashed my system again and i had to restart it again but thx for ur help man if i didnt have u i would be losing hair. :)

That's what these forums are for :-)  Sorry you couldn't get it working, but hey, I bet gutsy will have better ati support.  Best of luck

---

### Post by Benifited on 2007-04-27
man i give up i did everything that guide told me. and i still cant run it i still have the same problem :(

---

### Post by kevinlyfellow on 2007-04-27
Where is it that things go wrong?  Is it installing the ati driver or is it when you try to get beryl itself to run?

Its cool if your done with the whole getting beryl to work, just curious.

---

### Post by WakkiTabakki on 2007-04-28
Have you added:
Section "Extensions"
  Option "Composite" "True"
End Section

to your xorg.conf.

Depending on what driver you're using it may or may be necessary... BTW, what driver are you using? fglrx, ait?

To verify that your video driver has the proper 3D-extensions (well, actually to check whether the 3D-love is getting handled by your video hardware), open a terminal and run
```
glxinfo | grep vendor
```
Since you have an ATI-card it should say something about ATI, and NOT mesa (which is the software fallback if no proper hardware or driver is active)

If all is well there, your problem is either with xorg.conf or with beryl or a combination... 


/N

---

### Post by kevinlyfellow on 2007-04-29
> **Benifited said:**
> oh man i feel like the biggest noob ever :)

haha I didn't catch that earlier.  Actually I started using linux in 02 and I just learned how to automatically reconfigure xorg.conf about a month ago.  I used to have to do it either by hand or play 20 questions with the computer.

---

### Post by Benifited on 2007-05-01
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.

this is what i get for the graphics drivers

---

### Post by jiminycricket on 2007-05-01
Have you tried glxgears and post the info you get from 'glxinfo | grep rendering'  and 'lspci | grep AGP' or 'lspci | grep ATI'

---

### Post by Benifited on 2007-05-01
> **jiminycricket said:**
> Have you tried glxgears and post the info you get from 'glxinfo | grep rendering'  and 'lspci | grep AGP' or 'lspci | grep ATI'

the glxgeras works but i dont know exactly what it is that your asking me for the command you gave me doesnt work

---

### Post by Ianman on 2007-05-01
I used to run Beryl with XGL because I also have an ATI card. But now using this tutorial:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

I have it running with the open source ATI driver and AIGLX (which is better IMHO). I simply followed that tutorial to the letter and everything worked great!

What model ATI card do you have?

---

### Post by Benifited on 2007-05-01
> **Ianman said:**
> I used to run Beryl with XGL because I also have an ATI card. But now using this tutorial:
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

I have it running with the open source ATI driver and AIGLX (which is better IMHO). I simply followed that tutorial to the letter and everything worked great!

What model ATI card do you have?

i have a radeon 9600 XT i have tryed that guide that u linked me to but i keep messing up.when i get to the xorg.conf  editing i dont know what im doing wrong but when i save the changes it forces my system to crazy and i loss my whole OS.

---

### Post by Ianman on 2007-05-01
When you first start to edit the xorg.conf file, do you just copy what is on the site? It is important to note that at that step you have to change the identifier to match you system!

I don't see any other reason why it may be going wrong. Your card is listed in the experimental 3D support list but so is mine and mine works fine (X850XT PE). Can you double check that you are changing the identifier int he xorg.conf file?

---

### Post by Benifited on 2007-05-02
> **Ianman said:**
> When you first start to edit the xorg.conf file, do you just copy what is on the site? It is important to note that at that step you have to change the identifier to match you system!

I don't see any other reason why it may be going wrong. Your card is listed in the experimental 3D support list but so is mine and mine works fine (X850XT PE). Can you double check that you are changing the identifier int he xorg.conf file?

what do you mean by identifier?

---

### Post by Ianman on 2007-05-02
This bit in your xorg.conf file:
Section "Device"
        [COLOR="Red"]Identifier [/COLOR]       "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver                "ati"
        BusID                "PCI:1:0:0"
EndSection
(See red string)

You have to change that to match your situation.

---

### Post by Benifited on 2007-05-02
> **Ianman said:**
> This bit in your xorg.conf file:
Section "Device"
        [COLOR="Red"]Identifier [/COLOR]       "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
        Driver                "ati"
        BusID                "PCI:1:0:0"
EndSection
(See red string)

You have to change that to match your situation.

oh yea that part i leave the identifier alone i dont just erase everything and just copy and paste. but i dont know what part im messing up in. but when im done editing it the system always crashes.

---

### Post by Ianman on 2007-05-03
The system actually crashes while you are editing the xorg.conf file or after you have made changes?

You have to change the identifier when editing. If you copy and paste from the tutorial then it won't be correct and it is understandable that it crashes. There is even a note about it in the tutorial.

---

### Post by Benifited on 2007-05-03
> **Ianman said:**
> The system actually crashes while you are editing the xorg.conf file or after you have made changes?

You have to change the identifier when editing. If you copy and paste from the tutorial then it won't be correct and it is understandable that it crashes. There is even a note about it in the tutorial.

yea i know thats why i dont change mine i didnt mean it the other way around. and the system crashes after i restart my computer

---

### Post by Ianman on 2007-05-03
Ok what do you get when you use this command:
lspci
(just paste your output)
?

---

### Post by Benifited on 2007-05-03
this is what i get : 

00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
02:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
02:08.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
02:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

---

### Post by Ianman on 2007-05-03
Ok so what you have to enter for the Identifier is this:

Section "Device"
   Identifier         "ATI Technologies Inc RV350 AR [Radeon 9600]"
   Driver              "ati"
   BusID              "PCI:1:0:0"
EndSection

Is that what you have been trying?

---

### Post by Benifited on 2007-05-03
well i normally left it the way it was.but i will try it, hey do u know anyway i could back up my system just in case i mess up my system again?

---

### Post by Benifited on 2007-05-03
the identifier already says that so i dont think that is my problem

---

### Post by Ianman on 2007-05-03
Well you can ofcourse just backup the xorg.conf file. If it messes up you can copy it back. So if it messes up, you will still be able to login without X loading and just copy the xorg.conf file back. I am not currently behind my Linux machine (I am at work) so have a look at the commands you need before you try this.

It is something like:
cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
(assuming you named your backup file xorg.conf.backup and you saved it to the /etc/X11/ directory)

Someone please correct me if I am wrong to help Benefited out! I am terrible with the terminal still. Thanks.

---

### Post by Benifited on 2007-05-03
dam command didnt work for me. god i really what to get this thing working but i just dont know why it wont let me i cant even restore my system and i did the command right and everything. it was on page 3 of this thread so i know i did it right so know i have to start my system all over again.

---

### Post by Ianman on 2007-05-03
Sorry to hear that dude. I am afraid I am out of ideas. Anyone else have any ideas?

---

### Post by Benifited on 2007-05-03
can u post ur xorg.conf file so that i can see the way u did it

---

### Post by Ianman on 2007-05-03
sure.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
Load "dbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
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
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

#Section "Device"
# Identifier "ATI Technologies Inc R481 [Radeon X850XT-PE]"
# Driver "ati"
# BusID "PCI:2:0:0"
#EndSection

Section "Device"
Identifier "ATI Technologies Inc R481 [Radeon X850XT-PE]"
Driver "radeon"
BusID "PCI:2:0:0"
Option "XAANoOffscreenPixmaps"
Option "AGPMode" "8"
Option "AGPFastWrite" "true"
Option "DisableGLXRootClipping" "true"
Option "AddARGBGLXVisuals" "true"
Option "AllowGLXWithComposite" "true"
Option "EnablePageFlip" "true"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
#HorizSync 28-51
HorizSync 30-81
VertRefresh 56-75
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc R481 [Radeon X850XT-PE]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

Section "ServerLayout"
Option "AIGLX" "true"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

### Post by Benifited on 2007-05-03
ok now i know what i have to do u see ive been replacing the device part i didnt know that u had to have 2 of them :p

---

### Post by Ianman on 2007-05-03
Sorry to disappoint you but lines with a "#" character are ignored by Linux so essentially I only have one "Device" definition.

---

### Post by Benifited on 2007-05-04
OH WOW so im right back where i started at i see

---

