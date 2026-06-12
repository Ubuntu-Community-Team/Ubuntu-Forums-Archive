---
title: "Display Overlaps including on a fictitious extended display"
date: 2017-07-13
forum: Desktop Environments
---

### Post by thatsmyboy on 2017-07-13
It's been a couple years since I [thread=2236871]last had this issue[/thread], but I'm running into problems with my monitor again. The ONLY display is a Polaroid 22" class HDTV (Model#: [TLAC-02255]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=9134866")) that is connected to my ZBOX SD. I believe what is happening is that my computer (which has two video outputs VGA and HDMI) is connecting to the display via VGA, but seems to think there are two connected monitors and that the visible display is the extended portion of the screen (no programs, no dash, no buttons or menus of any kind). I can sometimes see that Ubuntu is spawning errors, but they don't stay on screen long enough for me to take note of them. 

The box specifications are [as follows]("http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=149867&SRCCODE=WEBLET03ORDER&cm_mmc=Email-_-WebletMain-_-WEBLET03ORDER-_-Deals"):
Zotac ZBOXSD-ID12-PLUS Barebone Mini-PC
Intel Atom D525 1.8GHz processor
4GB DDR3 Ram
500GB Toshiba [Hybrid Drive]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=8511352&Sku=ZOI-101759008")
Intel GMA 3150 Graphics, HDMI, WiFi

In an effort to troubleshoot this issue, I booted to a LiveUSB of Trusty (14.04) and EVEN THAT has problems with the display, but I managed to get a little bit further there. As you can see in screenshots linked below, the display shows two screens of different size overlaid on one another. After moving the displays in the Settings panel, I got to a reasonable setup, but I'm not sure how to port that back to my hard drive installation of Ubuntu. There may be some other intricacies I am skimming over, but at the moment any help would get me on my way.
[IMG]http://i.imgur.com/oVRTYDx.jpg[/IMG]
[http://imgur.com/a/B7xNr](http://imgur.com/a/B7xNr)


So in summary, I cannot use the graphical interface of my computer because for some reason unknown to me my display only shows the background, no buttons, no dash, no icons, no settings. Getting to the command line TTY1 by Ctrl-Alt-F1 works fine. I would like to rebuild or reset the display server parameters so that I only use one display via the VGA port. I can switch that to HDMI if I must, but the solution seems like it might be cleaner through VGA.

---

### Post by thatsmyboy on 2017-07-18
The problem I describe is replicated almost exactly by [another poster on AskUbuntu]("https://askubuntu.com/questions/881608/ubuntu-16-10-with-multiple-graphics-issues-on-atom-intel"). I will follow the recommendations given there and get back if the problem is solved.

---

### Post by thatsmyboy on 2017-08-01
Just for starters, none of the above recommendations worked, so unfortunately it wasn't as easy as that. I was able to use failsafeX mode by booting into recovery mode (hold left shift when booting up). I used xrandr but found unsatisfying results (it's in recovery mode after all). ```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768       0.00* 
   800x600        0.00  
   640x480        0.00  

```
I have a modeline that I got from cvt and I will try to employ that plus X -configure to create an xorg.conf to store away and hopefully put this problem behind me. more updates upon successful conclusion

---

### Post by deadflowr on 2017-08-03
You might get a good understanding of what is what by looking at the monitors.xml file
```
cat ~/.config/monitors.xml
```

---

### Post by thatsmyboy on 2017-08-27
Thanks for trying, No such file or directory. I have tried several iterations of editing and placing a xorg.conf file in /etc/X11/xorg.conf but i haven't gotten the syntax down quite yet. It keeps recognizing something is wrong with the file and defaulting to bad settings. 
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Polaroid 22in"
	VendorName   "Polaroid"
	ModelName    "TLAC-02255"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "kmsdev"             	# <str>
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "PageFlip"           	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card0"
	Driver      "modesetting"
	BusID       "PCI:0:2:1"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by SunnyDaze on 2017-08-30
If the numbers in **CompizConfig Setting Manager** don't represent your monitor dimensions, offsets, and rotations, and the numbers don't match the numbers in your **~/.config/monitors.xml** file, Compiz might draw and stretch windows into other areas, and possibly respond to mouse clicks in the different areas.

You might have too physically configure Compiz and the monitors.xml file yourself, so they each have the same sizes and offsets.  Most of the time, Compiz will not autodetect this correctly.

First step is to bring your setup down to one monitor.  Then install and open **CompizConfig Settings Manager**.  Go to **General Options->Display Settings**.  There you un-check **Detect Outputs**.  Then you type in all your monitor resolutions, and offsets, one monitor at a time, starting with the upper-left monitor.

I am going to give you my extreme 4-monitor example, so hopefully you get a better example of what needs to happen, and can figure out how to apply it to a two, or three monitor situation.

My 4 monitors looks like this:

 ```
         1080         1920         1080
       ________ _______________ _________ 
      |        | 1             |         |
    1 |        | 0             |         | 1
    9 |        | 8   2nd       |         | 9
    2 |  1st   | 0             |   4th   | 2
    0 |        |_______________|         | 0
      |        | 1             |         |
      |        | 0             |         |
      |________| 8   3rd       |_________|
               | 0             |
               |_______________|

```

Which means I set them up like this in **CompizConfig Settings Manager -> General Options -> Displays Settings**.

    1080x1920+0+0        = (1080 wide, 1920 tall, w/offset from upper-left of x=0    too the right, y=0    down)
    1920x1080+1080+0     = (1920 wide, 1080 tall, w/offset from upper-left of x=1080 too the right, y=0    down)
    1920x1080+1080+1080  = (1920 wide, 1080 tall, w/offset from upper-left of x=1080 too the right, y=1080 down)
    1080x1920+3000+0     = (1080 wide, 1920 tall, w/offset from upper-left of x=3000 too the right, y=0    down)

Then you need to go into **System Settings->Display** and drag the monitor screens around and rotate them to match what you set up in **CCSM**.  The **Display** GUI is very buggy.  You have to make sure the screen you are dragging around is touching another or it won't move.  So don't leave a screen hanging off by itself.  Once you have them rotated and arrange to match the **CCSM** settings, click **Apply**.  This will write the **~/.config/monitors.xml** file with your configuration.  This should put you in a working state, which won't be overwritten next time you log in.  Back up the monitors.xml file!

If you unplug or turn off a monitor, things will probably go haywire, so make sure you have a backup of the working monitors.xml file, and know how to go to a tty terminal to restore the file. (Hit CTRL-ALT plus any one of the F1 through F6 keys)

---

### Post by thatsmyboy on 2017-09-27
I tried your suggestion and it looked like it was about to work, but no love yet. I also went back to the LiveUSB (Xenial this time) and got a working monitors.xml from that which I imported into my installation - still the same behavior. 

```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="LVDS1">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
      </output>
      <output name="VGA1">
          <vendor>TAL</vendor>
          <product>0x8800</product>
          <serial>0x00000000</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="VIRTUAL1">
      </output>
  </configuration>
</monitors>
```

---

### Post by thatsmyboy on 2017-11-28
Tried my luck with another monitor and the problem just vanished! I'll still investigate, but this is promising.

---

