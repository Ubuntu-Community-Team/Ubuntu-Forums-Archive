---
title: "The Jackalope eats my desktop effects!"
date: 2009-04-25
forum: Desktop Environments
---

### Post by calvinps on 2009-04-25
Hello!

This might be a bit minor, but when I upgraded to Jaunty, I noticed that the "wobbly windows" effect was not enabled, so I went in to the Appearance settings, and when I clicked the "Extra" effects setting, an error box pops up saying that desktop effects could not be enabled.

Please help me - I miss the effects already! :mad: :lol:

---

### Post by loklaan on 2009-04-25
Have you installed propriety video drivers? You need them to run compiz, at least I did

---

### Post by calvinps on 2009-04-25
I have not installed proprietary drivers.

The desktop effects were working fine on Intrepid :confused:

---

### Post by loklaan on 2009-04-25
You had probably looked away when the drivers were being installed on Ibex? Haha idk. Look in System > Administration > Hardware Drivers to see what drivers you can download. If you already have a driver magically installed, well... :s

What graphics card do you have btw?

---

### Post by calvinps on 2009-04-25
I don't know how to get info about my graphics card although i have a pretty good guess that you put the following into a terminal:

```
lspci
```

---

### Post by solidsnake204 on 2009-04-25
You can install Sysinfo to get information about your system:
```
sudo apt-get install sysinfo
```

You can find it in your System Tools sub-menu.

Launch Sysinfo then goto Hardware.
There's a dropdown box on the top right, select Graphic Card.

---

### Post by loklaan on 2009-04-25
^ hazza, though lspci does will enough, mine for example in the lspci print-off: ```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500M GS (rev a1)
```

Did you look in System > Administration > Hardware Drivers calvinps?

---

### Post by calvinps on 2009-04-25
> **BuNsiE said:**
> ^ hazza, though lspci does will enough, mine for example in the lspci print-off: ```
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500M GS (rev a1)
```Did you look in System > Administration > Hardware Drivers calvinps?

I did but all there is is my alternate wifi driver (MadWIFI) on the list, and no mention of proprietary graphics drivers

---

### Post by loklaan on 2009-04-25
Ah ok, and what is your graphics card? (VGA controller)

---

### Post by calvinps on 2009-04-25
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

The VGA-compatible controller is also listed on sysinfo.

Hope this helps :D

---

### Post by calvinps on 2009-04-25
bump :P

---

### Post by aikiwolfie on 2009-04-25
Go to: **System > Preferences > Appearance**. Click the "**Visual Effects**" tab. See if you can enable any of those options. Those might be the limit to what your system can handle as you seem to have an integrated graphics chip.

---

### Post by GolemdX on 2009-04-25
In his first post, he said he already tried that and it failed, but it was working fine in Inteprid.

Having the same problem with 2 of my computers. Here's info on 1:

```
VGA compatible controller
Intel Corporation 82865G Integrated Graphics Controller (rev 02)
Subsystem: Dell Device 019d
```

Nothing in Hardware Drivers, also was working on Inteprid.

---

### Post by calvinps on 2009-04-25
> **aikiwolfie said:**
> Go to: **System > Preferences > Appearance**. Click the "**Visual Effects**" tab. See if you can enable any of those options. Those might be the limit to what your system can handle as you seem to have an integrated graphics chip.

I can't enable any of these options.

---

### Post by GolemdX on 2009-04-25
Having an integrated graphics chip doesn't really put very many limitations when it comes to ubuntu, although with Windows it can cause problems.

---

### Post by aikiwolfie on 2009-04-25
It all depends on the capabilities and compatibility of the graphics chip. Intel in general aren't that great for graphics. Try and run a lot of heavy eye candy and the system will get bogged down.

The Nvidia card in my Dell XPS M1330n starts to suffer with 4 virtual desktops. Especially if I enable the cube effects.

I'm wondering how much of the effects were enabled last time around. Was the desktop cube enabled?

---

### Post by calvinps on 2009-04-25
I don't run Compiz on my laptop.

I don't see the point on having multiple workspaces. Its the desktop effects i'm concerned about

---

### Post by D1ZZ4ZZT3R on 2009-04-25
i'm not trying to steal this thread but, it's related and, no body has answered my thread in three days so...

i have an nvidia card, and everytime i turn the comp on, my resolution gets set too high. i have to manually set it back using my graphic driver vendors tool (which i never had to use in intrepid or hardy). using that, i go to x server display configuration, change my resolution, and it works fine (until i turn comp back on). i also attempt to save to x configuration file (with merge with existing file checked) but, it tells me "unable to create new x config backup file '/etc/X11/xorg.conf.backup'.


anyone?

---

### Post by aikiwolfie on 2009-04-25
Okay what you need to do is go and read the following.

[https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance]("https://wiki.ubuntu.com/X/Troubleshooting/IntelPerformance")
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

### Post by aikiwolfie on 2009-04-25
It's Compiz that provides the wobble in your wobbly windows.

---

### Post by GolemdX on 2009-04-25
For me, I had Wobbly Windows, Desktop Cube, Rotate Cube, 3D Windows, Reflection and Deformation, Paint fire on Screen, and other desktop effects that I'm forgetting.

My Acer Aspire One netbook (which also has an intel integrated card) had:
Desktop Cube, Rotate Cube, 3D Windows, Reflection and Deformation (With deformation disabled), Paint Fire on Screen, the one that made it rain, and other desktop effects that I'm forgetting.

---

### Post by aikiwolfie on 2009-04-25
Have you tried editing the file manually D1ZZ?

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth 24
        SubSection "Display"
                Depth     24
                Modes     "1024x768"
        EndSubSection
EndSection
```

---

### Post by aikiwolfie on 2009-04-25
> **GolemdX said:**
> For me, I had Wobbly Windows, Desktop Cube, Rotate Cube, 3D Windows, Reflection and Deformation, Paint fire on Screen, and other desktop effects that I'm forgetting.

My Acer Aspire One netbook (which also has an intel integrated card) had:
Desktop Cube, Rotate Cube, 3D Windows, Reflection and Deformation (With deformation disabled), Paint Fire on Screen, the one that made it rain, and other desktop effects that I'm forgetting.

So which revision of which Intel integrated graphics chip do you have?

---

### Post by D1ZZ4ZZT3R on 2009-04-25
i did, aikiwolfie but, i didn't have permission, and it wouldn't let me change permission adn, i don't know how : /

---

### Post by Seq on 2009-04-25
Alright guys, as to the original issue in the thread, desktop effects is blacklisted for several Intel cards currently in jaunty. Please read the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/904#Display%20freezes%20with%20Intel%20graphics%20cards") for a bit more information.

The compiz website has information on the [Blacklist]("http://wiki.compiz-fusion.org/Hardware/Blacklist") (at least stuff that gets blacklisted upstream). At the bottom of that page is information on how to skip the blacklist check. Note that this MAY cause the stability problems that prompted the blacklist in the first place.

That said, I'm running jaunty with desktop effects enabled on a 965 (x3100) without any issues.  I'm also running UXA instead of EXA as well, which apparently causes stability issues for some right there.

---

### Post by GolemdX on 2009-04-25
> **aikiwolfie said:**
> So which revision of which Intel integrated graphics chip do you have?

I posted it earlier in this topic... This is the first computer, not the netbook.

```
VGA compatible controller
Intel Corporation 82865G Integrated Graphics Controller (rev 02)
Subsystem: Dell Device 019d
```

---

### Post by aikiwolfie on 2009-04-25
> **D1ZZ4ZZT3R said:**
> i did, aikiwolfie but, i didn't have permission, and it wouldn't let me change permission adn, i don't know how : /

Press Alt+F2 or open a terminal windows and type the following:
```
gksudo gedit /etc/X11/xorg.conf
```

Enter your password when asked and you should now have permission.

---

### Post by GolemdX on 2009-04-25
> **aikiwolfie said:**
> Press Alt+F2 or open a terminal windows and type the following:
```
gksudo gedit /etc/X11/xorg.conf
```

Enter your password when asked and you should now have permission.

Does this apply to me too, or just him. If it does apply to me, what should I edit?

---

### Post by aikiwolfie on 2009-04-25
No. If you're having the same issue as the original poster then you should look at the same links I gave him earlier.

---

### Post by GolemdX on 2009-04-25
Installing the 2.4 driver fixed it, after reboot everything was back to normal!

---

### Post by D1ZZ4ZZT3R on 2009-04-26
> **aikiwolfie said:**
> Press Alt+F2 or open a terminal windows and type the following:
```
gksudo gedit /etc/X11/xorg.conf
```Enter your password when asked and you should now have permission.


well, thanks aikiwolfie but, i did that, pasted into it (after clearing what was there) what i was given in the preview of what the nvidia config tool was attempting to save with out success, restarted and it didn't work. i then did it again with what you provided earlier, changing the resolution to what i actually wanted, restarted and, it worked but, it doesn't use the graphics card anymore (no more effects).

i'm sure the fault is mine, i'm tired of trying, i'm tired and hungry. thank you anyway, i'll probably try again later with more attention to detail at a later date.

---

### Post by telmac on 2009-04-26
naughty naughty jackalope!

---

### Post by aikiwolfie on 2009-04-26
> **D1ZZ4ZZT3R said:**
> well, thanks aikiwolfie but, i did that, pasted into it (after clearing what was there) what i was given in the preview of what the nvidia config tool was attempting to save with out success, restarted and it didn't work. i then did it again with what you provided earlier, changing the resolution to what i actually wanted, restarted and, it worked but, it doesn't use the graphics card anymore (no more effects).

i'm sure the fault is mine, i'm tired of trying, i'm tired and hungry. thank you anyway, i'll probably try again later with more attention to detail at a later date.

Sorry it didn't work. Try reinstalling the nvidia driver. Then just add the section for the resolutions to what is already there.

---

### Post by D1ZZ4ZZT3R on 2009-04-26
> **aikiwolfie said:**
> Sorry it didn't work. Try reinstalling the nvidia driver. Then just add the section for the resolutions to what is already there.


well, i think i know what happened. i looked at the box of text you provided and it seems there's no specific information included (which there wouldn't be, seeing as you don't know my personal specs). like i said, i was tired. i'll just go in and add that stuff and see what happens.

first breakfast.

how's the OP's problem coming along? i almost forgot this wasn't my thread. hey, aikiwolfie, would you mind taking a look at this thread for me? 

[http://ubuntuforums.org/showthread.php?t=1134582](http://ubuntuforums.org/showthread.php?t=1134582)

it's got this problem and one more... you seem helpful and like you know what you're doing. also, i don't want to take away from this threads OP's problem.

---

### Post by aikiwolfie on 2009-04-26
Actually I took that file from a virtual machine. Probably not the best idea. But then again my actual xorg.conf file doesn't look much different. As far as I know the xorg development guys are trying to get away from using that config file for some reason. Which has left a lot of people with display issues.

My actual xorg.conf file. I don't use the resolution settings. But I do need the BusID option because I have two graphics cards and the new xorg doesn't select a default. Like DOH!
```
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	BusID	"01:00:00"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by calvinps on 2009-04-27
Just a small question:

The page says that I need to restart X after the driver was installed. Does that mean restarting the computer? if not, what do I have to do?

---

### Post by aikiwolfie on 2009-04-27
Normally logging out and back in again is enough. But restarting the whole PC will have the same effect.

---

### Post by calvinps on 2009-04-27
> **aikiwolfie said:**
> Normally logging out and back in again is enough. But restarting the whole PC will have the same effect.

Ok. I restarted my box when I installed the drivers, but I still get this "can't enable desktop effects" thingy

I really want my FX back!!! :lol:

---

### Post by calvinps on 2009-04-28
bump

---

### Post by Seq on 2009-04-28
> **calvinps said:**
> Just a small question:

The page says that I need to restart X after the driver was installed. Does that mean restarting the computer? if not, what do I have to do?

Which drivers did you install, calvinps?

Note that if you're enabling desktop effects on an Intel 965 (like you indicated you had in the earlier) that you are probably blacklisted. I had already posted a link to a workaround, but it may cause stability problems (which is why it is blacklisted until the Ubuntu devs can push an intel driver that works).

Edit: If the card is blacklisted (likely) then changing the driver won't unblacklist it -- though it might solve the problems that caused the blacklist in the first place. You will have to tell compiz (which is what provides desktop effects) to ignore the blacklist.

EDIT: a bit more info

---

### Post by calvinps on 2009-04-28
> **Seq said:**
> Which drivers did you install, calvinps?

Note that if you're enabling desktop effects on an Intel 965 (like you indicated you had in the earlier) that you are probably blacklisted. I had already posted a link to a workaround, but it may cause stability problems (which is why it is blacklisted until the Ubuntu devs can push an intel driver that works).

Edit: If the card is blacklisted (likely) then changing the driver won't unblacklist it -- though it might solve the problems that caused the blacklist in the first place. You will have to tell compiz (which is what provides desktop effects) to ignore the blacklist.

EDIT: a bit more info

I reverted the Intel driver to the version used in intrepid.

Speaking of blacklists, I dealt with one when I had issues with wi-fi on Intrepid, but now we're probably having to deal with them again here; this time with graphics issues. :/

Where could the blacklists be? I have a good guess that they could be in [FONT=Courier New]/etc/modules [FONT=Verdana]or something.[/FONT][/FONT]

---

### Post by Seq on 2009-04-28
> **calvinps said:**
> I reverted the Intel driver to the version used in intrepid.

Speaking of blacklists, I dealt with one when I had issues with wi-fi on Intrepid, but now we're probably having to deal with them again here; this time with graphics issues. :/

Similar principle, but different blacklist. In this case it's a Compiz built-in blacklist (known problems running compiz on specific hardware), not a kernel module blacklist (known problems with driver). Your driver is loaded (no kernel blacklist), it's just Compiz has a list of cards that are known to cause problems. These problems are often due to the driver, but compiz has no idea what driver version will resolve an issue, so it just blocks the card (based on hardware IDs) until further notice. If it recognizes your card from this list it gracefully quits (thus reverting to metacity) rather than potentially crashing X (or causing whatever issues caused the card to appear on the blacklist).

Unfortunately you get the less than helpful "Unable to start" message that could mean one of 100 things...

> **calvinps said:**
> Where could the blacklists be? I have a good guess that they could be in [FONT=Courier New]/etc/modules [FONT=Verdana]or something.[/FONT][/FONT]

[My post earlier in the thread had the relavant links to the compiz website on how to disable the compiz blocklist]("http://ubuntuforums.org/showpost.php?p=7144022&postcount=25").

---

### Post by IsolatedSheep on 2009-10-17
Hello, I'm new to ubuntu. i installed Jaunty Jackalope, but could not get the desktop effect to work, hope you can help me with this. Here's my system info:

```
andi@andi-laptop:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
andi@andi-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1366x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 
```
And the terminal stop after the line that has "/usr/bin/metacity", it does not prompt for new command. If i try to close the terminal an error dialog shows up warning me about a process still running. I don't know why this happen, help you can answer this aswell.

Thanks in advance.. :D

---

