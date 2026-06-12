---
title: "UT2k4 Demo with twinview....half on left, half on right screen."
date: 2006-06-24
forum: Gaming &amp; Leisure
---

### Post by electrosoccertux on 2006-06-24
Its kinda hard to [RIGHT]play UT2k4[/RIGHT]   
when everything [RIGHT]is split between two [/RIGHT]
screens. Here's [RIGHT]my xorg.conf:[/RIGHT]

```
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
    Identifier     "NEC E700"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Driver         "nvidia"

    Option	"TwinView"	"yes"
    Option "MetaModes" 	"1600x1200,1600x1200;1280x960,1280x960;1024x768,1024x768;800x600,800x600"

    Option "TwinViewOrientation"	"CRT-0 LeftOf CRT-1"
    Option "RenderAccel" "true"
#####################################
####Enable below for TV-out
#   Option "TwinView" "true"
#   Option "TwinViewOrientation" "Clone"
#   Option "TVOutFormat" "S-VIDEO"
#   Option "TVStandard" "NTSC-M"
#   Option "SecondMonitorHorizSync" "30-50"
#   Option "SecondMonitorVertRefresh" "60"
#   Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;512x384,512x384"








EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Monitor        "NEC E700"
    DefaultDepth    24
    Option         "RenderAccel" "false"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


```

[CENTER]Help?[/CENTER]

---

### Post by monkey4 on 2006-06-24
I've always wondered what UT would look like across multiple screens. Got any pictures of this setup in action?

---

### Post by autocrosser on 2006-06-25
I just tried it with TwinView--I'm using two fairly thin frame LCD's & in the Video prefs there is 1600x1024!!!! Just say I want my frames thinner!! As soon as I get my new computer (Pent D 3.2) I'll try to get some good shots:)

---

### Post by electrosoccertux on 2006-06-25
OK I checked around some and it appears if you add "1600x1200,NULL" after "1600x1200,1600x1200;" in your Metamodes option, the driver uses the second setting "1600x1200,NULL" and the second screen gets turned off.

---

### Post by autocrosser on 2006-06-25
I tried that & can't seem to get it to work--I've got two 1280x1024 monitors--my Metamodes look like--

Option      "MetaModes"     "1280x1024-1280x1024 1280x1024,NULL 1024x768-1024x768 800x600-800x600"

I'll try different ways to express it--but it won't work the way I have it now---

---

### Post by autocrosser on 2006-06-25
OK--I tried it with my MetaModes looking like--
Option      "MetaModes"     "1280x1024,1280x1024;1280x1024,NULL;1024x768,1024x768;800x600,800x600"

And the Xranr Applet gives me--2560x1024-1280x1024-2048x768-1600x600

So, that works--I went to one monitor & started UT2k4 & got a seconds worth of splash screen & it bugged out--went back to 2560x1024 & it started--I need to do more checking with starting it in the terminal to see what the problem is:???:--but it seems to work.

---

### Post by autocrosser on 2006-06-25
OK--I'm ready to laugh at myself:rolleyes:

I started the game with 2560x1024 for my TwinView settings & was looking thru the display sizes in the video preferences----went to 1280x1024 &-----wait for it-----it all came up on my LEFT SCREEN--LOL--went back to 1600x1200 & it split between the two......

So I'm here to say that the programmers are smarter that me](*,)--I would guess that you would need to select the mode(s) in your MetaModes (like the 1280x1024,NULL)--but the game will auto select & your screens will return back to the prior settings (I was running UT2k4 in Mac OSX before & I would guess that is where the code came from)when the game closes--I went back to the 1600x1200 setting before I quit the game just to be sure:???: 

Played a good round to warm up in Antalus in 1280x1024--felt good!!!

For all you that have only played in Windoze--when we wanted to add maps--etc to the game--in macxosx you would just open the app & put everything where it needed to go--I'm going to load up my stuff I've saved & will say if it works the way I think it well.

---

### Post by autocrosser on 2006-06-26
OK--I know this is offtopic, but---I have UT2k4 on a external drive (the Mac OSX version) & I loaded all my maps-textures-mods from the .app to my new install in Ubuntu.
 
How? It's simple--I opened a terminal & did "sudo nautilus"--opened a nautilus root window & then just did a drag/drop from the .app to my install in /usr/local/games/ut2004--easy. And because the files are in the same format for Windoze-Mac-Linux---when I started the game all my mods were there. I just need to see if the .ini file that has my personal prefs from OSX will work in Linux..........
 
(I did take some time adding stuff--I only added files that my Linux install didn't have)

---

