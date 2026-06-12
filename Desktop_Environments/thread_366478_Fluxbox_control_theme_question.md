---
title: "Fluxbox control theme question"
date: 2007-02-20
forum: Desktop Environments
---

### Post by gabng on 2007-02-20
I have Fluxbox installed a command line install and am using gnome-settings-daemon to set the control themes.  Everything is fine except that the themes are not applied to Synaptic's controls.  Can someone tell me why that is?  And how to apply the theme to Synaptic's controls?  Thanks.

---

### Post by kerry_s on 2007-02-20
I can't believe you went through the trouble of doing a command-line+fluxbox install and then you bogged it down with a gnome app's and all it's dependency's. So sad. Normally you would use "gtk-theme-switch" which would give you a gtkrc2.0 that you can just copy to /root. Since your using gnome-settings-daemon, just launch that as root and set your theme(gksu gnome-settings-daemon).

---

### Post by gabng on 2007-02-21
> **kerry_s said:**
> I can't believe you went through the trouble of doing a command-line+fluxbox install and then you bogged it down with a gnome app's and all it's dependency's. So sad. Normally you would use "gtk-theme-switch" which would give you a gtkrc2.0 that you can just copy to /root. Since your using gnome-settings-daemon, just launch that as root and set your theme(gksu gnome-settings-daemon).

I know gnome-settings-daemon bogs down fluxbox, but I found it is the only thing that makes my laptop's special function keys' OSD work.  Or maybe you can direct me to how to make it work without using the daemon?  Coz I'd love to lose that if I know what packages will make the OSD work.  Also, I found after starting the gnome-settings-daemon, the fonts in Fluxbox are rendered much better, anyway to have the same effect without the daemon?

Btw, when I do gksu gnome-settings-daemon, an error of "Unable to connect to dbus: Did not receive a reply." showed up.  Any ideas?

---

### Post by yabbadabbadont on 2007-02-21
sudo -s -H
cd
(you should be in /root now)
ln -s /home/yourusername/.gktrc-1.2
ln -s /home/yourusername/.themes
(I'm assuming that the gnome theme you are using is in ~/.themes)

---

### Post by gabng on 2007-02-21
> **yabbadabbadont said:**
> sudo -s -H
cd
(you should be in /root now)
ln -s /home/yourusername/.gktrc-1.2
ln -s /home/yourusername/.themes
(I'm assuming that the gnome theme you are using is in ~/.themes)

Great!  That did the trick!  Thanks for the help!


Now, can someone help me out with the other question?
1) how to make the OSD (sound and brightness controls) work without gnome-settings-daemon?
2) how to have Fluxbox fonts rendered nicely without running gnome-settings-daemon?

---

### Post by yabbadabbadont on 2007-02-21
Can't help you on 1), but for 2), read the fonts-conf manpage.  (then read it about four more times  :D)  Then put your own font settings in ~/.fonts.conf

Here is what I have in mine:  (Note that I have these settings for a CRT monitor, not LCD)
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign"><bool>true</bool></edit>
  </match>
  <match target="font">
    <edit name="antialias" mode="assign"><bool>true</bool></edit>
  </match>
  <selectfont>
    <rejectfont>
      <pattern>
         <patelt name="scalable"><bool>false</bool></patelt>
      </pattern>
    </rejectfont>
  </selectfont>
</fontconfig>

```

---

### Post by kerry_s on 2007-02-21
> **yabbadabbadont said:**
> sudo -s -H
cd
(you should be in /root now)
ln -s /home/yourusername/.gktrc-1.2
ln -s /home/yourusername/.themes
(I'm assuming that the gnome theme you are using is in ~/.themes)

That is a nice little trick, i never thought of linking to the users settings. I usually just copy them over, but the linking is much better. Your mad genius! :)

---

### Post by yabbadabbadont on 2007-02-21
> **kerry_s said:**
> Your mad genius! :)

Mad genius... or just 2 exits past crazy?  ;)


Edit: If you link them, then they automatically get updated whenever you change your theme settings.

---

### Post by gabng on 2007-02-21
> **yabbadabbadont said:**
> Can't help you on 1), but for 2), read the fonts-conf manpage.  (then read it about four more times  :D)  Then put your own font settings in ~/.fonts.conf

Here is what I have in mine:  (Note that I have these settings for a CRT monitor, not LCD)
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign"><bool>true</bool></edit>
  </match>
  <match target="font">
    <edit name="antialias" mode="assign"><bool>true</bool></edit>
  </match>
  <selectfont>
    <rejectfont>
      <pattern>
         <patelt name="scalable"><bool>false</bool></patelt>
      </pattern>
    </rejectfont>
  </selectfont>
</fontconfig>

```

Thanks for the advice, however I've already configured my own language-selector.conf file in /etc/fonts/ (which should act the same as .font.conf).  But even with that (enabled hinting and antialias for the fonts), running gnome-settings-daemon makes the fonts much nicer for some reason, I have no idea why.....

I notice you have scalable option in your .fonts.conf, would that cause any major difference since I don't have that in my font settings.

---

### Post by kerry_s on 2007-02-21
> **gabng said:**
> Great!  That did the trick!  Thanks for the help!


Now, can someone help me out with the other question?
1) how to make the OSD (sound and brightness controls) work without gnome-settings-daemon?
2) how to have Fluxbox fonts rendered nicely without running gnome-settings-daemon?


1. You would use ~/.fluxbox/keys with xmodmap, but i can't remember what the exact commands are, you'll have to google.

2. Gnome settings has settings for fonts, you can manually set up the fonts with-> sudo dpkg-reconfigure fontconfig-config
and you might want to set up your dpi in /etc/X11/xorg.conf

sudo youreditor /etc/X11/xorg.conf
under 
Section "Monitor"
add
```
    Option         "DPI" "109 x 109"
```

Use this page to find your dpi-> [http://www.raydreams.com/prog/dpi.aspx](http://www.raydreams.com/prog/dpi.aspx)
then replace my 109 with your dpi.

---

### Post by kerry_s on 2007-02-21
But you know since you already got gnome settings installed you can continue using it, for convince there's no need to jump through hoops, that way is faster, with less work then what we would do. But there are many ways to do things in linux and you usually want to stick to the ones that work for you. :)

---

### Post by yabbadabbadont on 2007-02-21
> **gabng said:**
> I notice you have scalable option in your .fonts.conf, would that cause any major difference since I don't have that in my font settings.

The scalable option in there forces fontconfig to choose scalable (truetype or type1 for example) fonts over bitmapped fonts.  If I don't do that, I end up with really bad fonts.

Edit: I agree about just continuing to use gnome-settings-daemon.  If it ain't broke, don't fix it.  ;)

---

### Post by kerry_s on 2007-02-21
> **yabbadabbadont said:**
> Mad genius... or just 2 exits past crazy?  ;)


Edit: If you link them, then they automatically get updated whenever you change your theme settings.

Ya, i figured that out right away, that's why i called you a genius. I would normally want to keep root and user separate, but in this case there would be no downside or permission problems in the user account.

---

### Post by gabng on 2007-02-21
> **kerry_s said:**
> But you know since you already got gnome settings installed you can continue using it, for convince there's no need to jump through hoops, that way is faster, with less work then what we would do. But there are many ways to do things in linux and you usually want to stick to the ones that work for you. :)

I totally agree with you there.  Couple of reasons I wanna jump through these hoops is that most important of all, it's a good learning process for me to get familiar with the ins and outs of linux, second is that I'm running it on an old laptop, so I wanna get the most performance out of it as possible, which means if I can get away without running gnome-settings-daemon, I'll try to do it no matter what. :)

One question I ahve about setting that DPI option in xorg.conf is that does the DPI number have to be integer?  I found my screen DPI to be 82.6, so I should set it as "82.6 x 82.6"?

Really appreciate you guys' help here.

---

### Post by yabbadabbadont on 2007-02-21
I would go with either 82x82 or 83x83.  I don't think fractional parts are allowed.

---

### Post by kerry_s on 2007-02-21
> **gabng said:**
> I totally agree with you there.  Couple of reasons I wanna jump through these hoops is that most important of all, it's a good learning process for me to get familiar with the ins and outs of linux, second is that I'm running it on an old laptop, so I wanna get the most performance out of it as possible, which means if I can get away without running gnome-settings-daemon, I'll try to do it no matter what. :)

One question I ahve about setting that DPI option in xorg.conf is that does the DPI number have to be integer?  I found my screen DPI to be 82.6, so I should set it as "82.6 x 82.6"?

Really appreciate you guys' help here.

You can just go head and round that off to 83, mine actually comes out to 109.3 so i just went with 109 for mine. It's just to get you close to the optimal settings for your screen size. Remember to take effect you need to restartX.(ctrl+alt+backspace) Then you readjust your font size if needed.

---

### Post by gabng on 2007-02-21
I did the reconfigure fontconfig thing and added the DPI option in xorg.conf, restarted X, but still there isn't much change to the fonts.  Attached are the difference of font without and with gnome-settings-daemon.  The daemon must have done something else to the fonts settings... any ideas?

---

### Post by kerry_s on 2007-02-21
First i would ask which is which, but i'm guessing the second one is the fugly one. I would say the difference is the font. 
What font's do you have conky set to in .conkyrc?
Without the settings daemon you'll need to choose your own fonts instead of 1 font for the whole desktop. in my .conkyrc i have it set to use xft and selected my font.

```
# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Sans-Serif:size=10
```

You can do the same thing using .gtkrc-2.0
create the file and put->

gtk-font-name = "Sans 10"

of course changing the font to the one you want.

---

### Post by gabng on 2007-02-21
Actually, first one is without daemon, you can see all the fonts are squished together.
In conky, I'm using use_xft yes xftfont Arial:size=7.
And the fluxbox style is using sans-9:bold.

So you think it's the font that's giving the problem?

---

### Post by gabng on 2007-02-21
> **kerry_s said:**
> 
You can do the same thing using .gtkrc-2.0
create the file and put->

gtk-font-name = "Sans 10"

of course changing the font to the one you want.

Will setting the font in .gtkrc-2.0 apply the same font to window title, application font, etc?  Since in the settings daemon, it allows you to set fonts for different parts of the window/applications.

---

### Post by kerry_s on 2007-02-21
It should be all applications. I'm kinda flying blind right now the hard drive with my fluxbox install is corrupt so it won't boot or mount, i'm on xubuntu now. Just try it and see what happens, you have to log out and back in to take effect.

---

### Post by gabng on 2007-02-21
Since in both conky and fluxbox style the fonts are specified, I'm not sure setting gtkrc2.0 will affect them.  However I found the font in conky without settings daemon that matched the font with settings daemon.

Without daemon, I had to change the font to Arial:size=9 (from Arial:size=7) for it to look the same as that with the daemon.  So I'm guessing the daemon override it somehow.

As for the fluxbox style, the font with daemon is totally different from the font without daemon, so I have no idea what's going on there....

---

### Post by yabbadabbadont on 2007-02-21
> **kerry_s said:**
> It should be all applications. I'm kinda flying blind right now the hard drive with my fluxbox install is corrupt so it won't boot or mount, i'm on xubuntu now. Just try it and see what happens, you have to log out and back in to take effect.

Actually, I don't think it will affect the font Firefox uses for it's menu and such...  Firefox respects gnome-settings-daemon, but not your .gtkrc (or .gtkrc-2.0) file.  You have to change it in your userChrome.css file in your Firefox profile's chrome directory.  :mad: 

(assuming that you don't like the default one it uses)

---

### Post by gabng on 2007-02-21
I'm lost as to how the fonts are being managed in both cases.  When I download a fluxbox style, there is a preview.jpg that demos the style.  When I compare that jpg to both cases, the font is different in all of them.  The clock font style is suppose to be bold, but if I don't use settings daemon, the fonts are clearly not bold.  What is up with that...?

---

### Post by kerry_s on 2007-02-21
But were not talking about firefox fonts yet. :) 
Sorry, if i'm  a little slow to respond, i'm hacking my way into that corrupted hard drive to see what i can recover. Trying to use anther install to rebuild the parts.

---

### Post by gabng on 2007-02-21
> **kerry_s said:**
> But were not talking about firefox fonts yet. :) 
Sorry, if i'm  a little slow to respond, i'm hacking my way into that corrupted hard drive to see what i can recover. Trying to use anther install to rebuild the parts.

No problem, take your time :)
I'll have to leave for a few hours before coming back.
Really appreciate your help, can't stress that enough :KS

---

### Post by kerry_s on 2007-02-21
Okay, it's got to be your font selection type, ariel is just ugly.
I did a clean install of fluxbox and just did->

sudo dpkg-reconfigure fontconfig-config
Autohinter> Always> No

and

sudo leafpad /etc/X11/xorg.conf
under
Section "Monitor"
add
Code:

Option "DPI" "109 x 109"

That's all it took to get great looking fonts.
The first pic is the before shoot the second is the after.

---

### Post by yabbadabbadont on 2007-02-21
> **kerry_s said:**
> Okay, it's got to be your font selection type, ariel is just ugly.
I did a clean install of fluxbox and just did->

sudo dpkg-reconfigure fontconfig-config
Autohinter> Always> No

and

sudo leafpad /etc/X11/xorg.conf
under
Section "Monitor"
add
Code:

Option "DPI" "109 x 109"

That's all it took to get great looking fonts.
The first pic is the before shoot the second is the after.
And I got better results with the autohinter and antialias always on...  you'll probably just have to try various combinations until you find one that looks good on your setup.  :D

---

### Post by kerry_s on 2007-02-21
Here's the fix for all those errors in xorg.0.log for the fonts.

sudo leafpad /etc/X11/xorg.conf  <-replace leafpad with your editor
delete all the font paths, should just be empty like this->

```
Section "Files"

EndSection

```
in terminal:

```
sudo su
cd /usr/share/fonts/truetype/ttf-dejavu
mkfontscale
mkfontdir

cd /usr/share/fonts/truetype/ttf-bitstream-vera
mkfontscale
mkfontdir

ln -s /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/X11/TTF
ln -s /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/X11/OTF
ln -s /usr/share/fonts/X11/Type1 /usr/share/fonts/X11/CID
fc-cache -f

```

---

### Post by gabng on 2007-02-22
Thanks for the input guys, and baring with me for so long!  Sorry for the late reply, but I was busy doing some testing and research.

After a day (couple hours to be exact) of trial and error, I found out gnome-settings-daemon actually bumped up the font size specified in fluxbox style and conky by 2.  So in conky I set the font size to be 7 in order to display nicely with the settings daemon, and when I don't start the daemon, the fonts become smaller and squished together.  If I set the font size to 9 in conky, it is exactly the same as running the daemon with font 7.  Also, running the daemon overrides my fontconfig settings according to what is set in the gnome control center.  So it is just a matter of setting the fonts and properly enabling antialias, hinting and autohinting to make the fonts look nice like with running the daemon.

Also with a little research I found out that the volume OSD in gnome was actually supplied by a package called ACME, which was integrated into the gnome-settings-daemon few years back.  This means that the OSD comes from the daemon and no daemon means no volume OSD.  So does anyone know if there are any software/packages that can bind with hotkeys to show a volume OSD?  And if it would also show monitor brightness OSD would be excellent (the function keys for controlling monitor brightness came with the gnome-power-manager, which is quite lightweight by itself).


> **kerry_s said:**
> Here's the fix for all those errors in xorg.0.log for the fonts.

sudo leafpad /etc/X11/xorg.conf  <-replace leafpad with your editor
delete all the font paths, should just be empty like this->

```
Section "Files"

EndSection

```
in terminal:

```
sudo su
cd /usr/share/fonts/truetype/ttf-dejavu
mkfontscale
mkfontdir

cd /usr/share/fonts/truetype/ttf-bitstream-vera
mkfontscale
mkfontdir

ln -s /usr/share/fonts/truetype/ttf-dejavu /usr/share/fonts/X11/TTF
ln -s /usr/share/fonts/truetype/ttf-bitstream-vera /usr/share/fonts/X11/OTF
ln -s /usr/share/fonts/X11/Type1 /usr/share/fonts/X11/CID
fc-cache -f

```

Are the above steps' purpose only to eliminate the errors in the log?  Because I don't see any difference in the font display.

---

### Post by kerry_s on 2007-02-22
Yes, they correct the errors and set up the font correctly so they show up in all apps. With out the correction they don't show in all applications.

Fluxbox is famous for it's slit apps, the slit is on the right side. It's what holds those special apllications, like for volume control, i use wmix. You don't see it in my screen shots because my slit is set on auto hide. Here's a good site to look at the dock apps, then just find it in synaptic and install.-> 
[http://dockapps.org/](http://dockapps.org/)

Look at the right bottom corner in the pic.

---

### Post by kerry_s on 2007-02-22
I know that error thing is minor, but i feel if you can correct the errors everything should run as smooth as possible. Here's what my log looks like->

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux Linux2 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 22 00:25:36 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is disabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3116 card 1106,3116 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b091 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1462,7380 rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,3177 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1462,7380 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1462,7380 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1462,738c rev 74 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0185 card 1554,1115 rev a4 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe1ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] rev 164, Mem @ 0xe0000000/24, 0xd8000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[1] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[6] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[8] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[1] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[2] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[3] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[4] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[6] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[8] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[12] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[14] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[5] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[17] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "true"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "1280x1024, 1280x1024"
(**) NVIDIA(0): Option "DPI" "109 x 109"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 4000 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.18.20.40.08
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 4000 at PCI:1:0:0:
(--) NVIDIA(0):     HP HWPD5259A (CRT-0)
(--) NVIDIA(0):     Gateway VX920 (CRT-1)
(--) NVIDIA(0): HP HWPD5259A (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Gateway VX920 (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024,1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 2560 x 1024
(**) NVIDIA(0): DPI set to (109, 109); computed from "DPI" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[1] 0	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe2001000 - 0xe20010ff (0x100) MX[B]
	[7] -1	0	0xe2000000 - 0xe20000ff (0x100) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000ac0f (0x10) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a01f (0x20) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024,1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

My xsession-errors->

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "user"
/etc/gdm/Xsession: Beginning session setup...
BScreen::BScreen: managing screen 0 using visual 0x21, depth 24
Conky: forked to background, pid is 3856

Conky: desktop window (a1) is root window
Conky: window type - desktop
Conky: hint - below
Conky: drawing to created window (400002)
Conky: drawing to double buffer

```

---

### Post by gabng on 2007-02-22
Cool, thanks for the tips.

I'm not too big a fan of the slits, since I can never find a proper place to put them due to the limited screen space of my laptop, plus they don't look too appealing to me... as a matter of fact, I compiled the slits out of my Fluxbox install :P

I've done some more research and can't really find a suitable replacement for the gnome volume OSD.  Do any Fluxbox users have a solution/replacement for this other than using slit controls??  This is the only thing that's keeping me from ditching gnome-settings-daemon on my fluxbox... :(

---

