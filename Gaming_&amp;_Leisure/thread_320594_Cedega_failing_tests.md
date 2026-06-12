---
title: "Cedega failing tests"
date: 2006-12-17
forum: Gaming &amp; Leisure
---

### Post by FlashOmega on 2006-12-17
so heres my problem :D.... first off cedega works great on my other computer....  but this one is different.

Intergreated Nvidia 6100
amd64 (b4 bit)

where as my other is a 32 bit system with an agp nvidia card... so im hitting some problems

Open Gl Rendering FAILED.... BUT!!!! glxinfo | grep direct ....... returns direct rendering : yes
3d acceleration FAILED..........BUT!!!! glxgears runs with a pretty good fps (cedega website says thats what this test does)
posix threads pass
copy protection pass
oss sound pass
ALSA sound FAILED..... I have no rebutal to this one... this is a stab in the dark for me

so being a smarter brand of noob I ran it from terminal to get the standard error output.... upon running the above tests these errors are generated 

/usr/lib/transgaming_cedega/tests/glxinfo: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory
/usr/lib/transgaming_cedega/tests/gl_test: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory

NOTE: libGLU.so is installed ... so is libX11.so

if anyone wants anything else from me just ask... ill post anything you would like

Thanks

---

### Post by wounded on 2006-12-17
I've had similar issues with installing other applications where something would need a .so file and it would be installed, just named differently. I had to make a link so that it could be found. Since it appears to be looking for libGLU.so.1 and libX11.so.6 (and not libGLU.so and libX11.so) I would imagine making links in the appropriate directory will fix this.

but I might be wrong simply because I am me :P

---

### Post by FlashOmega on 2006-12-18
So far you are the only one to reply... so wrong or not I appreciate the help ... and seeing as I have no other options at this point... ill give it a try... no harm in that.

Thanks

---

### Post by hikaricore on 2006-12-18
Is this Cedega or CVSCedega?  You could probaby find better support at cedega's forums if you can't find it here.  Just a suggestion.

---

### Post by FlashOmega on 2006-12-18
its not CVS cedega ( not that I know what that is )

I posted both here and on cedega... figured SOMEONE must have the answer.  I know its not a ubuntu problem ... but people are this forum are SO smart and SO kind... and above all helpfull... I figured it cant hurt to ask here...just incase its a configuration issue with my nvidia card.

So just an update... on the cedega forum I was told how to completly reconfigured my nvidia card to make sure its all up to par... 

So heres what its looking like... I was reading somewhere in a FAQ about how cedega is a 32bit program... and by nvidia drivers are 64 bit... and that I should have some sort of 32 bit nvidia driver also installed... the FAQ said that while installing the nvidia drivers I would be prompted to install 32bit support... however I used the nvidia-glx deb file from the repositories... so I never came across that option... and cant seem to make the nvidia drivers from [www.nvidia.com](www.nvidia.com) to work ... always errors out.... 

This is where I think the people on this forum stand more of a chance of helping as there or more ubuntu users then cedega users (non open source jerks... but only way I know how to play city of heroes)

Any thoughts on my next step?

---

### Post by Sammi on 2006-12-18
Why not just try Wine instead?

---

### Post by FlashOmega on 2006-12-18
you can run city of heroes in wine?... I didnt think it possible

I google search "City of Heroes"+linux

and only cedega came up... I was under the impression that cedega had made modifications to wine to the extent that it wouldnt work with just wine.....

and...... I dont know how to use wine

---

### Post by Delvien on 2006-12-18
Cedega sux, i tried to use it once, and i will never touch that piece of garbage ever again, try some WINE.

---

### Post by FlashOmega on 2006-12-18
if someone call tell me how to run City Of Heroes in WINE I will happily delete Cedega... but right now my options are Cedega or WINDOWS.... so ..... ya..... cedega

---

### Post by PriceChild on 2006-12-18
To install nvidia drivers: [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy) or [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Use method 2, and change the filenames to the 64bit versions.

---

### Post by Sammi on 2006-12-18
Wine isn't hard to use.

I found these simple instructions, you can follow, in order to get it installed:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

For gaming you need the newest version, so follow this section:
> 
[[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] WineHQ]("http://www.winehq.com/") provides the newest versions of Wine packaged for Ubuntu. To use these, you need to add the WineHQ repository and then install Wine with Synaptic. For help on adding repositories, see the [Repositories]("https://help.ubuntu.com/community/Repositories") page.[LIST=1]
[*]Add the repository:[LIST]
[*] For Ubuntu 6.10 (Edgy Eft): Add the following repository, deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
[*] For Ubuntu 6.06 LTS (Dapper Drake): Add the following repository, deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
[*] For Ubuntu 5.10 (Breezy Badger): Add the following repository, deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main[/LIST] [/LIST]Note that these repositories are recommended on the WineHQ website: [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] http://winehq.org/site/download-deb]("http://winehq.org/site/download-deb")[LIST=1]
[*]Update the package cache using "sudo apt-get update" or by clicking 'Reload' in Synaptic
[*]Install Wine using "sudo apt-get install wine"[/LIST]
That page also has info on how to use Wine, but basically all you have to do after Wine is installed, is run the installation .exe file of the game you want, in order to install it. You do this just by writing "wine" in front of it, just like this:
```
wine /insert-path-to-file/install.exe
```
And after the that you launch the game executable with the "wine" command in front, just like above.

---

### Post by FlashOmega on 2006-12-18
That walkthrough was AWESOME... got the new drivers in with NO problems... BUT!!! still doesnt work.  its a 64 vs 32 bit issue...

My next question (as im afraid of trying without asking) is what would happen if I fallowed that guide and put the 32 bit driver in instead?

P.S installing and trying wine right now... if I have not added onto this post... it means im still trying it

Ok done trying it.... WINE hates me too... your above steps worked on my 32 bit system... so goodbye cedega

BUT they do not work on the 64 bit system... the update fails

```
http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-amd64/Packages.gz: 404 Not Found

```

---

### Post by FlashOmega on 2006-12-19
Man you are right... Wine is much better... because I was able to compile it in 64 bit (cant with closed source cedega) ... but unfortunatly Wine doesnt support city of heroes. Seems wine isnt really being developed much anymore.  Which totally sucks.  I would help program it... but im not that good..... yet..... So back to Cedega... how

any thoughts?

---

### Post by pay on 2006-12-19
To install Wine on 64bit try ```
wget http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.27~winehq0~ubuntu~6.10-1_i386.deb
sudo dpkg -i --force-architecture wine_0.9.27~winehq0~ubuntu~6.10-1_i386.deb
```Wine's development cycle is ALOT faster than Cedega's. Wine release a new version every 2 weeks or so.

---

### Post by FlashOmega on 2006-12-19
well Wine doesnt support City Of Heroes... doesnt run.. says so right on their application db... where cedega has it running... and at this point all I need to do is get 32bit opengl support to run on an amd64 and it will work.

I have wine fully installed... doesnt work.. and the application db shows my exact error... no known resolution yet.

Man I wish wine could do it... and im sure they will... just not at the moment

---

### Post by pay on 2006-12-19
For the sound issue try```
sudo apt-get install alsa-oss
```For the video look at this [http://transgaming.org/forum/viewtopic.php?t=5072](http://transgaming.org/forum/viewtopic.php?t=5072)

---

### Post by FlashOmega on 2006-12-19
lol just did that... and there is another package I got that made the 3d accerlation work as well... so now im down to JUST opengl... in 32bit... on an amd 64... man that seems pointless... never thought id be trying to do something like that... but here I am

---

### Post by pay on 2006-12-19
> **FlashOmega said:**
> so now im down to JUST opengl... in 32bit... on an amd 64... man that seems pointless.I have no idea what you mean.

---

### Post by FlashOmega on 2006-12-19
to be honest I dont get it much myself...... here is what ive read 

From cedega troubleshooting page:
> If you are running a 64-bit distribution of Linux, and only see entries in a directory like /usr/lib64 and not /usr/lib, then this is a good indicator that you are probably missing 32-bit versions of the OpenGL libraries. If you are using a NVIDIA video card, then installing the 32-bit libraries means reinstalling your drivers and selecting "Yes" when prompted as to whether or not you wish to install 32-bit libraries.

However this option did not come up for me as I was forced to use method 2 from the above mentioned link for installing nvidia drivers

---

### Post by pay on 2006-12-19
Try ```
sudo apt-get install libc6-i386
cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.s
```

---

### Post by silvagroup on 2006-12-19
Unfortunately wine is not a panacea for windows programs. It's a great idea but even after 5 years of trying to crack that nut they haven't. I still run the same three programs I did five years ago and still can not run the rest I would like to. Your best bet is to wait for the VT and Xen technology. Lets hope that Microsoft involvement in it along with the Novells deal won't mess up the open source world to badly. I for one am already looking to BSD, I have never seen to many things in which M$ doesn't destroy once they get their hooks onto it (rare examples).

---

### Post by FlashOmega on 2006-12-20
Ok I have it running... so here is the trick... this SHOULD work for ALL people in my situation... which to recap is 64 bit processor trying to run 32 bit cedega (as there is no 64 bit cedega)

first off

NVIDIA !!!! ... when
use the walk through provided by PriceChild earlier in this post
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
using Method 2... BUT!!!!!!!! (this is how I messed up the first few times)
In step 7... you will see this line
```
sudo sh NVIDIA-Linux-x86_64-1.0-8776-pkg2.run -n -s --x-prefix=/usr/lib64/xorg/ --kernel-source-path=/usr/src/linux-headers-`uname -r`
```

DONT USE IT... remove the -s... because it will cause it to auto answer NO to 32bit support
it will then ask you a bunch of questions just answer them by pressing enter... making sure when it asks if you want 32 bit support to say yes

Then its just a matter of 
```
sudo apt-get install libc6-i386
cd /usr/lib32
sudo ln -s libX11.so.6 libX11.so
sudo ln -s libXext.so.6 libXext.so
sudo ln -s libfreetype.so.6 libfreetype.so
sudo ln -s libz.so.1 libz.so
sudo ln -s libGL.so.1 libGL.so
sudo ln -s libGLU.so.1 libGLU.s
```

As per Pay's post on page 2.  and all should be well:D

If anyone else has this problem feel free to let me know... ive learnt enough about it now I think I can help.

Thanks everyone for your help

---

### Post by conreyt on 2006-12-20
So you got CoH running with cedega ok?

---

### Post by FlashOmega on 2006-12-20
Yup works great

---

### Post by silvagroup on 2006-12-21
Sorry I failed to mention this in my previous post, which is that for running windows applications which can not run under wine I use win4linpro. Runs all windows applications (not all games) extremelt well. I have 512 mg on my system and with win4linpro running at 128 it runs like xp on a 128 machine. One of these days I may fork over the money and put in a couple gig and get rid of the little bit of loss, for know works as well as I need it too.

---

### Post by ashmew2 on 2007-02-08
I use UBuntu 6.06 (32 bit) but ill givethose things a try , will get back to u about working or not :P

---

### Post by thejaunt on 2007-03-06
Thanx 
FlashOmega  but unfortunately your method did not work for me I think it may be my xorg.conf


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Fri Dec 15 10:40:27 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "dri"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
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
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by PriceChild on 2007-03-07
please remove the triplebuffer and disableglxrootclipping lines.

---

### Post by thejaunt on 2007-03-07
I removed the lines to no avail Cedega video tests still failing. Im checking other forums hopefully I will find something. Thx though bro

---

### Post by thejaunt on 2007-03-10
im also getting this libGL is too old when I run driinfo ?????Please help 

Here are my specs: compaq presario v3000
AMD Turion 64 x2 / gig of ram
NVIDIA GeForce Go 6150 256mb.

I had cedega running fine on a previous install of ubuntu edgy 6.10  but then I did some stupid **** and had to reinstall and now that I got everything set up almost like I had it things are different like the stuff I mentioned above.

---

### Post by thejaunt on 2007-03-13
Lots of help this forum has been. I guess I will just reinstall ubuntu. Thx to none

---

### Post by Sammi on 2007-03-14
@thejaunt
You are not being fair. You haven't even posted one line of error text. What exactly is your problem?

You are seriously not giving us enough info to work with.

---

### Post by thejaunt on 2007-03-14
@Sammi

Thx for replying. 

One error message I get is when I run driinfo I get : libGL is too old.

Also when I run the cedega video tests it fails both of them.
Open Gl Rendering FAILED.... BUT!!!! glxinfo | grep direct ....... returns direct rendering : yes
3d acceleration FAILED..........BUT!!!! glxgears runs with a pretty good fps (cedega website says thats what this test does)
This is the same thing flash omega got which is exactly my problem which is why I decided to post here.
I have beryl installed fine and I also have some ubuntu opengl games installed then run perfect.
I think my xorg.conf may not be set up correctly and I was hoping someone a bit more inclined would be able to spot what is wrong in my xorg.conf.

Thx Sammi

---

### Post by thejaunt on 2007-03-21
@Sammi

See my point has been proven I waited 6 days to get a reply and nothing. The only reply I got was you telling me I was not being fair when you could have used your energy to give a solution. As for me not posting enough information, if you would have read my previous posts you would know that my problem was the same as flash omegas and his fix did not work for me so that is information right there. Meh what ever nuts to this forum

---

### Post by Sammi on 2007-03-21
I didn't post back because I have no solution for you. Probably the same with all the other people who've read this tread.

Is it still fair to expect that regular Ubuntu users should be able to solve your problem? You are aware that this isn't a professional commercial technical support forum, right?

This forum is in fact a open forum where regular people come to chat about all things that are related to Ubuntu. There are only volunteers here and we don't take money for wasting your time.

---

### Post by PriceChild on 2007-03-21
> **thejaunt said:**
> @Sammi

See my point has been proven I waited 6 days to get a reply and nothing. The only reply I got was you telling me I was not being fair when you could have used your energy to give a solution. As for me not posting enough information, if you would have read my previous posts you would know that my problem was the same as flash omegas and his fix did not work for me so that is information right there. Meh what ever nuts to this forumGo to Cedega for their support that YOU paid for by purchasing Cedega Legally.

If you didn't purchase it then don't expect any support.

No-one seems to know here.

Remember not even the staff here are paid, people will help if they know how... or can research quickly to assist you.

Pricey

---

### Post by thejaunt on 2007-04-28
This issue is now resolved for me. My fix was upgrading to feisty from edgy and installing the nvidia drivers through automatix2. My guess is simply installing the driver through automatix2 should fix the problem in edgy as well since the driver was nvidia-glx-new and not nvidia-glx I think that was the problem so if anyone still has this problem try it out and good luck im sure it will work. Only problem now is I have no sound and wifi not working correctly but im hoping to have that fixed soon also. Thx guys for all your good hard help.

Peace

---

