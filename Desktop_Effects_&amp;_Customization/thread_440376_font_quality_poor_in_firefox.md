---
title: "font quality poor in firefox"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by Bashed on 2007-05-11
I need help to get the BEST, sharpest, most crisp font quality (including proper size) in Firfox, using Ubuntu Feisty Fawn, to match Windows as much as possible (Vista). I've tried so much, no matter what I've done I cannot get the fonts as crisp as Windows at all.

I installed 32bit Ubuntu Feisty Fawn and by default, the resolution was properly set to 1280x800 (widescreen) on 60Hz refresh.

I'm struggling to get the best font quality possible

What I've done
- msttcorefonts [http://www.warrenguy.com/docs/ubuntu...ing-fonts.html](http://www.warrenguy.com/docs/ubuntu...ing-fonts.html)
- freetype [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)
- copy over all segoe*, calabra* and tahoma* fonts from Windows
- cloned firefox 2 font settings of Windows into here in Ubuntu
- I have gtk2-engines-pixbuf enabled by Ubuntu's default (double checked via synaptic)

I already applied [http://www.howtoforge.com/sharp_fonts_gnome](http://www.howtoforge.com/sharp_fonts_gnome) as well, but look at the comparison of font size and boldness. They are still getting bolded, enlarged for GOD knows what reason, in linux.

Linux:
[http://www.imagehost.ro/pict//112035194644a95749e50.png](http://www.imagehost.ro/pict//112035194644a95749e50.png)
Look at the fonts all over the screen, mainly the forum category titles
and text on right column too. They are bigger, bolder. I do not know why.

Windows:
[http://www.imagehost.ro/pict//112035394644a96bba186.png](http://www.imagehost.ro/pict//112035394644a96bba186.png)

See now in Windows, this is how it SHOULD appear in linux.

How can I fix this?

My current font settings:

Ubuntu
[http://www.imagehost.ro/pict//112037114644a9c7e97b0.png](http://www.imagehost.ro/pict//112037114644a9c7e97b0.png)

Firefox
[http://www.imagehost.ro/pict//112037394644a9e396549.png](http://www.imagehost.ro/pict//112037394644a9e396549.png)
(firefox setting matches exact settings in default firefox windows settings)

Right now, I have .fonts.conf file with this, taken from the link you mentioned and unchanged:

```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<!-- Give all fonts light hinting and subpixel smoothing -->
<!--
<match target="font">
    <edit mode="assign" name="rgba">
        <const>rgb</const>
    </edit>
    <edit mode="assign" name="hinting">
        <bool>true</bool>
    </edit>
    <edit mode="assign" name="hintstyle">
        <const>hintslight</const>
    </edit>
    <edit mode="assign" name="antialias">
        <bool>true</bool>
    </edit>
</match>
-->

<!--
     <match target="font">
        <test qual="all" name="rgba"><const>unknown</const></test>
           <edit name="rgba" mode="assign"><const>rgb</const></edit>
     </match>
-->

<!--  Do not smooth Fixedsys  -->
<match target="font">
    <test name="family">
        <string>FixedsysTTF</string>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<!--  Do not smooth Tahoma 8pt and under  -->
<match target="font">
    <test name="family">
        <string>Tahoma</string>
    </test>
    <test compare="less" name="size" qual="any">
        <double>9</double>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<!--  Do not smooth Times New Roman or Courier New for 12pt and under  -->
<match target="font">
    <test name="family">
        <string>Times New Roman</string>
    </test>
    <test compare="less" name="size" qual="any">
        <double>13</double>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<match target="font">
    <test name="family">
        <string>Courier</string>
        <string>Courier New</string>
        <string>Courier 10 Pitch</string>
    </test>
    <test compare="less" name="size" qual="any">
        <double>11</double>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<!-- Do not autohint Courier New, Fixedsys, Tahoma, or Times New Roman -->
<match target="font">
    <test name="family">
        <string>Courier New</string>
        <string>Times New Roman</string>
        <string>Tahoma</string>
        <string>FixedsysTTF</string>
    </test>
    <edit mode="assign" name="hintstyle">
        <const>hintslight</const>
    </edit>
    <edit mode="assign" name="autohint">
        <bool>false</bool>
    </edit>
</match>

<match target="pattern">
            <test qual="any" name="family">
                    <string>Bitstream Vera Sans</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
    <match target="pattern">
            <test qual="any" name="family">
                    <string>Helvetica</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Palatino</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Georgia</string>
            </edit>
</match>
</fontconfig>
``` 
Please help out!

Specs:
Sony Vaio FE770G Laptop
15.4" Widescreen (1280x800)

---

### Post by kpolice on 2007-05-11
You will never get the same look as in Windows.

There is no right or wrong look, you say Windows is the good look because you use Windows but Mac OS users say the same about OS X.

---

### Post by airtonix on 2007-05-11
Try using the font called HandelGotDilg . 

the windows one is the poor one when i look at the screenshots...

all the fonts are pixelated the curves on some of the letters are jaggy where as in ubuntu the curves are actually perfect curves.

and when you mention bold....take a close look again at waht you claim should not be bold it is in fact bold on both screenshots.

seriously.... the only thing i can think of is that you somehow think pixelated fonts are superior....why you would use that kind of font for anything other than terminals and programming i have no idea

i have a windows machine infront of me and a ubuntu ..both sitting next to each other.....(all of which works flawlessly networking, wireless, 3d, everything....nothing wrng) and i tell you right now.....windows suck **** at graphics....

hell the acorn risc machines i was using ten years ago could do better graphics than the piffy windows vista you get today.......and they were only 300 odd mhz cpus!!!

im actually beginning to think your either biased or having vision problems.

---

### Post by Bashed on 2007-05-11
Did it ever occur to you that some like the windows quality of fonts better? Its clear your a linux worshipper, good for you but don't insult me telling me I'm biased.  You have no idea what your talking about at all. 

The world does not revolve around your opinions.  Everyone is entitled to like windows or linux or mac as they wish. 

I don't have vision problems, but you have an attitude problem

---

### Post by flowingfire on 2007-05-11
Umm TalkJesus, do you suppose Jesus would get all upset about people trying to be helpful talking about font? Cool down.

Anyway, I have actually done all the same things you have to my font settings... I actually went as far as to install the entire Windows Vista font set in Kubuntu.... No help there, though.  My font still looks all linux-ish.

I really, really doubt it's personal preference because I can literally read the text in Vista better -visibly- on my monitor.  Same resolution, same fonts, same settings... But I can lean back and read a web page in Vista where I must lean forward to read it in Linux...

I'm not surprised that Microsoft has better font rendering-- they pull in more money than some governments!  I think they do smoothing better... and they obviously have some kind of psychological effect...  Which pixels are highlighted... how it appears smoothed...   

My next greatest hope is for a superior font-rendering addition to the Linux family... Until then, maybe we're just stuck with pixels and rouch, smushed-looking rendering...

Peace,
-David

---

### Post by trmiv on 2007-05-11
I'm with TalkJesus on the font issue, they just don't look as good TO ME in Firefox within Ubuntu as they do in Firefox within Windows.  I've followed all the font improvement guides out there and got the fonts much much better than out of the box, but it still isn't what I want it to look like. They are too small when they should be bigger, too big when they should be smaller, bold when they shouldn't be, and all the fonts have this overly anti-aliased blurry look to them.  Now I know how to turn off the anti-aliasing, but that isn't what I want either.  What I'm after is what the fonts look like in XP with cleartype enabled.

 Since I switched to Linux full time a little over a month ago, I've noticed my eyes are much more tired after reading things online than they ever were after doing the same thing in Windows.  After a few hours my eyes are super tired, and I never had that problem in Windows. That is the biggest judge for me that the fonts aren't working for me.    When I boot my wife's Windows XP laptop up and view the exact same page side-by-side with my Ubuntu laptop, the Windows side is just so much better to my eyes.  I love Ubuntu and I want to stay with it, but my eyes are telling me otherwise.  If I can't get this issue fixed, I may have to switch back to Windows and I would hate to do that.

---

### Post by sowelie on 2007-05-11
I found this article and it REALLY improved the font rendering in firefox, and the whole OS actually.  Check it out:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_improve_sub-pixel_font_rendering_for_Feisty)

---

### Post by trmiv on 2007-05-11
That's the one I followed.  It's much better than default, but still not right.

---

### Post by sowelie on 2007-05-11
Okay, I also customized a bit. If you go to System -> Preferences -> Font, then click on details at the bottom, I found these options worked best on my LCD:

[IMG]http://www.rtech-online.com/fonts.jpg[/IMG]

---

### Post by trmiv on 2007-05-12
That's exactly how mine is set. Also, the fonts look much better on the desktop and in menus then in Firefox.  Firefox seems to render the fonts differently for some reason.

---

### Post by shanepardue on 2007-05-12
I also have been having this issue. This thread has helped me drastically fix many issues, but some websites look worse than others. It's only in firefox that I experience the problems.

---

### Post by djchandler on 2007-05-12
The only thing I've noticed is that normal text in the Linux version of Firefox always looks smaller to start with, and I don't quite understand why. Could it be that Microsoft is holding out again when it comes to their technological secrets? But I rather doubt that's the problem. I use VNC quite a bit to access my Linux box upstairs from my XP box downstairs. After reading your discussion thus far, I have one suggestion, and one speculation.

First suggestion is try to use the latest fonts from Bitstream and URW. They're quality font foundries, and do have access to the Microsoft/Adobe specs as they produce fonts for not only Windows and OSX platforms, but they're also interested in maintaining a following by graphics professionals who use these other platforms. You'll find a similar suggestion from the developers of Scribus, THE desktop publishing solution for Linux. So try being aware of the foundries of the fonts you're using. For starters, try Bitstream DejaVu family, Bitstream Vera family, and the Type 1 fonts you get when you download Ghostscript which include these URW families: Nimbus Sans (Helvetica and Helvetica Narrow), Nimbus Roman (Times), Nimbus Mono (Courier), GothicL (Avant Garde), BookmanL , Century SchoolbookL, PalladioL (Palatino), Dingbats, Chancery, and Symbols. The URW fonts are beautiful replacements for the basic 35 Adobe Postscript Type 1 fonts.

My speculation is that Windows graphic drivers are inherently more refined than the open-source graphics card drivers we're using. I think that my Linux screens look a bit better when I'm using VNC to control my Linux box from Windows when I'm downstairs in my office working. The Linux box is in my living room hooked into our home entertainment system for my convergence experiment. In other words, Windows for work, Linux for fun.

( I bet some people think I have that backwards, but when you use Adobe stuff for work, thats the only way it can be, and I refuse to use windows more than I have to. Apple and I parted ways about 10 years ago when they obsoleted my huge investment in Mac graphics tools by adopting the Power PC platform and entered into what I then believed was an unholy alliance with IBM to develop the RISC Power PC CPU.)

It could be just the difference in monitors, the WinXP box uses a CRT, and my Ubuntu uses a widescreen LCD, or it could be the difference in graphics cards. They're both Nvidia cards, but I use a higher end card in my Windows box because that's where I do my professional graphics work. CRTs are really better when it comes to color reproduction, because you can get truer whites and blacks.

That's the end of what I have to add except for this. Besides experimenting with the font rendering settings, go to the details settings, and manipulate the smoothing, hinting, and subpixel order. If you work at it, I think you can get excellent font rendering. I also suggest (I always have one more suggestion :-D) using screen captures using various settings, and then viewing them side by side on your WindowsXP box since that's where you think you get the best rendering. Gosh, this kind of sounds almost scientific!

---

### Post by sowelie on 2007-05-12
There is an option in the firefox font settings "Allow pages to choose their own fonts..." uncheck that and you can directly control the fonts.  I find it looks a lot better this way.

---

### Post by ghettro on 2007-05-13
thanks guys, this helped a lot.  btw Talkjesus, what theme are you running? your menus look really nice compared to the standard ones.

Cheers

---

### Post by Bashed on 2007-05-13
> **sowelie said:**
> There is an option in the firefox font settings "Allow pages to choose their own fonts..." uncheck that and you can directly control the fonts.  I find it looks a lot better this way.

True, but you know that kills the uniqueness of each site and makes browsing become dull with only one font type.

---

### Post by airtonix on 2007-05-14
well i do know what im talking about i used windows 95- xp pro fro webdev an graphics...

the gnome-terminal doesnt seem to render fonts properly, it bunches them up together the its as if the letter spacing is = letter-spacing:-0.5em;

the reason why fonts look diff in browsers on diff systems  is due to : 
 a) default style sheets that specify exactly how to display a H5 or a EM in tthe first place.
 b) the system font you use and your screen dpi settings
 c) the font settings in the browser, like have you acidentally held down ctrl and scrolled your mouse wheel unwittingly one day? if so ctrl+0 to return to normal.

Another thought  are you using CRT or LCD screens.?

edit : 

i just went back and looked at your two screenshots of windows and linux together. I still maintain that the linux one is more favourable.

and when i make web pages that have to look similar in most platforms....i code for linu and the gecko engine first because its the one im on and then i go back and use "conditional-comments" to load in the appropriate style sheet for IE.

conditional comments are not a hack it is created specifically by microsoft for ther browser so you can create styles for specific versions of IE.

if you code for linux-firefox first then modify for the others you will find that you can get it pretty darn close .... in fact i can get it perfect pretty much all the time. but then i've been using xml/xsl/css/html/js since 1997.

---

### Post by Bashed on 2007-05-14
[http://browsershots.org/website/http://www.talkjesus.com/#success](http://browsershots.org/website/http://www.talkjesus.com/#success)

That's my site.  I use 96dpi, 1280x800 resolution and 24bit. 

The windows one is the smoothest and in Vista, it is even smoother (but they show XP)

Somehow, PLD linux is a lot better by default than Ubuntu. What they do , Ubuntu should learn from. PLD linux, it does not mysteriously enlarge fonts and bold them 10x more than they should be.

---

### Post by ghettro on 2007-05-14
I have the fonts looking schmicko now in everything, except the firefox menus, which have lots of colour fringing left over.  It only seems to affect the menu text, not the page text or anything outside of firefox.
I followed the guide [http://www.howtoforge.com/sharp_fonts_gnome](http://www.howtoforge.com/sharp_fonts_gnome) and did everything exactly.  See attachment for what I mean.  Evolution looks fantastic, the actual webpage in firefox looks great too, its only the menus which have this leftover subpixel hinting.  I have it turned on at Full at 96dpi.  

Any ideas??

this is my xorg.conf:

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
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"L1710S"
	Option		"DPMS"
#       DisplaySize    270    203    # 1024x768 96dpi
#       DisplaySize    338    254    # 1280x960 96dpi
        DisplaySize    338    270    # 1280x1024 96dpi
#       DisplaySize    370    277    # 1400x1050 96dpi
#       DisplaySize    423    370    # 1600x1400 96dpi

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"L1710S"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Bashed on 2007-05-14
ghettro, could you do me a favor and provide the following?

screenshots of:

- font settings (hinting window and regular font type/style window)
- full screen shot of my site, talkjesus.com
- current resolution / dpi settings
- hardware info (graphic driver, version, color depth, lcd or crt?)

Thanks.

---

### Post by ghettro on 2007-05-15
The monitor is a 17" LCD, Radeon 9550, Resolution is in the Xorg.conf I printed out, 1280x1024x24.  Fonts at 96dpi, subpixel smoothing on full.  Running Beryl on Feisty Fawn

The weird thing is that it only affects firefox and only in the menus [file, edit, view, history etc and the tabs but not in the page content or the window title], every other program's fonts look fine.  It might be hard to discern in my screenshot.  Also italics look really shite, as you can see in the screenie on the emerald menu.

---

### Post by dptxp on 2007-05-15
I am in this forum now because of the poor font quality and no control on size in Firefox.

I hate what I see. I think that I saw better fonts in SeaMonkey in PuppyLinux.

I also want to know how to install Fonts in Ubuntu. I have many Microsoft Fonts in Windows. I have installed the basic ones by the method given elsewhere but I did not get what I wanted.

HELP HELP HELP

I am sure that there is some expert here in the forums.

Please HELP, my eyes are aching.

---

### Post by airtonix on 2007-05-15
still cant see the difference in quality other than your now using pixelated fonts.
 ie not anti-aliased.

just for your ref here is my desktop. nothing looks ugly to me. 

it may be that your monitor is not display the software pixels to the hardware pixels ie the sub pixel rendering is not happneing properly.

---

### Post by djchandler on 2007-05-16
I screwed this up and forgot to upload my font configuration preferences.
Sorry about that. First time I attached a graphics file.

Dan

---

### Post by djchandler on 2007-05-16
I think my firefox screens look fine. I'm using an LCD @ 1360x768
I'm attaching screenshots of my font configuration, Doesn't bother my eyes. I don't even need my reading glasses with the 27 inch Viewsonic LCD,

---

### Post by djchandler on 2007-05-16
And here's the screenshot of my Previous thread reply.

---

### Post by seanf on 2007-05-16
I just experienced my own two-hour battle with Firefox font ugliness.

Earlier today, I wanted to give KDE a shot, so I installed kubuntu-desktop. Played with KDE for five minues, decided I hated it, then painstakingly uninstalled everything that kubuntu-desktop had added to my system. Rebooted and went back into Gnome.

Before my adventure into KDE, the fonts in my Firefox installation were beautifully antialiased, just like everything else in Gnome. After KDE, Firefox fonts looked like crap.

I tried every solution I could find, including changing freetype options in about:config and telling Firefox to override any font choices specified by a web page. Nothing worked.

Finally, I noticed that there was a .fonts.conf file in my home directory, created the same time as my KDE installation. 

I removed .fonts.conf from my home directory, restarted X, and bingo - antialiased fonts in Firefox!

---

### Post by seanf on 2007-05-17
> **dptxp said:**
> I also want to know how to install Fonts in Ubuntu. I have many Microsoft Fonts in Windows. I have installed the basic ones by the method given elsewhere but I did not get what I wanted.

Create a folder named **[COLOR="DarkRed"].fonts[/COLOR]** in your home directory (don't forget the dot), then drag your fonts into that folder.

---

### Post by dptxp on 2007-05-17
> **seanf said:**
> Create a folder named **[COLOR="DarkRed"].fonts[/COLOR]** in your home directory (don't forget the dot), then drag your fonts into that folder.

Thanks. Shall do today. I too had installed Kubuntu yesterday, but kubuntu-core, not desktop.
So I do not feel the need to remove it. I shall check the /home folder though.

---

### Post by dptxp on 2007-05-17
Getting and installing fonts from Windows was easy with kde-core installed.

There is Add Fonts in it.

Just select from Windows directory and click ADD or OK.

---

### Post by Bashed on 2007-05-17
Found *somewhat* of a trick to rid the firefox mysterious enlarged font size and exaggerated boldness on some fonts, in this case verdana (it seems so anyway)

I added this to .fonts.conf file:

```

<match target="pattern">
            <test qual="any" name="family">
                    <string>Verdana</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Bitstream Vera Sans</string>
            </edit>
</match>
```However, still a little flaky. For example, I'm typing here in the forum inside this WYSIWYG editor, compared to Vista, the font size is about 2pt larger for some reason. I do not know how to tell firefox, or ubuntu to correct that. For the record, it was this way berfore I added the above code.

My current .fonts.conf file:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<!-- Give all fonts light hinting and subpixel smoothing -->
<!--
<match target="font">
    <edit mode="assign" name="rgba">
        <const>rgb</const>
    </edit>
    <edit mode="assign" name="hinting">
        <bool>true</bool>
    </edit>
    <edit mode="assign" name="hintstyle">
        <const>hintslight</const>
    </edit>
    <edit mode="assign" name="antialias">
        <bool>true</bool>
    </edit>
</match>
-->

<!--
     <match target="font">
        <test qual="all" name="rgba"><const>unknown</const></test>
           <edit name="rgba" mode="assign"><const>rgb</const></edit>
     </match>
-->

<!--  Do not smooth Fixedsys  -->
<match target="font">
    <test name="family">
        <string>FixedsysTTF</string>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<!--  Do not smooth Tahoma 8pt and under  -->
<match target="font">
    <test name="family">
        <string>Tahoma</string>
    </test>
    <test compare="less" name="size" qual="any">
        <double>9</double>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<!--  Do not smooth Times New Roman or Courier New for 12pt and under  -->
<match target="font">
    <test name="family">
        <string>Times New Roman</string>
    </test>
    <test compare="less" name="size" qual="any">
        <double>13</double>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<match target="font">
    <test name="family">
        <string>Courier</string>
        <string>Courier New</string>
        <string>Courier 10 Pitch</string>
    </test>
    <test compare="less" name="size" qual="any">
        <double>11</double>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<!-- Do not autohint Courier New, Fixedsys, Tahoma, or Times New Roman -->
<match target="font">
    <test name="family">
        <string>Courier New</string>
        <string>Times New Roman</string>
        <string>Tahoma</string>
        <string>FixedsysTTF</string>
    </test>
    <edit mode="assign" name="hintstyle">
        <const>hintslight</const>
    </edit>
    <edit mode="assign" name="autohint">
        <bool>false</bool>
    </edit>
</match>

<match target="pattern">
            <test qual="any" name="family">
                    <string>Bitstream Vera Sans</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
    <match target="pattern">
            <test qual="any" name="family">
                    <string>Helvetica</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Palatino</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Georgia</string>
            </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Verdana</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Bitstream Vera Sans</string>
            </edit>
</match>
</fontconfig>
```

On a side note, I'd rather see the sites' original font settings than forcing ubuntu to use an alternative.

---

### Post by dptxp on 2007-05-20
I edited my xorg/conf file as per the howtoforge page, saved and rebooted.

Yes, I removed the # from the dimensions of 1024 x 768 resolution

But my dimensions still stay at 302 x 232 mm and resolution at 84 x 84 dpi.

How do I change the dimensions to new values and X to 96 X 96 dpi ?

---

### Post by blakkandekka on 2007-06-01
> **seanf said:**
> 
Finally, I noticed that there was a .fonts.conf file in my home directory, created the same time as my KDE installation. 

I removed .fonts.conf from my home directory, restarted X, and bingo - antialiased fonts in Firefox!

Bingo!  Thanks for pointing that out - FF fonts are now 100% better with all the fuzziness in the menu and the jaggies on the page gone.  Just as well - I was about to reach the hair tearing out stage.  I had the misfortune to install and remove K-desktop at the same time as Ubuntu auto-updated libcairo and the freetype stuff, so I was headed off down a complete blind alley.

---

### Post by blakkandekka on 2007-06-01
> **blakkandekka said:**
>  FF fonts are now 100% better with all the fuzziness in the menu and the jaggies on the page gone.  
PS - It's fixed Opera as well.

---

### Post by dannymichel on 2007-06-14
> **TalkJesus said:**
> Found *somewhat* of a trick to rid the firefox mysterious enlarged font size and exaggerated boldness on some fonts, in this case verdana (it seems so anyway)

I added this to .fonts.conf file:

```

<match target="pattern">
            <test qual="any" name="family">
                    <string>Verdana</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Bitstream Vera Sans</string>
            </edit>
</match>
```However, still a little flaky. For example, I'm typing here in the forum inside this WYSIWYG editor, compared to Vista, the font size is about 2pt larger for some reason. I do not know how to tell firefox, or ubuntu to correct that. For the record, it was this way berfore I added the above code.

My current .fonts.conf file:

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<!-- Give all fonts light hinting and subpixel smoothing -->
<!--
<match target="font">
    <edit mode="assign" name="rgba">
        <const>rgb</const>
    </edit>
    <edit mode="assign" name="hinting">
        <bool>true</bool>
    </edit>
    <edit mode="assign" name="hintstyle">
        <const>hintslight</const>
    </edit>
    <edit mode="assign" name="antialias">
        <bool>true</bool>
    </edit>
</match>
-->

<!--
     <match target="font">
        <test qual="all" name="rgba"><const>unknown</const></test>
           <edit name="rgba" mode="assign"><const>rgb</const></edit>
     </match>
-->

<!--  Do not smooth Fixedsys  -->
<match target="font">
    <test name="family">
        <string>FixedsysTTF</string>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<!--  Do not smooth Tahoma 8pt and under  -->
<match target="font">
    <test name="family">
        <string>Tahoma</string>
    </test>
    <test compare="less" name="size" qual="any">
        <double>9</double>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<!--  Do not smooth Times New Roman or Courier New for 12pt and under  -->
<match target="font">
    <test name="family">
        <string>Times New Roman</string>
    </test>
    <test compare="less" name="size" qual="any">
        <double>13</double>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<match target="font">
    <test name="family">
        <string>Courier</string>
        <string>Courier New</string>
        <string>Courier 10 Pitch</string>
    </test>
    <test compare="less" name="size" qual="any">
        <double>11</double>
    </test>
    <edit name="antialias">
        <bool>false</bool>
    </edit>
</match>

<!-- Do not autohint Courier New, Fixedsys, Tahoma, or Times New Roman -->
<match target="font">
    <test name="family">
        <string>Courier New</string>
        <string>Times New Roman</string>
        <string>Tahoma</string>
        <string>FixedsysTTF</string>
    </test>
    <edit mode="assign" name="hintstyle">
        <const>hintslight</const>
    </edit>
    <edit mode="assign" name="autohint">
        <bool>false</bool>
    </edit>
</match>

<match target="pattern">
            <test qual="any" name="family">
                    <string>Bitstream Vera Sans</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
    <match target="pattern">
            <test qual="any" name="family">
                    <string>Helvetica</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Arial</string>
            </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Palatino</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Georgia</string>
            </edit>
</match>
<match target="pattern">
            <test qual="any" name="family">
                    <string>Verdana</string>
            </test>
            <edit name="family" mode="assign">
                    <string>Bitstream Vera Sans</string>
            </edit>
</match>
</fontconfig>
```

On a side note, I'd rather see the sites' original font settings than forcing ubuntu to use an alternative.

WOW
I used your fonts.conf and everything in Firefox is great, but look at the underline on VBulletin.com forums.

---

### Post by crimesaucer on 2007-06-14
> **trmiv said:**
> That's exactly how mine is set. Also, the fonts look much better on the desktop and in menus then in Firefox.  Firefox seems to render the fonts differently for some reason.

I use hinting, as well as sub-pixel hinting and anti-aliasing with my settings set to Slight and RGB in my xubuntu, and my fonts are very beautiful.

I also use this for my fonts in my mousepad: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_smooth_fonts](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_smooth_fonts)

---

